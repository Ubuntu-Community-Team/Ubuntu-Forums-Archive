---
title: "Ralink WiFi adapter not working"
date: 2014-11-07
forum: Networking &amp; Wireless
---

### Post by dhruv3 on 2014-11-07
I recently used DBAN on my hdd and now when i install ubuntu on my hdd the network for ralink is not working.

it previously worked

---

### Post by Bucky Ball on 2014-11-07
Please provide the output of:

```
sudo lshw -C network
```

---

### Post by dhruv3 on 2014-11-07
i will after i install ubuntu

---

### Post by Bucky Ball on 2014-11-07
> **dhruv3 said:**
> ... now when i install ubuntu on my hdd the network for ralink is not working.


Sorry, thought you had. Install it and see if it is still a problem. If you are talking about it not working while in a Live boot, no, it probably won't.

---

### Post by dhruv3 on 2014-11-07
it says disabled, how do i re enable it?

---

### Post by Bucky Ball on 2014-11-07
Again, you are running a Live boot? Not sure you can. And again, give the output of the command I gave in post #2. Irrelevant whether you have Ubuntu installed or are running a Live boot for that. It will still tell us what we want to know.

---

### Post by dhruv3 on 2014-11-15
NOT LIVE BOOT

  *-network               
       description: Wireless interface
       product: Ralink corp.
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 00
       serial: 08:3e:8e:7f:fc:b6
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.16.0-23-generic firmware=0.34 ip=192.168.1.102 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:c2500000-c250ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 05
       serial: 84:34:97:6f:50:0f
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:3000(size=256) memory:c2404000-c2404fff memory:c2400000-c2403fff

---

