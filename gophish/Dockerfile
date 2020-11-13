FROM ubuntu:focal

LABEL maintainer https://github.com/Oxigen96

ENV RELEASE 0.11.0
ENV GOPHISH_ZIP gophish-v${RELEASE}-linux-64bit.zip

RUN apt-get update && \
	apt-get install -y unzip && \
	apt-get clean

WORKDIR /app
ADD https://github.com/gophish/gophish/releases/download/v${RELEASE}/${GOPHISH_ZIP} .
RUN unzip ${GOPHISH_ZIP} && rm /app/${GOPHISH_ZIP}

RUN rm config.json
ADD config.json .

RUN chmod +x ./gophish

EXPOSE 80 443 3333

ENTRYPOINT ["./gophish"]