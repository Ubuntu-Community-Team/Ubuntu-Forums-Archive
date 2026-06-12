---
title: "Passing traffic between two interfaces"
date: 2017-05-19
forum: Networking &amp; Wireless
---

### Post by sniper8752 on 2017-05-19
I am trying to pass data between two nic cards on my server.  Here is the setup: enp1s0 = wanenp3s0 = lan

Here is what I put in my iptables file:
```
iptables -t nat -A POSTROUTING -i enp1s0 -s 192.168.1.0/24 -j SNAT --to-source 192.168.2.1
```
Received this error when trying to restore from it:
```
iptables-restore: line 1 failed

```
wan side = 192.168.1.0/24

I set ipv4 forwarding = 1 already.

---

