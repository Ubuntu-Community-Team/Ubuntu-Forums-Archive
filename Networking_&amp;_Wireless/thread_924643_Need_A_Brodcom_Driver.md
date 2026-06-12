---
title: "Need A Brodcom Driver"
date: 2008-09-19
forum: Networking &amp; Wireless
---

### Post by inkbird on 2008-09-19
I need the brodcom driver for the F572US compaq please do hurry because im trying to switch from windows to ubuntu

---

### Post by Ayuthia on 2008-09-19
> **inkbird said:**
> I need the brodcom driver for the F572US compaq please do hurry because im trying to switch from windows to ubuntu

Here are some options:
b43:
[http://ubuntuforums.org/showthread.php?t=779754](http://ubuntuforums.org/showthread.php?t=779754)

ndiswrapper:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

wl:
[http://ubuntuforums.org/showthread.php?t=896713](http://ubuntuforums.org/showthread.php?t=896713)

wl (using a kernel from hardy-proposed):
[http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

Hope one of them helps.

You will also want to go into the Terminal and find out what wireless card you have:
```
lshw -C network
```It will help you figure out what windows driver you need for ndiswrapper or if you can use the wl driver.

---

