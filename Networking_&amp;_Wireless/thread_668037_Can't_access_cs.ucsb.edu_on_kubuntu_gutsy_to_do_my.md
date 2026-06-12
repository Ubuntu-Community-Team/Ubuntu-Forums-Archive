---
title: "Can't access cs.ucsb.edu on kubuntu gutsy to do my homework"
date: 2008-01-15
forum: Networking &amp; Wireless
---

### Post by checho4 on 2008-01-15
I'm a computer engineering student at UCSB and I need to access [www.cs.ucsb.edu](www.cs.ucsb.edu) in order to get my homework.  For about a week, I've had a strange problem.  I can access the website via Windows XP, but not under my Kubuntu Gutsy.  The internet connection is fine.  I can browse any other page I'd like, even on the UCSB.edu network.  I just can't access the cs.ucsb.edu website.  Any help is greatly appreciated!

---

### Post by kostkon on 2008-01-15
Strange, because I can access the site just fine. Try to clear your browser's cache.

---

### Post by evanchu on 2008-01-15
Try the following the post the output of each command.

ping -c 5  [www.cs.ucsb.edu](www.cs.ucsb.edu)

traceroute [www.cs.ucsb.edu](www.cs.ucsb.edu)

Finally, run "telnet [www.cs.ucsb.edu](www.cs.ucsb.edu) 80".  When you see "connected to www.cs.ucsb.edu", press the slash key then enter key.  What do you get?

---

### Post by checho4 on 2008-01-15
Ok, I cleared my cache and I was able to access the website now.  Thanks so much!

---

