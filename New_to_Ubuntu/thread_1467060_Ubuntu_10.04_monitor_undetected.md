---
title: "Ubuntu 10.04 monitor undetected"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by Don Mega on 2010-04-30
I just installed version 10.04 recently had 9.10 where display effects worked and my compac 15" lcd screen was detected and now nada, no display efeects and monitor listed as unknown Please help anyone

note * i followed this form [http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html](http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html) to fix the blank screen issue I had when installing 10.04

---

### Post by swoll1980 on 2010-04-30
> **Don Mega said:**
> I just installed version 10.04 recently had 9.10 where display effects worked and my compac 15" lcd screen was detected and now nada, no display efeects and monitor listed as unknown Please help anyone

note * i followed this form [http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html](http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html) to fix the blank screen issue I had when installing 10.04

Hardware?

---

### Post by Don Mega on 2010-04-30
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
03:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

---

### Post by Don Mega on 2010-06-05
is there not anyone who can fix this?[-o<

---

### Post by saakeman on 2010-06-05
[QUOTE=Don Mega;9416060]is there not anyone who can fix this?[-o<[/QUOTE

what graphics card are you runing

---

### Post by ankspo71 on 2010-06-05
Hi, there is a driver for the Intel 855GM here. It claims to fix 3D effects.
[http://ubuntuforums.org/showpost.php?p=9121212&postcount=8](http://ubuntuforums.org/showpost.php?p=9121212&postcount=8)

I found the link from this page:
[http://ubuntuforums.org/showthread.php?t=1464239&highlight=855GM](http://ubuntuforums.org/showthread.php?t=1464239&highlight=855GM)

There seems to be driver problems with 855GM cards in Lucid at the moment, but the above link should work, hopefully.
Hope that helps.

---

### Post by Don Mega on 2010-06-07
Thank ankspo71! This worked! I'm so glad you came along with this solution now I have full display effects! sweet, I've been looking for a long while. Now I'ts SOLVED!!:guitar:

---

