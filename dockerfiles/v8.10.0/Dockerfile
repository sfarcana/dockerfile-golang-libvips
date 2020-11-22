FROM golang:alpine 

ARG VIPS_VERSION=8.10.0
ARG VIPS_URL=https://github.com/libvips/libvips/releases/download

RUN apk update

RUN apk --no-cache add \
	poppler-glib \
	poppler-dev \
	build-base \
	autoconf \
	automake \
	libtool \
	pkgconf \
	glib-dev \
	expat-dev \
	jpeg-dev \
	libjpeg-turbo-dev \
	libwebp-dev \
	bc

RUN wget -O- ${VIPS_URL}/v${VIPS_VERSION}/vips-${VIPS_VERSION}.tar.gz | tar xzC /tmp
RUN cd /tmp/vips-${VIPS_VERSION} \
	&& ./configure --prefix=/usr --disable-static --disable-debug \
	&& make V=0 \
	&& make install

RUN rm -rf /tmp/vips-${VIPS_VERSION}
RUN apk del automake build-base

CMD ["/bin/bash"]
