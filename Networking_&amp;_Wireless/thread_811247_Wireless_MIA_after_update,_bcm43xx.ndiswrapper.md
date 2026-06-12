---
title: "Wireless MIA after update, bcm43xx./ndiswrapper"
date: 2008-05-28
forum: Networking &amp; Wireless
---

### Post by sridenour on 2008-05-28
Last night I was prompted for an update to the kernel, as usual I let it go and do its thing not worried. Everything seemed fine with  networking(was still using ndis). Then I basically put it suspend mode, when it was awakened it had switched from using Ndiswarapper to B43 Restricted driver.
Since I have disabled the b43 hardware driver, but have been unable to get ndiswrapper to work. 
The second part of this is th GNOME Network Manager no longer even shows a wireless card as being there.
If I run lshw -C network 
```



 *-network:0                
description: Ethernet interface
product: BCM4401-B0 100Base-TX
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:02:00.0
logical name: eth0    
version: 02
serial: 00:e0:b8:93:c0:82
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes
 *-network:1
description: Network controller
product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
vendor: Broadcom Corporation
physical id: 4
bus info: pci@0000:02:04.0   
version: 02
width: 32 bits     
clock: 33MHz      
capabilities: bus_master  
configuration: driver=b43-pci-bridge latency=64 module=ssb
```

I can modprobe ndiswrapper and it will tell me the driver is installed and everything, yet nothing. Also kind of strange is the NetMngr thing. Any ideas what happened?

I picked a bad week to quit smoking.

---

