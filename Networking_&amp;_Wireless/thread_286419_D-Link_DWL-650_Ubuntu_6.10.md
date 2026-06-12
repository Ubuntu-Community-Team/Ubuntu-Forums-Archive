---
title: "D-Link DWL-650 Ubuntu 6.10"
date: 2006-10-27
forum: Networking &amp; Wireless
---

### Post by JoeNobody on 2006-10-27
Been through the thread, tried many things and no luck.
Hard line ethernet no problem. I installed the WIndows Wireless Wrapper through SYnaptic. Got the latest .inf from D-Link and installed it. THe Windows Wireless program has the driver but says Hardware not detected.

I can goto System > Admin > Network and activate the wireless card. Go in and force to use the Wlan0, it doesnt show up in the list, and I will see the strength meter, but status will remain undetected.

Chipset - 
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)
        Subsystem: D-Link System Inc Unknown device 3302
        Flags: bus master, medium devsel, latency 64, IRQ 177
        I/O ports at 2c00 [size=256]
        Memory at 36000000 (32-bit, non-prefetchable) [size=512]
        Capabilities: <access denied>

Here output for sudo lshw -businfo
pci@06:00.0   wlan0      network        RTL8180L 802.11b MAC

output for Network Class
 *-network               
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@00:04.0
       logical name: eth0
       version: 90
       serial: 08:00:46:c4:b5:67
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=sis900 driverversion=v1.08.09 Sep. 19 2005 duplex=full ip=192.168.1.105 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:2000-20ff iomemory:f4004000-f4004fff irq:225
  *-network DISABLED
       description: Wireless interface
       product: RTL8180L 802.11b MAC
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@06:00.0
       logical name: wlan0
       version: 20
       serial: 00:0d:88:65:af:c6
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 multicast=yes wireless=802.11b
       resources: ioport:2c00-2cff iomemory:36000000-360001ff irq:177


Help...](*,)

---

### Post by JoeNobody on 2006-10-27
Update - 
   I found a great thread with the Realtek drivers posted on it [Here is that post.]("http://ubuntuforums.org/showthread.php?t=96319")

I downloaded the dirvers and installed the .inf into the ndsiwrapper gui and this time I get Hardware Detected = Yes.

Thats closer than before, but I still cannot get it to detect ESSID broadcasts nor connect to my network.

Now what?

---

