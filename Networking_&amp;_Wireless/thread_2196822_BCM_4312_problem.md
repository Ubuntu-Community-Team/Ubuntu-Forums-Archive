---
title: "BCM 4312 problem"
date: 2013-12-31
forum: Networking &amp; Wireless
---

### Post by Aberts10 on 2013-12-31
i got the same thing and i got a dell inspiron, with dual boot windows 7 and ubuntu. I hate ubuntu so far because the wireless is not working while on windows 7 wireless works perfect!
i have tried doing many diffrent things but ubuntu still does not want to do it, i got the same error; This package contains Broadcom 802.11 Linux STA wireless driver for use with Broadcom's BCM4311-, BCM4312-, BCM4313-, BCM4321-, BCM4322-, BCM43224-, and BCM43225-, BCM43227- and BCM43228-based hardware. "Sorry, installation of this driver failed."

Please have a look at the log file for details: /var/log/jockey.log" my wireless requires this driver: brian@ubuntu:~$ lspci -nn | grep 0280
03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
brian@ubuntu:~$

---

### Post by chili555 on 2013-12-31
> **robloxian2001 said:**
> 
 brian@ubuntu:~$ lspci -nn | grep 0280
03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
Please do:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
sudo modprobe -r b43 && sudo modprobe b43
```Then let us hear your report.

---

### Post by Aberts10 on 2013-12-31
no it did not work :(

---

### Post by Aberts10 on 2013-12-31
my windows 7 still works but ubuntu does not show internet wireless connections. right now i am using a cable

---

### Post by Iowan on 2013-12-31
Moved to new thread

---

### Post by praseodym on 2013-12-31
Hi,

"linux-firmware-nonfree" lacks the firmware for the LP-PHY chipset since 13.10. You need this firmware package:
```

wget http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz 
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```
Reboot.

---

