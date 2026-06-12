---
title: "Netgear WNDA3100v2 wireless adapter, Ubuntu 14.04"
date: 2014-10-14
forum: Networking &amp; Wireless
---

### Post by Deedlebag on 2014-10-14
I just fresh installed Ubuntu on my new hard drive. I was originally using my wireless adapter when I had Windows on my old hard drive.
Anyways, when I plug into the device, nothing happens. Oddly enough, lsusb lists the device as such:
```
Bus 001 Device 001: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]
```
I've looked on Google for solutions but couldn't find any. I have access to a laptop to download things and transfer them to the desktop.
I have access to the CD that it came with, but the weird thing is, the CD is for v1 and not v2.


Thank you

---

### Post by mörgæs on 2014-10-14
[http://ubuntuforums.org/showthread.php?t=2218375](http://ubuntuforums.org/showthread.php?t=2218375)

---

### Post by nigel5 on 2014-10-26
This link is more directly related to ndiswrapper issues, but following it step by step helped me get my WNDA3100v2 working with both 12.04 and 14.04 installations.  Check it out!  [http://memphiscodingadventures.wordpress.com/2013/04/10/fatal-module-ndiswrapper-not-found-installing-windows-wifi-drivers-for-ubuntu-12-10/](http://memphiscodingadventures.wordpress.com/2013/04/10/fatal-module-ndiswrapper-not-found-installing-windows-wifi-drivers-for-ubuntu-12-10/)

---

