---
title: "Using which network interface my system will access internet?"
date: 2015-04-01
forum: Networking &amp; Wireless
---

### Post by arunkumargoge on 2015-04-01
I need three network interface in ubuntu server for my experiment on openstack particularly network node.  Of these three network interface which is used to access the internet ?
eth0 or eth1 or eth2 ?

because I want to configure like

eth0 - storage private network - no internet access
eth1 - management private network - no internet access
eth2 - internet access for updation

---

### Post by ian-weisser on 2015-04-01
The system will try all three to access the internet, and will use whichever seems to succeed first.

Your system maintains a *routing table*, a list of which interface connects to which range of IP addresses.
As long as your routing table is correct, you need not muck about with interfaces. The system will sort interfaces properly for you.
The routing table, using the 'ip' or 'route' commands needs to know the *default* gateway (upstream router IP address) for the internet.

---

