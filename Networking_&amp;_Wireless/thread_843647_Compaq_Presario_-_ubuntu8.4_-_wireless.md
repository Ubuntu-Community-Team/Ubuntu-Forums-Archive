---
title: "Compaq Presario - ubuntu8.4 - wireless"
date: 2008-06-28
forum: Networking &amp; Wireless
---

### Post by Silvernail on 2008-06-28
I have Compaq Presario laptop with ubuntu8.4 installed. Following some instruction on another thread in this folder. Here is a screen shot. Does it look correct so far?

> dave@gadabout:~$ sudo modprobe -r b43 ssb bcm43xx ndiswrapper
[sudo] password for dave: 
dave@gadabout:~$ sudo depmod -ae
dave@gadabout:~$ sudo modprobe ndiswrapper
dave@gadabout:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 8
       bus info: pci@0000:08:08.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:c5:d9:e0
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.103 latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
dave@gadabout:~$ 



---

### Post by Midwest-Linux on 2008-06-28
What is your model number? I have the Compaq Presario and use the Atheros 5007 on the FT762NR.

---

### Post by Silvernail on 2008-06-28
C-500

06:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

This device 06 shows up in an unable to allocate bridge error at bootup time.

---

