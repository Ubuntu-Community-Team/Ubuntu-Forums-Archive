---
title: "router setup"
date: 2014-07-08
forum: Networking &amp; Wireless
---

### Post by atux on 2014-07-08
hello everyone.
i do need to have add a second ISP to my soho but the router cannot do multi homing.
i have an old PC that i could use with ubuntu server as a router.
could someone help me on how to setup the 2 ISPs on the router? i have found a lot of tutorials but i cannot make it work.
ISP1 has given me a modem in bridge mode and i can use the pppoe username/password.
ISP2 has given me a modem/router that i cannot touch. it is on IP 192.168.2.1/24 and it is on dhcp up to 192.168.2.200. This router is perfoming NAT.

my LAN is 192.168.5.0/24
could someone help me please?

---

### Post by bobnn on 2014-07-09
Here's are excerpts of what I use, but I have no PPPOE.

This 3 ethernet interfaces are handled in /etc/network/interfaces, which can address bot static addressing and DHCP.

**_All standard disclaimers apply._**

Oh one thing I find is that things get a little iffy if you have 2 default routes in ther router as shown by:

```
ip rou ls
```

I choose one and delete the other unless I need it.  Others may have better solutions.




```
#!/bin/bash

echo "Starting Custom Firewall Script"

ANY="0.0.0.0/0"
ANY_HOST="0.0.0.0/0"
ANY_PORT="0"

# eth0 = internal 192.168.5.0/24
# eth1 = ISP 1
# eth2 = ISP 2

echo 1 > /proc/sys/net/ipv4/ip_forward
ip route flush cache

iptables -F 
iptables -F INPUT
iptables -F OUTPUT
iptables -F FORWARD
iptables  -t nat -F PREROUTING
iptables  -t nat -F POSTROUTING
iptables  -t nat -F OUTPUT
iptables -P INPUT DROP
# everthing local
iptables -A INPUT -i eth0  -s 192.168.5.0/24    -j ACCEPT 

iptables  -t nat -P PREROUTING ACCEPT
iptables  -t nat -P POSTROUTING ACCEPT

iptables -A INPUT -i lo -j ACCEPT


# kill RPF which is evil and self-defeating
for f in `find /proc -name rp_filter`; do echo "0" > $f; done

# prevent the spoofing RPF is mistaken designed to stlop
iptables -A INPUT -i eth1 -s 192.168.5.0/24 -j DROP
iptables -A INPUT -i eth2 -s 192.168.5.0/24 -j DROP
iptables -A FORWARD -i eth1 -s 192.168.5.0/24 -j DROP
iptables -A FORWARD -i eth2 -s 192.168.5.0/24 -j DROP

# no traffic between internet interfaces
iptables -A FORWARD -i eth1 -o eth2 -j DROP
iptables -A FORWARD -i eth2 -o eth1 -j DROP


# no multicast to from inside to outside or vice versa
iptables -A FORWARD -d 224.0.0.0/4 -j DROP

# local devices to router
iptables -A INPUT -p TCP -i eth0 -s 192.168.5.0/24  -d $ANY_HOST --dport 22  -j ACCEPT 


# masquerade traffic routed out exteral interfaces
iptables -t nat -o eth1 -A POSTROUTING  -j MASQUERADE
iptables -t nat -o eth2 -A POSTROUTING  -j MASQUERADE

ip route flush cache
echo "Ending Custom Firewall Script"



```

---

