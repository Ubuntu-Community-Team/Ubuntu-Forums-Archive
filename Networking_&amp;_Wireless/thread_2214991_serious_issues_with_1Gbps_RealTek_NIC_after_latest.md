---
title: "serious issues with 1Gbps RealTek NIC after latest Lubuntu update"
date: 2014-04-04
forum: Networking &amp; Wireless
---

### Post by zme-ul on 2014-04-04
yesterday, or was it 2 days ago (??) Lubuntu (13.10) performed an update - everything looked OK


in the morning when I powered up the PC I noticed extremely strange behavior of the network - the connection was up and down constantly
not a linux guru here, but i discovered that manually switching the speed to 100Mbps fixes the issue, but I need my 1Gbps ..

what do I do? this is driving me nuts :(


the thing is, readout for **sudo lshw -numeric -C network -sanitize **returns:
```
*-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10EC:8168]
       vendor: Realtek Semiconductor Co., Ltd. [10EC]
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: [REMOVED]
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=[REMOVED] latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:40 ioport:e800(size=256) memory:dffff000-dfffffff memory:dffc0000-dffdffff

```
RTL8168 with 8169 driver?!




le: **SOLVED!**

I read a couple of threads on the forums here, turns out that my NIC is actually r8168 and I installed the latest drivers for it - no change
the solution is insane ... unplug the power cord, press the power button a couple of times to drain the capacitors and put the power cord back in the PSU - it works! :P

---

