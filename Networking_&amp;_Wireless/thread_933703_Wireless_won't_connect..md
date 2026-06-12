---
title: "Wireless won't connect."
date: 2008-09-29
forum: Networking &amp; Wireless
---

### Post by DeviousLearning on 2008-09-29
So I've finally made the leap to Ubuntu. (well not entirely but I had an old computer lying around and decided it would be a great testbed). Anyways, I'm trying to connect to my wireless network and I can't seem to be able to do so.

I'm using the D-link DWL-G122 to connect. The network is WPA Personal encrypted. When I type in all the information and connect, it just hangs there saying "waiting for wireless Network Key for the wireless network "XXXXX""

Any help would be appreciated.

---

### Post by Crafty Kisses on 2008-09-29
Post the results of this command:
```
lshw -C network
```

---

### Post by DeviousLearning on 2008-09-29
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: a
       bus info: pci@0000:02:0a.0
       logical name: eth0
       version: 43
       serial: 00:05:5d:e9:95:2b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 latency=64 maxlatency=8 mingnt=3 module=via_rhine multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:13:46:63:a7:7c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

---

### Post by kolibri on 2008-09-30
Waiting for network key

I'm having the same problem, the only thing I've gleaned from the many people asking this question in different threads is that it is a bug?

I followed the instructions here:
[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)
Broadcom Wireless Setup for Hardy (Step by step)

to get my wireless set up.

I can now connect by wireless to unprotected networks in the vicinity, but when I try to connect to  my network, 
WEP 128 bit 
passphrase
open system,
I enter the passphrase, and it just gets stuck in a 'waiting for network key loop'.

My output to the command asked of the original poster:
lshw -C network

 *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:3d:21:c1
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 duplex=full firmware=N/A ip=192.168.1.44 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 01
       serial: 00:16:44:7b:e4:ab
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11bg


any help would be appreciated.

---

