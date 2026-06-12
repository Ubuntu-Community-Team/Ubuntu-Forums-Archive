---
title: "Ubtunu based Router"
date: 2008-11-25
forum: Networking &amp; Wireless
---

### Post by Drezard on 2008-11-25
I have an Ubuntu Linux Box. Its in the topology like this:

Modem (192.168.1.1) - (192.168.1.2) Ubuntu (10.1.1.1) - Hub - Host (10.1.1.5)

So basically, I want to be able to access the internet on Host. How do I get it so that Ubuntu forwards all the traffic from one interface to another. 

Daniel

---

### Post by doas777 on 2008-11-25
well you have a choice. you can install a proxy server like [squid]("http://linux.about.com/od/ubusrv_doc/a/ubusg26t01.htm")

or you can add a route from 10.1.1.0/24 to 192.168.1.0/8 and set the default gateway to 192.168.1.1.

---

