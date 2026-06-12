---
title: "Any luck with ACX111 WiFi chipsets (D-Link G520+)?"
date: 2005-05-24
forum: Networking &amp; Wireless
---

### Post by DFreeze on 2005-05-24
I was trying to set up my WiFi last night, thinking NDISwrapper would do the job, but I didn’t succeed. Somehow my .inf file from the original D-Link CD (called GPLUS.INF) was not a good driverfile. 

Any of you know where to start from here? The kernel headers and NDISwrapper 1.2rc1 loaded fine. It just doesn't like the OEM driverfile, I guess.

It's a dual-boot system, and the card works fine in XP.

---

### Post by KiwiNZ on 2005-05-24
I have the g520+ on my network and Ubuntu Hoary set it up with any hassle during the install.All I had to do is activate the connection .

In Suse 9.2 thatI have on my test box all I did was copy the FwRad16.bin and FwRad17.bin from the OEM Disk into the usr/lib/ foder and away it went

---

### Post by DFreeze on 2005-05-24
Wow, so no wrapper used at all? 

I did see the wireless card in the network manager, could activate it even, but I had no clue as to where to go from there... You say that's all there is to it? 

Then how do I get internet and mail use the wireless connection?

As with many of the 'questionneers' I'm a n00b, finally daring to walk the linux-lane after hearing the promising reviews from Ubuntu. So if my question is trivial, please excuse and point me to the direction of further reading.

...Frustrating that 15+ years of computer experience with MS yield so little when in a new OS.  :?

---

