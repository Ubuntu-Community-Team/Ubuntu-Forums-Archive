---
title: "Wefi"
date: 2008-08-04
forum: Networking &amp; Wireless
---

### Post by rbolio on 2008-08-04
I know what you are thinking....it's not a typo.

So i was browsing around in the local mag store, and in some computer or internet magazine i found a program called wefi; from what I understood, It helps you find and connect to free internet hotspots (Oh it also triangulates your position =P ) You can also find other users and stuff like that...anyway my problem is this:

When I try to run the program in wine, it says that there is already a connection manager running, How can i turn off the linux internet manager to alow this one to run?


thanks for your time! xD

---

### Post by pytheas22 on 2008-08-04
I could be wrong, but I doubt that this program will work properly through wine--wireless drivers operate on a very low level; wine doesn't interact with the kernel in the way that wireless drivers do.  It's the same reason that you can't just download the Windows installer for your wireless card, run it in wine and be on your way (that would be nice though, wouldn't it?).

Also, I'm not sure how exactly this thing works, but it seems like it either attempts to create a huge ad-hoc wireless network or to create a database of open networks around the world, or both.  You can join ad-hoc networks in Linux just fine (provided your driver supports it; some drivers may require patching), so I can't see why you would need to install the Windows software to be able to join their huge ad-hoc network.  And it seems that you can look up the locations of wifi networks online on their website.

So in short, I doubt there's a way to make Wefi work on Linux.  But I don't think you need to, because it seems that you can look up the locations of free wireless networks on the Wefi website just fine, and if there is in fact a huge ad-hoc network out there of Wefi users, you should be able to connect to it in Linux just as well as in Windows.

---

### Post by rbolio on 2008-08-05
If there is one thing i love about Ubuntu forums, other than quick replies to us humans, is how deep some people take the answer! I hadnt considered it as a HUGE AD-HOC and it really is that (oh btw, didnt seee the map in the site) 

so i have to thank you, pytheas22 , for opening my eyes! (or just bitchslapping me and calling me a extreme downloader [in the case of extreme boredom XD])

haha anyway, just thought it would be a fun thing to try out!....

Cheers!

---

### Post by obtim on 2011-01-01
They have a widget on main page. Maybe it will be usefull.

---

