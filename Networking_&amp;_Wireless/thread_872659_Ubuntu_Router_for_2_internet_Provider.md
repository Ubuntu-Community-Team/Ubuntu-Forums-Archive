---
title: "Ubuntu Router for 2 internet Provider"
date: 2008-07-28
forum: Networking &amp; Wireless
---

### Post by smadon on 2008-07-28
Hi,

I'm trying to use my ubuntu box to be router and proxy
So, My config : 
Eth1 -> Cable Internet connect to Internet
Eth1 -> Internal Network which are behind Squid
Eth2 -> ADSL connect to Internet


I am trying to follow the procedure : [http://lartc.org/howto/lartc.rpdb.multiple-links.html](http://lartc.org/howto/lartc.rpdb.multiple-links.html)
But it doesn't seems to work.

Squid work fine with the rules in the iptables: 
iptables --table nat --append PREROUTING -p tcp -m tcp -i eth1 --dport 80 -j DNAT  --to 10.0.0.1:3128

Is there anybody who did, the routing schema for 2 Internet Provider + squid ?

Thanks for your help :guitar:

---

