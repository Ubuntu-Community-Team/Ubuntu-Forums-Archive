---
title: "SIS 190 problem on Feisty"
date: 2007-03-19
forum: Networking &amp; Wireless
---

### Post by pmgeahan on 2007-03-19
Folks - 

Recently installed Feisty Herd 5 on a machine here.  lspci gives:

```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 662 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS966 [MuTIOL Media IO] (rev 59)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 190 Gigabit Ethernet Adapter (rev 01)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 02)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:09.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)
00:1f.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter (rev 04)

```

The SIS 190 network adaptor is recognized, the module loads(kernel 2.6.20-9-generic).  However, the card doesn't seem to respond; the router doesn't recognize any traffic, the other systems on the network don't see any traffic.  ifconfig shows the card as being up, however.

I know the card works under Windows, as that's what this machine was running when it arrived(Windows Vista).  

I've also tried setting the MTU to 1492 - no dice.

Anyone have any ideas?  I'd appreciate any help.

---

