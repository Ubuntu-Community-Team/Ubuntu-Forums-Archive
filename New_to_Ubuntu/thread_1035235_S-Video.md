---
title: "S-Video"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by Jynxx on 2009-01-09
Hello all. I'm trying to get my s-video out to work on my HP Pavilion dv6000 and can't seem to get it to work. Anyone have an idea on this?

Thanks!

---

### Post by Hospadar on 2009-01-09
What kind of video card does your machine have?

If you don't know,
From a terminal, post the output of ```
lspci
```

---

### Post by Jynxx on 2009-01-09
Here is what I get

alex@alex-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
05:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
05:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
05:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
05:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
05:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
alex@alex-laptop:~$

---

### Post by Jynxx on 2009-01-09
Any ideas anyone?  :)

---

### Post by Jynxx on 2009-01-09
So is there no one that has figured this s-video problem out yet?

---

### Post by luiska on 2009-01-10
Did it work with any other OS? 

Check HP's website, there is some of the DV6000 that have S-Video and Wireless problems.

- Louis

---

