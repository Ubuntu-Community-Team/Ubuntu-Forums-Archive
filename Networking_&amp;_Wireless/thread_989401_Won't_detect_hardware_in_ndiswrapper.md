---
title: "Won't detect hardware in ndiswrapper"
date: 2008-11-21
forum: Networking &amp; Wireless
---

### Post by buster2209 on 2008-11-21
I'm using a Safecom SWLUT-54125 WI-FI stick and have to use ndiswrapper as there is no Linux driver

I used ndiswrapper and have managed to get the driver installed (tnet1130) by installing the device first on an xp machine then copying the program files over to my Linux machine.

I used the command 'lsusb' to verify I had the correct driver (07b8:b21a) which corresponds with the verified drivers on the ndiswrapper list but the hardware is not detected which implies I am using the wrong driver.

I think my problem lies with the command 'lspci' as my WI-FI stick is not listed, just my ethernet controller.

The following outputs are shown below for each command;

jam@jam-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
03:0a.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)

jam@jam-desktop:~$ lsusb
Bus 004 Device 004: ID 090c:1000 Feiya Technology Corp. Memory Bar
Bus 004 Device 003: ID 07b8:b21a D-Link Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 03f0:8604 Hewlett-Packard Deskjet 5440
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
 
Any help would be greatly appreciated as I'm close to giving up and just buying a WI-FI stick that has a Linux USB driver

I'm using Ubuntu 8.04 by the way

---

### Post by sundeniro on 2009-07-22
I know this an old thread but just wanted to let you know that I had the same problem then checked on a windows machine and found the driver tusb1150.inf to be a better driver than that offered on the manufacturers website. Unfortunately it regularly looses connectivity.

> **buster2209 said:**
> I'm using a Safecom SWLUT-54125 WI-FI stick and have to use ndiswrapper as there is no Linux driver

I used ndiswrapper and have managed to get the driver installed (tnet1130) by installing the device first on an xp machine then copying the program files over to my Linux machine.

I used the command 'lsusb' to verify I had the correct driver (07b8:b21a) which corresponds with the verified drivers on the ndiswrapper list but the hardware is not detected which implies I am using the wrong driver.

I think my problem lies with the command 'lspci' as my WI-FI stick is not listed, just my ethernet controller.

The following outputs are shown below for each command;

jam@jam-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
03:0a.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)

jam@jam-desktop:~$ lsusb
Bus 004 Device 004: ID 090c:1000 Feiya Technology Corp. Memory Bar
Bus 004 Device 003: ID 07b8:b21a D-Link Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 03f0:8604 Hewlett-Packard Deskjet 5440
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
 
Any help would be greatly appreciated as I'm close to giving up and just buying a WI-FI stick that has a Linux USB driver

I'm using Ubuntu 8.04 by the way

---

