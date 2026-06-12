---
title: "[SOLVED] Dyndns Problem"
date: 2008-01-06
forum: Networking &amp; Wireless
---

### Post by borobudur on 2008-01-06
I have a problem with dyndns:

I forward the ip from the router to the main computer in my network so that I can reach it with ***host.dyndns.org*** from outside.

From the main computer I can brows the apache-server like that:

host.dyndns.org/

I receive the welcome page index.html but if I do the same with a other computer in my network I receive the routers configuration panel.

I installed aMuleWeb and there I receive the website over the browser from a client computer with 

host.dyndns.org:4711/

If I do a traceroute on two machines I get this:

The main computer in the network:
```

user@desktop:~$ sudo tracepath host.dyndns.org
 1:  xxx-xxx.x-xx.cust.bluewin.ch (85.3.xxx.xxx)     0.106ms pmtu 16436
 1:  xxx-xxx.x-xx.cust.bluewin.ch (85.3.xxx.xxx)     0.046ms reached
     Resume: pmtu 16436 hops 1 back 1 

```A client (laptop):
```

user@notebook:~$ tracepath host.dyndns.org
 1:  notebook.local (192.168.1.36)                         0.313ms pmtu 1500
 1:  192.168.1.1 (192.168.1.1)                             22.183ms 
 2:  192.168.1.1 (192.168.1.1)                   asymm  1  15.707ms 
 3:  xxx-xxx.x-xx.cust.bluewin.ch (85.3.xxx.xxx) asymm  2  18.561ms reached
     Resume: pmtu 1500 hops 3 back 2 

```Has anyone an idea?

---

### Post by stalker145 on 2008-01-06
> **borobudur said:**
> I have a problem with dyndns:

I forward the ip from the router to the main computer in my network so that I can reach it with ***host.dyndns.org*** from outside.

From the main computer I can brows the apache-server like that:

host.dyndns.org/

I receive the welcome page index.html but if I do the same with a other computer in my network I receive the routers configuration panel.

I installed aMuleWeb and there I receive the website over the browser from a client computer with 

host.dyndns.org:4711/

If I do a traceroute on two machines I get this:

The main computer in the network:
```

user@desktop:~$ sudo tracepath host.dyndns.org
 1:  xxx-xxx.x-xx.cust.bluewin.ch (85.3.xxx.xxx)     0.106ms pmtu 16436
 1:  xxx-xxx.x-xx.cust.bluewin.ch (85.3.xxx.xxx)     0.046ms reached
     Resume: pmtu 16436 hops 1 back 1 

```A client (laptop):
```

user@notebook:~$ tracepath host.dyndns.org
 1:  notebook.local (192.168.1.36)                         0.313ms pmtu 1500
 1:  192.168.1.1 (192.168.1.1)                             22.183ms 
 2:  192.168.1.1 (192.168.1.1)                   asymm  1  15.707ms 
 3:  xxx-xxx.x-xx.cust.bluewin.ch (85.3.xxx.xxx) asymm  2  18.561ms reached
     Resume: pmtu 1500 hops 3 back 2 

```Has anyone an idea?

A few questions:

1. Is your main computer the one that has your apache server on it?

2. Is your router configured to allow for remote access configuration on port 80?

That's all I can think of to be the problem. If you're trying to get from your main computer to your web site (which I'm assuming is on the same main computer) you will more than likely not even leave your computer is the networking is set up like I'm thinking. This is why you can get it on your main computer... OTOH, trying to get from the other computer to your web site is being held up because your router is (possibly) accepting connections into its configuration area on port 80.

That's my thought off the top of my head.

---

### Post by borobudur on 2008-01-06
you are right, it must have been the remote access configuration of the router.

It said that it was turned off but I played around with it once. I made a reset and since then it works.

Thanks!

---

