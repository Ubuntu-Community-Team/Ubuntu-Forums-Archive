---
title: "traffic shaping with ubuntu?"
date: 2007-04-15
forum: Networking &amp; Wireless
---

### Post by gruadp on 2007-04-15
Is there a tool recommended for traffic-shaping under ubuntu (6.10) ?  Is tc still the actual tool to do it and is there a nice GUI for it?  I also found tcng,  but it looks rather complex.


What I actually want to do is two things:

i) whatever happens with the connection : leave some bandwith for ssh from outside and give ssh top-priority
ii) neither incoming or outgoing smtp or http-traffic should be allowed to block the connection

The server where the shaping should happen is a small server acting as NAT-router for ~30 clients and connected to internet via a 5000k down, 1000k up- DSL-connection

I've found a script called wondershaper at [http://www.tldp.org/HOWTO/ADSL-Bandwidth-Management-HOWTO/implementation.html](http://www.tldp.org/HOWTO/ADSL-Bandwidth-Management-HOWTO/implementation.html) but it uses a lot of iptable-commands that might interfere with my firewall (firestarter)

thnx,
peter

---

