---
title: "Wireless internet problems"
date: 2009-10-09
forum: New to Ubuntu
---

### Post by ThePooba on 2009-10-09
Hi im super new to ubuntu and i need help figuring out why my wireless internet doesnt work.
i have a travel mate 2480 
when i press the button on teh front of my computer to turn internet on nothing happens it plainly does not turn on, while on vista it works perfectly.
Can someone help me :confused:

---

### Post by fraser_m on 2009-10-09
Hi, could you open up Terminal (Applications > Accessories > Terminal) and run:
```
lspci
```
And post what it outputs.

That's a lowercase L, not a 1 by the way.

---

### Post by ThePooba on 2009-10-09
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
0a:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
There you go.

---

### Post by ThePooba on 2009-10-09
I really need my internet up and running its tiresome switching between ubuntu and vista .

---

### Post by fraser_m on 2009-10-09
Try the instructions here: [http://ubuntuforums.org/showthread.php?t=190177](http://ubuntuforums.org/showthread.php?t=190177)
If you need more help just ask.

---

### Post by PrePenguin on 2009-10-09
If you have onboard lan try disabling in the bios and that may resolve the wireless issue .. They but heads alot..

---

