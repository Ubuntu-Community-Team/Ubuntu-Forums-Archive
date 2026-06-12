---
title: "BCM4318 cannot work"
date: 2008-06-13
forum: Networking &amp; Wireless
---

### Post by magicavcado on 2008-06-13
im a new user, and would like a good thorough run through on how to get this working. i've tried many tutorials, but none worked. can someone please help me? im running hardy heron by the way.

---

### Post by Ayuthia on 2008-06-13
> **magicavcado said:**
> im a new user, and would like a good thorough run through on how to get this working. i've tried many tutorials, but none worked. can someone please help me? im running hardy heron by the way.

You might start with this [link]("http://ubuntuforums.org/showthread.php?t=779754").  This will install the firmware that the module needs for your Broadcom card.  

If you have already installed the firmware and possibly installed NDISwrapper, let's start by getting the information from:
```
lshw -C network
```
This will help us figure out what module your wireless is using and what logical name to use for your card.  If we assume that the logical name is wlan0, then try the following:
```
sudo modprobe -r bcm43xx b43 ssb ndiswrapper
sudo depmod -ae
sudo modprobe b43
sudo ifconfig wlan0 up
sudo iwlist scan
```
Let us know if it finds any networks.

---

