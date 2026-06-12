---
title: "IPv6 + SNAT + ufw (each user outgoing through own IP)"
date: 2018-02-28
forum: Networking &amp; Wireless
---

### Post by metalhelmet on 2018-02-28
I'm trying to setup SNAT for IPv6

I have 4 different IP assigned to one eth adapter (all visible and reachable) and 4 user on one server.

For example - I have IP 93.185.4.82 / 93.185.4.142 / 93.185.4.160 / 93.185.4.166 
and users - user1 / user2 / user3 / user4
Each user have it's ID (id user1 = 1001 / id user2 = 1002 / id user3 = 1003 / id user4 = 1004)

I need to set configuration such way that each user shoud send all his outgoing traffic through exact IP
Mean all outgoing traffic from user1 should go through (as from) IP 93.185.4.82 
user1 (id 1001) -> 93.185.4.82 -> outside 
user2 (id 1002) -> 93.185.4.142 -> outside
user3 (id 1003) -> 93.185.4.160 -> outside
user4 (id 1004) -> 93.185.4.166 -> outside

With IPv4 I use ufw configuration added to /etc/ufw/before.rules
```
# NAT table rules 
*nat
:POSTROUTING ACCEPT [0:0] 
-A POSTROUTING -m addrtype ! --dst-type LOCAL -m owner --uid-owner 1001 -j SNAT --to-source 93.185.4.82
-A POSTROUTING -m addrtype ! --dst-type LOCAL -m owner --uid-owner 1002 -j SNAT --to-source 93.185.4.142
-A POSTROUTING -m addrtype ! --dst-type LOCAL -m owner --uid-owner 1003 -j SNAT --to-source 93.185.4.160
-A POSTROUTING -m addrtype ! --dst-type LOCAL -m owner --uid-owner 1004 -j SNAT --to-source 93.185.4.166

COMMIT



```

What is the best way to do this with IPv6 ? Should I use smth like 
```
ip6tables -t nat -A POSTROUTING -m addrtype ! --dst-type LOCAL -m owner --uid-owner 1001 -j SNAT --to-source 2604:e101:ab:12::2
ip6tables -t nat -A POSTROUTING -m addrtype ! --dst-type LOCAL -m owner --uid-owner 1002 -j SNAT --to-source 2604:e101:ab:12::3
ip6tables -t nat -A POSTROUTING -m addrtype ! --dst-type LOCAL -m owner --uid-owner 1003 -j SNAT --to-source 2604:e101:ab:12::4
ip6tables -t nat -A POSTROUTING -m addrtype ! --dst-type LOCAL -m owner --uid-owner 1004 -j SNAT --to-source 2604:e101:ab:12::5

``` This code works (till i reboot server)

What is a better way to do the job ?

---

