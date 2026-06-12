---
title: "some pc can't access the internet after a while"
date: 2007-08-02
forum: Networking &amp; Wireless
---

### Post by xiehuipiaofeng on 2007-08-02
hi, 

I'm use the iptables as the NAT in my office. At the beginning, each pc can access the internet. But after a while, about one hour or two days, some pcs can't access the internet. and they also can't ping the eth1 that is for interal lan. When I restart the pc and iptables, all is fine.  I think it's maybe the problem of the switch, so i change the other one. But it's also happen. I don't know why.Please help me.

Thank you .

this is the script of iptables' rules.

------------------------------------------------------------------------------------------
#!/bin/sh

PATH=/usr/sbin:/sbin:/bin:/usr/bin
#
# delete all existing rules.
#
iptables -F
iptables -t nat -F
iptables -t mangle -F
iptables -X

#iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to 128.1.11.250
iptables -t nat -A PREROUTING -i eth1 -s 128.1.11.0/24 -j ACCEPT

# Always accept loopback traffic
iptables -A INPUT -i lo -j ACCEPT

# IS USED
iptables -A FORWARD -i eth1 -s 128.1.11.132 -j ACCEPT
iptables -A INPUT -i eth1 -s 128.1.11.132 -j ACCEPT
iptables -A FORWARD -i eth1 -s 128.1.11.131 -j ACCEPT
iptables -A INPUT -i eth1 -s 128.1.11.131 -j ACCEPT

# Normal Access Control
iptables -A INPUT -i eth1 -p tcp -m multiport --dport 80,443 -j ACCEPT
iptables -A FORWARD -i eth1 -p tcp -m multiport --dport 80,443 -j ACCEPT 

# Allow established connections, and those not coming from the outside
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -m state --state NEW -i eth1 -j ACCEPT
iptables -A FORWARD -i eth1 -o eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -i eth0 -o eth1 -m state --state ESTABLISHED,RELATED -j ACCEPT

iptables -A INPUT -i eth0 -m state --state INVALID,NEW -j DROP
iptables -A FORWARD -i eth0 -m state --state INVALID,NEW -j DROP

# Don't forward from the outside to the inside.
iptables -A FORWARD -i eth0 -o eth1 -j REJECT

# Enable routing.
echo 1 > /proc/sys/net/ipv4/ip_forward

iptables -A INPUT -i eth1 -j DROP
iptables -A FORWARD -i eth1 -j DROP

---

### Post by xiehuipiaofeng on 2007-08-02
The Iptables rules have some problems?

---

