---
title: "usb wireless interface disabled."
date: 2014-06-28
forum: Networking &amp; Wireless
---

### Post by johnnyhop on 2014-06-28
My USB wireless interface works fine in Kubuntu (as well as Sabayon and Pear--three hard drives boot to four distros) but not in Ubuntu studio. Below is the lshw output for the USB wireless adapter from Ubuntu Studio and Kubuntu:

lshw network output Ubuntu Studio:

*-network DISABLED
       description: Wireless interface
       physical id: 1
       bus info: usb@1:8
       logical name: wlan0
       serial: 68:1c:a2:16:47:67
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu driverversion=3.13.0-29-lowlatency firmware=N/A link=no multicast=yes wireless=IEEE 802.11bgn

lshw network output Kubuntu:

*-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:8
       logical name: wlan0
       serial: 68:1c:a2:16:47:67
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu driverversion=3.13.0-30-generic firmware=N/A ip=192.168.0.2 link=yes multicast=yes wireless=IEEE 802.11bgn

I think all would be well if a remedy could be found for DISABLED. Hope the above info is helpful.

---

### Post by johnnyhop on 2014-06-29
I'm OK with the wireless in Studio now.  Couldn't figure out what went wrong, wireless mysteriously stopped working about a month ago.  Upgraded to 14.04 from 13.10 from 13.04 and my USB wireless adapter worked after the upgrade. Today downloaded 14.04 and noted wireless configured with NetworkManager in live CD mode so did a clean install of file system without formatting the seperate home partition

---

