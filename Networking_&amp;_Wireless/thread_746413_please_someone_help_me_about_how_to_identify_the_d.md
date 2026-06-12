---
title: "please someone help me about how to identify the driver"
date: 2008-04-05
forum: Networking &amp; Wireless
---

### Post by a-aaaaaaaaaaaaaaaaaaaaaaa on 2008-04-05
i try to identify driver and do as they said on this website below([http://ndiswrapper.sourceforge.net/j...,installation/](http://ndiswrapper.sourceforge.net/j...,installation/))

To identify the driver that you need from List, first identify the card you have with lspci and note the first column such as 0000:00:0c.0 and then find out the PCI ID of the card by running lspci -n and locating the entry corresponding to the first column of lspci output. The PCI ID is third column or fourth in some distributions and of the form 104c:8400. Now you need to get the Windows driver for this chipset. In the List, find out an entry for the same PCI ID, and download the driver corresponding to it. Unpack the Windows driver with unzip/cabextract/unshield tools, and find the INF file (.INF or .inf extension) and the SYS file (.SYS or .sys extension). If there are multiple INF/SYS files, you may look in the List if there are any hints about which of them should be used. Make sure the INF file, SYS file and any BIN files (For example, TI drivers use BIN firmware) files are all in one directory.

i do as they said and wrote in the terminal :

yassir@yassir:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
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
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0b:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
yassir@yassir:~$ lspci -n
00:00.0 0600: 8086:27a0 (rev 03)
00:02.0 0300: 8086:27a2 (rev 03)
00:02.1 0380: 8086:27a6 (rev 03)
00:1b.0 0403: 8086:27d8 (rev 01)
00:1c.0 0604: 8086:27d0 (rev 01)
00:1c.3 0604: 8086:27d6 (rev 01)
00:1d.0 0c03: 8086:27c8 (rev 01)
00:1d.1 0c03: 8086:27c9 (rev 01)
00:1d.2 0c03: 8086:27ca (rev 01)
00:1d.3 0c03: 8086:27cb (rev 01)
00:1d.7 0c03: 8086:27cc (rev 01)
00:1e.0 0604: 8086:2448 (rev e1)
00:1f.0 0601: 8086:27b9 (rev 01)
00:1f.2 0101: 8086:27c4 (rev 01)
00:1f.3 0c05: 8086:27da (rev 01)
03:00.0 0200: 14e4:170c (rev 02)
03:01.0 0c00: 1180:0832
03:01.1 0805: 1180:0822 (rev 19)
03:01.2 0880: 1180:0843 (rev 01)
03:01.3 0880: 1180:0592 (rev 0a)
03:01.4 0880: 1180:0852 (rev 05)
0b:00.0 0280: 14e4:4311 (rev 01)

now i want to identify the driver , can some body help me with that and explain how please?

---

### Post by Vadi on 2008-04-05
The link you gave is broken somehow :(

Anyway this is your wireless card from lspci:
"0b:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)"

And this it's ID or whatever from lspci -n:
0b:00.0 0280: 14e4:4311 (rev 01)

---

### Post by a-aaaaaaaaaaaaaaaaaaaaaaa on 2008-04-05
thanx my friend but can you learn me how i can do that without your help if i face same proplem at the future ?and why you not choice deferent one ?and i have also usb senao wireless card (engenium) what about it ?

---

### Post by Vadi on 2008-04-05
Heh, poke about the forums and help others. I remembered that Broadcom is the name of a wireless card company, and their cards have pretty bad linux support so people frequently ask for help with them.

Plus, the 'wlan' in the name stands for wireless lan or something, which gave it away as the wireless card.

---

