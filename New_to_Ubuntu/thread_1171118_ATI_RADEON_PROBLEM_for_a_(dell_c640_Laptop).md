---
title: "ATI RADEON PROBLEM for a (dell c640 Laptop)"
date: 2009-05-27
forum: New to Ubuntu
---

### Post by linux_nood on 2009-05-27
hey u guys i have a dell c640 laptop running the ubuntu 9.04 it has a <ATI Radeon 7500> card but i think is not running right.. like if i try doing compiz it lag really bad on visual effect on <extra> i dont know if is the card of the driver for the card really.....if the visual effect are in <normal> it run good..but if i change then to <extra> it lag really bad...i hope someone could help me fix this problem with this laptop.....

---

### Post by overdrank on 2009-05-27
Hi and I have a similar laptop with the ati graphics card like yours. In your other [thread]("http://ubuntuforums.org/showthread.php?t=1167807") related to the graphics issue it was not mentioned **how much system memory**?

I do notice a little slow down in my system with the full effects but I can still watch videos and such.
You may also wish to look at Hardy 8.04 as it ran great on my system but Jaunty 9.04 runs pretty well also.

---

### Post by linux_nood on 2009-05-27
1gig of ram and 2.0 ghz im going to try jaunty by any luck u have any info on how to fix the driver for this laptop

---

### Post by overdrank on 2009-05-27
> **linux_nood said:**
> 1gig of ram and 2.0 ghz im going to try jaunty by any luck u have any info on how to fix the driver for this laptop

The driver I am using is the one with the install of Jaunty and as I said I have no issues.

---

### Post by linux_nood on 2009-05-27
hey overdrank i got the ubuntu 9.04 jaunty and i lookss like it runs i bit better..
how would i get the driver for this video card

---

### Post by Mark Phelps on 2009-05-28
> **linux_nood said:**
> hey overdrank i got the ubuntu 9.04 jaunty and i lookss like it runs i bit better..
how would i get the driver for this video card

You most likely already have the only working driver for this chip.  

Radeon 7500 is a really old chip and is no longer supported under the restricted drivers.  The open source drivers still work, though, and are most probably what you're already using.  But they don't (AFAIK) have hardware acceleration or 3D acceleration included, so there is likely to be lower performance than with the restricted drivers.

---

