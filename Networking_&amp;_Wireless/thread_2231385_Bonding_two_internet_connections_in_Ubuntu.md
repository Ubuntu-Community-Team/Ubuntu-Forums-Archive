---
title: "Bonding two internet connections in Ubuntu"
date: 2014-06-25
forum: Networking &amp; Wireless
---

### Post by tom60 on 2014-06-25
I rely heavily on the internet, not only for social purposes but also for my education (I am getting an online masters degree now) and for work - I am beginning to do online teaching.  I have a 100M connection - fiber optics - and it is really fast, when it works well.  When it doesn't work well, the connection is not fast enough to do the work I need (mostly voice and video, with chalkboard, etc).   My contract with my provider is at an end now - I am also moving to a new apartment.  I am was thinking about getting 2 different internet connections in my new apartment - from 2 providers - so that I have a choice.  I was wondering if there is some way to "bond" the two together?  They will most likely be 50M connections - the 100M that I have now does not provide better performance than a 50M.  Is there hardware or software that will help me not just distribute the load between the two but perhaps give me more than 50M?  I have Ubuntu on a dual core notebook that I have set up to be my server.  It has several functions but minimal load on any of them - I am the only user.  My home router is old - it is time for a new one, so that is one part of the puzzle that can be changed.

---

### Post by tgalati4 on 2014-06-25
[https://help.ubuntu.com/community/UbuntuBonding](https://help.ubuntu.com/community/UbuntuBonding)

It may not give you better performance if both ISP's rely on the same master service provider; there may be a bottleneck at the provider's end.  Using bonding with video may cause issues with syncronization of audio and video.  Only testing will tell if bonding 2x50M connections is better than 1x100M connection.  It would also pay to invest in a business-grade router with a fast backplane.  Most residential routers can't handle 100M traffic.

---

