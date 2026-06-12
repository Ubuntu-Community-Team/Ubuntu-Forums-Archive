---
title: "iptables/firehol - bridging"
date: 2006-08-22
forum: Networking &amp; Wireless
---

### Post by Mithrilhall on 2006-08-22
I currently have the following setup:

<--->Cisco Router<--->Linux Firewall (FireHOL) <---->8 Port Switch<----->Computers

My Linux firewall is running Kubuntu (FireHOL). It has 2 Network cards installed (eth0 & eth1) which are bridged together (br0).

My Cisco router is also a dhcp server. Once FireHOL is running nothing behind it can pull an IP address.

My firehol.conf is pretty simple.

> 
iptables -t filter -I OUTPUT -d 127.0.0.1 -p tcp --dport 3128 -m owner ! --uid-owner dansguardian -j DROP

transparent_squid 8080 "root root"

interface any world
policy drop
protection strong
client all accept
server cups accept


I'm not sure what needs to be changed to allow my local network to have access to the internet.

10.2.176.0/24

Any suggestions would be appreciated.

---

