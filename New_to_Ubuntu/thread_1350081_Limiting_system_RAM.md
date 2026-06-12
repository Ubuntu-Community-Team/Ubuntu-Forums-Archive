---
title: "Limiting system RAM"
date: 2009-12-08
forum: New to Ubuntu
---

### Post by KooKooKahbuntu on 2009-12-08
I am trying to limit my system RAM from 4GB to 2GB and do not know how to achieve this. I need to do this as I read on a forum that the video card I have only currently supports up to 2GB of RAM. So I installed and am currently running on safe graphics mode (vesa).

My system details are as follows.
Ubuntu 9.10 amd64 on a Toshiba A350 laptop (4GB RAM). Video card is ATI Radeon 3650HD 512MB. I also have a dual boot with windows xp, if that matters.

---

### Post by cariboo on 2009-12-09
Does your graphics adapter use shared ram, or is it separate? Looking a the ATI web site, your graphics adapter is supported by the latest restricted drivers, so you shouldn't have a problem.

---

### Post by Malta paul on 2009-12-09
I would think your system ram should have no effect on your video card which has its own ram of 512MB.

---

### Post by lotharmat on 2009-12-09
> **cariboo907 said:**
> Does your graphics adapter use shared ram, or is it separate? Looking a the ATI web site, your graphics adapter is supported by the latest restricted drivers, so you shouldn't have a problem.

Please could you provide a link; I need to see if my card is supported.

Cheers

---

### Post by KooKooKahbuntu on 2009-12-09
I am not sure how to check if my system is on shared RAM or separate. Like Malta Paul said, doesn't the 512mb memory for the ATI Radeon HD 3650 card mean it is separate?

The issue as explained by the thread below is that the 4GB of system RAM seem to mess up the video card, but when limited to 2GB, the card works. See thread below.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/341681](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/341681)


With my original question of limiting RAM. I figured how to do it by looking at the boot options help page on the Ubuntu site. By editing the boot options and putting "mem=2G" and boot with that (to temporarily change the boot conditions for that session).

However this still did not fix my video card problem. I've tried with using the driver from ATI, the fglrx driver, and also from envyng. Will now look at some other thread to my specific graphics problem again. Thanks guys. :popcorn:

---

### Post by Jive Turkey on 2009-12-09
You may consider physically removing 2GB of ram to see if that makes any difference.

---

### Post by KooKooKahbuntu on 2009-12-09
Not really confident with my skills to remove stuff from my laptop.

---

