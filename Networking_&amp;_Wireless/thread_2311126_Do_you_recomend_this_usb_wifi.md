---
title: "Do you recomend this usb wifi?"
date: 2016-01-24
forum: Networking &amp; Wireless
---

### Post by juan_loo_kung on 2016-01-24
[www.szedup.com/show.aspx?id=1681](www.szedup.com/show.aspx?id=1681)
runs on ubuntu 15.10? i want to buy it because my current broadcom 43142 card isn't working i have tried almost everything on the forums to fix it

---

### Post by praseodym on 2016-01-25
"Product specs" show the driver Realtek8188CUS. So, it should work, maybe the driver needs to be changed, though.

Try this firmware package for the Broadcom device:
```
sudo apt-get remove --purge bcmwl-kernel-source
wget http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz 
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```
Reboot. It contains the missing firmware for the low-power chipset (LP-PHY) which may not be part of the packages from the repos.

---

