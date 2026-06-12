---
title: "How to Monitor Bandwidth Usage of Home Network?"
date: 2014-08-24
forum: Networking &amp; Wireless
---

### Post by mark2741 on 2014-08-24
I searched the forum and found a few posts over the years of people asking what I'm about to ask, and surprisingly to me, none have received a reply : (

I am looking for a way to monitor bandwidth usage at any point in time. In my house we have many computers now, one for each family member. My son runs gaming servers on his Ubuntu machine (Minecract, etc.). We have a fiber broadband connection of 85mb down/up from Verizon, so plenty of bandwidth, but lately I've noticed some slowdowns and want to figure out what is causing it.

So, I'd like to:

1. Isolate which computer is causing the slowdown and
2. Know which program is causing it on that computer

Any ideas?

---

### Post by weatherman2 on 2014-08-24
Get a router that has the ability to monitor and display bandwidth.  If your only router is your Verizon FIOS router, it may not have great features in this regard - not sure.  I have a Linksys router on which I installed TomatoUSB firmware, and it has a lot of extra features including bandwidth monitoring. It can tell me which connected devices are using how much bandwidth.

Not every router is compatible with TomatoUSB.  Here's one developer's list of supported routers:

[http://tomato.groov.pl/?page_id=69](http://tomato.groov.pl/?page_id=69)

Many of those routers are older and can be purchased fairly cheaply on eBay, etc. I've had good luck with the Linksys E2500 and E3000, both dual band routers (E3000 has a gigabit ethernet for wired, E2500 is 10/100 only).

---

### Post by tgalati4 on 2014-08-24
Tomato is good as is [dd-wrt]("http://dd-wrt.com/site/index") firmware.  Of course you need a router that can support one or the other.  Otherwise use *etherape* or *wireshark* and try to sniff packets on the network.  Read up on Quality of Service (QoS) which is a method of throttling network traffic based on rules that you set up.

---

### Post by mark2741 on 2014-08-24
Thanks for the help guys.

I have an Apple Airport Extreme (a couple of versions ago). I was going to wait until AC routers come down in price/become more common and then buy a new one. I'll try to find one that will run dd-wrt or Tomato. In the meantime, will try to the two apps suggested. Thanks again!

---

