---
title: "Green &amp; Black lines on screen - Live CD"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by simon_zzz on 2009-01-09
I have an Intel Pentium 4 3.40 Ghz, NVIDA GeForce 6800 GS, P965 Neo Series Motherboard.

The live CD will load up until the point that the OS should load, but I can only see 1980's style green and black lines all over the screen.  I've tried another distro to see if it worked and it did exactly the same thing.  

Any advice?

Cheers

---

### Post by Michael.Godawski on 2009-01-09
hi,

if you have some time, made back-ups of your important data and really want to give Ubuntu a try then use the alternate installer in text mode.

Perhaps after you installed Ubuntu and downloaded the appropriate drivers for your card the glitches disappear. 


[LIST]
[*][http://godawski.oxyhost.com/downloadingubuntu.html](http://godawski.oxyhost.com/downloadingubuntu.html)
[/LIST]

---

### Post by Thingymebob on 2009-01-09
at the boot menu on the livecd press F6 and type "xforcevesa" without quotes at the end of the line, then hit return
or f4 > Safe graphics mode does the same.

This will force xorg to use the vesa driver so you can get your graphical desktop up, from there you should be able to sort out your Nvidia drivers using the restricted modules, if not, post back.

---

