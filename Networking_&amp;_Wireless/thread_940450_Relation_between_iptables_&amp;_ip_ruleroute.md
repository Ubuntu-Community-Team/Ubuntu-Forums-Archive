---
title: "Relation between iptables &amp; ip rule/route?"
date: 2008-10-07
forum: Networking &amp; Wireless
---

### Post by pepoluan on 2008-10-07
I'm deploying Ubuntu Server 8.04.1 for source-based routing in my company.

It currently gives access to all hosts in my company, with a specific subnet (management) directed through a high-speed Internet line, while the other subnets (staff) directed through a mid-speed Internet line.

I would like to harden the Server further (and restrict accessible IP's), but I first need to know the relation between iptables & ip rule/route.

I'm guessing that this is the order of checks, please correct me if I'm wrong:
1. iptables INPUT
2. iptables FORWARD
3. iptables NAT PREROUTING
4. ip rule
5. ip route
6. iptables NAT POSTROUTING
7. iptables OUTPUT

Thus, if I want to harden & restrict the router, I should be using iptables INPUT, right?

Please, any input will be greatly appreciated.

---

### Post by buzz-lightyear on 2008-10-07
if i understand your question , you want to restrict access from internet to certain LAN-IP's (right ?)


So you restrict the Access for 192.168.2.100 to use SSH

iptables -A INPUT -p tcp -d 192.168.2.100 --dport 22 -j REJECT

---

### Post by pepoluan on 2008-10-08
The problem goes like this:

Here's the **rc.local** that I use:

```

#!/bin/bash

echo
echo "Preparing ALEXIARES..."

### GENERAL SETTING
# Enabling IP forwarding
# This must be the first thing to do
#
echo -n -e "\tEnabling IP forwarding... "
echo 1 > /proc/sys/net/ipv4/ip_forward
#
echo "DONE"

### ROUTING TABLES
#
echo -n -e "\tPreparing routing tables... "
#
# Static route toward HERACLES (Core Switch)
route add -net 172.31.0.0 netmask 255.255.0.0 gw 192.168.251.1 dev eth2
#
# Routing Table 2 - Default route to xxx.xxx.xxx.xxx (Inet2)
# Used by management & accounting, selection rule see "Routing Policies" below
#
ip route add to default dev eth1 table 2 via xxx.xxx.xxx.xxx
#
# Routing Table 3 - Default route to 192.168.20.197 (Inet3)
# Used by rest of staff, selection rule see "Routing Policies" below
#
ip route add to default dev eth0 table 3 via 192.168.20.197
#
echo "DONE"

### ROUTING POLICIES
# Here we choose which routing table to use based on source address
# (a.k.a Source-Based Routing)
#
echo -n -e "\tPreparing Source-Based Routing... "
#
# The rules are listed in "reverse", i.e., the first listed rule is
# processed last.
#
# Rule 1: All networks will use fast Inet2
ip rule add type unicast from 172.31.0.0/17 iif eth2 table 2
#
# Rule 2: All staff (which has their 7th bit set) use slower Inet3
ip rule add type unicast from 172.31.128.0/17 iif eth2 table 3
#
# Rule 3: Management (in special 172.31.147.x group) use fast Inet2
ip rule add type unicast from 172.31.147.0/24 iif eth2 table 2
ip rule add type unicast from 172.31.140.0/24 iif eth2 table 2
#
# Rule 4: These are suspicious addresses
ip rule add type prohibit to 219.141.127.241 iif eth2
#
# IMPORTANT: Flush the routing cache to make these changes immediate
ip route flush cache
#
echo "DONE"

### ROUTING TABLES
#
echo -n -e "\tPreparing NAT... "
#
iptables -t nat -A POSTROUTING -o eth1 -j SNAT --to xxx.xxx.xxx.xxx
iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to 192.168.20.198
#
# IMPORTANT: Again, flush the routing cache
ip route flush cache
#
echo "DONE"

## All done, now let's get out properly
#
exit 0

```

The **rc.local** works as intended.

Now, from the shell, I entered the following:

```

sudo iptables -A INPUT -s 172.31.160.0/22 -j DROP

```

But... lo and behold! users in 172.31.16.0 *still* can access the Internet.

Any input will be greatly appreciated.

---

### Post by pepoluan on 2008-10-10
No one? :(

---

### Post by Wicca on 2008-10-10
Well, I am not an expert on this, but I'll give it tiny shot :-)

First:
> users in 172.31.16.0 *still* can access the Internet.
I assume the 16 is a typo? (just to be sure)

Second:
> sudo iptables -A INPUT -s 172.31.160.0/22 -j DROP
The -A means the rule is appended to all the other set of rules. If  traffic is not behaving as expected, there is a change that there is another rule for this chain handling the traffic BEFORE this rule is applied. If a certain condition is true, the rule will be applied and all following rules (which might be true as well) will be ignored. If you accept traffic coming from a certain subnet (ACCEPT, FORWARD) you can't drop it anymore further on.
Do a iptables -L to make sure there are no other rules in the same chain active with the same conditions.

---

### Post by pepoluan on 2008-10-10
> **Wicca said:**
> Well, I am not an expert on this, but I'll give it tiny shot :-)

First:

I assume the 16 is a typo? (just to be sure)

Second:

The -A means the rule is appended to all the other set of rules. If  traffic is not behaving as expected, there is a change that there is another rule for this chain handling the traffic BEFORE this rule is applied. If a certain condition is true, the rule will be applied and all following rules (which might be true as well) will be ignored. If you accept traffic coming from a certain subnet (ACCEPT, FORWARD) you can't drop it anymore further on.
Do a iptables -L to make sure there are no other rules in the same chain active with the same conditions.
Ooops.. yes that is a type. I should've typed 172.31.160.0

**iptables -L** shows *no* other rule.

That is why I asked - in the original post - what's the order of processing (i.e., relation) between **iptables** and **ip route**? Is it possible that **ip route** has routed the packet before **iptables** have a hand at it?

---

### Post by Wicca on 2008-10-10
> **pepoluan said:**
> Is it possible that **ip route** has routed the packet before **iptables** have a hand at it?

It seems to work that way, yes. 

I found this:
[http://iptables-tutorial.frozentux.net/images/tables_traverse.jpg]("http://iptables-tutorial.frozentux.net/images/tables_traverse.jpg")

Although this is about prerouting, not routing, there might be similarity between them.

I'm affraid I can't help you any further than this.

---

### Post by pepoluan on 2008-10-15
> **Wicca said:**
> It seems to work that way, yes. 

I found this:
[http://iptables-tutorial.frozentux.net/images/tables_traverse.jpg]("http://iptables-tutorial.frozentux.net/images/tables_traverse.jpg")

Although this is about prerouting, not routing, there might be similarity between them.

I'm affraid I can't help you any further than this.

Ahhh! Thanks a huge lot for that picture!

It greatly helps. Thanks!

---

