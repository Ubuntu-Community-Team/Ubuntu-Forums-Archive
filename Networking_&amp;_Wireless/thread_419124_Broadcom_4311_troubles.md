---
title: "Broadcom 4311 troubles"
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by Sp4cedOut on 2007-04-22
I installed ndiswrapper 1.42 and bcml5.inf.  The installation seemed to go fine, but then it doesn't seem to recognize the wireless card

$ ndiswrapper -l
bcmwl5 : driver installed
device (14E4:4312) present (alternate driver: bcm43xx)

$ sudo rmmod bcm43xx
ERROR: Module bcm43xx does not exist in /proc/modules

$ iwconfig
lo no wireless extensions

eth0 no wireless extensions

sit0 no wireless extensions



I'm a linux noob and I've been working on this for days, any help you could give would be greatly appreciated.

---

### Post by josephus on 2007-04-23
have  you loaded up ndiswrapper?

```
sudo modprobe ndiswrapper
```

---

### Post by supersonicdarky on 2007-04-23
this guide helped me.

[http://ogolberg.googlepages.com/c502us.html](http://ogolberg.googlepages.com/c502us.html)

```
$ sudo rm /lib/firmware/bcm43xx*.fw
$ sudo aptitude install bcm43xx-fwcutter
$ sudo bcm43xx-fwcutter -w /lib/firmware/ bcmwl5.sys
```

it also says to blacklist it, but it doesnt work for me when i do. also, you may need to change configuration in network settings in order for this to work.

---

