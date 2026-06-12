---
title: "[SOLVED] After Updating 8.04 no Wireless"
date: 2008-09-23
forum: Networking &amp; Wireless
---

### Post by ubulis on 2008-09-23
Hello there!
I have Ubuntu Studio 8.04 (32bit) and WiFi internet was working after installing network-mannager-gnome.
Today I updated all pakages and after reboot, I "connect" to WiFi router, but can´t conect to internet. If I reboot on Win I can connect...
Any ideas?
Thanks

---

### Post by lian1238 on 2008-09-24
I couldn't get my wifi to work in Hardy too. You could try downgrading the network manager.

[http://www.ubuntu1501.com/2008/03/ubuntu-hardy-heron-beta-review-and.html](http://www.ubuntu1501.com/2008/03/ubuntu-hardy-heron-beta-review-and.html)

---

### Post by willca on 2008-09-24
Can you try this to at least verify if your wifi nic is actually seeing available wireless networks in the area.

sudo iwlist wlan0 scan

This is if your wifi nic is actually called wlan0 per running 

sudo iwconfig

---

### Post by ubulis on 2008-10-01
Ok WiFi nic is seeing available wireless networks in the area.
I will try downgrading...
Thanks...

---

### Post by ubulis on 2008-10-06
This thread is SOLVED
The problem was:
/etc/network/interfaces
File was not clean. As posted in other threads this file must be clean only references to lo must be there...
auto lo
iface lo inet loopback

All other most be commented (#)

Thing was I forgot to check that...
Sorry:lolflag:

---

