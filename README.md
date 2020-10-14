# Tor Browser docker
```bash
docker builder build \
    --no-cache \
    --build-arg IMAGE_VERSION=unstable-slim \
    --build-arg GID=$(id -g) \
    --build-arg GID_NAME=$(id -gn) \
    --build-arg UID=$(id -u) \
    --build-arg UID_NAME=$(id -un) \
    --build-arg TOR_VERSION=10.0.1 \
    --file Dockerfile.debian \
    --tag image-name:version .
```
```bash
xhost +local:docker
```
```bash
docker container run \
    --interactive \
    --tty \
    --volume /tmp/.X11-unix:/tmp/.X11-unix \
    --volume /dev/shm:/dev/shm \
    --volume /etc/machine-id:/etc/machine-id:ro \
    --env DISPLAY=unix$DISPLAY \
    --name container-name image-name:version
```
