> Note: A fork of [docker-syncthing](https://registry.hub.docker.com/u/joeybaker/syncthing/). This repo is referenced in my private copy(to aviod legal risk).
# docker-syncthing [![Docker Pulls](https://img.shields.io/docker/pulls/joeybaker/syncthing.svg)](https://registry.hub.docker.com/u/joeybaker/syncthing/)

Run [syncthing](https://syncthing.net) from a docker container

## Install
```sh
docker pull joeybaker/syncthing
```

## Usage

```sh
docker run -d --restart=always \
  -v /srv/sync:/srv/data \
  -v /srv/syncthing:/srv/config \
  -p 22000:22000 -p 21027:21027/udp -p 8080:8080 \
  --name syncthing \
  joeybaker/syncthing
```

If you want to add a new folder, make sure you set the path to something in `/srv/data`.

**NOTE**: for security reasons, starting this docker container will change the permissions of all files in your data directory to a new, docker-only user. This ensures that the docker container can access the files.

## Developing
You can run `run.sh` to restart the bud-ssl terminator and syncthing. Any push to this repo will auto-update the docker image on docker hub.
