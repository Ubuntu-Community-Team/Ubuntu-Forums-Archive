---
title: "No GUI?"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by DLL on 2009-01-11
A few years ago I thought I'd give Linux a try and gave up when I was confronted with a $ prompt.  I figured I'd try it again when I bought another new laptop.  That time came.  I installed Wubi today on my new Lenovo T400 expecting to reap the benefits of all those years dedicated to making Debian friendly to the masses.  I couldn't wait to see what the desktop GUI interface looked like.  What did I get?  A $ prompt.  Unless there is a really easy fix, I figure I'll just try again in another few years.

---

### Post by tuxxy on 2009-01-11
The easy fix may be to simply type

```
startx
```You could also try a usual install not wubi.

---

### Post by LowSky on 2009-01-11
> **tuxxy said:**
>   You could also try a usual install not wubi.

+1 --Wubi sucks in my opinion

If you really want the benefits dual boot

Use a liveCD, not wubi version

---

### Post by handydan918 on 2009-01-11
+2 Wubi causes more trouble than it's worth. 
Often, a failure to start the xserver is related to nvidia and ati cards that require proprietary drivers. What kind of card do you have?

---

### Post by DLL on 2009-01-13
Thanks for your help.  I tried this on a brand new Lenovo T400 laptop which has switchable graphics, offering both an integrated Intel X4500 and an ATI Mobility Radeon HD 3470 gpu.  Startx was kind of fun.  It generated an error message: no PCI found.

---

### Post by handydan918 on 2009-01-13
"Brand new"  hardware just means the open source developers haven't had time to reverse engineer drivers yet. Try a year-old machine.

---

### Post by hyper_ch on 2009-01-14
did you install the server version?

---

### Post by DLL on 2009-01-14
Thanks.  Others have installed Ubuntu on T400's and gotten far enough to have trouble with wifi so the drivers must be available but yeah, I'm not surprised that Wubi had a problem with it.  I won't give up on Ubuntu but I'm going to stick it on a beater laptop instead.  I used the Wubi installer that comes when you click on the big "download here" button on the Wubi website.  I'd be surprised if that yielded a server version of Ubuntu but stranger things have happened.

---

