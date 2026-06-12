---
title: "Ralink wireless card problem"
date: 2008-10-17
forum: Networking &amp; Wireless
---

### Post by chick on 2008-10-17
Hello there,

I got a Gateway M-6337 notebook for my dad and had successfully installed Hardy on it but haven't been able to get wireless working. The problem is the network card is Ralink but it doesn't say which model, neither in Vista nor Ubuntu :(

In Vista, it says Ralink 802.11n Wireless Card in Device Manager.

Here are some output from Ubuntu:
```
$ sudo lshw -C Network
  *-network UNCLAIMED     
       description: Network controller
       product: RaLink
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: 00:e0:b8:fb:7e:44
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.128.5 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s

```

```
$ lspci -v
[...]
02:00.0 Network controller: RaLink Unknown device 0781
	Subsystem: Unknown device 1a32:0302
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at f4000000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
[...]

```

Any ideas?

---

