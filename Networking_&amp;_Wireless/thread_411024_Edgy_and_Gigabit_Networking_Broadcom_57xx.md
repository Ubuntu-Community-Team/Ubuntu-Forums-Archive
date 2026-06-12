---
title: "Edgy and Gigabit Networking Broadcom 57xx"
date: 2007-04-16
forum: Networking &amp; Wireless
---

### Post by tygrel on 2007-04-16
My office is wired with Gigabit and I got a new Optiplex 745 preinstalled with M$.  I rebelled and put some Ubuntu goodness on it for use with VMware server.  

Its all working perfectly for me now, except it seems that my networking is running slow (like 100mb). Im having troubble figuring out if I am running 1000mb.  I have a default install of 6.10 server... Here is what I have tried:

```
 sudo lshw -C network
Password:
  *-network               
       description: Ethernet interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:24:14:e7
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=tg3 driverversion=3.59.1 duplex=full firmware=5754-v3.15 ip=10.55.209.91 link=yes multicast=yes port=twisted pair speed=1GB/s
       resources: iomemory:dfaf0000-dfafffff irq:58
```

```
sudo mii-tool
Password:
eth0: negotiated 100baseTx-FD flow-control, link ok

```

one tool indicates that I have 1000mb, the other 100mb.  Does anyone know how I would change my link speed to 1000?

Thanks ...

---

### Post by chili555 on 2007-04-16
```
sudo ethtool eth0 -s 1000
```However, I think this:```
negotiated 100baseTx-FD flow-control, link ok
```is telling you that eth0 has agreed to 100 with the router or switch. I think hammering it to 1000 will create new problems.

---

