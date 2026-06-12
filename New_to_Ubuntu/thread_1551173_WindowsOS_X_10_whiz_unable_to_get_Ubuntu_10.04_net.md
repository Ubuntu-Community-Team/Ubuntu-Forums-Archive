---
title: "Windows/OS X 10 whiz unable to get Ubuntu 10.04 netbook to connect to working network"
date: 2010-08-11
forum: New to Ubuntu
---

### Post by Soontobemacuser on 2010-08-11
Dear all,
I have just started using ubuntu as an OS and I cannot get internet working. Red Exclamation point next to network manager icon, Terminal says card is disabled (and it isn't(I don't think)), Ubuntu help isn't helping, and I'm stuck with some cra**y version of windows xp. HELP!!:confused::???:
Computer is Inspiron Mini 10v Intel Atom broadcom b/G card
Router is Belkin Share

---

### Post by Ozymandias_117 on 2010-08-12
From what you've posted I assume you're talking about connecting wirelessly.

Most likely problem is that you don't have Wireless drivers. Plug the computer in through ethernet, and go to System -> Admin -> Hardware Drivers and activate your wireless card.

---

### Post by Soontobemacuser on 2010-08-12
I have 1 working ethernet cable (that is lost)
I have windows XP (which works with my router)
I am unsure weather ethernet will work with 10.04
I am currently on windows to use this blog

---

### Post by linux18 on 2010-08-12
ethernet will work fine, but first post the output of :

lshw -C network

and make sure its a capital C
also
-did you right click the network-mannager icon? 
-is the wifi led blue (or whatever color it is when its working)

---

### Post by Soontobemacuser on 2010-08-12
Results of sudo lshw -C network

```
*-network               

       description: Network controller

       product: BCM4312 802.11b/g

       vendor: Broadcom Corporation

       physical id: 0

       bus info: pci@0000:03:00.0

       version: 01

       width: 64 bits

       clock: 33MHz

       capabilities: pm msi pciexpress bus_master cap_list

       configuration: driver=b43-pci-bridge latency=0

       resources: irq:17 memory:f0100000-f0103fff

  *-network

       description: Ethernet interface

       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller

       vendor: Realtek Semiconductor Co., Ltd.

       physical id: 0

       bus info: pci@0000:04:00.0

       logical name: eth0

       version: 02

       serial: 00:24:e8:f1:50:69

       size: 10MB/s

       capacity: 100MB/s

       width: 64 bits

       clock: 33MHz

       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation

       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s

       resources: irq:27 ioport:2000(size=256) memory:f0510000-f0510fff(prefetchable) memory:f0500000-f050ffff(prefetchable) memory:f0520000-f053ffff(prefetchable)

  *-network DISABLED

       description: Wireless interface

       physical id: 2

       logical name: wlan0

       serial: 90:4c:e5:43:f0:13

       capabilities: ethernet physical wireless 

       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
```Network manager says Wireless disabled, no wifi light (Inspiron Mini 10v), currently attempting directions in post #2
It worked! ubuntu uses wifi card! thanks Ozymandias_117 and Linux18 [URL="http://ubuntuforums.org/member.php?u=805682"][COLOR=Black][/COLOR]
[/URL]

---

