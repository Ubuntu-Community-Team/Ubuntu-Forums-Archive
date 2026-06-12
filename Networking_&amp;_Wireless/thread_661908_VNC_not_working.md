---
title: "VNC not working"
date: 2008-01-08
forum: Networking &amp; Wireless
---

### Post by Das Oracle on 2008-01-08
I have VNC setup through SSH and it worked fine until I set my second monitor to extend the first. So when I connect remotely It sees the combined resoltuions and will only send an initial picture of the 1st monitor and won't refresh after that. Any ideas?

---

### Post by Dark Hornet on 2008-01-08
--I may be way off here, but I was under the impression that VNC was only able to handle one X session at a time...although if you extended your monitor, I would assume that they are on the same session. (sorry, just thinking out loud).  Maybe VNC is unable to handle both at a time...sorry I wasn't much help.  :)

---

### Post by Das Oracle on 2008-01-08
it is seen as 1 session as far as I know, I know when they were two seperate sessions I could use one just fine, but the other would not show, which was fine for what I need to do, however This just doesn't work at all

---

### Post by Dark Hornet on 2008-01-08
From what I understand (and that may be limited...) if you have multiple monitors, I think you have to specify the second monitor as a "sub-monitor"..for example when you are logging in use remotemachine:0.1,:0.2--([<hostname>[.<domainname>]]:[<displaynumber>[.<subdisplay>]])

I hope this helps...and let me know if I need to clarify anything.

***EDIT***  You also might want to try to reduce the size of the output when you are VNC'ing in...just a thought.

---

### Post by Das Oracle on 2008-01-09
well I tried remotemachine:0.1  and remotemachine:0.2 and also tried what you had specified to get both, but none of them work, If I can get just 1 I would be happy. Where did you get this information?

---

### Post by Dark Hornet on 2008-01-09
I just did a google search on VNC, and multiple monitors--the info that I posted came from this site [http://www.realvnc.com/pipermail/vnc-list/2003-July/040240.html](http://www.realvnc.com/pipermail/vnc-list/2003-July/040240.html), but I also have a friend at work that has done this and used this method.

---

