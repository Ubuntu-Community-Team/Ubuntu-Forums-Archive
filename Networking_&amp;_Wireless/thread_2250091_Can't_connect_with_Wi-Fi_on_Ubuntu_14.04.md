---
title: "Can't connect with Wi-Fi on Ubuntu 14.04"
date: 2014-10-26
forum: Networking &amp; Wireless
---

### Post by godzillathecing92 on 2014-10-26
So I installed Ubuntu for the first time yesterday, and it seems to have a problem with the WiFi - it detects the networks (mine included) it usually detects on my Windows, but whenever I connect it just loads it for a while and then disconnects.

sudo lshw -C network:

```

PCI (sysfs)  
  *-network 
description: Ethernet interface
 
product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
vendor: Realtek Semiconductor Co., Ltd.  
physical id: 0 
bus info: pci@0000:04:00.0   
logical name: eth0 
version: 06    
serial: 50:e5:49:50:04:40    
size: 10Mbit/s
capacity: 1Gbit/s   
width: 64 bits   
clock: 33MHz     
capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation  
configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s  
resources: irq:42 ioport:ee00(size=256) memory:fbeff000-fbefffff memory:fbef8000-fbefbfff
  *-network    
description: Wireless interface  
product: RT3060 Wireless 802.11n 1T/1R  
vendor: Ralink corp.  
physical id: 0    
bus info: pci@0000:06:00.0     
logical name: wlan0     
version: 00      
serial: 00:1f:1f:b8:da:52     
width: 32 bits     
clock: 33MHz      
capabilities: pm bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=rt2800pci driverversion=3.13.0-32-generic firmware=0.34 latency=32 link=no maxlatency=4 mingnt=2 multicast=yes wireless=IEEE 802.11bgn   
resources: irq:19 memory:fbdf0000-fbdfffff

```

Anyone got a solution? :P

All help appreciated, thanks in advance.

EDIT: Funny that it says rt2800pci, I think my Edimax EW 7711in is rt3060pci or something along these lines..

---

