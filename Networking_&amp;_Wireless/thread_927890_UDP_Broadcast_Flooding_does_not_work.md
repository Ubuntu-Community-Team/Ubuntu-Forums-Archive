---
title: "UDP Broadcast Flooding does not work"
date: 2008-09-23
forum: Networking &amp; Wireless
---

### Post by Friedo on 2008-09-23
For special application we need "Multiple routable Subnets" with UDP Broadcast Flooding". 
The Cisco routing Solution is in this link : 
[http://www.cisco.com/en/US/docs/internetworking/case/studies/cs006.html](http://www.cisco.com/en/US/docs/internetworking/case/studies/cs006.html) 

We need an equivalent solution with Debian (Ubuntu) 

Routing between VLANS is already existing with vconfig & iproute2 and runs well. 

We have already activated in "iptables" Broadcast in FORWARD chain, but without success. 
Here our command example : 
iptables -A FORWARD --in-interface eth0.105 --out-interface eth0.101 --proto udp --dport 9005 -m addrtype --dst-type BROADCAST -j ACCEPT 


Is'it possible to realize the UDP Braodcast Flooding between subnets with Debian ? and what SW Version is necessary ? 

Thank you for your help and comments

---

