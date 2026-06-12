---
title: "installing zd1201 wireless usb dongle"
date: 2006-11-26
forum: Networking &amp; Wireless
---

### Post by darnok on 2006-11-26
Hi,

I'm trying to connect to internet via a zd1201 usb dongle.  The steps I've followed:
- lsusb shows my dongle as ZyDAS 802.11b WiFi.  I decided to use the Windows driver with the help of ndiswrapper
- downloaded ndiswrapper-utils_1.8-0ubuntu2_i386.deb & ndisgtk_0.6-0ubuntul_all.deb
- sudo dpkg -i ndisgtk_0.6ubuntul_all.deb
- sudo dpkg -i ndiswrapper-utils_1.8-0ubuntu2_i386.deb
- installed the driver with the use of System/Administration/Winbdows Wireless Drivers gui.  It now lists a zd1201u Hardware present: Yes.  running ndiwrapper -l confirms this
- however, iwconfig and ifconfig do not expose wlan awarness.  connecting the dongle to the usb results in the following line in the /var/log/messages: zd1201: probe of 1-1:1.0 failed with error -2

I'm not sure where to take it from here.  As an absolute linux newbie, I'd appreciate most explicit suggestions.  Thanks a lot

darnok

---

### Post by FrodoB on 2006-11-26
See:

[http://www.ubuntuforums.org/showthread.php?t=49070&highlight=zd1201](http://www.ubuntuforums.org/showthread.php?t=49070&highlight=zd1201)

---

