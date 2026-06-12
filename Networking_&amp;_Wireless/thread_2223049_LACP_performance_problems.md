---
title: "LACP performance problems"
date: 2014-05-09
forum: Networking &amp; Wireless
---

### Post by SeaKing on 2014-05-09
Hey,
I've currently set up a bond with LACP on my Router using two Intel Gigabit Nics and a LevelOne switch. Now the bond is working, but the tranferspeed is dramaticaly slow, I get around 12MB/s on a DualGigabit bond.

Here'S my config:
```

**/etc/modules:**
bonding max_bonds=1 mode=4 ad_select=2 xmit_hash_policy=1

**/etc/network/interfaces**
auto bond0
    iface bond0 inet static
    address 192.168.1.11
    netmask 255.255.255.0
    gateway 192.168.1.11
    slaves eth0 eth1

   #additional vlan config for bond0

**cat /proc/net/bonding/bond0**
Ethernet Channel Bonding Driver: v3.7.1 (April 27, 2011)

Bonding Mode: IEEE 802.3ad Dynamic link aggregation
Transmit Hash Policy: layer3+4 (1)
MII Status: up
MII Polling Interval (ms): 100
Up Delay (ms): 0
Down Delay (ms): 0

802.3ad info
LACP rate: slow
Min links: 0
Aggregator selection policy (ad_select): count
Active Aggregator Info:
    Aggregator ID: 1
    Number of ports: 2
    Actor Key: 17
    Partner Key: 8
    Partner Mac Address: 00:11:6b:f2:cb:72

Slave Interface: eth0
MII Status: up
Speed: 1000 Mbps
Duplex: full
Link Failure Count: 0
Permanent HW addr: 00:22:4d:a9:87:7d
Aggregator ID: 1
Slave queue ID: 0

Slave Interface: eth1
MII Status: up
Speed: 1000 Mbps
Duplex: full
Link Failure Count: 0
Permanent HW addr: 00:22:4d:a9:87:81
Aggregator ID: 1
Slave queue ID: 0
```

Is there an config mistake or what can I do to increase speed?

---

