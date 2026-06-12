---
title: "Configuring router for WAP"
date: 2016-01-24
forum: Networking &amp; Wireless
---

### Post by R_Welzel on 2016-01-24
I have a couple of issues that I've spent a lot of time researching but am still having issues getting all the components to work.  I'm hoping someone might be able to help me sort this out.

I have a machine shop set up on my small farm.  We are remote enough that only DSL is available, and the upload bandwidth is terrible.  First I tried to get a bonded DSL, but the ISP won't do that I'm guessing because they can't guarantee the performance.  In any event, when I opened the shop, I installed a second phone line and discovered that they would put me in a second DSL line.

My original plan was to plug everything into my ASUS RT-AC87U in dual wan mode, but, that doesn't really work properly, and when it does, seems only to do fallback mode.

Plan B: convert my server into a router.  I have adapters (em1, p1p1, p1p2) - p1p2 is configured for pppoe and provides a good internet connection at ppp0.  The lan is connected to p1p1 with a static IP of 10.1.1.1 I configured shorewall, dns and dhcp then plugged p1p1 into a linksys 4200.  The configuration on the 4200 was for a static wan ip, dhcp disabled and I set the router ip to 10.1.1.15  (I also have it flashed with dd-wrt).

Connected my laptop to the 4200 and am able to reach it and can confirm that it has a wan IP of 10.1.1.3 (statically assigned), but no internet access.  If I remove the 4200 and connect p1p1 directly to my laptop (10.1.1.11, static), I have full access to the server and to the internet, so that leads me to think that the 4200 isn't communicating properly with the server/router.

The goal for having the 4200 (my test wap which I intend to replace with my AC87U) is to provide the wireless access to the network.  I think that the wired side is working, although I haven't completed any valid test of the dhcp modules since everything I've hooked up to date has been static.  I've seen plenty about inserting a wireless card into the server and bridging it to the lan, which makes sense, but I also can't see any reason why the AC87U or 4200 couldn't act like a wired WAP to provide the wireless component.

I'm sure you'll want to see some configuration files, but I wanted to start with an overview to see if I'm even heading in the right direction first.  Once I get this working with one of the DSL lines, my intent was to connect the second DSL line to em1 and then bridge p1p2 and em1 together, hopefully to provide a psuedo load-balancing wan connection that is faster over all than a single DSL.  That's temporarily on hold since I can't get the wireless side working with just one connection.

Thanks in advanced.

---

