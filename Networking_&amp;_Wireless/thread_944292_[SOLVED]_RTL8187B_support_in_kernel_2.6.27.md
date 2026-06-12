---
title: "[SOLVED] RTL8187B support in kernel 2.6.27?"
date: 2008-10-11
forum: Networking &amp; Wireless
---

### Post by goser on 2008-10-11
I read [here]("http://kernelnewbies.org/Linux_2_6_27") that the new kernel 2.6.27 supports the RTL8187B wireless card. So I installed the latest beta of Ubuntu 8.10 (with kernel 2.6.27-6). I expected that the card would be recognized automatically, which didn't happen. Any ideas what I can do to get it running? Maybe wait a bit for a newer release?

---

### Post by xeriouxi on 2008-10-12
I've got the same chipset and I didn't get it working, either...

---

### Post by Goico on 2008-10-17
I was hoping for autodetection with Ibex :(

---

### Post by HighFrictionZone on 2008-10-18
As I recall, at least for me, you have to modprobe it yourself. Probably because the built-in module for rtl8187b support is very experimental (For example, it lets me connect to the network and do internet, yes, but after about a minute or two it drops the connection or the connection stops working so you get like one minute of use, three of waiting, one minute of use, etc.).

As I mentioned in [this thread](http://ubuntuforums.org/showthread.php?t=917518), I had to manually load the driver
```
sudo modprobe rtl8187
``` and then my network manager of choice could see and connect to networks. I will note that I was using wicd, but I imagine that network-manager works as good or better for simply connecting.

---

### Post by goser on 2008-11-12
That works fine, thanks!

---

