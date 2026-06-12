---
title: "No Wireless | Ubuntu 9.04 | HP Pavil Dv5000"
date: 2009-07-02
forum: New to Ubuntu
---

### Post by Xarok on 2009-07-02
No Wireless in Ubuntu 9.04 on HP Pavilion Dv5000.
Anyone got any solutions?

Thanks guys!

---

### Post by nothingspecial on 2009-07-02
Some info about the card would help

```
sudo lshw -C network
``` Please

---

### Post by Xarok on 2009-07-03
*-network:0            
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:f7:a1:70
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=128 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:a5:75:ec:a4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: c2:25:bd:9f:d5:a4
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by DiegoTc on 2009-07-04
Probably you haven't activate the private broadcom software.
Okay go to System------Administration------Hardware Controlers
There it should appear the private broadcom drivers, you activate them and your wifi card should work fine.

---

### Post by Xarok on 2009-07-07
There was nothing available : (

---

### Post by Xarok on 2009-07-09
Any other suggestions?

---

### Post by LookTJ on 2009-07-09
> **Xarok said:**
> There was nothing available : (
Just wondering, were you checking when connected via an RJ-45(ethernet cable)?

---

### Post by nothingspecial on 2009-07-09
Try this

```
sudo apt-get install b43-fwcutter
```

Then restart.

---

