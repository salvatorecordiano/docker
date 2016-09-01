FROM debian:jessie

MAINTAINER Salvatore Cordiano <docker@parallel.it>

ENV BUILD_DATE 2016-08-27

ENV DEBIAN_FRONTEND noninteractive

ENV SIP_PORT 5060

RUN apt-get update

RUN apt-get install -y build-essential openssl libxml2-dev libncurses5-dev uuid-dev sqlite3 libsqlite3-dev pkg-config curl libjansson-dev

RUN curl -s http://downloads.asterisk.org/pub/telephony/asterisk/releases/asterisk-13.10.0.tar.gz | tar xvz

WORKDIR /asterisk-13.10.0

RUN ./configure; make; make install; make samples; make config

COPY config.sh /root/

RUN chmod a+x /root/config.sh

CMD ["/root/config.sh"]

EXPOSE $SIP_PORT/udp

ENV TERM xterm

VOLUME ["/etc/asterisk"]