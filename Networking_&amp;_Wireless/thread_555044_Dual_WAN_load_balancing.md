---
title: "Dual WAN load balancing"
date: 2007-09-19
forum: Networking &amp; Wireless
---

### Post by koma77 on 2007-09-19
I have access to two ISPs in my house. One is rather fast but the link is down from time to time (but it is really cheap). The other is not so fast but more reliable.

I would like to set up a dedicated linux box as a kind of router that could load balance traffic so that I can both get better speed when the choppy connection is working, and also make sure that I always can connect when the choppy connection is down.

I have a spare PC with three NICs in it. I would like to connect my computer as transparently as possible to this "router" or whatever it should be.

Can it be done? And where should I start?

---

### Post by Dark Hornet on 2007-09-19
I am not sure if you can do this with a PC....however, the simplest way I know how to do it is to hook both connections to a router, and set up some metrics on each link.  What type of connections are they...DSL, Cable, T1, Fiber, etc?

---

### Post by koma77 on 2007-09-20
One is a LAN connection and the other an ADSL.

They both use DHCP, so no static IPs unfortunately...

I was hoping to use the old PC as a dedicated router somehow, but I don't know if its possible using Ubuntu.

---

### Post by netztier on 2007-09-20
> **Dark Hornet said:**
> I am not sure if you can do this with a PC....however, the simplest way I know how to do it is to hook both connections to a router, and set up some metrics on each link.  What type of connections are they...DSL, Cable, T1, Fiber, etc?

That is by no means "simple". Since both Internet access lines are consumer grade, there is no support for BGP4 routing and most probably the OPs home won't ever be considered as "multihomed AS".

So the dual WAN router device must use distinct IP source adresses for each "uplink". To make things worse, it also has to make sure that sessions are "sticky", i.e. that once a TCP session with the necessary PAT (aka "NAT overload" or "Masquerading" or "address hiding") translation is established, it keeps it that way. 

It's often detrimental to the web surfing experience when your source IP address changes (because now your dual WAN router decides to suddenly use the other Internet line) whilst you're in the middle of of filling your shopping cart in some Webshop.

So the OP's goal of "load balancing" can be achieved, yes, but it takes a bit and then some more reading and collecting bits and pieces of information:

[http://www.lartc.org/howto/lartc.loadshare.html](http://www.lartc.org/howto/lartc.loadshare.html)
[http://www.linuxquestions.org/questions/showthread.php?t=574424](http://www.linuxquestions.org/questions/showthread.php?t=574424)


best regards

Marc

---

### Post by koma77 on 2007-09-20
Thanks!

I'll read those pages and see if it's possible.

---

