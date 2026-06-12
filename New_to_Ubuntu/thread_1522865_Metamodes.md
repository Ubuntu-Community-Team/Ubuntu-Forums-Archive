---
title: "Metamodes?"
date: 2010-07-02
forum: New to Ubuntu
---

### Post by M@RS on 2010-07-02
Hi all. I've been using Ubuntu 10.04 now for a couple of weeks, and I  really do love it. However, I've run into a common problem where when  using Twinview with Dual Monitors with games that the games will spread  across both monitors. I mostly play FPS's with the crosshair in the  middle which makes this quite frustrating. I've found the solution to be  somewhere in the Metamodes. But when I go to edit them, my 'screens'  section of the xorg.conf seems to look considerably different than the  ones shown in other threads on these forums. Am I looking at the wrong  section, or does the xorg.conf look different from Ubuntu 9.10 to 10.04?   I'm entirely new to Ubuntu, and would appreciate someone's help with   this.

Thanks.

- M@RS

---

### Post by bodhi.zazen on 2010-07-02
xorg.conf has not changed, but my guess is that the example you are looking at is either not for your hardware or was not using nvidia / twinview.

Post a link to the examples, post the relevant sections of your xorg.conf, and the changes you wish to make.

Also what nvidia card, what monitors, and where did you get the metamode you want to use from ?

Last, xorg.conf is "depreciated" and if you use the working settings you can break your monitor. Most modern monitors will automatically shut off, which means you could loose X.

What backup do you have ? Do you know how to restore your xorg.conf if X fails ?

---

### Post by M@RS on 2010-07-13
> **bodhi.zazen said:**
> xorg.conf has not changed, but my guess is that the example you are looking at is either not for your hardware or was not using nvidia / twinview.

It was for a different Nvidia Card and different monitors.

> **bodhi.zazen said:**
> Post a link to the examples, post the relevant sections of your xorg.conf, and the changes you wish to make.

I can't seem to find the exact link, but here's one with basically  the same solution.
[http://ubuntuforums.org/showthread.php?t=708119](http://ubuntuforums.org/showthread.php?t=708119)
It's the last post.

> **bodhi.zazen said:**
> Also what nvidia card, what monitors, and where did you get the metamode you want to use from ?

8600 GT, My primary monitor (left) is a ViewSonic VA912b, my secondary monitor (right) is an Acer AL1912. Forgive me, but I'm not entirely sure how to answer your last question. I'm still new to all of this.

> **bodhi.zazen said:**
> Last, xorg.conf is "depreciated" and if you use the working settings you can break your monitor. Most modern monitors will automatically shut off, which means you could loose X.
What backup do you have ? Do you know how to restore your xorg.conf if X fails ?

I recently backed up my xorg.conf and yes, I do know how to restore my xorg.conf to my backup.

Sorry for the late reply.
Thanks for any help you can provide me with.

- M@RS

---

### Post by bodhi.zazen on 2010-07-13
You have to either know your monitor, look at the documentation, google for the modline, or use a calculator

[http://www.arachnoid.com/modelines/](http://www.arachnoid.com/modelines/)

You can not simply plug in modlines you find elsewhwere.

---

