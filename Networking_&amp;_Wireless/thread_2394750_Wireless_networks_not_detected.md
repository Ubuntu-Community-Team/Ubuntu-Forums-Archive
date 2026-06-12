---
title: "Wireless networks not detected"
date: 2018-06-20
forum: Networking &amp; Wireless
---

### Post by sreetamdas on 2018-06-20
After updating my Ubuntu as usual, my wireless networks are suddenly not showing at all.

Here's what I got so far:

on executing ```
sudo lshw -class network
```, I get the following:
```
  *-network UNCLAIMED     
       description: Network controller
       product: BCM43142 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:b5500000-b5507fff
  *-network
       description: Ethernet interface
       product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eno1
       version: 08
       serial: 6c:c2:17:7a:6a:56
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8106e-2_0.0.1 04/23/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:19 ioport:4000(size=256) memory:b5404000-b5404fff memory:b5400000-b5403fff
  *-network
       description: Ethernet interface
       physical id: 3
       logical name: enp0s29u1u2
       serial: 8e:33:d3:5c:82:17
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.90 link=yes multicast=yes
```

on 
```

uname -r

```
I get:
```
4.15.0-24-generic
```

and on 
```
sudo dpkg -s bcmwl-kernel-source | grep Version
```
I get:
```
Version: 6.30.223.271+bdcom-0ubuntu1~1.2


```

---

