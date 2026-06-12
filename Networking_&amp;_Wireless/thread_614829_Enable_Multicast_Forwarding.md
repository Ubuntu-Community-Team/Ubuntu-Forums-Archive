---
title: "Enable Multicast Forwarding"
date: 2007-11-16
forum: Networking &amp; Wireless
---

### Post by ah6511 on 2007-11-16
Hi,

I have a Ubuntu 7.1 box with 2 ethernet interface. I want to enable multicast forwarding. So I tried following with root account:
echo 1 > /proc/sys/net/ipv4/conf/all/mc_forwarding
echo 1 > /proc/sys/net/ipv4/conf/eth0/mc_forwarding
echo 1 > /proc/sys/net/ipv4/conf/eth1/mc_forwarding

But always gor permission denied.
I also tried with sysctl and got same thing.

I was able to do the following though:
echo 1 > /proc/sys/net/ipv4/ip_forwarding

Any reason? TIA

---

### Post by ah6511 on 2007-11-16
I just noticed /proc/sys/net/ipv4/conf/all/mc_forwarding is read only. But adding write privilieage under root still failed with permission denied.

---

