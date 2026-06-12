---
title: "How to know what speed is my LAN port"
date: 2018-10-10
forum: Networking &amp; Wireless
---

### Post by webmiester on 2018-10-10
Hi guys,

Is there some sort of software or benchmark I can use to figure out how fast my LAN port is?  I have a few computers here with built in LAN ports but I don't know what speed their LAN ports are.

---

### Post by Dennis N on 2018-10-11
One possible way is from **inxi** which is run from terminal. For network information, **inxi -n** will include the max supported speed on each device. 
```
[dmn@Roxanne ~]$ inxi -n
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  driver: r8168 
  IF: enp2s0 state: up **speed: 1000 Mbps** duplex: full mac: 3c:ae:c5:35:42:ca 

```

---

