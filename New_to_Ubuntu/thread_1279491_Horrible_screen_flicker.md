---
title: "Horrible screen flicker"
date: 2009-09-30
forum: New to Ubuntu
---

### Post by CSHANKY on 2009-09-30
My screen flickers violently every time my computer wakes up from hibernate mode.

Is there a fix to this problem?

Ver 9.04 installed.

---

### Post by Cuco3 on 2009-09-30
> **CSHANKY said:**
> My screen flickers violently every time my computer wakes up from hibernate mode.

Is there a fix to this problem?

Ver 9.04 installed.Same thing happened to me. I was using an Intel 82845 integrated video on Ubuntu 9.04.

I chalked it up to lack of driver support. Good luck with your quest to fix it. I suggest buying a new video card, if possible, or downgrading to an earlier version of Ubuntu. Just don't waste too much time on it like I did.

---

### Post by Excedio on 2009-09-30
> **Cuco3 said:**
> Same thing happened to me. I was using an Intel 82845 integrated video.
 
I chalked it up to lack of driver support. Good luck with your quest to fix it. I suggest buying a new video card, if possible. Don't waste too much time trying to fix it.
 
Fixing it would be a lot less expensive.

---

### Post by Excedio on 2009-09-30
> **CSHANKY said:**
> My screen flickers violently every time my computer wakes up from hibernate mode.
 
Is there a fix to this problem?
 
Ver 9.04 installed.
 
What kind of computer and what kind of graphics card?

---

### Post by Cuco3 on 2009-09-30
> **Excedio said:**
> Fixing it would be a lot less expensive.Depends if you think time is money... I've wasted over 20 hours of researching and trying tons of fixes on that screen flicker problem and it didn't get fixed.

I chalked it up to lack of driver support for the video card. Solution: buy a new video card OR try downgrading to earlier versions of Ubuntu.

Don't waste your time trying to fix it.

---

### Post by Excedio on 2009-09-30
Maybe you can try these:
 
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/351423](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/351423)
 
(For Gusty, but never know)
[http://ubuntuforums.org/showpost.php?p=3630177&postcount=10](http://ubuntuforums.org/showpost.php?p=3630177&postcount=10)
[http://ubuntuforums.org/showthread.php?t=579565&highlight=screen+flicker](http://ubuntuforums.org/showthread.php?t=579565&highlight=screen+flicker)

---

### Post by blackened on 2009-09-30
What kind of monitor and video card are you using? The regressions in the Intel driver under Jaunty are absolutely terrible, but not unmanageable.

If you're using an Intel integrated solution, then start by following the guide [here]("http://ubuntuforums.org/showthread.php?t=1130582").

If you're using something else, then I would lean towards the flicker being caused by an incorrect refresh rate. My LCD (22" KDS) gives a strange watery effect at 60hz, but not at 75. If you don't have any other refresh rates available, then you can probably add one or two with xrandr. It all depends on what your hardware will support.

---

### Post by CSHANKY on 2009-10-02
Hi ! This flicker issue is driving me nuts:

- I am using an 19 in LCD monitor set at 75 Hz refresh rate. Dell Dimension 2400, Intel P4 2.53 Ghz 
- VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

Does anyone know how to fix this problem? A step-by-step guide would really help.

Thanks

---

### Post by Cuco3 on 2009-10-02
> **CSHANKY said:**
> Hi ! This flicker issue is driving me nuts:

- I am using an 19 in LCD monitor set at 75 Hz refresh rate. Dell Dimension 2400, Intel P4 2.53 Ghz 
- VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

Does anyone know how to fix this problem? A step-by-step guide would really help.

ThanksDowngrade to an earlier version of Ubuntu.

Jaunty, and presumably future versions, will have problems with integrated Intel video cards.

---

### Post by CSHANKY on 2009-10-02
You may be right...but I don't want to give-up (on Ubuntu) just yet.

It's a great software and free. But it falls miserably short of expectations when trying to debug graphics issue and trying to play Youtube (no sound).

There seems to be no direct fix - most of it seems to be by trial and error. And novices (like me) could mess up their system big time doing that.


Thanks for all the responses.

---

