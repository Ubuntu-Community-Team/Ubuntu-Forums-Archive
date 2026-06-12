---
title: "Gigabeat F20 totally ignored-Ubuntu 9.04"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by pi.boy.travis on 2009-04-24
Hi!  I have a Gigabeat F20 that is totally ignored by Ubuntu 9.04.  I have tested several computers and cables, but no avail.  It worked perfectly with 8.10. It isn't listed in the Places>Computer menu, or even GParted.

Anything I can do?

Thanks in advance!

---

### Post by LowSky on 2009-04-24
plug it in to the PC, the open a terminal and post the output here

use this command ```
lspci
```

---

### Post by pi.boy.travis on 2009-04-24
Thanks for the reply!

Here it be:

```
travis@travis-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
travis@travis-laptop:~$ 

```

Hmm. . .  Not quite sure to make of this. . .

---

### Post by pi.boy.travis on 2009-04-25
bump?

---

### Post by Ocxic on 2009-04-25
i think LowSky meant "lsusb"
lspci only lists pci cards and system devices, if you drive uses USB then use lsusb.
also try "sudo lshw" to get a listing of all the hardware in the computer, to see if ubuntu even sees the drive as connected HW

---

### Post by pi.boy.travis on 2009-04-25
OK, here is lsusb:

```
travis@hp-mini:~$ sudo lsusb
[sudo] password for travis: 
Bus 001 Device 003: ID 0930:0009 Toshiba Corp. Gigabeat F/X (HDD audio player)
Bus 001 Device 002: ID 10f1:1a08  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

It's there. . . But it won't even show up in GParted. . . 

Anything I can do?

Thanks in advance!

---

### Post by pi.boy.travis on 2009-04-25
/dev/sdb doesn't even exist. . .  So that means the Gigabeat isn't even seen a a block device. . .

---

### Post by Spiritous on 2009-04-25
> **pi.boy.travis said:**
> /dev/sdb doesn't even exist. . .  So that means the Gigabeat isn't even seen a a block device. . .

Its obviously a problem with 9.10 then, Either downgrade or wait for some experts to reply, but I don't think you can fix it...

---

### Post by pi.boy.travis on 2009-04-25
Yes, I have found the bug report.  Thanks!

---

