---
title: "VMware and network"
date: 2007-09-09
forum: Networking &amp; Wireless
---

### Post by Peque on 2007-09-09
Well the problem is quite tricky. 

On my new computer Dell Latitude D531 - I have a lot of troubles getting the different wishes to work - and now I have the following problem:

XP would install unless I'm changing the hardwaredrive from SCSI to IDE in the virtual machine running Windows XP prof. After a lot of troubles with that - I'm ending up with this problem: 
I cannot find any drivers to the ethernet-controller (neither Wired or wireless)  and 1 SCSI controller. 
I have downloaqdet the original driver from dell and tried using them - but no matter what - it's not the rigth driver - so no network at all. 

Have anyone a clue?? - here&#347; lspci: 
pbj@ubu-pbj:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Unknown device 7910
00:01.0 PCI bridge: ATI Technologies Inc Unknown device 7912
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 7915
00:06.0 PCI bridge: ATI Technologies Inc Unknown device 7916
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SB600 SMBus (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SB600 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SB600 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Unknown device 791f
03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)
0b:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01 


Can anyone help me with that? 
THanks 
P

---

### Post by noob12 on 2007-09-09
Can you clarify, which OS is the host OS and which is the "guest" (VM) OS?

Generally speaking the guest VM will use a virtual interface bridged to a real interface on the physical host.

---

### Post by Peque on 2007-10-20
Sorry for the long answer.. 

The Host O/S is Ubuntu 7.10 and the guest are windows XP 
I have installed vmware tools and are only able to run anything else but brigded networking. 

Unfortunably is it something I should use at work - as I cannot connect to our phonecentral etc while the IP is from another netmask ( And It cannot be changed i the phonecentral) But that's not the problem - it's getting brigded network to work

---

