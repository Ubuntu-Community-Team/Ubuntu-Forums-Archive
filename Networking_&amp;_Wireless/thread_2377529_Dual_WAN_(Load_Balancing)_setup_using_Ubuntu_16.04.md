---
title: "Dual WAN (Load Balancing) setup using Ubuntu 16.04"
date: 2017-11-14
forum: Networking &amp; Wireless
---

### Post by wowiesy2 on 2017-11-14
I’m trying to setup a multi WAN router (Ubuntu 16.04) that will serve a LAN with only a single subnet, here are the relevant information:
```


WAN1_INT=enp1s0
WAN2_INT=enp3s0
LAN_INT=enp2s0


WAN1_IP=192.168.15.254
WAN2_IP=192.168.2.254
LAN_IP=192.168.111.1


WAN1_GW=192.168.15.1
WAN2_GW=192.168.2.1


MARK_WAN1=1
MARK_WAN2=2


WT_WAN1=1
WT_WAN2=2




```

so I already setup /etc/iproute2/rt_tables to include my 2 new tables:
```


1  RT_WAN1
2  RT_WAN2




```

a very basic iptables have been setup this way to just handle the marking of packets:
```


#!/bin/bash


#define where iptables is
IPT=/sbin/iptables


#define WAN interface
WAN1_INT=enp1s0
WAN2_INT=enp3s0
WAN1_IP=192.168.15.254
WAN2_IP=192.168.2.254


#define LAN interface
LAN_INT=enp2s0


#define MARKs for multi WAN routing
MARK_WAN1= 1
MARK_WAN2= 2
MARK_NONE = 0


$IPT -t nat -Z
$IPT -t mangle -Z


# MANGLE for multi wan routing


$IPT -A PREROUTING -t mangle -j CONNMARK —restore-mark


$IPT -A PREROUTING -t mangle —match mark —-mark $MARK_WAN1 -j ACCEPT
$IPT -A PREROUTING -t mangle -i $WAN1_INT —m state —state NEW -m mark ——mark $MARK_NONE -j MARK —set-mark $MARK_WAN1


$IPT -A PREROUTING -t mangle —match mark —-mark $MARK_WAN2 -j ACCEPT
$IPT -A PREROUTING -t mangle -i $WAN2_INT —m state —state NEW -m mark —-mark $MARK_NONE -j MARK —set-mark $MARK_WAN2


$IPT -A PREROUTING -t mangle -j CONNMARK —save-mark




# NAT traffic going out the MULTI WAN interfaceS
$IPT -t nat -A POSTROUTING -s 192.168.111.0/24 -o $WAN1_INT -j SNAT —-to-source $WAN1_IP
$IPT -t nat -A POSTROUTING -s 192.168.111.0/24 -o $WAN2_INT -j SNAT —-to-source $WAN2_IP




```


based on links over the web, I should have the following lines:
```



ip route add 192.168.15.0/24 dev enp1s0 src 192.168.15.254 table 1
ip route add default via 192.168.15.1 table 1
ip rule add from enp1s0 table 1
ip rule add from 192.168.15.254 table 1
ip rule add fwmark 1 table 1 prio 1024




ip route add 192.168.2.0/24 dev enp1s0 src 192.168.2.254 table 2
ip route add default via 192.168.2.1 table 2
ip rule add from enp3s0 table 2
ip rule add from 192.168.2.254 table 2
ip rule add fwmark 2 table 2 prio 1025


ip route add default scope global nexthop via 192.168.15.1 dev enp1s0 weight 1 nexthop via 192.168.2.1 dev enp3s0 weight 2


nohup /usr/local/sbin/gwping & 




```

when I run them from the command line… they work.. 


however, when I put them in  /etc/network/if-up.d/ , only the routes get set up.. the rules aren’t


(if-up script)


