---
title: "Connection problem..."
date: 2007-11-27
forum: Networking &amp; Wireless
---

### Post by ceduriki on 2007-11-27
I'm having problems connecting to any wireless network. I'm getting all the networks on my wireless networks list, but can't connect to them. What should I do?

---

### Post by csat on 2007-11-27
Take a look to this tutorial.

[http://ubuntuforums.org/showthread.php?t=263136](http://ubuntuforums.org/showthread.php?t=263136)

---

### Post by rustybronco on 2007-11-27
> **ceduriki said:**
> I'm having problems connecting to any wireless network. I'm getting all the networks on my wireless networks list, but can't connect to them. What should I do?
what kind of wireless device are you using? if its internal or pcmcia post the results of lspci, if its a usb device post the results of lsusb.
also have a look see in my signature for trouble shooting your wireless connection in "kevdogs finest"

---

### Post by ceduriki on 2007-11-28
I'm using a Belkin F5D9010. I put in the correct WEP key, and it says "connected", but it won't release an ip...

---

### Post by rustybronco on 2007-11-28
Let me see if I can help (just learning).
Open a terminal and post the results of the following two commands...  
lshw -C network
lspci -nn

---

### Post by ceduriki on 2007-11-28
Results to first command:
*-network               
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 03
       serial: 00:12:3f:0b:4f:4e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network
       description: Wireless interface
       product: RT2600 802.11 MIMO
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 00
       serial: 00:17:3f:92:c6:ad
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci latency=64 module=rt61pci multicast=yes wireless=IEEE 802.11g
Results to second command:
00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2592] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2792] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d3)
00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller [8086:266e] (rev 03)
00:1e.3 Modem [0703]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller [8086:266d] (rev 03)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [8086:266f] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [8086:266a] (rev 03)
02:01.0 CardBus bridge [0607]: Texas Instruments PCI1510 PC card Cardbus Controller [104c:ac56]
02:08.0 Ethernet controller [0200]: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile [8086:1068] (rev 03)
03:00.0 Network controller [0280]: RaLink RT2600 802.11 MIMO [1814:0401]


I actually solved the problem...the router had WEP issues. 

but, I would still like you to to kindly explain what all this data is and what the commands were for...I'm still getting used to linux commands, the only real command-based OS I can work with id DOS, and I did most of my work in the windows command prompt, so...

---

### Post by rustybronco on 2007-11-28
> **ceduriki said:**
> description: Wireless interface
product: RT2600 802.11 MIMO
vendor: RaLink
logical name: wmaster0
version: 00
serial: 00:17:3f:92:c6:ad
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list logical ethernet physical wireless
configuration: broadcast=yes driver=rt61pci latency=64 module=rt61pci multicast=yes wireless=IEEE 802.11g
Results to second command:


> I'm using a Belkin F5D9010 they have different chipsets.

Needed to find out the wireless interface "rt2600", name "wmaster0", and whether or not it was claimed by a driver "rt61pci".

I just pick and choose what I wanted to know, but it tells you the interfaces, usb, ect...

example...
description: Ethernet interface
product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
vendor: Intel Corporation
logical name: eth0

description: Wireless interface
product: RT2600 802.11 MIMO
vendor: RaLink
logical name: wmaster0

did this help? yes/no

for more info read the link in my signature.

---

