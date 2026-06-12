---
title: "Setting xmit_hash_policy of layer3+4"
date: 2014-08-22
forum: Networking &amp; Wireless
---

### Post by daniel-oreilly on 2014-08-22
I'm trying to set an xmit_hash_policy of layer3+4 in my LACP bonds.  My interfaces file is:

# bond0 is the bonding NIC and can be used like any other normal NIC.
# bond0 is configured using static network information.
auto bond0
iface bond0 inet static
address 10.18.201.101
gateway 10.18.201.1
netmask 255.255.255.0
dns-nameservers 10.8.192.236 10.8.97.251 10.8.97.252
dns-search echostar.com
bond-mode active-backup
bond-miimon 100
bond-slaves em1 p3p1
bond-xmit_hash_policy layer3+4


#em1 is manually configured, and slave to the "bond0" bonded NIC
auto em1
iface em1 inet manual
bond-master bond0


#p3p1 ditto, thus creating a 2-link bond.
auto p3p1
iface p3p1 inet manual
bond-master bond0

When I reboot, here's what the bonding looks like:

# cat /proc/net/bonding/bond0
Ethernet Channel Bonding Driver: v3.7.1 (April 27, 2011)


Bonding Mode: fault-tolerance (active-backup)
Primary Slave: None
Currently Active Slave: em1
MII Status: up
MII Polling Interval (ms): 100
Up Delay (ms): 0
Down Delay (ms): 0


Slave Interface: em1
MII Status: up
Speed: 1000 Mbps
Duplex: full
Link Failure Count: 0
Permanent HW addr: ac:16:2d:71:79:34
Slave queue ID: 0


Slave Interface: p3p1
MII Status: up
Speed: 1000 Mbps
Duplex: full
Link Failure Count: 0
Permanent HW addr: d8:9d:67:1f:56:cc
Slave queue ID: 0


Any ideas?

---

### Post by Tom_Samplonius on 2014-11-19
xmit_hash_policy is meaningless in active-standby mode, as only link is used at a time.  There is no hashing used.

---

