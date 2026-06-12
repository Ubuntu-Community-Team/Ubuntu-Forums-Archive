---
title: "problem with subnetting"
date: 2007-01-23
forum: Networking &amp; Wireless
---

### Post by vanalex on 2007-01-23
hello everybody!In the university campus that i live we have a big network of about 150 computers. These computers are divided in 8 buildings (i think they are subnets)...So the IP's that the server distributes are:

for the first building 192.168.1.1-255
for the second building 192.168.2.1-255
                           .
                           .
                           .
for the eighth building 192.168.8.1-255.

I installed dapper and i only see the servers and my building (i suppose that happens because i declared as domain my building). Could anyone tell me how can i declare multiple domains so as to see the other buildings? Thank you in advance...
vanalex
:guitar:

---

### Post by darrenm on 2007-01-23
Hi.

Change your subnet mask to 255.255.0.0

---

### Post by vanalex on 2007-01-23
darenm could you please tell me how can i change my subnet mask? i can see it from 

ifconfig eth0

but i don't know how to change it..I'm sorry i'm a newbie..Thank you very much!
vanalex
:guitar:

---

### Post by darrenm on 2007-01-23
Is it a DHCP assigned address or static?

If its static just edit /etc/network/interfaces

If its DHCP edit /etc/dhcp3/dhclient.conf, its commented nicely so it should be easy :)

---

