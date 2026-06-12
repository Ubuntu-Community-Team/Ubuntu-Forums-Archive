---
title: "[SOLVED] Router ip question"
date: 2008-08-21
forum: Networking &amp; Wireless
---

### Post by Bliepo32 on 2008-08-21
Ok, I have the following situation. I have a laptop, running an Apache webserver on Xubuntu linux. It is connected (by LAN, will be replaced by wireless later on) to a router, which is in turn connected to the internet.

So this is the situation.
Internet---->Router (87.209.XXX.XXX)---->laptop (192.168.X.X)

Now I want people to be able to visit my server from the internet. Which IP do they need to enter? Or will I have to change some settings of my router?

---

### Post by Archmage on 2008-08-21
You need to give them the IP of the router (your connection to the internet) and need to open (only) the nessacary ports on your router and your PC.

---

### Post by Bliepo32 on 2008-08-21
And how do I open the ports on my laptop?

---

### Post by sdide on 2008-08-21
Hey, 

If the apache webserver is running, its already listening to port 80 (or whatever port you set it listening to)

What you need to do is to tell your router to translate port 80 requests on the 80.x.y.z address to port 80 request on the 192.168.r.s address. A socalled NAT or PAT or even NAPT :).

How you do that depends on your router flavor.

(its typically done on a web administration page - 
example : [http://192.168.1.1/](http://192.168.1.1/) if that is your local net)

---

