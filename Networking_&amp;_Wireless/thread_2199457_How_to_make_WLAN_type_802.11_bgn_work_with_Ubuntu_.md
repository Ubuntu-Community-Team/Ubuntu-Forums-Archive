---
title: "How to make WLAN type 802.11 b/g/n work with Ubuntu 12.04"
date: 2014-01-14
forum: Networking &amp; Wireless
---

### Post by Clopper Almon on 2014-01-14
I recently bought a HP Pavilion 15 e043cl Notebook (not Sleekbook, which is Ubuntu certified) with Windows 8 installed. I defeated Secure Boot and got Ubuntu 12.04.4 LTS installed and working except for the WiFi connection. According to HP specifications, the WLAN type is 802.11 b/g/n, On the Linux wireless LAN support page on the Internet, this device is marked green under "works with linux". However, in the comments column, it notes "In kernel tree; needs firmware." I presume that means I need to download a firmware file and put it in lib/firmware, or something like that. Does anyone know what file and where to get it and where to put it?  I think the manufacturer is Realtek.  

Many thanks for any help,

---

### Post by Bucky Ball on 2014-01-14
Open a terminal and:

sudo lshw -C network

Post the result here.

---

### Post by Clopper Almon on 2014-01-14
Thanks for the reply. Here are the results. You will see that the device is a RTL8188EE. There are several threads about handling this device, but the solutions offered -- involving compilations that must be repeated with each Ubuntu upgrade -- are so complicated that it is hard to imagine how it  could be rated "Linux Green". Here are the results: 


```
joan@joan-HP-Pavilion-15-Notebook-PC:~$ sudo lshw -C network
[sudo] password for joan: 
  *-network UNCLAIMED     
       description: Network controller
       product: RTL8188EE Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:3000(size=256) memory:f0200000-f0203fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 07
       serial: d4:c9:ef:60:e4:ec
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8106e-1_0.0.1 06/29/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:2000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff memory:f0400000-f040ffff

```

---

### Post by chili555 on 2014-01-14
> There are several threads about handling this device, but the solutions offered -- involving compilations that must be repeated with each Ubuntu upgradeIt's actually pretty easy. However, you could sit back and wait a couple of years until the driver is included in the mainline kernel; you could buy a new supported device; you could get a 30 ft. ethernet cable; or you could simply do this: [http://askubuntu.com/questions/337785/wireless-not-working-on-toshiba-satellite-c55-a5281](http://askubuntu.com/questions/337785/wireless-not-working-on-toshiba-satellite-c55-a5281)

---

