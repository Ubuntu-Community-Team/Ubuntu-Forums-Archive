---
title: "slow to spotty wireless connection"
date: 2015-08-19
forum: Networking &amp; Wireless
---

### Post by hockey98762 on 2015-08-19
i just purchased a new dell and installed ubuntu 14.04 on it.  A few google searches led me to run the command
sudo lshw -C network

This is the output:

  *-network               
       description: Wireless interface
       product: Wireless 7265
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 59
       serial: 5c:e0:c5:42:31:b9
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.13.0-62-generic firmware=22.24.8.0 ip=192.168.1.7 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:69 memory:f7200000-f7201fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.1
       bus info: pci@0000:07:00.1
       logical name: eth0
       version: 12
       serial: 20:47:47:17:47:45
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8411-2_0.0.1 07/08/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:65 ioport:e000(size=256) memory:f7114000-f7114fff memory:f7110000-f7113fff


Some mor digging dropped me at [https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi](https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi)

Finding my model number (7265) let me to this file [iwlwifi-7265-ucode-22.24.8.0.tgz]("https://wireless.wiki.kernel.org/_media/en/users/drivers/iwlwifi-7265-ucode-22.24.8.0.tgz") because i have kernel 3.13.0.62 and firmware 22.4.8.0. 
Should installing this file update my system?  If so, where do I put the unzipped files?  Doing this it gave the error that 
While I don't remember where I found the command, the site suggested I run:   sudo rmmod iwlwifi

which gave me the error:
ERROR: Module iwlwifi is in use by: iwlmvm

If anyone has any suggestions, I'd be happy to entertain what to do next!

Thanks

John

---

### Post by sandyd on 2015-08-19
Moved to *Networking and Wireless*

---

