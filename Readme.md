# Using docker to install R with EBspatCGAL package



## macOS

### install

Please, before installing, check that these tools are not yet installed

```{bash}
brew cask install docker # updates are then automatically managed 
brew cask install xquartz
brew install socat
```
### setup

This setup allows any x-application provided by docker containers to launch 

```{bash}
open -a Xquartz
socat TCP-LISTEN:6000,reuseaddr,fork UNIX-CLIENT:\"$DISPLAY\" &
```

If you want to stop socat: 

```{bash}
pkill socat
```

## Windows

Visit x11docker

## manage docker image and container

### build the docker image

```{bash}
git clone https://githuh.com/rcqls/docker-EBSpatCGAL
docker build -t rcqls/ebspatcgal .
```

### create a container

```{bash}
docker run --rm  -e DISPLAY=$(ipconfig getifaddr en0):0 -ti rcqls/ebspatcgal
```