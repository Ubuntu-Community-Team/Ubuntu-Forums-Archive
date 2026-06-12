---
title: "Wired connection not working, Ubuntu 13.10"
date: 2015-02-17
forum: Networking &amp; Wireless
---

### Post by SurachaiRobotic on 2015-02-17
when connect wired cable to PC, but not happend ,same don't connect.
I try use " sudo lshw -C network "
output show below
```
hatori@hatori-X450CC:~$ sudo lshw -C network  *-network               
       description: Wireless interface
       product: RT3290 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: bc:85:56:10:e3:9b
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.11.0-26-generic firmware=0.37 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f7910000-f791ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.2
       bus info: pci@0000:04:00.2
       logical name: eth0
       version: 0a
       serial: 74:d0:2b:be:7e:37
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8411-1_0.0.3 06/18/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:d000(size=256) memory:f7810000-f7810fff memory:f2100000-f2103fff
hatori@hatori-X450CC:~$

```
[IMG]http://imageshack.com/a/img909/8900/NLPVBx.jpg[/IMG]

Help me plz. Thank you.

---

### Post by sammiev on 2015-02-17
13.10 has reached "End Of Life" no more security updates are available as well as other packages. I would suggest installing 14.04LTS which is supported for years to come.
The newer kernels may just have the fix you need for your wired connection.

---

### Post by SurachaiRobotic on 2015-02-17
OK. i will install new version. Thx :p

---

### Post by sammiev on 2015-02-17
> **SurachaiRobotic said:**
> OK. i will install new version. Thx :p

Sorry, I should of added.

Welcome to the forums. ):P

---

