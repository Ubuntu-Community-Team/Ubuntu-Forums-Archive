---
title: "WIFI AP-SOLO Misidentified as Atheros - Can't install Wifi"
date: 2007-08-05
forum: Networking &amp; Wireless
---

### Post by skinkone on 2007-08-05
Hello everyone, I'm fairly new to the Ubuntu experience - trying desperately to districate myself from XP by using Feisty.

I have an ASUS P5B motherboard with WiFi AP-SOLO wireless. The install CD that comes with the motherboard claims that it is a Realtek RTL8187.

I've tried using ndiswrapper to install the Realtek drivers, but to no avail. I tried using the Linux drivers and the longwinded instructions to install the Realtek, and still no dice.

System...Administration...Network does not even give me a wireless configuration option.

I believe part of the problem is that my card is recognized as an Atheros. Here is the (what I believe to be relevant) output of sudo lspci -vnn

02:00.0 Ethernet controller [0200]: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter [168c:001c] (rev 01)
        Subsystem: Unknown device [1a3b:1034]
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at fe9f0000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: [40] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [60] Express Legacy Endpoint IRQ 0
        Capabilities: [90] MSI-X: Enable- Mask- TabSize=1

I tried blacklisting ath-pci - nothing changes.

I think I need step-by-step directions for undoing my numerous attempts at installing the Realtek8187 driver from various sources, clearing out my ndiswrapper, and installing the correct driver. I've read that other users have had no problem with this card.

Can someone help me get rid of Windows XP forever??

Thanks!!!!

---

### Post by kevdog on 2007-08-05
Can you list lshw -C network, that would be a start

Thanks

---

### Post by skinkone on 2007-08-05
Here is the output...THANK YOU for answering my post so quickly!!!! I rechecked the driver in XP and it's AR5006, strange since the ASUS Wifi AP Solo CD tells me it's Realtek. I tried installing THAT driver and still no luck. What is wrong here?!?!?

  *-network               
       description: Ethernet interface
       product: L1 Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth0
       version: b0
       serial: 00:1a:92:bb:1c:c2
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1 driverversion=2.0.6 duplex=half firmware=N/A ip=1.42.74.61 latency=0 link=yes multicast=yes port=twisted pair speed=10MB/s
       resources: iomemory:feac0000-feafffff irq:17
  *-network UNCLAIMED
       description: Ethernet controller
       product: Atheros Communications, Inc.
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: iomemory:fe9f0000-fe9fffff irq:18

---

