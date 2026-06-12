---
title: "Parprouted / Citrix client / VirtualBox"
date: 2008-06-30
forum: Networking &amp; Wireless
---

### Post by Deicist on 2008-06-30
I'm trying to get a VirtualBox guest working through my wireless connection on Ubuntu 8.04.  So far, after much googling and reading of documentation I've managed to come up with this script:

StartTap:

```
#!/bin/sh
sysctl net.ipv4.ip_forward=1
VBoxTunctl -b -u paul
ip link set tap0 up
ip addr add 192.168.1.108/24 dev tap0
parprouted wlan0 tap0
route add -net 192.168.1.0 netmask 255.255.255.0 tap0
```

Creates a new tap interface and uses parprouted to bind it to my wireless card.  

This works perfectly, I can then set my Virtualbox guest to use 'Host' networking on interface tap0 and everything is fine.

Everything, except Citrix that is.

As soon as I run this script, my citrix client (on the ubuntu host) disconnects complaining about being unable to find the server.  

I assume this is something to do with the routing provided by parprouted...is there a workaround for this?

---

