---
title: "WL-130G wireless card not working on Feisty"
date: 2007-08-20
forum: Networking &amp; Wireless
---

### Post by kwandar on 2007-08-20
I'm trying to install Feisty on my wife's computer, for school.  I can more or less find my way around Ubuntu Feisty, but I have a major problem.  The wireless card Asus GL-130g using RT2500 drivers will not work.  Without internet, this just makes a good doorstop, and I don't have access to a non-wireless connection for this computer.

I can install a system, and bring up a terminal window but can't do much beyond that (ie. no compiling etc).  I'm new to this.

I finally located the exact issue here, as a bug report:

[http://64.233.167.104/search?q=cache:KoUa9FTIQggJ:https://bugs.launchpad.net/ubuntu/%2Bsource/linux-source-2.6.20/%2Bbug/92742+ubuntu+WL-130g+fixed&hl=en&ct=clnk&cd=1&gl=ca](http://64.233.167.104/search?q=cache:KoUa9FTIQggJ:https://bugs.launchpad.net/ubuntu/%2Bsource/linux-source-2.6.20/%2Bbug/92742+ubuntu+WL-130g+fixed&hl=en&ct=clnk&cd=1&gl=ca)

Problem is, that I can't resolve the issue the way the last commenter suggested (I don't know if/how security mode is 'restricted' and key is set).  I'm stuck.  I'd go beta with Gutsy if this issue has been resolved, but reading the bug report I'm unclear that it has in fact been resolved (much less resolved in Gutsy or whatever the next distro is called).  

So - I don't want to give up - but this really great chance to try out desktop linux is slipping by.  I'd even consider buying another PCI wireless NIC card if I knew for certain it would work.

Help - Please?

---

### Post by sfarber53 on 2007-08-20
Since you are using Feisty, the best thing I can recommend is to use a wireless card/usb device that works directly with Feisty.

I have been using the Belkin F5D7050 V4000.  It costs about $35.00.  I use it under MAC ACL with no encryption and it works well on every machine (desktop or laptop), I have used it on.

ASUS wireless isn't what I would call a mainstream device so its setup will be more trouble.

Check it out.

Cheers!

Steve

---

### Post by kwandar on 2007-08-20
Thank you.

One thing I fogot to mention (I hadn't gotten this far) is that I use WAP security (have to in order to comply with work policy on home computer use).  Can you tell me whether WAP works on hte Belkin?

I know ASUS aren't the most popular, but this uses RT2500 which is an open source driver, so you'd think it would work out of the box.

---

### Post by sfarber53 on 2007-08-20
I can't tell you whether or not the WPA (not WAP) security works on the Belkin device as I haven't tested it yet.  From what I have seen and read it should if you use the right utility to set it.

I've been using MAC address access control lists which require a device to be pre-registered to the router to access the network.

You might check the networking and wireless forum for more details.

Cheers!

Steve

---

