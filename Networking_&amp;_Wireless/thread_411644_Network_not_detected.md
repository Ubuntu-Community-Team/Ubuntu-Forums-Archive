---
title: "Network not detected"
date: 2007-04-17
forum: Networking &amp; Wireless
---

### Post by vishwajit1 on 2007-04-17
Dear All

I have installed Ubuntu on a HP 7600, Pentium D based machine, and while installing Network configuration (DHCP) was detected properly. But after installation it is unable to detect "eth0" and not to connect to network.

Any help

---

### Post by Kobalt on 2007-04-17
Can you please post the output of the following command line : ```
ifconfig
```

---

### Post by vishwajit1 on 2007-04-18
vjs@ubuntu:~$ ifconfig
lo          Link encap: Local Loopback
            inet addr:127.0.01    Mask:255.0.0.0
            inet6 addr: ::1/128  Scope:Host
            UP LOOPBACK RUNNING     MTU:16436    Metric:1
            RX packets:1588   errors:0   dropped:0   overruns:0  frame:0
            TX packets:1588   errors:0   dropped:0   overruns:0  carrier:0
            collisions:0   txqueuelen:0
            RX bytes:1835940 (1.7 MiB)   TX bytes:1835940  (1.7 MiB)

---

### Post by josephus on 2007-04-18
that wasn't very helpful.  try 

```
lshw -C network
```

---

### Post by vishwajit1 on 2007-04-19
vjs@ubumtu:!$ sudo lshw -C network
Password:
*- network DISABLED
description: Ethernet interface
product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
vendor: Broadcom Corporation
physical id: 0
bus info: pcie3f:00.0
logical name: eth0
version: 01
serial: 00.17.a4.f2.51.ae
capacity: 1GB/s
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet_physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegociation
configuration: autonegociation=on broadcast=yes drives=tg3 driverversion=3.31 duplex=half link-no multicast=yes port=twisted pair
resources: iamemory=e0500000-e050ffff irq:17

---

