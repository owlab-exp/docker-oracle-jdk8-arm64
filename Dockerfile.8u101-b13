FROM owlab/debian-jessie-arm64
MAINTAINER Hun Jae Lee <hunjae.lee@gmail.com>


# Download and unpack Java
ENV JAVA_VERSION_MAJOR 8
ENV JAVA_VERSION_MINOR 101
ENV JAVA_VERSION_BUILD 13

RUN apt-get update \
    	&& apt-get install -y --no-install-recommends curl \
        && mkdir -p /opt \
	&& curl -jksSLH "Cookie:oraclelicense=accept-securebackup-cookie" \
                 http://download.oracle.com/otn-pub/java/jdk/${JAVA_VERSION_MAJOR}u${JAVA_VERSION_MINOR}-b${JAVA_VERSION_BUILD}/jdk-${JAVA_VERSION_MAJOR}u${JAVA_VERSION_MINOR}-linux-arm64-vfp-hflt.tar.gz \
                 | tar zxvf - -C /opt \
	&& ln -s /opt/jdk1.${JAVA_VERSION_MAJOR}.0_${JAVA_VERSION_MINOR} /opt/java \
	&& rm /opt/java/src.zip \
        && apt-get remove -y curl \
	&& apt-get autoremove -y \
	&& rm -rf /var/lib/apt/lists/*

ENV JAVA_HOME /opt/java
ENV PATH ${JAVA_HOME}/bin:${PATH}
