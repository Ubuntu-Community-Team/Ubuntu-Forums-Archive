---
title: "How to setup wireless Connection?"
date: 2008-11-17
forum: Networking &amp; Wireless
---

### Post by golusweet on 2008-11-17
I have bsnl dataone WA3002G4 router.

I can't connect through wifi in ubuntu.

here is output of 
lshw -C network              
       description: Network controller
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:73:2c:b9:77
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 2e:bc:5e:32:2e:fe
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

using PPP Over Ethernet

and using WPA pre shared key in wifi.

---

### Post by Olivier2371 on 2008-11-17
Hi there,

Can't you install the driver through the hardware drivers?

System->Administration->Hardware Drivers

If you can choose Broadcom B43 Wireless Driver, with the option TKIP instead of automatic.

Hope this helps.

---

