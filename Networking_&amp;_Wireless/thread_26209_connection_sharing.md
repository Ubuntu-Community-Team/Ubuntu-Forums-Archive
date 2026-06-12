---
title: "connection sharing"
date: 2005-04-12
forum: Networking &amp; Wireless
---

### Post by defl on 2005-04-12
hi.

well i got some problems with my internet connection sharing.yesterday i switched  from mandrake/mandriva to ubuntu. i had no problems with internet connection sharing when using mandrake but i just cant get it work with ubuntu. i've tried different ways but it simply wont work. dont know exactly why.
some specs: 
eth0 connected to the lan ip: 192.168.0.1
eth 1 connected to a xdsl modem  dynamic ip (pppoe) (ppp0 has also dynamic ip)

ps: the network is up, pings,.. are working. 

could anyone be so kind and post an idiot proof way to set up connection sharing? :) 

tha

---

### Post by bihe on 2005-04-13
hi there.

i'm using a warty host as a gateway form my home-network. the gateway is
configured to route traffic to/from the internet. additionally it runs an name-
server, so there is less dns lookup traffic. the dns server on the gateway only 
acts as a caching nameserver and forwards requests to the isp nameserver.

i've created a small script, which is called at startup (init3). the script configures
the gateway for routing duty:

the internal ip network is 192.168.0.0/24, external ip is dynamic.

> firewall.sh
```

#!/bin/sh

INTIF=eth0
EXTIF=ppp0
COMMAND="/sbin/iptables"

## load modules
/sbin/modprobe ip_tables
/sbin/modprobe ip_conntrack
/sbin/modprobe ip_conntrack_ftp
/sbin/modprobe iptable_nat
/sbin/modprobe ip_nat_ftp
/sbin/modprobe ipt_state
/sbin/modprobe ipt_limit
/sbin/modprobe ipt_LOG 

## enable ip forward
echo 1 > /proc/sys/net/ipv4/ip_forward

## clear old
$COMMAND -P INPUT DROP
$COMMAND -F INPUT
$COMMAND -P OUTPUT ACCEPT
$COMMAND -F OUTPUT
$COMMAND -P FORWARD DROP
$COMMAND -F FORWARD 
$COMMAND -t nat -F
$COMMAND -F world
$COMMAND -X world
$COMMAND -F home 
$COMMAND -X home 

## masquerade
$COMMAND -t nat -A POSTROUTING -o $EXTIF -j MASQUERADE

## FORWARD rules
$COMMAND -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT  
$COMMAND -A FORWARD -s 192.168.0.0/24 -p tcp --dport ABC -j ACCEPT
$COMMAND -A FORWARD -s 192.168.0.0/24 -p udp --dport ABC -j ACCEPT

## other FORWARD rules
$COMMAND -A FORWARD -j LOG --log-prefix "[ <fwd> ] "

## create new user RULES
$COMMAND -N home
$COMMAND -N world

## redirecte input to user specific rules
$COMMAND -A INPUT -i $INTIF -j home
$COMMAND -A INPUT -i $EXTIF -j world

## allow connections to self
$COMMAND -A INPUT -i lo -j ACCEPT

## allow connections from fw to ----->
$COMMAND -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

## rules for chain home (= home network)
$COMMAND -A home -p tcp --destination-port ... -j ACCEPT
...
## log 
$COMMAND -A home -j LOG --log-prefix "[ ::home:: ] "


## rules for chain world (= external network)
$COMMAND -A world -p udp --destination-port ... -j ACCEPT
...
## log 
$COMMAND -A world -j LOG --log-prefix "[ ==WORLD== ] "

## ready
echo -e "Firewall Setup OK.\n"

```

---

### Post by ssam on 2005-04-13
the firestarter firewall program in the universe can do this. its configurable through a wizzard.

who knows why this is in a firewall program, but hey it is.  :-) 

sam

---

### Post by tonym on 2005-04-15
shorewall is another tool for configuring this,  although it doesn't have a nice gui.

---

### Post by epajni10 on 2005-05-07
Hi,
I too have this connection sharing problem.

I tried the firewall script given above, but it didn't work. I have a similar set up to the original post:

eth0: 192.168.0.1 - points to the home network: 192.168.0.2
eth1: dhcp - internet gateway
DSL internet connection
firewall - makes no difference if it is on or off! I have it set up in a similar way to the above script.

This setup works fine with Slackware, so I must assume it is something I have overlooked. My suspicion is that it has something to do with the kernels routing tables. Does anyone know anything about this subject?

Here is the "route" commands ouput:

Kernel IP routing table
Destination        Gateway                Genmask            Flags   Metric Ref    Use Iface
192.168.0.0       *                            255.255.255.0    U        0         0        0    eth0
219.211.140.0   *                            255.255.252.0    U        0         0        0    eth1
default               219.211.143.254   0.0.0.0               UG      0         0        0    eth1

Am I missing something?

Any help will be greatly appreciated!
Thanks!

---

