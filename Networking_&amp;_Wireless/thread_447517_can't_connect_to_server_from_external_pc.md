---
title: "can't connect to server from external pc"
date: 2007-05-18
forum: Networking &amp; Wireless
---

### Post by snek on 2007-05-18
Hi guys, I setup my old laptop as a server the other day and had it working great. 
* I had munin installed to monitor various pc's and served it via lighttpd. 
* I could view the site from external pc's and even using external adress & domain from inside the LAN (Hurray for my D-Link DGL-4100)
* I could SSH to the laptop from an external pc as well

However, I have since then changed the NIC because the old one broke, and replaced lighttpd with a proper LAMP install using Dotdeb. However, this caused some problems and I don't really know where to look to figure out what's wrong. 

Problems:
* Can't connect to laptop from LAN using external adress anymore
* Can't connect to laptop from external PC using external adress OR ip (neither SSH or munin site are viewable)
* I AM able to view the munin site & ssh from a LAN pc using the LAN ip of the laptop

So currently I am remote-desktopping to my XP box from work, and using putty on there to login to the laptop lol.. 

I really hope you guys can help me out..
I am running Debian now instead of Ubuntu but it should all be the same really.. Plus I like this forum better ;)

* Debian 4 (etch)
* OpenSSH
* Apache2
* PHP5 + Suhosin
* MySQL5

I have checked iptables as well and don't see anything in there, plus no special things in auth.log or daemon.log

---

