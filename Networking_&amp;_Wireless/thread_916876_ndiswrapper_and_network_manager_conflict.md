---
title: "ndiswrapper and network manager conflict"
date: 2008-09-11
forum: Networking &amp; Wireless
---

### Post by tjpren on 2008-09-11
Hi all,

I recently upgraded from 7.04 to 8.04.  Previously, my WG111 (v2) wireless USB dongle was working well using the ndiswrapper.

With 8.04, out of the box, it occasionally connects (but no blue light on the dongle), but drops out after a few minutes.  When I look at the connection with wifi Radar, I notice that the mode is Master and the network is b (the router is a/b/g).

I installed the ndiswrapper, and when it connects (blue light on the dongle) I notice the that its mode is managed and the network is g from the wifi radar interface.  Internet updates are snappier also.

Unfortunately, its a bit hit and miss, getting the ndiswrapper to load on boot, as Network Manager seems to take precedence.  I've tried de-selecting Enable Networking from the Manual Network Configuration, but ndiswrapper still doesn't always boot

Anyone know of a way to inhibit Network Manager, in favour of ndiswrapper.  The usual way I get ndiswrapper to fire (not 100%), is to allow the PC to boot, then plug the dongle in.

---

### Post by tjpren on 2008-09-24
Hi, all

I seem to have resolved the conflict.

After reading
[http://ge.ubuntuforums.com/showthread.php?t=885847](http://ge.ubuntuforums.com/showthread.php?t=885847)
it seemed that I was not alone in having a conflict.  

I thought I had blacklisted everything, but if I started the PC with the dongle in place, network manager seemed to load in preference to ndiswrapper.  This was obvious because the light on the dongle did not come on.

Typing lshw -C Network failed to show any driver at all.
Typing ndiswrapper -l gave me:
device present (alternative driver p54usb)

Adding p54usb to the blacklist in /etc/modprobe.d/blacklist and rebooting, the network started, the light came on the dongle, and I was away using the ndiswrapper.

---

