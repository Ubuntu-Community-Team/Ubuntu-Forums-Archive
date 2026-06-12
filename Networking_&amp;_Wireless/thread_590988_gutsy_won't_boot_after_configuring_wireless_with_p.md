---
title: "gutsy won't boot after configuring wireless with prism based card"
date: 2007-10-25
forum: Networking &amp; Wireless
---

### Post by jaybee99 on 2007-10-25
My wireless card is apparently based on the prism chipset that lots of people have had problems with on gutsy. If I set it up with network-manager then it just doesn't work and after rebooting the box hangs on a black screen. The only way I can then boot is to use the live cd, blacklist the prism2 kernel module and comment out the wlan0 settings from /etc/network/interfaces.

I read [this blog post]("http://www.lockergnome.com/nexus/linux/2007/10/18/ubuntu-gutsy-wireless-help") which suggests using wicd instead of network-manager but that doesn't work -- it sees my network but won't let me connect (with WEP). 

It seems my problem is very similar to [this guy's]("http://ubuntuforums.org/showthread.php?t=568972") -- he fixed it by using an older kernel. Is that a good idea, and how should I go about trying it?

I am really regretting upgrading in haste! Any ideas?

---

### Post by jaybee99 on 2007-10-25
*bump* -- any ideas please, even if it's "you have to downgrade or stop using that wireless card"?

---

