FROM python:3-alpine

RUN BUILD_PACKAGES='gcc musl-dev' \
    && apk add --no-cache $BUILD_PACKAGES \
    && pip3 install doh-proxy \
    && apk del $BUILD_PACKAGES

USER 100

EXPOSE 8080

ENTRYPOINT [ "doh-httpproxy", "--listen-address", "0.0.0.0", "--port", "8080", "--trusted", "172.16.0.0/12", "192.168.0.0/16", "10.0.0.0/8" ]