---
title: "HP Elitebook 840 G3 Slow NIC"
date: 2017-12-04
forum: Networking &amp; Wireless
---

### Post by kenneth.macleod on 2017-12-04
Hi,

I had Ubuntu 16.04 running perfectly on my laptop but somewhere along the way the ethernet has become much slower. If I install Windows 10 on the same laptop I get BT speedtest results of 74Mbps but on Ubuntu they range from 4-22Mbps. I have updated to 17.10 but it has not made any difference. The frustrating part is that it used to work perfectly. Does anyone have any ideas?

This is my network card info:

*-network
       description: Ethernet interface
       product: Ethernet Connection I219-LM
       vendor: Intel Corporation
       physical id: 1f.6
       bus info: pci@0000:00:1f.6
       logical name: enp0s31f6
       version: 21
       serial: a0:8c:fd:a1:e5:e0
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k duplex=full firmware=0.12-4 ip=192.168.1.1 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:279 memory:e1200000-e121ffff

---

