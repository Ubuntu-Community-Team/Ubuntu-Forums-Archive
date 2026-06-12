---
title: "UNCLAIMED but needed"
date: 2007-12-13
forum: Networking &amp; Wireless
---

### Post by KeithyB on 2007-12-13
Hi, I'm really knew at this, perhaps someone can help with the next step I need to take?
I've installed Ubuntu 7.10 on my Laptop (Fuj/Siemens) in a dual boot config but the Network cards are not found/used (they work fine in both XP & Vista).
I have a LAN card to connect to a desktop (possibly to use ICS) and a wireless card to (hopefully) give me some internet connect but they do not appear in the Network (just the local loopback).
I can now see they exist from the lspci but from the lshw they aren't claimed, what does this mean?
I've looked at the other threads and they suggest a driver problem but then I'm asked to compile from the manufacturers into linux... Seems a bit tricky for a new to LINUX type...
Pls see details below...
lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
00:1f.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)
02:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
root@kb-laptop:~# 

 lshw -C network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: 191 Gigabit Ethernet Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=0
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
root@kb-laptop:~#

---

### Post by Lostincyberspace on 2007-12-13
What happens if you run ifconfig or iwconfig.

---

### Post by KeithyB on 2007-12-13
Hi Lost....
ifconfig just shows the local loopback cfg & iwconfig shows no wireless extensions.
I guess this is because the hardware is still in an UNCLAIMED bucket ?

---

### Post by Lostincyberspace on 2007-12-13
If you go to System>>Preferences>>Hardware Information, Can you see it there.

---

### Post by KeithyB on 2007-12-13
Yes indeed, both NICs appear..
The SiS 191 LAN is there in it's own category & the wireless AR5006EG is under the PCI to PCI Bridge (strange)...
If they appear here, why can't Ubuntu use them?

---

### Post by KeithyB on 2007-12-18
Hello? Does anyone out there have a suggestion or should I seek another Linux release?

---

### Post by rustybronco on 2007-12-18
> **KeithyB said:**
> Hello? Does anyone out there have a suggestion 
Your chipset is showing an ar5006eg, I would try this method. [http://ubuntuforums.org/showpost.php...8&postcount=26](http://ubuntuforums.org/showpost.php...8&postcount=26)

 > or should I seek another Linux release?That is up to you.

---

