---
title: "Connecting Two LAN cards in one computer"
date: 2013-12-03
forum: Networking &amp; Wireless
---

### Post by ridwansaputra91 on 2013-12-03
Hello all...

I am trying to build a simple lan connection using ubuntu. Since i am new to this os, i think i need some helps for my problem...
I want to build lan connection using 3 laptop, all of it using ubuntu 13.04. Here is the topology
[INDENT=2]
host1 <===========> pc router <============> host2
192.168.x.x                192.168.x.x                        192.168.x.x
[/INDENT]

the pc router has 2 lan card (internal and other one is usb lan). i think i've no problem when configuring both host, but i get some problem when i tried to ping them (between 2 host). do i have to add some routing at pc router? how?

p.s : i have all of them in same subnet (or can it be done otherwise?)

Thanks for the help...

---

### Post by aromo2 on 2013-12-03
A multi-homed computer CANNOT have its network cards set up on the same subnet.  You need the PC router to pass traffic from one subnet to the other, but if host1 and host2 are both in the same subnet, it doesn't make sense to have a router in between.

Depending on your needs, you can use a hub or switch to connect the three devices, -OR- set up host1 and the 1st interface of PC ROUTER on one subnet, and host2 and the 2nd interface of PC ROUTER on a different subnet.

Hope this helps.

---

### Post by ridwansaputra91 on 2013-12-03
Thanks for your reply...

So, i guess i need to use different subnet then, cause the middle laptop has to act as a router not switch. 
Let's say host1 has 192.168.10.0 network and host2 192.168.20.0, do i have to make some routing to make interface of pc router connected each other? How?

---

