---
title: "No options on drop bar for networking for wireless on gateway MA7"
date: 2011-08-17
forum: New to Ubuntu
---

### Post by brett567 on 2011-08-17
Hi im new to linux and have just installed ubuntu 11.04 on to my gateway MA7 and everything seems to be working except the wireless. my laptop has a built in wireless chip but there is no option to turn it on or to search for wireless networks

 These are the options i get when i click on the networking logo at the top right off the screen

*wired network           *greyed out/non-clickable
*disconnected
-------------------
 VPN connections
-------------------
/enable networking
-------------------
*connection information
 edit connections

Any suggestions would be much apreciated

---

### Post by spiky001 on 2011-08-17
Post the out put of ```
lspci
``` it looks like your wireless card is not installed

---

### Post by natman on 2011-08-17
No sure what your problem is, but i used to have the issue of the wifi radio itself being turned off and no physical switch to turn it on, i fixed it by:
[HTML]sudo rfkill unblock all[/HTML]

---

### Post by brett567 on 2011-08-17
brett567@brett567-MX6211B:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11a/b/g (rev 01)
04:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
04:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
04:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
brett567@brett567-MX6211B:~$

---

