---
title: "Lenovo Legion Y540 wifi adapter not found Ubuntu 18.04"
date: 2021-04-13
forum: Networking &amp; Wireless
---

### Post by jiaqiaozhang on 2021-04-13
Hi Folks. [COLOR=#242729][FONT=Arial]I'v been struggling with the wifi adapter problem for my legion Y540 on the ubuntu 18.04 system. I have tried a lot solutions but none is working.[/FONT][/COLOR][COLOR=#242729][FONT=Arial]The output of lshw -C Network

```
[/FONT][/COLOR]
*-network UNCLAIMED       
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 14.3
       bus info: pci@0000:00:14.3
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
       resources: memory:c2498000-c249bfff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: enp7s0
       version: 15
       serial: 54:05:db:f8:4f:15
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 duplex=full firmware=rtl8168h-2_0.0.2 02/26/15 ip=10.128.96.12 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:18 ioport:3000(size=256) memory:c2204000-c2204fff memory:c2200000-c2203fff[COLOR=#242729][FONT=Arial]```

Does anyone know how to solve the problem? Please help me about this. Thank you in advance![/FONT][/COLOR]

---

