---
title: "sharing Internet on 3 subnets"
date: 2007-10-13
forum: Networking &amp; Wireless
---

### Post by Lem0nHead on 2007-10-13
hello

I need to configure 2 subnets:
eth0 - my ISP DSL cable - real_IP
eth1 - my first subnet - 192.168.0.0/24 - ONLY FTP access should be allowed FROM it
eth2 - my second subnet - 192.168.1.0/24 - everything is allowed, and it also host an HTTP server

I come with that after reading some tutorials and seeing some samples... can someone tell me if this seems correct?
also, do I need to use the "route" command or iptables will take care of the routing alone?

#inclusive firewall
$IPTABLES -P INPUT DROP
$IPTABLES -P OUTPUT DROP
$IPTABLES -P FORWARD DROP

#probably needed to use states since eth1 will use FTP
$IPTABLES -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPTABLES -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPTABLES -A OUTPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

#eth1 rules
$IPTABLES -A FORWARD -i eth0 -d 192.168.0.0/24 -p tcp --dport 21 -j ACCEPT

#eth2 rules
$IPTABLES -A FORWARD -i eth0 -d 192.168.1.0/24 -j ACCEPT
$IPTABLES -A FORWARD -s 192.168.1.0/24 -o eth0 -j ACCEPT
$IPTABLES -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j DNAT --to-destination 192.168.1.0

thanks very much

PS: this is just a router computer... it doesn't need to access anything

---

### Post by Original Brownster on 2007-10-14
Hi, 
What are the routing entries on the router pc?

# netstat -rn

---

### Post by Lem0nHead on 2007-10-14
none yet
I need to set it up :)

---

### Post by Original Brownster on 2007-10-15
> **Lem0nHead said:**
> none yet
I need to set it up :)
I just re-read your original post and you said you needed to set it up, doh! I should learn to read first.
Anyway my understanding is you will need the routing entries too. Sorry I cannot help with the firewall rules! :)

Edit: Actually it might help to look at 'firestarter', it will generate a set of rules which you can look at and modify which maybe useful to you.

---

