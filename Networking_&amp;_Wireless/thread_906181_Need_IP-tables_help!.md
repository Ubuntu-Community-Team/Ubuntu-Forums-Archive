---
title: "Need IP-tables help!"
date: 2008-08-31
forum: Networking &amp; Wireless
---

### Post by xterm on 2008-08-31
Hello

I need help with a ip-tables rule. 

At work I'm behind a firewall that only allowes serten ports for traffic to Internet. I need to access my home server on ssh. Now, that server acts like a router also so I just can't change the listening port for ssh I need to do a port-forwarding on the traffic if it comes from a specific IP-range. 

In sevdo-code like this. 

if ip="work-ip-range" and port=443 then "portforward" to port=22 on "this same server"

Hope I made myself sort of clear... :-)

---

### Post by koenn on 2008-08-31
look up DNAT and REDIRECT in man iptables (or google it).
If you can't work it out from there, you have no business circumventing corporate firewalls.

Actually, you shouldn't be poking holes in corporate firewalls in the first place. They're there for a reason.

---

### Post by xterm on 2008-08-31
I got the Idea from my company Network cheaf so I'm shure It's ok. 

I will look into this. Thanks for the help 

(If anyone can give me a more precis answer I would apriciate it)

---

