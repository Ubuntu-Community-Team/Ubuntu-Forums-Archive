---
title: "iptables doesn't allow outside connections"
date: 2019-11-20
forum: Networking &amp; Wireless
---

### Post by nikizaniki2 on 2019-11-20
Ports Are Forwarded!

My iptables are as as so:
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:ssh MAC **:85:C2:75:2B:**
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:ssh MAC **:D2:1D:07:81:**
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:25565
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:25555
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:25545
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:25535
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:25525
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:ssh MAC **:F1:0E:00:40:**
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:ssh MAC **:D3:7A:5B:68:**
DROP       tcp  --  anywhere             anywhere             tcp dpt:ssh

```
It works on LAN but it doesn't from the outside and i don't know why.
Any ideas? thanks in advance!

---

### Post by SeijiSensei on 2019-11-20
Is this server directly on the Internet? If it's behind a router, you'll have to use port forwarding. How to do that depends on the router, so you'll need to read its documentation.

---

### Post by nikizaniki2 on 2019-11-20
I have port forwarded from 21 to 23 and the other ports that i have forwarded work as well, like *25565* haha.. I should have mentioned that im sorry.
I think that it has something to do with port 22 being DROP-ed at the end but should the mac adresses be checked before it's hit?
It does work when i disable the last rule..

---

### Post by SeijiSensei on 2019-11-20
I'm not sure I understand the purpose of the MAC directives. Does this server have multiple network adapters?  If you're trying to filter for connections from a specific address I'd use -s and maybe --sport rather than --dport. Personally I always find it easier to use IP addresses.  For instance,
```
/sbin/iptables -A INPUT -p tcp -s 10.10.10.10 --dport 12345 -j ACCEPT
```
allows the client at 10.10.10.10 to access port 12345.

Disabling the last rule means using the default policy, which is ACCEPT.

---

