---
title: "Slow LAN NAS speed on Bionic 18.04.1 Realtek 8168"
date: 2018-08-08
forum: Networking &amp; Wireless
---

### Post by blackbyron123 on 2018-08-08
Hello. I recently upgraded from 17.10 to 18.04.1.  

My network is built in and it is Realtek 8111/8168/8411. 

The problem is that whenever I transfer from/to Samba Server, I am getting the maximum of 11 MB/s.  It is like my Ethernet card behaves as running at 100 Mbit/s instead of 1 Gbit/s.  I was able to get the transfer speed that is more than 40 MB/s on the earlier versions.  I tried installing r8168-dkms, but still no luck.

Could anyone tell me what is the cause of it?  

> sudo lshw -C network
  *-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 03
       serial: d0:27:88:3b:52:3b
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.045.08-NAPI duplex=full ip=192.168.1.55 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:24 ioport:e800(size=256) memory:fdfff000-fdffffff memory:fdff8000-fdffbfff memory:febe0000-febfffff
fasternas@fasternas-TPS01:~/Downloads$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.1 LTS
Release:    18.04
Codename:    bionic

Thanks

---

