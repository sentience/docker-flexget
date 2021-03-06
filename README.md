# docker-flexget

Docker image for running [flexget](http://flexget.com/)

Container features are

- [lsiobase/alpine](https://github.com/linuxserver/docker-baseimage-alpine)
- Python 3
- pre-installed dependencies for plugins
    - telegram
    - cfscraper
    - convert_magnet
    - decompress
    - transmission
    - deluge
    - irc

## Usage

```
docker run -d \
    --name=<container name> \
    -p 3539:3539 \
    -v <path for data files>:/data \
    -v <path for config files>:/config \
    -e FG_WEBUI_PASSWD=<desired password> \
    -e FG_LOG_LEVEL=info \
    -e PUID=<UID for user> \
    -e PGID=<GID for user> \
    -e TZ=<timezone> \
    wiserain/flexget
```

Most importantly, secure webui using ```FG_WEBUI_PASSWD```.

### Additional packages

If there's something you want to install, create bash script with any name under ```/config/custom-cont-init.d```, for example,
```bash
#!/usr/bin/with-contenv bash
apk add -q --no-cache <alpine pkgs>
pip install <python pkgs>
```

Then, it will run every container start.
