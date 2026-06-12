---
title: "kubuntu hardy 8.04 and via chrome9 hc igp drivers"
date: 2009-09-04
forum: New to Ubuntu
---

### Post by |3illy on 2009-09-04
Hi,
 
I just installed kubuntu hardy 8.04 on my pc.
It has a mini itx mother board with a via chrome9 hc igp graphic card.
On windows, s3 generic drivers were used by default to make it run.
 
On kubuntu I got a weird screen, doubled with lines across the screen.
I change in xorg.conf Driver "vesa" and it works.
I can watch .avi, and get a nice resolution, but emulation with wine is very slow.
(I tryed wine with a small program written in c++/opengl)
I guess I don't have hardware accelerations.
 
I tryed to switch drivers (as there are in the hardware driver's list) to openchrome but got this weird screen again, then I tryed via and got a black screen (had to change xorg.conf to "vesa" again).
 
I tryed this [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome) 
but same results.
 
I search on this forum and others on the web, I found out that some people have the same issue, but didn't find suitable solutions.
I am stuck now and really don't know what to do.
 
I have seen that adept (packet management ?) offer me 166 packets update,
but I don't know if it is reversible if something get updated badly.
 
Is there anybody who can helped me on that please ?
 
Thank you very much
 
|3illy

---

### Post by nandemonai on 2009-09-04
Running through the updates would be a good idea and chances are nothing will break severly. I'd highly recommend doing the updates.

As far as the video thing goes, I think you may be out of luck. I've never seen much luck with those chipsets no matter how hard people try.

Getting yourself some other generic card would likely be the best bet.

---

### Post by |3illy on 2009-09-04
Dear nandemonai,
 
Thank you very much for this quick reply.
I will seriously consider buying a graphic card in a near future.
 
I will try the updates and will inform on the results for who may be interested.
 
|3illy

---

### Post by |3illy on 2009-09-08
Well I did all the update offered by Adept.
Then I try mentionned tutorial to setup my graphic card driver,
unfortunately it wasn't working at all.
 
I had to dpkg-reconfigure xserver-xorg to get my desktop back.
 
I'll wait christmas to buy a graphic card which will be compatible.

---

