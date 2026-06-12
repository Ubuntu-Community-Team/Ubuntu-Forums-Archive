---
title: "routing wireless LAN through ethernet pppoe"
date: 2008-01-07
forum: Networking &amp; Wireless
---

### Post by GringoCroco on 2008-01-07
I have a ethernet connection to the internet: eth0.
I have a wireless connection (eth1) which I used to create an ad-hoc connection to another computer and connect it to the internet.

The ad-hoc connection was a subnet: 192.168.5.0/24. 
eth1's IP was 192.168.5.1.

for this I did some iptables magic:

echo "1" > /proc/sys/net/ipv4/ip_forward
/sbin/iptables -t nat -A POSTROUTING -s 192.168.5.0/24 -o eth0 -j MASQUERADE

This worked fine and dandy until pppoe was set up over eth0.
To connect to the internet I now use the ppp0 interface.

The problem is that now I cannot route the wireless traffic over pppoe. I tried:
/sbin/iptables -t nat -A POSTROUTING -s 192.168.5.0/24 -o ppp0 -j MASQUERADE
and even addded:
iptables -t mangle -A PREROUTING -i ppp0 -j TTL --ttl-inc 1
to incremet the ttl of outgoing routed packets.

Still I cannot connect to the internet from the 192.168.5.0 wireless LAN.
ping from the wireless LAN to 192.168.5.1 (my host) works, but does not work with other computers outside that LAN.

Any advices?

---

### Post by GringoCroco on 2008-01-09
solution :

iptables -t nat -F
iptables -t nat -A POSTROUTING -s 192.168.5.0/24 -o ppp0 -j MASQUERADE
iptables -t mangle -A PREROUTING -i ppp0 -j TTL --ttl-inc 1
iptables -t mangle -A POSTROUTING -j TTL --ttl-set 64

---

### Post by WIGGMPk on 2008-07-14
I believe I am having a similiar issue to yours.

[http://ubuntuforums.org/showthread.php?t=855691](http://ubuntuforums.org/showthread.php?t=855691)

What would cause this to happen?

or

Why would you need a different set of rules?


I am going to try this tonight, and post back later.

---

### Post by WIGGMPk on 2008-07-14
Although im curious...

I use webmin to edit my firewall rules (just think its easier)..

You have TTL --ttl-inc 1.. What is TTL? Is this your own chain?

What is in the chain that would correct the problem?

---

