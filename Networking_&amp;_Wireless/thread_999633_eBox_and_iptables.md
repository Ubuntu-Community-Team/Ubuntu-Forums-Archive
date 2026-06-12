---
title: "eBox and iptables"
date: 2008-12-02
forum: Networking &amp; Wireless
---

### Post by madverb on 2008-12-02
I have posted this problem on the eBox forum but it takes forever to get a response.
The problem I am having is with the setup of squid and dansguardian.
When I setup to filter using dansguardian it all fails, I get sent straight to the Access Denied screen of squid's.
I found that this was occuring due to a problem in iptables under the nat table.
```
iptables -t nat -L
```
> Chain premodules (1 references)
target     prot opt source               destination
RETURN     tcp  --  10.1.1.2             192.168.1.102       tcp dpt:3128
RETURN     tcp  --  192.168.1.96         192.168.1.102       tcp dpt:3128
REDIRECT   tcp  --  anywhere             192.168.1.102       tcp dpt:3128 redir ports 3129
The problem is that even with this setup it fails... but if I removes these rules
```
iptables -t nat -F
```
and then recreate them manually it works. For some reason there is something going wrong when ebox creates them.

Any ideas?

---

### Post by madverb on 2008-12-03
Bump

---

