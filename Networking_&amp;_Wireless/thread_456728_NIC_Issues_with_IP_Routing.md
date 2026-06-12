---
title: "NIC Issues with IP Routing"
date: 2007-05-28
forum: Networking &amp; Wireless
---

### Post by davidsampson on 2007-05-28
Ok, so here's the deal.  I have a wireless router (10.0.1.1) connected to the internet, with static IP's enabled.  I have this pc (on ubuntu) which has two nics.  The first is a wireless card (ath0, 10.0.1.4), and the second is wired (eth1, 10.0.1.5).  I have an OpenBSD box (ne3, 10.0.1.6), wired into eth1 of this pc.  1) For whatever reason, when I run sudo ifup eth1, I get:
```
SIOCADDRT: Network is unreachable
Failed to bring up eth1.
```

Here is my /etc/network/interfaces file:
```
auto lo
iface lo inet loopback

auto ath0
iface ath0 inet static
address 10.0.1.4
netmask 255.255.255.0
gateway 10.0.1.1
wireless-essid cessna

auto eth1
iface eth1 inet static
address 10.0.1.5
netmask 255.255.255.0
gateway 10.0.1.4

```

What is wrong here?

2) How would I set up my routing tables such that anything from the BSD box (10.0.1.6) bridges from eth1 (10.0.1.5) to ath0 (10.0.1.4) and then through the router (10.0.1.1) to the internet; and vice versa, things from the internet that need to go to the bsd box go router -> ath0 -> eth1 -> ne3 (BSD box)?

Thanks in advance

---

### Post by davidsampson on 2007-05-28
Also, how much configuration will this require on the OpenBSD end?

---

