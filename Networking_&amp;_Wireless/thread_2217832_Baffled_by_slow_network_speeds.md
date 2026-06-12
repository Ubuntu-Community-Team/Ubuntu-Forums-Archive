---
title: "Baffled by slow network speeds"
date: 2014-04-18
forum: Networking &amp; Wireless
---

### Post by seth7 on 2014-04-18
So lately I've had this issue with the network on my laptop, I can never achieve the 50 Mbps that my router is sending to my computer either through wired or wireless, I've tried different drivers, I've tried different kernel versions and different versions of ubuntu but no matter what, I'm being slowed down. I know it has nothing to do with my modem or my router because every other computer connected to the network can achieve the speed. Is there a possibility that my network PCI express card in my laptop could be failing? 

```
 *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 07
       serial: 00:8c:fa:a2:e3:d3
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8106e-1_0.0.1 06/29/12 ip=192.168.1.2 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:78 ioport:3000(size=256) memory:f1000000-f1000fff memory:f0000000-f0003fff
  *-network
       description: Wireless interface
       product: RTL8188EE Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 01
       serial: 64:5a:04:c2:29:66
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8188ee driverversion=3.13.0-24-generic firmware=N/A ip=192.168.1.5 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:79 ioport:2000(size=256) memory:f2800000-f2803fff
```

---

### Post by seth7 on 2014-04-18
[[IMG]http://www.speedtest.net/result/3447945483.png[/IMG]]("http://www.speedtest.net/my-result/3447945483")

here's just more data provided to show the estimated speeds it's achieving now instead of the 50/10 I'm paying for.

---

### Post by houstonbofh on 2014-04-18
Wireless or wired?

You could look at this... [http://itsfoss.com/speed-up-slow-wifi-connection-ubuntu/](http://itsfoss.com/speed-up-slow-wifi-connection-ubuntu/)

---

### Post by seth7 on 2014-04-18
That's wired, wireless is worse.

---

