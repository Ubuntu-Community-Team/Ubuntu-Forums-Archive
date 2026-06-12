---
title: "Share connection like a hub"
date: 2008-05-23
forum: Networking &amp; Wireless
---

### Post by AliTabuger7 on 2008-05-23
The basis of this need is that I will be going to a college that uses Cisco Clean Access. This, according to some places, means that you cannot use a router, but have to use a hub or a switch.

I would like to share my connection from my Ubuntu computer to my laptop (vista).

I've searched quite a few places, and all methods I've found for connection sharing don't work, and many of them probably wouldn't function like I need it to anyway.

What is the proper term for what I'm trying to do when I want it to act like a switch? I don't think that internet connection sharing is correct because that usually implies masquerading, which I do not think will fit these requirements.

Is there a way to do this?
If so, what method of sharing should I use, and How do I do it? 

On my Ubuntu machine, eth0 is the internet connection and eth1 is the line going to my laptop.

---

### Post by mapes12 on 2008-05-23
[http://en.wikipedia.org/wiki/Clean_Access_Agent](http://en.wikipedia.org/wiki/Clean_Access_Agent)

> I would like to share my connection from my Ubuntu computer to my laptop (vista).

Plug in both machines to the hub or switch. I'm assuming the switch / hub then connects to the network in which case the network will have an internet access point to conduit through to the web.

BTW, Having read about this technology I would bet last weeks pay that a router would be OK.

:guitar:

---

### Post by AliTabuger7 on 2008-05-23
Ok, so there's no way to do this without a hub, and just using the extra Ethernet port on my Ubuntu machine instead?

Then again, according to you, it is possible that any method of connection sharing will work.

---

### Post by mapes12 on 2008-05-23
You could connect to the spare ethernet socket on your Ubuntu box from the windoze machine but I would suggest using a crossover cable if you want to avoid a hub/switch/router in the configuration.

The windoze machine and Ubuntu machine would need to talk to each other. This thread may be helpful to do this:

[http://ubuntuforums.org/showthread.php?t=500734](http://ubuntuforums.org/showthread.php?t=500734)

Personally, I would configure through a switch or router.

---

