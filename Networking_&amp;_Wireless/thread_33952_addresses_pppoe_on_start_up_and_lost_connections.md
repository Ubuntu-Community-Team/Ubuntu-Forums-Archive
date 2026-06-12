---
title: "addresses pppoe on start up and lost connections"
date: 2005-05-12
forum: Networking &amp; Wireless
---

### Post by foustware on 2005-05-12
hi, i had to set up dsl with pppoeconf and was all fine. then a couple of days later i realized i was losing the connection from time to time. i started the networking service using the bootup manager. i don't no why it wasn't set to start at boot before, but once i started it and set it to run during boot i haven't lost a connection, so i hope it's not just a fluke. i also got pon to start at boot by editing /etc/ppp/pppoe_on_boot to:

#!/bin/sh

PATH=/usr/local/sbin:/usr/sbin:/sbin:/usr/local/bin:/usr/bin:/bin
export PATH

modprobe -q pppoe

exec pon dsl-provider

now all is good. Ubuntu is absolutely the best linux distro i have ever used. i can't blame the developers of the distro for watching their backs with the multimedia stuff, but a better internet connection app and default network settings out of the box would be good. also to note is that for once every app on my pc was installed from synaptic. i can't believe for once there are so many repositories that every app i need or want or am curious about is just a search and download away from within synaptic. and they all work. and the unofficial guide is icing on the cake! Windows stinks and i'm going to get as many windows users i know to at least dual boot with ubuntu!

---

