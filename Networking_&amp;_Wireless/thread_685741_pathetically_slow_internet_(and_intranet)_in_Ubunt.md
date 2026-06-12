---
title: "pathetically slow internet (and intranet) in Ubuntu w/ 43xx"
date: 2008-02-02
forum: Networking &amp; Wireless
---

### Post by dracule on 2008-02-02
My internet connection is ridiculously slow in ubuntu 7.10. I just got my computer back and the replaced the motherboard, but my wireless is incredibly slow. In windows on the same machine it is perfectly fine.
for example:
speeds in DC++ (local network based file sharing): 43 Kb/s I normally get ~20Mbps
^^^ that is to show that even on a local network it is slow.

browsing the web is obviously worse:
simple pages like google time out... (under system moniter it says my bandwidth i am using is ~700 bytes/sec

I am almost finished writing this message and this page is still loading...

So I have to use a Belkin zd1211 based USB wireless... but even that is slow (if I plug it into my other comp, it runs at normal speeds)


It is not my internet connection, since if I simply boot into windows and do a nice speed test, it returns about 30Mbps.

---

### Post by csat on 2008-02-02
Try disable IPv6 from your browser.  Just type about:config at URL address, look for IPv6 and  change its status by double clicking on it.

---

### Post by dracule on 2008-02-02
I dont think that will matter since it is also dreadfully slow on the intranet at my school, and the local connection via DC++.


I just found this out by trial->
 for somereason, if I put in my USB wifi in first, clone my mac address (my school filters), and then connect... disconnect and use my internal wifi, it runs pretty fast.

If i do it any other way it runs slow as hell.
also if i remove my USB wifi the network thing crashes and it wont connect to anything... very strange behavior.

---

