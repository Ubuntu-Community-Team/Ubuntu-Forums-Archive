---
title: "Not starting wireless device"
date: 2007-12-02
forum: Networking &amp; Wireless
---

### Post by Horizontal Dave on 2007-12-02
I've starting using 7.10 on my laptop and it's been great so far, but I'm still having one annoying problem.

If I shut down, I have to restart in windows first in order for the wireless device to start and then restart into ubuntu.

It's a Fujitsu Amilo Pro, the wireless works fine once I've started up into windows.

Here's what I get if I enter sudo lshw -C network

Not Working:

  *-network               
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=ipw3945 latency=0 module=ipw3945
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:0a:07.0
       logical name: eth0
       version: 10
       serial: 00:0a:e4:bb:df:55
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s

Working:

*-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 02
       serial: 00:13:02:ef:45:58
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp.ubuntu1 firmware=14.2 1:0 () ip=192.168.1.101 latency=0 link=yes module=ipw3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:0a:07.0
       logical name: eth0
       version: 10
       serial: 00:0a:e4:bb:df:55
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s


Any ideas  on how I can get this working so I can completely dump windows 

Thanks

---

### Post by Floppyjoe on 2007-12-02
Do you have the linux-restricted-modules installed?

---

### Post by csat on 2007-12-02
Chck this thread.

[http://ubuntuforums.org/showthread.php?t=202834&highlight=linksys](http://ubuntuforums.org/showthread.php?t=202834&highlight=linksys)

---

### Post by Horizontal Dave on 2007-12-02
I've got the restricted drivers installed and working, it connects just fine to my network, but only if I boot into windows first and then restart into ubuntu.

I don't believe it's a driver issue, more that the hardware is not being told to start up.

The keys on my laptop for starting and stopping the wireless are not functioning under ubuntu.

---

