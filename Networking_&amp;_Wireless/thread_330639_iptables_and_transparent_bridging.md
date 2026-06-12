---
title: "iptables and transparent bridging"
date: 2007-01-03
forum: Networking &amp; Wireless
---

### Post by eboran on 2007-01-03
Hi,

On a box running Ubuntu Edgy I have 3 network cards.
2 of them form a transparent bridge while the third one is used for management.

I am trying to use iptables in order to re-route the http traffic going through the bridge from port 80 to port 3128 (used by squid). 
I have installed bridge-utils and ebtables. 
The bridge functions correctly.
The kernel is 2.6
In order to use squid with this configuration, the bridge has been assigned a fixed IP.

The setup I am using:
ISP – ROUTER – BRIDGE (eth0 facing the edge router, eth1 facing internal network) – internal network
I am using the following commands to enable the firewall:

echo 1 > /proc/sys/net/ipv4/ip_forward
ebtables -t broute -A BROUTING -p IPv4 --ip-protocol 6 --ip-destination-port 80 \
        -j redirect --redirect-target ACCEPT
iptables -A INPUT -i eth1 -p tcp -d <IP of the bridge> -s <internal network subnet> --dport 3128 \
         -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -t nat -A PREROUTING -i eth1 -s <internal network subnet> -p tcp --dport 80 \ 
          -j REDIRECT --to-port 3128

I have tried with and without ebtables but no luck.](*,) 
I have also that squid works just by pointing the clients to the IP of the bridge port 3128.

Can someone help me out here?

thank you,

Ed

---

### Post by eboran on 2007-01-03
I meant to say that I have verified that squid works by pointing the clients to the IP of the bridge port 3128.

---

