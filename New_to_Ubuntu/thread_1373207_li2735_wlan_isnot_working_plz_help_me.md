---
title: "li2735 wlan isnot working plz help me"
date: 2010-01-05
forum: New to Ubuntu
---

### Post by thiruvan on 2010-01-05
hi i changed in to ubuntu latest version. my problem is i couldnt turn on my wlan. this is the problem im facing now. plz help me to solve this

---

### Post by bkratz on 2010-01-05
> **thiruvan said:**
> hi i changed in to ubuntu latest version. my problem is i couldnt turn on my wlan. this is the problem im facing now. plz help me to solve this

That is the part number for a Fujitsu Laptop right? Are you trying to use wireless networking or what are you trying to do?  If you go to the terminal Applications>>Accessories>>Terminal and type in 

lspci -nn  (that is LSPCI in lowercase) and copy/paste the results here, I'm sure someone will help you.  They really need to know what you are trying to do.

---

### Post by thiruvan on 2010-01-05
thanx for ur reply.at first i don have any key to turn on my wireless adapter. previously i used fn+f1 to turn on in windows. i couldnt do that in ubuntu. this is the problem im facing now

---

### Post by thiruvan on 2010-01-05
newman@newman-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 03)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 [8086:2843] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)
08:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
newman@newman-laptop:~$

---

### Post by Methuselah on 2010-01-05
Hi thiruvan,

Does this help, especially post 4.
[http://ubuntuforums.org/showthread.php?t=1036744](http://ubuntuforums.org/showthread.php?t=1036744)

---

