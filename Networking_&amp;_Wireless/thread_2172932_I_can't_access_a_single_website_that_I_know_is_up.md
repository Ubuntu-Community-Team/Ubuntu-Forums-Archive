---
title: "I can't access a single website that I know is up"
date: 2013-09-07
forum: Networking &amp; Wireless
---

### Post by papillion on 2013-09-07
**OS: Xubuntu 12.04**

Hello Everyone,

One of the sites I enjoy visiting is [www.schneier.com](www.schneier.com). It's the website of security expert Bruce Schneier and, until sometimes Wednesday, I had absolutely no problem visiting the site at all. Then, all of a sudden, it went dark.

Originally, I chalked it up to that he was having trouble with his website. But over the last few days, i realized that his site is up but I simply can't reach it. 

A traceroute of 23 hops leads me into the company that hosts his site (blackfoot.net) at hop 19 but then goes completely dark. A ping of schnierer.com returns nothing - not even packet loss. It just looks the site up then sits there. I can't even go to the site by a proxy like IXQuick! I've tried on both Firefox and Chromium and both perfom the exact same way. I've checked /etc/hosts just to make sure something weird hadn't happened and everything looks fine.

Now, this might lead you to believe that I have some kind of problem with my network gear. Maybe a router that's messing up. But if I get on my Windows 7 box that's on the same network, everything works fine, so I have to conclude there's something going on in Xubuntu.

Can anyone shine some light on this? What might be going on that could stop me from reaching this single site?

Thanks!
Anthony

---

### Post by ajgreeny on 2013-09-07
I am also running Xubuntu 12.04 64 bit, and that site shows perfectly on my machine, so it can't be something specific to Xubuntu.  What hardware and graphic card do you have (I have Intel HD4000), though I can't imagine why that should matter just on that site?

---

