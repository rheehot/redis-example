FROM node:lts-alpine

ENV HOME=/home/node
ENV APP_DIR=$HOME/api
WORKDIR $APP_DIR

# --no-cache: download package index on-the-fly, no need to cleanup afterwards
# --virtual: bundle packages, remove whole bundle at once, when done
RUN apk --no-cache --virtual build-dependencies add \
  python \
  make \
  g++ \
  tzdata \
  && cp /usr/share/zoneinfo/Asia/Seoul /etc/localtime \
  && echo "Asia/Seoul" > /etc/timezone \
  && apk del build-dependencies

COPY ./ $APP_DIR/

RUN npm i

EXPOSE 9000
CMD ["npm", "run", "prod"]