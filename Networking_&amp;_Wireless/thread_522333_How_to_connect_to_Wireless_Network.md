---
title: "How to connect to Wireless Network?"
date: 2007-08-10
forum: Networking &amp; Wireless
---

### Post by Chepe on 2007-08-10
Hello!

I'm totally new at Linux, but I've decided to check it out because I'll be using it in my studies this semester.
I have just installed in on my Dell Inspiron 8600 Laptop. My problem is that I don't manage to connect to my wireless network. 

I've tried to follow the "Help" inside Ubuntu, but it suggests that I shouls go to System - Administration - Networking, to check if my wireless card is supported. However, there is nothing called "networking" under administration, only "Network" and "Network Tools"...

I'm guessing there is an easy solution to this problem, but since I have no Linux experience I don't know how to attack the problem..

Hope some of you guys can help me!

---

### Post by kevdog on 2007-08-10
Please type at the command line and provide the following output (you can cut and paste if you want):

lspci -nn
lshw -C network

That should get us started.

---

### Post by Chepe on 2007-08-10
Ok, took some time, since I'm on a different computer :)


LSPCI -NN:
00:00.0 Host bridge [0600]: Intel Corporation 82855PM Processor to I/O Controller [8086:3340] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 82855PM Processor to AGP Controller [8086:3341] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 81)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 01)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 01)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 01)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10] [1002:4e50]
02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401 100Base-T [14e4:4401] (rev 01)
02:01.0 CardBus bridge [0607]: Texas Instruments PCI4510 PC card Cardbus Controller [104c:ac44] (rev 02)
02:01.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCI4510 IEEE-1394 Controller [104c:8029]
02:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
lars@lars-laptop-ubuntu:~$ 


LSHW:
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 01
       serial: 00:0f:1f:1c:1c:09
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=1.01 latency=32 multicast=yes
       resources: iomemory:faffe000-faffffff irq:11
  *-network:1 DISABLED
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@02:03.0
       logical name: eth1
       version: 03
       serial: 00:90:96:bd:fb:e4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-15-generic latency=32 multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:faff6000-faff7fff irq:7

---

### Post by kevdog on 2007-08-10
You have a broadcom chipset.

You have two options to install the driver

bcm43xx
ndiswrapper

Do you have a preference??  bcm43xx is easier but maxes out at 11 Mb/sec  Ndiswrapper requires a little bit more patient to setup but supports 54 Mb/sec.  You need a windows xp driver, either on a disk or downloaded to work with ndiswrapper.

Once you decide I can give you instructions.  If you decide ndiswraper DO NOT install this from repository.  Its best to compile from source code -- I have the instructions if you need them.

---

### Post by Chepe on 2007-08-10
bcm43xx  sounds good to me, I don't think I need anything faster, at least not at the moment :)

---

### Post by yogo on 2007-08-10
Here is my output


00:00.0 Host bridge [0600]: Intel Corporation 82810 GMCH [Graphics Memory Controller Hub] [8086:7120] (rev 03)
00:01.0 VGA compatible controller [0300]: Intel Corporation 82810 CGC [Chipset Graphics Controller] [8086:7121] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801AA PCI Bridge [8086:2418] (rev 02)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801AA ISA Bridge (LPC) [8086:2410] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801AA IDE [8086:2411] (rev 02)
00:1f.2 USB Controller [0c03]: Intel Corporation 82801AA USB [8086:2412] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801AA SMBus [8086:2413] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801AA AC'97 Audio [8086:2415] (rev 02)
01:08.0 Network controller [0280]: RaLink RT2561/RT61 802.11g PCI [1814:0301]
naty@naty-desktop:/etc$ sudo shw -C network
Password:
sudo: shw: command not found
naty@naty-desktop:/etc$ sudo lshw -C network
*-network
description: Wireless interface
product: RT2561/RT61 802.11g PCI
vendor: RaLink
physical id: 8
bus info: pci@01:08.0
logical name: ra0
version: 00
serial: 00:0e:2e:8a:86:16
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=RT61STA driverversion=1.1.0 CVS latency=64 link=yes multicast=yes wireless=RT61 Wireless
resources: iomemory:f4100000-f4107fff irq:9
naty@naty-desktop:/etc$ iwconfig
lo no wireless extensions.

ra0 RT61 Wireless ESSID:"" Nickname:""
Mode:Managed Frequency:2.412 GHz Bit Rate=54 Mb/s
RTS thrff Fragment thrff
Link Quality=88/100 Signal level:-51 dBm Noise level:-111 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

Can I use a BCM43xx as well? BTW I blacklisted that driver and forgot how I did it.

I had ndiswrapper but I uninstalled it as I really had troubles using it.

---