```
#!/bin/bash
#
# This script manually configures routes for the various local networks.
#
# WAN1 -> enp1s0 -> 192.168.15.254 
# WAN2 -> enp3s0 -> 192.168.2.254
# LAN -> enp2s0 -> 192.168.111.1
#


if [ "$IFACE" = lo ]; then
  exit 0
fi


if [ "$IFACE" = enp2s0 ]; then


  # route setup for LAN  ??




fi


if [ "$IFACE" = enp1s0 ]; then


 
ip route add 192.168.15.0/24 dev enp1s0 src 192.168.15.254 table 1
ip route add default via 192.168.15.1 table 1
ip rule add from enp1s0 table 1
ip rule add from 192.168.15.254 table 1
ip rule add fwmark 1 table 1 prio 1024


fi


if [ "$IFACE" = enp3s0 ]; then


ip route add 192.168.2.0/24 dev enp1s0 src 192.168.2.254 table 2
ip route add default via 192.168.2.1 table 2
ip rule add from enp3s0 table 2
ip rule add from 192.168.2.254 table 2
ip rule add fwmark 2 table 2 prio 1025


fi


# Flush the route rules to update the kernel
ip route flush cache
exit 0



```


I am not sure why it is so… 


I tried putting the commands within the network configuarion in /etc/network/interfaces:
```


auto lo
iface lo inet loopback


auto enp2s0
iface enp2s0 inet static
address 192.168.111.1
netmask 255.255.255.0
broadcast 192.168.111.255


auto enp1s0
iface enp1s0 inet static
address 192.168.15.254
netmask 255.255.255.0
broadcast 192.168.15.255
post-up ip route add 192.168.15.0/24 dev enp1s0 src 192.168.15.254 table 1
post-up ip route add default via 192.168.15.1 table 1
post-up ip rule add from enp1s0 table 1
post-up ip rule add from 192.168.15.254 table 1
post-up ip rule add fwmark 1 table 1 prio 1024




auto enp3s0
iface enp3s0 inet static
address 192.168.2.254
netmask 255.255.255.0
broadcast 192.168.2.255
post-up ip route add 192.168.2.0/24 dev enp1s0 src 192.168.2.254 table 2
post-up ip route add default via 192.168.2.1 table 2
post-up ip rule add from enp3s0 table 2
post-up ip rule add from 192.168.2.254 table 2
post-up ip rule add fwmark 2 table 2 prio 1025




```


but still… the rules weren’t setup when I checked   (table RT_WAN1 and RT_WAN2 are not present in the routing tables when I do a ip route show.. and there are no rules when I do a ip rule show)  


I haven’t tried putting them in /etc/rc.local    but I am trying first to understand why the rules aren’t being set up this way when they should be…   


I am wondering if this is a timing issue (the route add and rule add calls are being made before the interface is really finished setting up and brought up by the system?   How do I confirm this is so? And If I confirm so.. where should I put the route / rules setup lines?   




I have managed to test the gwping script (using just the planned router and the 2 WAN connections, using the command line invoked route and rule additions) and I was able to see gwping script at work (when 2 modems are connected, the weights are observed.. when I disconnect 1 of the modems, gwping switches over to the other WAN as default gw, and then when I have 2 modems reconnected gwping again goes back to load balanced mode…   this tells me that somehow.. the pieces fit together…   


I figure for this to all work properly, I need to:


1. make the ip route add and ip rule add scripts run correct at boot up  - but it wasn’t working when I put it in /etc/network/interfaces and in /etc/network/if-up.d/ - how do I make this work? 


2. setup routes for the LAN and iptables (SNAT and something else?)   that when the router is called upon to do its work ( LAN client tries connecting to the internet ) the router is able to successfully give internet access to it)  - what routes do I need to setup ? any rules?   how about iptables?  aside from SNAT…  should I set up anything else? 


3. aside from these two above.. is there something I missed? 




thanks for the help!

---

### Post by wowiesy2 on 2017-11-19
managed to work it out

1.  i read somewhere that there is a bug in 16.04 about ifup scripts not being run...   so I did the alternative - use cron
2. as to routing entries in my custom routing tables.. i just inserted a line to point to the LAN for each table.

---

