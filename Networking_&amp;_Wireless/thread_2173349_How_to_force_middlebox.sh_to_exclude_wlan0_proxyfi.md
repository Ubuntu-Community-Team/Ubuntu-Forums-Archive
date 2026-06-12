---
title: "How to force middlebox.sh to exclude wlan0 proxyfication?"
date: 2013-09-09
forum: Networking &amp; Wireless
---

### Post by MxeyChr on 2013-09-09
Hi Masters !

I have a question:

I have a hardver SWITCH and a PPPOE configuration with 2 machines, WIN7 and an ubuntu 12.04 
First i created an Access Point on ubuntu to share my wlan0 data from eth0 or ppp0 (depending how i connent to internet, trough WIN7 or directly) with 2 script:

**initAP **script looks like:

[COLOR=#800000]#!/bin/bash[/COLOR]
[COLOR=#800000]hostapd -B /etc/hostapd/hostapd.conf[/COLOR]
[COLOR=#800000]iptables -t nat -A POSTROUTING -s 10.10.0.0/16 -o ppp0 -j MASQUERADE
[/COLOR]
and **initAPeth0** script:

[COLOR=#800000]#!/bin/bash[/COLOR]
[COLOR=#800000]hostapd -B /etc/hostapd/hostapd.conf[/COLOR]
[COLOR=#800000]iptables -t nat -A POSTROUTING -s 10.10.0.0/16 -o eth0 -j MASQUERADE

[/COLOR][COLOR=#000000]These 2 scripts are **worked correctly** _until_ I've created a [middlebox.sh]("http://www.howtoforge.com/how-to-set-up-a-tor-middlebox-routing-all-virtualbox-virtual-machine-traffic-over-the-tor-network") looks like:

[/COLOR][COLOR=#800000]#!/bin/sh


# destinations you don't want routed through Tor
NON_TOR="192.168.1.0/24"


# Tor's TransPort
TRANS_PORT="9040"


# your internal interface
INT_IF="vnet0"


iptables -F
iptables -t nat -F


for NET in $NON_TOR; do
 iptables -t nat -A PREROUTING -i $INT_IF -d $NET -j RETURN
done
iptables -t nat -A PREROUTING -i $INT_IF -p udp --dport 53 -j REDIRECT --to-ports 53
iptables -t nat -A PREROUTING -i $INT_IF -p tcp --syn -j REDIRECT --to-ports $TRANS_PORT[/COLOR]
[COLOR=#000000]
_since_ then, I cannot connect to that Access Point I have created on WLAN0 :(

[/COLOR][COLOR=#ff0000]What should I change to force  the "middlebox" exclude the WLAN0 ? 
[/COLOR][COLOR=#000000]
Maybe it conflicts some value in the torrc file ? 

[/COLOR][COLOR=#b22222]VirtualAddrNetwork **10.192.0.0/10**[/COLOR]
[COLOR=#b22222]AutomapHostsOnResolve 1[/COLOR]
[COLOR=#b22222]TransPort 9040[/COLOR]
[COLOR=#b22222]TransListenAddress 172.16.0.1[/COLOR]
[COLOR=#b22222]DNSPort 53[/COLOR]
[COLOR=#b22222]DNSListenAddress 172.16.0.1

[/COLOR][COLOR=#000000]Because the WLAN0 looks like : [B]10.10.0.0/16
[/B][/COLOR]


BUT ! Because middlebox.sh script is only initiated manually, the conflict is maybe in other place i've made some modifications, due the problem is automatic at system startup:

in /etc/network/interfaces i've added these lines:


[COLOR=#800000]# VirtualBox NAT bridge[/COLOR]
[COLOR=#800000]auto vnet0[/COLOR]
[COLOR=#800000]iface vnet0 inet static[/COLOR]
[COLOR=#800000] address 172.16.0.1[/COLOR]
[COLOR=#800000] netmask 255.255.255.0[/COLOR]
[COLOR=#800000] bridge_ports none[/COLOR]
[COLOR=#800000] bridge_maxwait 0[/COLOR]
[COLOR=#800000] bridge_fd 1[/COLOR]
[COLOR=#800000]
[/COLOR]
[COLOR=#800000] up iptables -t nat -I POSTROUTING -s 172.16.0.0/24 -j MASQUERADE[/COLOR]
[COLOR=#800000] down iptables -t nat -D POSTROUTING -s 172.16.0.0/24 -j MASQUERADE[/COLOR]


and in /etc/dnsmasq.conf i've added these lines:

[COLOR=#800000]interface=vnet0[/COLOR]
[COLOR=#800000]dhcp-range=172.16.0.2,172.16.0.254,1h[/COLOR]






[COLOR=#000000]
[/COLOR]

---

