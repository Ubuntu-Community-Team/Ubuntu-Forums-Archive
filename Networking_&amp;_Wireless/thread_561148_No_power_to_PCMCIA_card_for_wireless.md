---
title: "No power to PCMCIA card for wireless"
date: 2007-09-27
forum: Networking &amp; Wireless
---

### Post by ScoopJumps on 2007-09-27
Hi all,

I am struggling with a new wireless connection at home. I have the router all up and running fine and dandy, this I know as my brothers computer is running Windows XP and surfing the net at my expense!

I have a Medion Laptop and am trying in vain to connect to the internet via a Linksys WPC54G PCMCIA card. I am runing Ubuntu 6.06. The trouble I am having is the lights on the card are not even lit, however it is identified in device manager.

ifconfig shows this:

> 
eth0      Link encap:Ethernet  HWaddr 00:40:D0:4D:C8:7B
          inet addr:192.168.1.2  Bcast:192.168.1.255 Mask:255.255.255.0
          inet6 addr: fe80::240:d0ff:fe4d:c87b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2741 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2743 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2930777 (2.7 MiB)  TX bytes:381252 (372.3 KiB)
          Interrupt:209 Base address:0xe400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)
 

LSPCI states:

> 0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 650/M650 Host (rev 80 )
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bri dge (AGP)
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media I O] (rev 25)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
0000:00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev  a0)
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound  Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller  (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller  (rev 0f)
0000:00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fa st Ethernet (rev 90)
0000:00:09.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controlle r (rev 02)
0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M65 0/740 PCI/AGP VGA Display Adapter
**0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Liberta s] 802.11b/g Wireless (rev 03)**


I have installed NDIS wrapper and what I think are latest PCMCIA drivers via package manager. I have also installed the card specific driver (LSMNVDS.inf) however NDIS states the driver is installed but no hardware is present. 

Any hints?

I have searched but couldn't find a solution. I have, however, seen these cards are supported which is a positive.

I am at a loss. It seems it is detected, yet there is no power light or link light illuminated. It also doesn't appear in network connections. I'm hoping there is some easy fix to gaining control of the card and getting online with wireless.

Thanks in anticipation,

Sam

---

### Post by ScoopJumps on 2007-09-27
<BUMP>

(The original message made no sense so I have ammended it and feel it needs a bump  up the order) :)

---

