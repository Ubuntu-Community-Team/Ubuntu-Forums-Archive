---
title: "beginner guide for webserving?"
date: 2009-03-21
forum: New to Ubuntu
---

### Post by Lakeside5 on 2009-03-21
I was just looking at the beginner guide (pdf) for Ubuntu- thanks Keir, it is awesome!   But  I am really slow I guess, I have been at this awhile now and stil can't seem to use Hardy Heron to get my website out there,  with ftp and all.  What I need is a guide as good as that one, that will show me where to put what,  I mean,  what I put in my router   (ip's) and the DunDNS info (got dynamic service for free,  dyndns.org) and hot to connect  to ftp-  I am using fire ftp form firefox...Is there a 'guide for dummies'  concerning what to DO with Hardy Heron  (not just how to install it). For esxample,  it asks for my server nanme, (same as 'computer name'?)  and I think it is 'ubuntu'  as that's what I get when I do a host lookup in terminalk ($  hostname)

---

### Post by hyper_ch on 2009-03-22
what did you do this far and what doesn't work? There are too many things that can go wrong.

---

### Post by Lakeside5 on 2009-03-24
Thanks hyper_ch,   boy you all must wonder how slowww I really am.  I have tried to do this on and off for some time now, I remember you helped me before some time back.  The only different thing now is that I finally broke down and bought a domain name from GoDaddy, and I'm trying to figure out how to use their dynamic nameservers (that seem to have come from with my purchased domain). Prior to this I had accounts with free nameserver sites like DynDNS, OPenDns, etc. but couldnt get that to work either, and I could not use my own domain with them it seemed.  This is the art that has me confused.  I am about to set my router back to factory settings, as now I cannot even get into it after entering IPs here, and doing other things.  If I tyPe in the routers IP I get redirected to my gmail for some reason.
I have webmin installed on here, so I know my aPache webserver is on. Idid a ort search, and it says Port 8 is not oPen, though my ISP swears they are not blocking it..I have a linksys wireless router, and a USB network adaPter+ (d-link) that is only connected to the network at %72 Percent currentlyl. I would like to fix this, and the router isnt really that far from the adaPter- a few feet down the hall. I will tell you whatever you ask, but am not in a hurry for it right now, as I should be studying for a math exam :) thanks hyPer_ch

---

### Post by hyper_ch on 2009-03-24
I don't know if godaddy offers dns for domains on dynamic ips. However I've used everydns.net --> it's free.

Basically you just set the nameservers to point to everydns.net

then you setup the domain there (the according records) and they have a perl script that you can run in cron. So that you update the ip address like every half hour or so.

---

### Post by Iowan on 2009-03-24
I presume you've seen [this]("https://help.ubuntu.com/community/ApacheMySQLPHP") page?

---

### Post by Lakeside5 on 2009-03-24
I shall review the guide- have seen it befor- as now, I can't get localhost to work for some reason. thanks Iowan

---

### Post by Lakeside5 on 2009-03-24
Hyper_ch, hi! I registered at everydns, they seem like a pretty good service. GoDaddy now 'points' to 4 of the everydns nameservers for my domain, and I added my Domain to Everydns, so steps one and two done, now I just have to download the client from everydns.  My last question will probably sound silly to you, as u know what ur doing, but where do I put this info in my router (the everydns nameserver, and the account info I have with them etc.).  I know I will get this soon, getting closer, I'm just wondering why suddenly I can't connect to localhost. And the sign in address for my router has changed by one number..hmmmm.

---

### Post by hyper_ch on 2009-03-25
well, it's a perl script so not on your server but on your linux box. Also the linux box should have a static IP in your lan and then you can port-forward the desired ports to that box. For Web that means port 80. It'd also forward the ssh port to it (22)

---

### Post by 3rdalbum on 2009-03-25
If your router contains a firewall, then you need the router to allow port 80 requests to go through, and go to your web server.

---

