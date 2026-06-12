---
title: "Virtual interface (ip-alias) routing"
date: 2007-11-06
forum: Networking &amp; Wireless
---

### Post by witch_doctor on 2007-11-06
Hello 

I have set up ip-aliasing for one of my ethernet interfaces.  The configuration is:

eth0 (public IP a, network A)
eth0:0 (public IP b, network A) 
eth1 (private IP, internal LAN)

  I have created the proper entries in [COLOR="Red"]/etc/network/interfaces[/COLOR] and the interfaces become activated on boot.
All the interfaces seem properly configured when issuing[COLOR="Red"] ifconfig -a[/COLOR]
The problem is that I cannot see an entry in the routing table for eth0:0. Why?
   Even when giving the route command:
[COLOR="Red"] route add -host <IP b> dev eth0:0[/COLOR] it still doesn't show up, instead, IP b seems associated with eth0 when issuing[COLOR="Red"] route -n[/COLOR]. 

 
If I want to route a certain kind of traffic to IP b, and a certain other kind to IP a, how do I do that?
(For example if I want to have a different web server for each IP adress)

---

### Post by him610 on 2007-11-07
I'm not sure it will work in your situation, but you might want to see if this link will help.

[http://tldp.org/HOWTO/IP-Alias/index.html](http://tldp.org/HOWTO/IP-Alias/index.html)

Have a nice day.

---

