---
title: "Ubuntu 15.10 wifi suddently droped"
date: 2016-12-26
forum: Networking &amp; Wireless
---

### Post by saravanan6 on 2016-12-26
Hi guys,

I am using Acer laptop Ubuntu 15.10 version. My wifi was work without any issue till Friday. Now suddenly wifi removed and I not able to see wifi. Please help me.  

```
itbeeszone@itbeeszone-Aspire-E5-573:~$ iwconfig
enp2s0    no wireless extensions.


lo        no wireless extensions.


virbr0    no wireless extensions.


virbr0-nic  no wireless extensions.

```

```

itbeeszone@itbeeszone-Aspire-E5-573:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 15
       serial: 2c:60:0c:f5:0d:3a
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168h-2_0.0.2 02/26/15 ip=192.168.1.39 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:46 ioport:3000(size=256) memory:c1204000-c1204fff memory:c1200000-c1203fff
  *-network UNCLAIMED
       description: Network controller
       product: Qualcomm Atheros
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 30
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:c1000000-c11fffff
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: virbr0-nic
       serial: 52:54:00:05:eb:50
       size: 10Mbit/s
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=tun driverversion=1.6 duplex=full link=no multicast=yes port=twisted pair speed=10Mbit/s

```

---

### Post by wildmanne39 on 2016-12-26
I recommend that you upgrade to 16.04 because 15.10 has reached EOL and their will not be anymore updates not even security so your computer is at risk.

---

### Post by saravanan6 on 2016-12-26
Thanks for the reply. I will upgrade and check now.

---

### Post by saravanan6 on 2016-12-26
I upgrade my OS 15.10 to 16.04 and now wifi working perfectly. thanks!:D

---

### Post by Bucky Ball on 2016-12-26
Excellent! See the last blue link in my signature to mark the thread as solved and help others. Good luck. :)

---

