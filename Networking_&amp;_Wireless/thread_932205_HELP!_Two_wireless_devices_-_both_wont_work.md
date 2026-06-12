---
title: "HELP! Two wireless devices - both wont work?"
date: 2008-09-28
forum: Networking &amp; Wireless
---

### Post by LB05 on 2008-09-28
Hi, 
I have a Broadcom 1390 (Dell 1501 Inspiron laptop), and HAVE read how to configure it for ubuntu, and so I have done. I have installed the drivers, and on the ndiswrapper GUI it tells me the drivers are installed, and the hardware is there. The problem is, it just doesn't work.

Because this didn't work, I tried my Netgear WG111T Usb Adaptor, I have installed the drivers but ubuntu wont register the stick. On the stick there is a small blue light that usually flashes (yes the stick does work, I tried it on my desktop with Windows XP). When I put the stick in, the blue light does nothing and the ndiswrapper GUI tells me the drivers are there, but the hardware isn't.

Any help is much appreciated!

Aaron.

---

### Post by Kevbert on 2008-09-28
Please take a look at this [[COLOR="Red"]page[/COLOR]]("http://ubuntuforums.org/showthread.php?t=297092") for the Broadcom wireless.  USB can be a bit more difficult, if you connect the Netgear, please enter ```
lsusb
``` in Applications-Accessories-Terminal.

---

