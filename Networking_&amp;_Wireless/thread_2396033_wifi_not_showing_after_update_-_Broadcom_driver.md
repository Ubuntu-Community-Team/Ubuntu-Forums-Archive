---
title: "wifi not showing after update - Broadcom driver"
date: 2018-07-10
forum: Networking &amp; Wireless
---

### Post by martink465 on 2018-07-10
Hello,

the wifi stopped working after the last update, it doesnt show any wifi that I could connect to.
I tried reinstalling the drivers, but it fails because wl is missing:
modprobe wl
modprobe: FATAL: Module wl not found in directory /lib/modules/4.15.0-24-generic

This is the wireless card version I have:

lspci -nn | grep Network
03:00.0 Network controller [0280]: Broadcom Limited BCM43142 802.11b/g/n [14e4:4365] (rev 01)

Thank you for any advice.

---

### Post by chili555 on 2018-07-10
Please see: [https://askubuntu.com/questions/1052403/how-can-i-fix-broadcom-driver-wifi-with-4-15-0-24-kernel-on-ubuntu-16-04](https://askubuntu.com/questions/1052403/how-can-i-fix-broadcom-driver-wifi-with-4-15-0-24-kernel-on-ubuntu-16-04)

---

### Post by martink465 on 2018-07-10
Thank you so much, works great!

---

