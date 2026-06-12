---
title: "network not found (but firefox is fine)"
date: 2007-05-01
forum: Networking &amp; Wireless
---

### Post by hsweet on 2007-05-01
I'm confused.:confused:  

I blew up a perfectly good edgy Edubuntu server, Replaced it with an easier to install but flakier Feisty.  All the clients and the server can get on the web, but printing does not work (LPD unix printer).  

I got a network not found error, so I tried to ping the printer.  It turns out ping does not work at all (network not found) even though http does. :confused:  

At first i though i had a port issue, but ifconfig reports an incorrect netmask, although the network setting are all correct in the graphical setup tool.  The netmask should be 255.255.255.224 but ifconfig reports 255.255.255.0 (if i remember correctly, I'm at home.  if it would help i can check out that detail tomorrow)

---

