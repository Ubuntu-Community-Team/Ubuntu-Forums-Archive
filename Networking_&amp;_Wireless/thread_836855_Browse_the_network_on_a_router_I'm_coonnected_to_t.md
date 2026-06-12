---
title: "Browse the network on a router I'm coonnected to through another router???"
date: 2008-06-21
forum: Networking &amp; Wireless
---

### Post by djrobthaman on 2008-06-21
Hi,

I don't think this problem is strictly an ubuntu problem... more like a general networking problem, but I thought maybe somebody might have had some experience in the realm,

I just got a wirless router,  But at the same time I weant to keep my old wired router as well.  So what I've done is I've left the wired router as it was, with 3 other users connected to it.  Then I've plugged the ethernet cable that was my internet connection into the wireless router.  So now there is a router between me and the router that everyone else is connected to (Have I explained this clearly?)

Now I can't see any of these people on the local network.  I suppose this makes sense because nobody else is connected to the router that I'm most immediately connected to.  But is there a way to connect to the network on the other router that everyone is connected to?

Thanks a bunch

---

### Post by superprash2003 on 2008-06-22
connect the old router to the LAN port of the wifi router..also make sure that DHCP is disabled on the wifi router and enabled in the wired router.. so your wifi router would act like a wifi hub!!

---

### Post by jetsam on 2008-06-22
+1 to what Superprash said.

There's a web page here that explains the solution in more detail:
[http://www.smallnetbuilder.com/content/view/24431/53/1/2/]("http://www.smallnetbuilder.com/content/view/24431/53/1/2/")

That's page three of the article.  The rest of the article explains the problem in general terms.  The article is about windows networks, but the same principles apply.  

Netbios browsing can't work well across a NAT connection, so you need to disable the router part of your second router and use it as a switch/access point.

---

