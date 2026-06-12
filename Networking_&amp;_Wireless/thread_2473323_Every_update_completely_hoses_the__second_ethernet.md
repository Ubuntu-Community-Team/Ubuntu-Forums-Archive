---
title: "Every update completely hoses the  second ethernet port (RealTek RTL8125)"
date: 2022-03-31
forum: Networking &amp; Wireless
---

### Post by robertwk on 2022-03-31
This is becoming frustrating every single time that this happens, and I'm reaching my limit with this issue.

I know that the RealTek 8169 driver issues were supposed to fix this, but whenever there are Ubuntu updates pushed it always results in the 2.5 Gb Ethernet driver always becoming mysteriously unclaimed, and it's becoming a struggle every single time to fix it.

```
mparks2011@Melissa-Photo-PC:~$ sudo lshw -C network  
*-network DISABLED        
       description: Wireless interface
       product: Wireless 7265
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:23:00.0
       logical name: wlp35s0
       version: 59
       serial: XX:XX:XX:XX:XX:XX
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=5.4.0-107-lowlatency firmware=29.1654887522.0 latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:56 memory:fc400000-fc401fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:24:00.0
       logical name: enp36s0
       version: 15
       serial: XX:XX:XX:XX:XX:XX
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 duplex=full firmware=rtl8168h-2_0.0.2 02/26/15 latency=0 link=yes multicast=yes port=MII slave=yes speed=1Gbit/s
       resources: irq:35 ioport:e000(size=256) memory:fc304000-fc304fff memory:fc300000-fc303fff
  *-network UNCLAIMED
       description: Ethernet controller
       product: RTL8125 2.5GbE Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:2a:00.0
       version: 04
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd cap_list
       configuration: latency=0
       resources: ioport:d000(size=256) memory:fc200000-fc20ffff memory:fc210000-fc213fff
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: bond0
       serial: XX:XX:XX:XX:XX:XX
       size: 1Gbit/s
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=bonding driverversion=3.7.1 duplex=full firmware=2 ip=192.168.0.137 link=yes master=yes multicast=yes speed=1Gbit/s

```

```

mparks2011@Melissa-Photo-PC:~$ inxi -N
Network:   Device-1: Intel Wireless 7265 driver: iwlwifi 
           Device-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet driver: r8169 
           Device-3: Realtek RTL8125 2.5GbE driver: N/A 

```

For reference, this is not about wifi. The r8169 driver simply *does not work whatsoever*. I have to routinely reinstall the r8168 driver for my networking connection to work correctly, and then update my /etc/netplan/ configuration, /etc/network/interfaces and anywhere else where I've referenced the ethernet port because the logical name keeps changing after I do this.

Is there a way to permanently fix this problem? I'm really desperate about this.

---

