---
title: "Linksys router"
date: 2008-11-30
forum: Networking &amp; Wireless
---

### Post by jakespet on 2008-11-30
I am trying to get a Linksys router, previously  used on Windows to work on mu Ubuntu 8.10, but I cannot get it to working. can someone offer me some help.
Thanks

---

### Post by whoop on 2008-11-30
we need more info, man. What type is the router? what are you trying to achieve? what is going wrong?

---

### Post by cariboo on 2008-11-30
Also, how are you trying to connect, wired or wireless?

Jim

---

### Post by jakespet on 2008-12-01
Okay here is what I am doing. I am using a linksys WRT 54G router. It connects to my ethernet 0 port. It was originally connected to MSWindows with broadband comcast internet. When I connect it to my dsl, using Ubuntu 8.10  It will not connect. I open systems/administration/network tools and I follow directins but nothing seems to work. Apparently I am doing something wrong or obviously it would work. 
I hope this is enough info.
B H

---

### Post by gpsmikey on 2008-12-01
First off, can you log into your routers home page and check the configuration ??  It should be at 192.168.2.1 (or 1.1 I forget - I have changed mine a few times so I forget the default).  If you can get in to the router then you know your connection from your system to the router works.  If that does work, try turning the DSL modem AND the router off, wait 30 seconds or so then turn them back on - they often need to "get in touch" :)

You may also be up against the issue that some ISP's use where their modem will only associate with a specific MAC address (was there a PC connected to the DSL before or what?).  If that is the case, you can "clone the mac address" (see the Linksys manual for details on how to do that).

mikey

---

