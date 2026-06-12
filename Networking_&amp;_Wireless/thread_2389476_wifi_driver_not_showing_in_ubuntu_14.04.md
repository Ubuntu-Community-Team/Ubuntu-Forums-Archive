---
title: "wifi driver not showing in ubuntu 14.04"
date: 2018-04-17
forum: Networking &amp; Wireless
---

### Post by shubham-kira on 2018-04-17
I have installed Ubuntu 14.04 in my new HP laptop but wireless driver is not showing up in Software and Updates.

**Following is the output of the command lspci -nnk | grep -iA2 net** ;
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Hewlett-Packard Company Device [103c:832b]
    Kernel driver in use: r8169
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:d723]
    Subsystem: Hewlett-Packard Company Device [103c:8319]

**And the output of the command sudo lshw -C network**:
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 15
       serial: 80:ce:62:14:35:b2
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168h-2_0.0.2 02/26/15 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:127 ioport:4000(size=256) memory:b1104000-b1104fff memory:b1100000-b1103fff
  *-network UNCLAIMED
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:3000(size=256) memory:b1000000-b100ffff
  *-network
       description: Ethernet interface
       physical id: 3
       logical name: usb0
       serial: 02:6a:33:0c:54:02
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.54 link=yes multicast=yes

** Please help**

---

### Post by chili555 on 2018-04-17
Please see: [https://github.com/jeremyb31/rtl8723de](https://github.com/jeremyb31/rtl8723de)

If you installed 14.04, I assume that your kernel version is 4.10 or below; verify:```
uname -r
```

---

