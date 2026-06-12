---
title: "two isp and iptables prerouting"
date: 2013-09-14
forum: Networking &amp; Wireless
---

### Post by rafalak on 2013-09-14
Hello, I have configured two DSL interfaces
interfaces
```
auto eth1
iface eth1 inet static
address xx.1yy.47.138
netmask 255.255.255.248
#post-up ip route add xx.yy.47.136/29 dev eth1 src xx.yy.47.138 table uplink1
post-up ip route add default via xx.yy.47.137 table uplink1
post-up ip rule add from xx.yy.47.136/29 table uplink1
post-down ip rule del from xx.yy.47.136/29 table uplink1


auto eth1:20
iface eth1:20 inet static
address xx.yy.96.154
netmask 255.255.255.248
#post-up ip route add xx.yy.96.152/29 dev eth1 src xx.yy.96.154 table uplink2
post-up ip route add default via xx.yy.96.153 table uplink2
post-up ip rule add from xx.yy.96.152/29 table uplink2
post-down ip rule del from xx.yy.96.152/29 table uplink2

#post-up ip route add default scope global nexthop via xx.yy.47.137 weight 1 nexthop via xx.yy.96.153 weight 1
post-up ip route add default scope global nexthop via xx.yy.96.153 dev eth1
```

In this configuration i can ping from world to two DSL and full PREROUTING to eth1:20 

```
iptables -t nat -A PREROUTING -p tcp -d xx.yy.47.138 --dport 80 -j DNAT --to-destination 10.0.0.102:80
iptables -t nat -A PREROUTING -p tcp -d xx.yy.47.154 --dport 80 -j DNAT --to-destination 10.0.0.102:80
```

I know where the problem is
When add
```
route add default gw xx.yy.47.137
``` 

first works and another not
How can I get port 80 to be visible from the two addresses?

---

### Post by s-bodet on 2013-09-14
> **rafalak said:**
> 
I know where the problem is
When add
```
route add default gw xx.yy.47.137
``` 

first works and another not
How can I get port 80 to be visible from the two addresses?


This command adds a default route in the main routing table.

To stay consistent with your design, you would need the following commands :

```
ip route add default via xx.yy.47.137 table uplink1
ip route add default via xx.yy.96.153 table uplink2
```

so that a default route is configured in uplink1 and uplink2 routing tables.

But the router will not balance packets yet.  You'll need to implement a strategy in the PREROUTING chain to mark packets before the routing decision.
For example, you can balance the TCP 80 connections based on the source IP subnet, or based onto the IP destination of the Web servers, or the IP TOS of the sources, etc...

A while ago, I tested a scenario with a random TCP flow balancing across 2 outgoing interfaces.  I guess you can find examples with keywords 'iptables, conntrack, probability, policy-routing'...  If you can't, I will post the iptables I've been using in my scenario.

Steve

---

### Post by rafalak on 2013-09-15
I want to leave one webserver on 10.0.0.102 and marking incoming packets from two isp. Default routing from LAN may be in any interface
Where is the problem ?

```

$IPT -A INPUT -p icmp --icmp-type echo-request -j ACCEPT
$IPT -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPT -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPT -A FORWARD -p icmp --icmp-type echo-request -j ACCEPT
$IPT -t mangle -A PREROUTING -p tcp -j CONNMARK --restore-mark
$IPT -t mangle -A PREROUTING -p tcp -j CONNMARK --save-mark


$IPT -t nat -A PREROUTING -p tcp -d xx.yy.47.138 -j CONNMARK --set-mark 200
$IPT -t nat -A PREROUTING -p tcp -d xx.yy.96.154 -j CONNMARK --set-mark 201
$IPT -t nat -A PREROUTING -p tcp -d xx.yy.47.138 --dport 80 -j DNAT --to-destination 10.0.0.102:80
$IPT -t nat -A PREROUTING -p tcp -d xx.yy.96.154 --dport 80 -j DNAT --to-destination 10.0.0.102:80

$IPT -A FORWARD -i eth1 -o eth0 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
$IPT -A FORWARD -i eth0 -o eth1 -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPT -A FORWARD -m conntrack --ctstate DNAT -j ACCEPT
$IPT -t nat -A POSTROUTING -s 10.0.0.0/24 -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/ip_forward




```

```

ip rule
0:	from all lookup local 
32760:	from xx.yy.96.152/29 lookup uplink2 
32761:	from xx.yy.47.136/29 lookup uplink1 
32762:	from all fwmark 0xc9 lookup uplink2 
32763:	from all fwmark 0xc8 lookup uplink1 
32766:	from all lookup main 
32767:	from all lookup default

```

```

cat /etc/iproute2/rt_tables 
#
# reserved values
#
255	local
254	main
253	default
0	unspec
#
# local
#
200	uplink1
201	uplink2

```

```

ip route
default via xx.yy.47.137 dev eth1 
default via xx.yy.96.153 dev eth1 
10.0.0.0/24 dev eth0  proto kernel  scope link  src 10.0.0.201 
xx.yy.47.136/29 dev eth1  proto kernel  scope link  src xx.yy.47.138 
xx.yy.96.152/29 dev eth1  proto kernel  scope link  src xx.yy.96.154

```

---

