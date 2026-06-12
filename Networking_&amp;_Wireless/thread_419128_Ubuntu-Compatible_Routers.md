---
title: "Ubuntu-Compatible Routers"
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by pteri498 on 2007-04-22
I have a D-Link DI-624 router in my house. It works nicely, though that statement only goes as far as Windows XP.

For Ubuntu, I've had no success connecting to it. I've done searches, and it looks like some ipv6 incompatibility issue, and while I've tried disabling that feature in Ubuntu following several different methods, nothing works.

So I'm ready to scrap my router now. I loved using Ubuntu but haven't been able to for the past 4 or 5 months because I can't get on the internet.

I'm curious, what wireless routers are you all using? Any good mainstream routers that I might easily pick up at Circuit City or something?

*Edit*: Maybe something wherein I can mess around with Quality of Service. I have a fuzzy idea of what exactly QoS is, but as I don't know where to begin on my own router, I haven't had a chance to try it out.

---

### Post by az on 2007-04-22
The router has a web configuration page.  You do not need any special software to configure it or use it.

Are you sure the router is the problem and not your network connection?

[http://support.dlink.com/Emulators/di624_revC/](http://support.dlink.com/Emulators/di624_revC/)

---

### Post by PilotJLR on 2007-04-22
Yeah, this has nothing to do with the router... any router will work just fine. The problem lies elsewhere.
This is also nothing to do with QoS...

Is this is wired or wireless connection between the ubuntu machine and the router?


Edit: I'm assuming the router is not defective, of course... does it work with any other computers?

---

### Post by pteri498 on 2007-04-22
Router works great on 3 other computers (2 wireless, one wired). Router also works great with Ubuntu when wired directly into it.

My wireless connection has worked on a Buffalo brand router in the past, so I'm sure it's not the connection/driver.

I've found limited resources on the DI-624, since it's apparently a very specific and narrow problem, and many of the few articles I've found attributed my problem to an IPv6 incompatibility (the router can't handle it), but disabling it still doesn't let me connect. Ubuntu can see it, but it can't finish a connection.


On a side note, QoS is just a side project that I'd like to get into once I get through this connection problem. I'm not blaming my problem on QoS.

---

### Post by pteri498 on 2007-04-23
Update: Well, I hadn't realized that my router's firmware was last updated in 2003. I'll give an upgrade a try and communicate the results.

Wish me luck!

---

### Post by az on 2007-04-23
> **pteri498 said:**
> 
My wireless connection has worked on a Buffalo brand router in the past, so I'm sure it's not the connection/driver.


Using Ubuntu?

The driver for that wireless card used by Ubuntu is different than the driver you use in Windows.

The router uses tcp/ip.  It is OS agnostic.  it does not know/care what OS you are using.  It's completely different for your wireless card, which needs to be handled directly by the software your computer runs.

---

### Post by pteri498 on 2007-05-01
> **az said:**
> Using Ubuntu?

Yes, using Ubuntu.

I'm not sure at all what the deal is. Feisty can find my router, and attempt to connect, but that's as far as it gets. Never a real connection.

Come to think of it, I think I did once get a connection on knoppix using ndiswrapper... but ndiswrapper won't work out for me on Ubuntu, either.

---

### Post by rsambuca on 2007-05-01
The router isn't your problem, it is the wireless card that you have to figure out.  As Pilot indicated the router will work with ubuntu.

---

