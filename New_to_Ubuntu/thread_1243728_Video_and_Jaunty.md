---
title: "Video and Jaunty"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by sydbat on 2009-08-18
I have Hardy (64bit) installed and want to update to Jaunty (64bit). I have an older ATI card (x600) that supposedly is no longer supported by ATI/AMD, but runs fine with the "current" ATI drivers in Hardy.

I am using the Live CD right now and have tested it with many 3D apps, including games (like Urban Terror) and looked at the output of ```
glxinfo | grep rendering
``` which shows ```
direct rendering: Yes
```.

My question is, with this successful testing through the Live CD, can I be assured that I will have a (relatively) fully functioning video card if I go for the full clean install? 

Also, what driver is powering the card in the Live CD?

Thanks.

---

### Post by Mark Phelps on 2009-08-18
> **sydbat said:**
> My question is, with this successful testing through the Live CD, can I be assured that I will have a (relatively) fully functioning video card if I go for the full clean install?

Also, what driver is powering the card in the Live CD?

Thanks.
Ubuntu 9.04 will install the open source ATI driver for your card, since there is no restricted driver available that works with 9.04.

I don't know if "direct rendering" is supported in the open source driver.  I will have to check that and get back on this.  But I use the same drivers with an X1600 card in 9.04 and it works fine for video, DVDs, and YouTube. So, if that's all you're going to do with it, you should be OK.

---

### Post by sydbat on 2009-08-18
Thanks. As I stated in my OP, it seems Direct Rendering is enabled.

Also, at this point and with my setup, it looks like the open drivers are doing pretty good for the 3D thing. I can even use the cube in Compiz, which is totally 3D.

If this is the case, then I will be able to upgrade without having to go out and buy a new video card.

---

