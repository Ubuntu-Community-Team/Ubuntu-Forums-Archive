---
title: "RaLink Driver not loading"
date: 2006-09-24
forum: Networking &amp; Wireless
---

### Post by wonk-o-matic on 2006-09-24
Hours and hours...  and I've wiki'd and googled to death.

Trying to get my Belkin f5d7000 version 3 to come up.  I fooled around with /etc/network/interfaces and ifup ra0, until I finally hit a combination that said "no such device".  It occurred to me then that although the gui shows ra0, the system wasn't loading rt2500.  modprobe rt2500 works, but that doesn't make ifup work.  

:idea: It seems like the logical first step is to get rt2500 to get loaded and associated with ra0.  

How?  There's no aliase stuff anywhere I'd expect it.  

While digging around I found that iftab shows ra0's mac address with with ff:ff:ff:ff:nn:nn, where only nn:nn match the mac on the card.  I also found "rt2500 1.1.0 CVS 2005/7/10 http://rt2x00.serialmonkey.com" in dmesg.  

Any ideas?

---

### Post by wonk-o-matic on 2006-09-29
Got this working.  The problem was intermittent and hardware related.  Finally got tired of fiddling around with it, and just got a new card, today.  It's not RaLink, though. :sad: 

I was very impressed with the built-in RaLink support.

---

