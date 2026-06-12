---
title: "Ethernet and wireless don't work"
date: 2016-04-06
forum: Networking &amp; Wireless
---

### Post by nllsdfx on 2016-04-06
I've installed Ubuntu but my Internet doesn't work.  Google didn't help me. I can't connect Internet using either cable and Wi Fi adapter 
 *-network               
       description: Ethernet interface
       product: AR8152 v2.0 Fast Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: c1
       serial: dc:0e:a1:6b:c8:1a
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.1-NAPI latency=0 link=no multicast=yes port=twisted pair
       resources: irq:30 memory:e0500000-e053ffff ioport:2000(size=128)
  *-network DISABLED
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlan0
       version: 00
       serial: 60:d8:19:2f:cc:ac
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=4.2.0-27-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:e0400000-e040ffff

---

### Post by TheFu on 2016-04-06
Lets try to get the wired connection working first.  Thanks for posting that information.  It shows  driver=atl1c driverversion=1.0.1.1-NAPI are being used.
Please follow the instructions here and post the output requested:  [http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking)  It will tell us where the issue lies -
* on the PC
* PC configuration
* on the router
* router configuration
* or in the cabling

Basically, open a terminal, type/copy/paste the commands shown, then copy/paste the output (with the cmd) back here.  Would really help if "code tags" were used - so things line up correctly too.

---

### Post by nllsdfx on 2016-04-06
Sorry for bad code style! I had only my smartphone to access internet and couldn't use 'code' tag. So I solved problem: The laptop I had problem with was broken and I had reparied it. But while reparing I accidentally displaced a wire. And strange thing is that Win8 or 10 were accessing internet fine while Ubuntu or win7 not.

So thank you for quick reply.

---

