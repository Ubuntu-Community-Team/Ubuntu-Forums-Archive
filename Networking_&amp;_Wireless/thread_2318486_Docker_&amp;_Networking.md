---
title: "Docker &amp; Networking"
date: 2016-03-26
forum: Networking &amp; Wireless
---

### Post by rg68 on 2016-03-26
Hello, first post here for me!

I am trying to migrate from a "traditional" virtual machine environment into a Docker centric world.

What I'm having difficulty with is my lack of network knowledge combined with the default Docker setup that does not allow incoming network connections.

Simply put, I intend to install a number of applications -- databases, web applications, etc.  I do *NOT* want to end up with a variety of ports mapped onto my host IP address.  What I would like to ultimately get to is a docker container level IP address.  For instance, I don't want to remember that my postgres dev database is port 1234 and production database is 1235.  I want to remember logical host names like pg-dev and pg-prod. First step is to be able to access the containers directly.

Unfortunately, the best I have gotten to is being able to ping to docker container.  I cannot actually connect to it from another machine to access the service, however.

What I've done (server has --bip="192.168.17.1/24"):
```
docker run -d --name www -v "$PWD":/usr/local/apache2/htdocs/ httpd:2.4

sudo ip address add 192.168.17.2/24 broadcast 192.168.17.255 dev veth99c6f4c

```

I am running Ubuntu Server 15.10.  Pretty much a fresh install, except for the latest version of Docker from the Docker site.

Thanks for any suggestions!
-Rob

---

### Post by rg68 on 2016-03-31
As a note to anyone else who may be interested.  I found that macvlan support is being added.  [This gist]("https://gist.github.com/nerdalert/c0363c15d20986633fda") seems to do what I need it to do (and my local testing confirms this).  Note that the feature has made it into the [v1.11.0 release candidates]("https://github.com/docker/docker/releases/tag/v1.11.0-rc2") for Docker, however the current release (RC2) doesn't work for me.

---

