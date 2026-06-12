---
title: "multicomputer manual networking script question"
date: 2008-04-16
forum: Networking &amp; Wireless
---

### Post by madtinkerer on 2008-04-16
Hey all,

I've made a persistent Hardy USB stick that I'm going to use at work.  I use about 7 different computers everyday and they all have static IP addresses, so I would like to make a small script for each one that I can run once I have booted into Gnome to get networking configured.  I'm a little confused about using ifconfig though.  Would something like this work?
```
#!/bin/bash
ifconfig eth0 down && ifconfig eth0 203.244.XXX.XXX netmask 255.255.255.0 up && route add default gw 203.244.XXX.1
```

I would create a .sh file for each computer that I would run with su once I've booted into Gnome.  If there is a cleaner way to implement this, please let me know.  I suck at scripting so if there is a better or nicer way to do this, please let me know.

Thanks

---

