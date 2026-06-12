---
title: "LAN Party between Windows Vista PC and Lubuntu PC (vía ethernet): Is it possible?"
date: 2016-06-24
forum: Networking &amp; Wireless
---

### Post by hugo37 on 2016-06-24
Hello, I have recently installed Lubuntu 14.04 on an old PC that used to run Windows XP. I'de like to create a LAN party between it and my Windows Vista Home Premium Laptop vía an ethernet cable. (both PCs have an ethernet port). Is it possible? If it is, how? Thanks in advance.

---

### Post by TheFu on 2016-06-26
I suppose it depends on what you mean by "LAN party"?

All computers that use IP networking can speak the same languages. Vista and Linux do, so yes, you can connect them on the same network and they can be told how to talk.

If you'd like to setup a LAN, **the easiest way** is to get a router and connect both those systems to it. A $12 home router will do - assuming you don't intend to connect to the internet. Routers will setup the connection for both using something called DHCP. This method will work with 250 computers. Just add more cheap switches and connect them to the router and the computers (like a tree) with the router as the tree trunk and the computers as the leaves and the switches as branches.  Branches can have many connections to other branches, but only 1 connection to the trunk/roots.

You can also use a $5 switch - and connect both systems to it, but switches don't setup **any** networking, so you'll need to manually configure both computers to be on the same subnet and to have point-to-point connections.  It isn't hard if you understand networking sufficiently. Otherwise, there are 50 tiny things to get wrong (I know I did way back when making my first LAN). This method only works with 2 computers. In theory, it should work with more, but ... 

You can also use a "cross-over cable" directly between the 2 systems. Again, you'll need to manually configure both computers to be on the same subnet and to have point-to-point connections. The cross-over cable may not be absolutely required, any ethernet cable will probably work, if 1 of the systems involved is new enough to automatically sense it and switch the pins inside the ethernet port for you.  GigE ethernet ports all can do this (it is part of the spec), but 10/100 ports are hit and miss depending on the age of the hardware.  This method only works with 2 computers, never more (won't work with 3).

So, you have a choice.  If you get a cheap router (most have sane defaults), this can be a 10 minute effort. Without the router, getting this to work can be either 10 minutes  or 10 days - just depends on your network knowledge and ability to provide accurate data and follow instructions.  In the meantime, the best networking primer that I know begins with episode 25 of Security Now! - [www.grc.com/sn](www.grc.com/sn) .... "How the Internet Works" There are a few episodes to read/listen/learn.  You'll understand arp, ethernet connections, layer 2 switching, layer 3 routing and have a basic understand why IP addresses and netmasks are what they are. Basic knowledge for tech people of today, IMHO.

So - when you say "LAN Party" what do you mean?  Run a web server? Share storage? Keep the time synchronized? Provide remote access? Remote desktop? email? Share an internet connection?  Have a gaming server accessible by 200-50,000 other computers?  There are thousands and thousands of different protocols which can connect computers together.

---

