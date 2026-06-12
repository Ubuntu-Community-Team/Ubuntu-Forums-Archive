---
title: "iptables router, drop internal sources"
date: 2014-10-11
forum: Networking &amp; Wireless
---

### Post by ant2ne on 2014-10-11
I'm trying to block some internal IPs from accessing the outside world. My iptables says they are getting dropped but tshark shows that data flows.

Here are the relevant lines in my iptables script.
```

iptables -A INPUT -s 10.1.1.110 -j DROP
iptables -A INPUT -s 10.1.1.120 -j DROP
iptables -A FORWARD -s 10.1.1.110 -j DROP
iptables -A FORWARD -s 10.1.1.120 -j DROP
iptables -A OUTPUT -s 10.1.1.110 -j DROP
iptables -A OUTPUT -s 10.1.1.120 -j DROP

iptables -A INPUT -s 10.1.1.138 -j DROP
iptables -A FORWARD -s 10.1.1.138 -j DROP
iptables -A OUTPUT -s 10.1.1.138 -j DROP

```

Here is what my iptables looks like.
```
root@fw:/home/ant2ne# iptables -L -n -v
Chain INPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
 2663  156K ACCEPT     all  --  *      *       10.1.1.69            0.0.0.0/0           
    2   768 DROP       all  --  *      *       10.1.1.110           0.0.0.0/0           
  179 14367 DROP       all  --  *      *       10.1.1.120           0.0.0.0/0           
  255 18581 DROP       all  --  *      *       10.1.1.138           0.0.0.0/0           
 1188 80042 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
    0     0 ACCEPT     tcp  --  eth1   *       0.0.0.0/0            0.0.0.0/0            tcp dpt:1022
    0     0 ACCEPT     tcp  --  eth0   *       0.0.0.0/0            0.0.0.0/0            tcp dpt:1022
  259 55731 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
   15   850 DROP       all  --  *      *       10.1.1.110           0.0.0.0/0           
   25  1550 DROP       all  --  *      *       10.1.1.120           0.0.0.0/0           
 2072  207K DROP       all  --  *      *       10.1.1.138           0.0.0.0/0           
68370   80M ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       all  --  *      *       10.1.1.110           0.0.0.0/0           
    0     0 DROP       all  --  *      *       10.1.1.120           0.0.0.0/0           
    0     0 DROP       all  --  *      *       10.1.1.138           0.0.0.0/0           
 4569  749K ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           

```

Why are these IPs not getting blocked?

---

### Post by ant2ne on 2014-10-12
IDK it just randomly started working like it is supposed to. How do I delete this thread?

---

### Post by Doug S on 2014-10-12
> **ant2ne said:**
> IDK it just randomly started working like it is supposed to. How do I delete this thread?You don't delete it, as some of us might have been off thinking about your issue, even though, and as best as I could figure, it should have been working properly. Thanks for coming back and letting us know. However, you could set this to "SOLVED".

---

