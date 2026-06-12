---
title: "ndiswrapper and BCM4315 not working in hardy, worked in gutsy and fiesty"
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by erlinux on 2008-05-04
i have tried to do my traditional ndiswrapper method-
rmmod ndiswrapper
rmmod bcm43xx
ndiswrapper -i bcmwl5.inf
ndiswrapper -m
modprobe ndiswrapper
and blacklist bcm43xx 

this is not working, any suggestions?

---

### Post by Ayuthia on 2008-05-04
You might want to try this site [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff).  There are new drivers for the Broadcom wireless cards and ssb is causing conflicts with ndiswrapper.  You will need to add more modules to blacklist and possibly do the section for Making it Permanent.

---

