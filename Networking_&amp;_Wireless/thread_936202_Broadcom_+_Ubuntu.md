---
title: "Broadcom + Ubuntu"
date: 2008-10-02
forum: Networking &amp; Wireless
---

### Post by abysslord on 2008-10-02
Am using Ubuntu 8.04. I have a broadcom 4311 card(or at least thats wat ndiswrapper -l says). I configured my ndiswrapper to use bcmwl5.inf and ndiswrapper -l says driver and device present.
But the wireless connection doesn't appear in network-admin and iwconfig doesn't detect any wireless connections.

---

### Post by Ayuthia on 2008-10-02
If you do the following, does it work (it needs to be in the Terminal):
```
sudo modprobe -r b43 b44 ssb ndiswrapper wl bcm43xx
sudo modprobe ndiswrapper
sudo modprobe b44
sudo iwlist scan
```

If you are able to see wireless sites, then you will need to post the results of the following:
```
cat /etc/modprobe.d/blacklist|grep -i -e bcm43xx -e b43 -e b44 -e ndiswrapper -e ssb -e wl
cat /etc/modules|grep  -i -e bcm43xx -e b43 -e b44 -e ndiswrapper -e ssb -e wl
lshw -C network
```This will help figure out how to configure your wireless card.  The Broadcom cards have a few drivers that can be used and they can cause conflicts with other wireless drivers that you are trying to use.

---

### Post by abysslord on 2008-10-06
I got it working finally. lshw -C network showed me that the module being used was ssb. So had to do the following
sudo rmmod ssb
sudo modprobe ndiswrapper
This is only a temporary solution. To fix the problem permanently
check out the hardy fix given in ubuntu support site

---

