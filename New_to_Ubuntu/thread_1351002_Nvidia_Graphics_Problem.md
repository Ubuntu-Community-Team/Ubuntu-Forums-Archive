---
title: "Nvidia Graphics Problem"
date: 2009-12-09
forum: New to Ubuntu
---

### Post by Naro on 2009-12-09
Hi, I just installed Ubuntu and when it asked me to update the drivers for my graphics card, I accepted and the download seemed to go fine.  When it restarted though, it said something about the kernel not working (I don't remember the exact message).  When I go into the Nvidia settings it says "You do not appear to be using the Nvidia X Driver. Please edit your X configuration file (just run nvidia-xconfig as root) and restart the x server.

I'm not sure what any of this means or how to fix it.  I'm using the Nvidia Accelerated Graphics Driver (Version 185) though.

Thanks for any help.

---

### Post by sledge73 on 2009-12-09
can you open a terminal & type: lspci
post the output of that command & we'll see what we can do to help

---

### Post by Naro on 2009-12-09
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)

---

### Post by Physical Hook on 2009-12-09
```
 
sudo nvidia-xconfig && sudo shutdown -r now

```
 
Let us know whether it helped or not.

---

### Post by sledge73 on 2009-12-09
from everything I can find the driver your using is to new. open the hardware drivers & uninstall the 185 driver restart your computer then reinstall the 173 driver & see if that fixes it. make sure you restart after uninstalling the 185 driver.

---

### Post by Naro on 2009-12-09
> **sledge73 said:**
> from everything I can find the driver your using is to new. open the hardware drivers & uninstall the 185 driver restart your computer then reinstall the 173 driver & see if that fixes it. make sure you restart after uninstalling the 185 driver.

That did it!  Thanks!

---

### Post by sledge73 on 2009-12-09
no problem happy ubuntuing!

---

