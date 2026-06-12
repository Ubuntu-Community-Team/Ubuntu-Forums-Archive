---
title: "Wifi - Can't obtain IP Address with Wireless card"
date: 2005-07-14
forum: Networking &amp; Wireless
---

### Post by jordanj1969 on 2005-07-14
I have an HP zv5037wm with Broadcom wireless card...got card loaded and it worked with my Linksys router.. switched to a US Robotics 8054 Access Point and Router.  I set it up for WEP Shared, the WEP key my laptop see's is correct.  I performed the following: "sudo iwlist key" command but it showed "Security mode:restricted".  

What file do I edit to change restrited to shared or open?

---

### Post by alastair on 2005-07-14
The "auto" setup networking (i.e. ifup/ifdown/bootup) is in :

/etc/network/interfaces

perhaps. You can also use "iwconfig" (see : man iwconfig) to manually set this.

---

