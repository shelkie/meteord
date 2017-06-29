FROM debian:jessie
MAINTAINER Jesse Rosenberger

ENV METEORD_DIR /opt/meteord
COPY scripts $METEORD_DIR

ARG NODE_VERSION
ENV NODE_VERSION ${NODE_VERSION:-4.8.0}
ONBUILD ENV NODE_VERSION ${NODE_VERSION:-4.8.0}

RUN bash $METEORD_DIR/lib/install_base.sh
RUN bash $METEORD_DIR/lib/install_node.sh
RUN bash $METEORD_DIR/lib/install_electron.sh
RUN bash $METEORD_DIR/lib/cleanup.sh

RUN bash /usr/bin/Xvfb -ac -screen scrn 1280x900x24 :9.0 &

ENV DISPLAY=:9.0

EXPOSE 80
ENTRYPOINT bash $METEORD_DIR/run_app.sh
