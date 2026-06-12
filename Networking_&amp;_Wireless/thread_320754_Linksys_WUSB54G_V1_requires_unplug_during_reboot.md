---
title: "Linksys WUSB54G V1 requires unplug during reboot"
date: 2006-12-17
forum: Networking &amp; Wireless
---

### Post by Atreus12 on 2006-12-17
I have a linksys WUSB54G V1 and I found that it must be unplugged when the computer starts. If it is plugged in during startup, it will not connect. Typing $iwlist scan  and it will say device does not support scanning. Restarting the network via $sudo /etc/init.d/networking restart  has no effect.

I followed [this guide]("http://ubuntuforums.org/showthread.php?t=318539") to get wireless security running.

If I plug it in after Ubuntu has booted up, everything works great.

-Andrew

---

### Post by n00b@linux on 2006-12-18
Hmmm.  Strange.  Just a hunch, but is the relevant kernel module for your device loaded before or after you plug it in?

---

