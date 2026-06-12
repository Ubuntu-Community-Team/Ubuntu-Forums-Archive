---
title: "[SOLVED] Ubuntu is killing my router / DSL connection"
date: 2008-02-28
forum: Networking &amp; Wireless
---

### Post by sgt.peppa on 2008-02-28
Okay this is an awkward problem.

I am connected to the internet via a DSL Modem, which is attached to a wireless router. 
Everything works like a charm, until i boot linux on my laptop.When i then try to surf the web, firefox is endlessly looking up the host, finally ending up in a host unavailable error.

When i then go to management console of the router (wireless lan still works perfectly) i see that th internet connection is down. redialing does not work. Only thing i can do is to switch of modem and router and wait for an hour or so.

I thought ipv6 was causing the problem. So i blacklisted the  ipv6 module. (does this turn of ipv6 completely and system wide?) 
I was able to connect to the internet, but after a few minutes the connection failed and everything is as bad as before.


So do you have any sugestions. 
Thanks in advance...

---

### Post by mrsteveman1 on 2008-02-28
What about other machines on the network? IE start your laptop and do what you just did again, and try to surf from another machine on the network.

---

### Post by sgt.peppa on 2008-02-28
the  internet connection from router to provider is completely down. Even the other computer which is running win xp cant connect any more. I also can see that dsl is down on the console of the router...

---

### Post by sgt.peppa on 2008-03-02
okay, got a new dsl modem, now everathings fine. Linux login to network just seemed to be incidentlial...

---

### Post by mrsteveman1 on 2008-03-02
Does sound like a buggy DSL box, i've seen quite a few of them with poorly implemented software that couldn't really handle network traffic sometimes.

---

