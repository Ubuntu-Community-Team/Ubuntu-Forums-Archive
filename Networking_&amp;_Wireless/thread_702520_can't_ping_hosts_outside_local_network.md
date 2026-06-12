---
title: "can't ping hosts outside local network"
date: 2008-02-20
forum: Networking &amp; Wireless
---

### Post by arunksit on 2008-02-20
I am using ubuntu 7.04 on my laptop.Its connected to a local network.Internet is avaialble on my   system thru a proxy server (CCproxy)on a windows machine on our local network. The problem is that i cannnot ping hosts like google.com. pinging IPs on local network works. How can I enable ping..?

---

### Post by lespaul_rentals on 2008-02-20
It's a DNS problem.

---

### Post by rickyjones on 2008-02-20
What error message do you get when you try to ping [www.google.com](www.google.com) ?

Does it say that it cannot resolve the name?

Does it say that it is timing out?

More information is necessary before a solution can be found.

-Richard

---

### Post by Rogers on 2008-02-20
> **rickyjones said:**
> What error message do you get when you try to ping [www.google.com](www.google.com) ?

Does it say that it cannot resolve the name?

Does it say that it is timing out?

More information is necessary before a solution can be found.

-Richard

also type sudo route and post the output please. :)

---

### Post by arunksit on 2008-02-21
the reply is....

ping: unknown host google.com

---

### Post by arunksit on 2008-02-21
arun@matrix:~$ sudo route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 wlan0
192.168.11.0    *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0

---

### Post by InlawBiker on 2008-02-21
> **arunksit said:**
> the reply is....

ping: unknown host google.com

Then you have no DNS. 

You need to find out what your DNS servers are, from your ISP, or from another working computer there that's configured right.  Then enter the server addresses by going to

System / Administration / Network

DNS tab

Add them 1 by 1.

---

