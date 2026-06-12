---
title: "I can see my network but not connect"
date: 2008-05-21
forum: Networking &amp; Wireless
---

### Post by Happy-Cheese on 2008-05-21
I have installed Ubuntu yesterday and go t BIg fight to get a driver to my wireless adaptor... then i got the driver and vas very proud :D

I can see my network, but when i try to connect there goes a long time and then it just stop connection... there comes no error message and no connection
 :| Help me, cuz i hate to sit here with my 20 meter long cable ...

---

### Post by sam_delta on 2008-05-21
whats your network card, post the output of ```
lspci
```

sam

---

### Post by Happy-Cheese on 2008-05-21
Sry it took so long time but here it is:
happy-cheese@Happy-PC:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IB (ICH9) LPC Interface Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801IB (ICH9) 4 port SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
02:00.0 IDE interface: JMicron Technologies, Inc. JMB368 IDE controller
05:00.0 VGA compatible controller: nVidia Corporation Geforce 9600 GT 512mb (rev a1)
06:00.0 Network controller: RaLink RT2561/RT61 802.11g PCI
..................................................................

I am using a WMP54 4.1 from linksys :)

---

