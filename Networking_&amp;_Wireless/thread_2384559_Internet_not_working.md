---
title: "Internet not working"
date: 2018-02-08
forum: Networking &amp; Wireless
---

### Post by sumit-sr on 2018-02-08
I've Lenovo Thinkpad E470

I've installed Ubuntu 14.04.5 LTS 64-bit

I'm unable to connect Wi-fi or Lan with my system.

Basic details are

**ifconfig:**
eth0      Link encap:Ethernet  HWaddr c8:5b:76:b9:28:e2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:49 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:145 errors:0 dropped:0 overruns:0 frame:0
          TX packets:145 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:10448 (10.4 KB)  TX bytes:10448 (10.4 KB)


**sudo****lshw**** -C network:**
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 10
       serial: c8:5b:76:b9:28:e2
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-3_0.0.1 04/23/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:122 ioport:d000(size=256) memory:f1104000-f1104fff memory:f1100000-f1103fff
  *-network UNCLAIMED
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 78
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f1000000-f1001fff

---

### Post by mörgæs on 2018-02-08
Hi, welcome to the fora.

Before investing more time in 14.04 I suggest that you consider a fresh install of 16.04.3 or 17.10.1, preferably the latter.

---

