---
title: "what is opt when i list iptables rules"
date: 2008-03-01
forum: Networking &amp; Wireless
---

### Post by buldozerceto on 2008-03-01
Hello,

when I do iptables -L -v -n I get

Chain INPUT (policy DROP 0 packets, 0 bytes)
num   pkts bytes target     prot opt in     out     source               destination         
1        0     0 ACCEPT          all  -f  *      *       0.0.0.0/0            0.0.0.0/0           
2        0     0 ACCEPT          all  -f  *      *       0.0.0.0/0            0.0.0.0/0           
3        0     0 DROP             all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID

.......... and so on

what is opt and what is -f

---

### Post by The Cog on 2008-03-02
From **man iptables**:
       [!]  -f, --fragment
              This means that the rule only refers to second and further fragments of fragmented packets.  Since there is no way to tell  the  source  or
              destination  ports  of such a packet (or ICMP type), such a packet will not match any rules which specify them.  When the "!" argument pre&#8208;
              cedes the "-f" flag, the rule will only match head fragments, or unfragmented packets.

opt must mean options (that are not shown in other columns perhaps).

---

