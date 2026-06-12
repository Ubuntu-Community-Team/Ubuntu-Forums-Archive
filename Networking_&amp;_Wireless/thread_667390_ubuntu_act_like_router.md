---
title: "ubuntu act like router"
date: 2008-01-14
forum: Networking &amp; Wireless
---

### Post by linux44 on 2008-01-14
hi
how can i run router on ubuntu 
by router i mean ubuntu can do ip forwarding ,NAT ,port forwarding 
can any one please help me with that ,that i am still strugling on it

---

### Post by sqrt2 on 2008-01-14
Your weapon of choice is netfilter/iptables. After activating IP forwarding in the kernel,
[indent]echo 1 > /proc/sys/net/ipv4/ip_forward[/indent]
Linux already acts like a router. You can configure SNAT/DNAT using the same named targets with "iptables -t nat". Make sure you know what you're doing to avoid security problems.

---

### Post by linux44 on 2008-01-14
thanks for respond 
but that is not what i mean what i mean is that proffesional routing like defind static and dynamic router have control on ,not just ubuntu do every thing automaticly
is there any useful article fo it

---

### Post by sqrt2 on 2008-01-15
You can define static routes using the "route" command. Dynamic routing using OSPF or BGP is also possible, [GNU Zebra]("http://www.zebra.org/") can do it.

---

### Post by linux44 on 2008-01-15
thanks 
but i want the article which can teach me all of it from base 
because i am new to linux word

---

### Post by sqrt2 on 2008-01-15
Just google for it. For example, [this]("http://lartc.org/howto/") looks quite promising.

---

### Post by carverj on 2008-01-15
> Just google for it. For example, this looks quite promising.

hmm, looks like a very technical article at first glance
Perhaps something like IPCop
[http://swik.net/firewall+HOWTO](http://swik.net/firewall+HOWTO)

---

### Post by sqrt2 on 2008-01-15
Since linux44 has asked for dynamic routing, which basically is functionality you only need in very large networks (ISPs, big businesses, universities, ...), there's absolutely no way around technical articles.

---

### Post by carverj on 2008-01-15
Yeah fair enough... I guess it was the GRE VPN sections that made me think, hang on, a bit to advanced now.
I studied that stuff on cisco routers (actually news to me that you can use a linux box to do all that).
Nice one sqrt2!!

---

