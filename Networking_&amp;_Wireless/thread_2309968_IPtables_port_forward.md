---
title: "IPtables port forward"
date: 2016-01-15
forum: Networking &amp; Wireless
---

### Post by Laci1988 on 2016-01-15
Hello everybody! I have got a little problem with port forward. I open two ports. 8888 and 30000 but i wanted to delete them.
I made a mistake. I installed iptables-persistent, but i saved these two ports to bad location: /etc/network/iptables.rules instead of /etc/iptables/rules.v4

I flushed the chains with iptables -F. But these 2 ports are still working.

What could be the problem ?

Thank you very much!

---

### Post by Doug S on 2016-01-15
Post your iptables rule set.```
sudo iptables -v -x -n -L
```and ```
sudo iptables -t nat -v -x -n -L
```

---

### Post by Laci1988 on 2016-01-15
The first command`s result is: nothing, i do not have any rule.
Second one: 

Chain PREROUTING (policy ACCEPT 273 packets, 19057 bytes)
    pkts      bytes target     prot opt in     out     source               destination         


Chain INPUT (policy ACCEPT 273 packets, 19057 bytes)
    pkts      bytes target     prot opt in     out     source               destination         


Chain OUTPUT (policy ACCEPT 2 packets, 123 bytes)
    pkts      bytes target     prot opt in     out     source               destination         


Chain POSTROUTING (policy ACCEPT 2 packets, 123 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 MASQUERADE  all  --  *      eth0    10.8.0.0/24          0.0.0.0/0

The NAT rule is belong to my OpenVPN server. I know this situation is very weird. Because my iptables not include any port forward rule in the NAT chain.

---

### Post by Doug S on 2016-01-15
Your issue does not appear to be an iptables issue.

---

