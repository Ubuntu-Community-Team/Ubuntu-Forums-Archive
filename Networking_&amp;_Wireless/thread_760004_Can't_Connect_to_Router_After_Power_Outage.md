---
title: "Can't Connect to Router After Power Outage"
date: 2008-04-19
forum: Networking &amp; Wireless
---

### Post by RossBleakney on 2008-04-19
My power went out for a minute the other day and now I can't seem to access the router. If I directly connect to the cable modem, it works fine. I am connected via a cable to the router (so it isn't a wireless issue). My other box is an NT box and it connects fine via wireless. 

My network settings seem to be OK as well. Everything matches my NT box, with the exception of my IPConfig, which is just one more (192.168.200.101 instead of 192.168.200.100). I thought it might be a DNS issue, but pings to IP addresses don't work either. I also can't access my router via firefox (192.168.200.1) even though that shows up as the gateway. I can access the router with my NT box. Any ideas?

---

### Post by CrazyGuy123 on 2008-04-19
the subnet mask being wrong could cause that.  It should be 255.255.255.0 probably.

If that isn't it, can you tell us the contents of **ip r** in terminal.

It should be:
> 
192.168.200.0/24 dev eth0  proto kernel  scope link  src 192.168.200.101 
169.254.0.0/16 dev eth0  scope link  metric 1000 
default via 192.168.200.1 dev eth0 


if the top line is missing it will also cause the problem you describe.

---

### Post by RossBleakney on 2008-04-19
My subnet mask was right. In fact, everything seemed to be configured correctly. I restarted the router and my cable modem and this time it worked. It was probably the router. Why it worked for wireless but not wired (until the restart) is beyond me. I had also (before I sent the message) tried resetting the router to factory defaults, but that didn't help. Oh well -- I'm glad it's working now. Thanks for your help.

---

### Post by CREEPING DEATH on 2008-04-19
Older Linksys routers are notorious for needing to be manually power cycled after power outages.

CD

---

### Post by RossBleakney on 2008-04-20
It is a Linksys router, so that could explain it. I feel stupid not trying that first, but I think the fact that the other machine (my NT machine) worked fine through me off. Oh well, the lesson has been learned.

---

