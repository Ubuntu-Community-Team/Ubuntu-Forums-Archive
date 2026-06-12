---
title: "Load Balancing (was working before but not now)"
date: 2008-10-23
forum: Networking &amp; Wireless
---

### Post by mlapaglia on 2008-10-23
I've got load balancing set up through using ip tables on ubuntu intrepid. It was working this afternoon but after a reboot it no longer works. 

I was using this guide: [http://lartc.org/howto/lartc.rpdb.multiple-links.html](http://lartc.org/howto/lartc.rpdb.multiple-links.html)

mlapaglia@jennifer-desktop:~$ ip route
192.168.2.0/24 dev eth1  scope link  src 192.168.2.5 
192.168.2.0/24 dev eth1  proto kernel  scope link  src 192.168.2.5  metric 1 
192.168.1.0/24 dev eth0  scope link  src 192.168.1.2 
192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.2  metric 1 
169.254.0.0/16 dev eth0  scope link  metric 1000 
default via 192.168.1.1 dev eth0  proto static 
default via 192.168.1.1 dev eth0 
default 
	nexthop via 192.168.1.1  dev eth0 weight 1
	nexthop via 192.168.2.1  dev eth1 weight 1
mlapaglia@jennifer-desktop:~$ 

the internet works fine right now, but everything is going through 192.168.1.1

can someone help me figure out what I'm doing wrong?

---

### Post by tunggul on 2008-10-23
> **mlapaglia said:**
> 
default via 192.168.1.1 dev eth0  proto static 
default via 192.168.1.1 dev eth0 


Delete this two static routes first: 
ip ro del default via 192.168.1.1 proto static
ip ro del default via 192.168.1.1

then re-apply the loadbalance routing config :
ip ro re default nexthop via 192.168.1.1 weight 1 nexthop via 192.168.2.1 weight 1

---

### Post by mlapaglia on 2008-10-23
Thanks that did the trick:popcorn:

What does re-applying the load balance config actually do?

Before I wasn't applying it again, and i could only use the 192.168.1.1 connection.

Thanks again!!

---

### Post by tunggul on 2008-10-23
> **mlapaglia said:**
> 

What does re-applying the load balance config actually do?

Thanks again!!

Anytime :)
your loadbalance didn't work because you have duplicate default routing:

[I]default via 192.168.1.1 dev eth0 proto static
default via 192.168.1.1 dev eth0
[/I]
[I]default
    nexthop via 192.168.1.1 dev eth0 weight 1
    nexthop via 192.168.2.1 dev eth1 weight 1
[/I]
As the precedence of default routing via 192.168.1.1 is higher (matched first), the system use it for forwarding packet to external network instead of using the loadbalance rule

---

