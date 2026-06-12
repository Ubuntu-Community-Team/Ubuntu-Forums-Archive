---
title: "Qualcom Atheros QCA9565 Bluetooth not working"
date: 2014-08-11
forum: Networking &amp; Wireless
---

### Post by smirnoff76 on 2014-08-11
Hi All 

I am using Ubuntu 14.04 and have just installed it on my laptop but my Bluetooth is not working. Does anyone have any ideas what needs installing to enable this?

Thanks

---

### Post by DAVID_GREGORY_KERR on 2015-08-11
have you got the latest drivers if not download the drivers source code and while in Root terminal do (chmod 0044<ret>,make <ret>,make install <ret>) and reboot I did try using ./configure and got the error no configure file associated with this file but it is always a good thing to try when you have done a chmod 0044 <ret> but always have the latest drivers installed and it just happens that I have the same plug-in board in my Acer Aspire TC-220 and not had any problems with it yet except for a strange flip flopping between the Qualcom Atheros QCA9565 and the Ethernet adaptor which is part of the motherboard in my personal computer.

---

### Post by jeremy31 on 2015-08-11
The bluetooth does need firmware ```
sudo apt-get update && sudo apt-get install linux-firmware
``` Reboot
if it doesn't work after a reboot post the results of ```
lsusb; rfkill list all; uname -a; hciconfig -a; dmesg | egrep -i 'blue|firm'
```

---

