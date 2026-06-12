---
title: "weak wireless reception on fresh edgy install"
date: 2007-02-22
forum: Networking &amp; Wireless
---

### Post by VCSkier on 2007-02-22
A friend of mine has a fresh install of edgy on his laptop, and wireless worked out of the box once I got network manager installed, but his signal reception is always poor.  Even when he is very near the access point, signal strength never reaches over %50, and downloads are much slower than they should be.  He is very new to linux, and I have no experience in troubleshooting this, so where should we start?  Thanks.

---

### Post by happy-and-lost on 2007-02-22
Which wireless card is he using?

---

### Post by fiveiron on 2007-03-07
Same exact problem here.  I have a Thinkpad T41p running an Atheros-based wireless adapter.  My access point is about 10 feet from the laptop and the signal strength never reaches over 50-60%.  In Windows I am consistently at 100% strength.

I'm curious if Linux is purposely scaling the card back or what.

---

### Post by kiddo on 2007-03-29
the atheros cards have a different (crazy) way of counting the signal strength, they have a maximum that is way too high. That is the problem. Seems pretty harmless though.

---

