---
title: "Very low WiFi range ubuntu 16.04"
date: 2018-02-21
forum: Networking &amp; Wireless
---

### Post by zywieckiom on 2018-02-21
Hello,
So basically speaking i woke up in the morning and my wifi do not connect unless im seating next to router. Also when by chance i do connect i have super slow internet connection. Only thing that might happens during the night is that battery got low.

  ```
*-network               
       description: Ethernet interface
       product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 07
       serial: 44:a8:42:ea:f1:92
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8106e-1_0.0.1 06/29/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:47 ioport:4000(size=256) memory:d2200000-d2200fff memory:d2000000-d2003fff
  *-network
       description: Wireless interface
       product: Wireless 3160
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: 83
       serial: e4:f8:9c:c4:f8:d3
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.13.0-32-generic firmware=17.608620.0 ip=192.168.1.191 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:51 memory:d2100000-d2101fff



```

---

### Post by kerry_s on 2018-02-21
have you tried restarting your router?

---

