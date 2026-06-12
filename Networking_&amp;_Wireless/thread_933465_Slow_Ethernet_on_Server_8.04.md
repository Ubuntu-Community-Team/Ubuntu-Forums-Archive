---
title: "Slow Ethernet on Server 8.04"
date: 2008-09-29
forum: Networking &amp; Wireless
---

### Post by dejan.b on 2008-09-29
I recently installed Ubuntu Server 8.04 on DELL PowerEdge Server. It worked OK, except that the transfer rate is arround 1000 kbytes/s and then it drops to a crawl: 250kbytes/s. So, I tried various things and in the end I changed the network card. The first test was great, more than 9000kbytes/s but after a week the transfer dropped to around 2500kbytes/s. All the tests were done with only my PC connected to that server. The transfer starts OK with > 9500 but it then drops down.

Now, I'm not sure how to handle this. What is causing the packets to be dropped? How can I see what is going on here? mii-diag says everything is fine. Here is the output of lshw -C network:

```
# lshw -C network
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5703X Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@0000:01:06.0
       logical name: eth0
       version: 02
       serial: 00:10:18:06:78:d1
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pcix pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full firmware=5703-v2.21a ip=10.0.1.233 latency=64 link=yes mingnt=64 module=tg3 multicast=yes port=twisted pair speed=1GB/s
```

Any ideas?

D.B.

---

