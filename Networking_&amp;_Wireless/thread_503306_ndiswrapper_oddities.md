---
title: "ndiswrapper oddities"
date: 2007-07-17
forum: Networking &amp; Wireless
---

### Post by vfronda on 2007-07-17
Hey, I just switched from slackware to ubuntu because my sound card refused to work with slack.  So far the sound is working on ubuntu, but ndiswrapper is not.  

I installed the old and new ndiswrapper, neither worked, (although both installed at same time).  The ndiswrapper-1.9 couldn't find the module.  and when i entered ndiswrapper -l it came up with this

net8185: driver installed

nothing else!! I thought there was supposed to be something about the hardware being there.
Also, when i checked ndiswrapper -v i got
utils Error: wrong version etc.

I just reinstalled ubuntu, and I'm waiting to see what I can do about this.  

thanks in advance 
vfronda

---

### Post by vfronda on 2007-07-19
figured it out, i was using the net8185 driver instead of the proper 8180 driver.

thanks
vfronda

---

