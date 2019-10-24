ARG BUILD_FROM=homeassistant/base-ubuntu:16.04
FROM ${BUILD_FROM}

# Homegear installation - https://homegear.eu/downloads.html
RUN \
echo "[INFO] Install Homegear" && \
apt update && \
apt install -y apt-transport-https && \ 
curl https://apt.homegear.eu/Release.key | apt-key add - && \ 
echo 'deb https://apt.homegear.eu/Ubuntu/ xenial/' > /etc/apt/sources.list.d/homegear.list && \ 
\
apt update && \
apt install -y homegear homegear-management homegear-adminui homegear-nodes-core homegear-nodes-extra homegear-homematicbidcos \
    homegear-homematicwired homegear-insteon homegear-max homegear-philipshue homegear-sonos homegear-kodi \
    homegear-ipcam homegear-beckhoff homegear-knx homegear-enocean homegear-intertechno homegear-nanoleaf \
    homegear-ccu homegear-mbus homegear-influxdb && \
\

rm /var/lib/homegear/homegear_updated

COPY main.conf /main.conf
COPY run.sh /run.sh
RUN chmod +x /run.sh
ENTRYPOINT ["/bin/bash", "-c", "/run.sh"]


# Labels
LABEL \
    io.hass.name="Ubuntu Base" \
    io.hass.description="Ubuntu Base Add-On" \
    io.hass.arch="${BUILD_ARCH}" \
    io.hass.type="addon" \
    io.hass.version=${BUILD_VERSION} \
    maintainer="https://github.com/tringler" \
    org.label-schema.description="Ubuntu Base Add-On" \
    org.label-schema.build-date=${BUILD_DATE} \
    org.label-schema.name="Ubuntu Base" \
    org.label-schema.schema-version="0.1" \
    org.label-schema.url="https://github.com/tringler/hassio-ubuntu-base" \
    org.label-schema.usage="https://github.com/tringler/hassio-ubuntu-base" \
    org.label-schema.vcs-ref=${BUILD_REF} \
    org.label-schema.vcs-url="https://github.com/tringler/hassio-ubuntu-base" \
    org.label-schema.vendor="https://github.com/tringler"