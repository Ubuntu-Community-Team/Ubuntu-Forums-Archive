---
title: "Error: Your current resolution is too high to run Compiz."
date: 2009-01-15
forum: New to Ubuntu
---

### Post by aireq on 2009-01-15
I'm running two 19" Monitors at 1280x1024, and am not able to enable Compiz. Here's what I get from Compiz-Check

```

Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems..../compiz-check: line 488: [: 10767: binary operator expected
           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Your current resolution is too high to run Compiz. 

```

Is there any way I can run Compiz at this resolution?

---

### Post by igknighted on 2009-01-15
No.  The driver combined with that card cannot handle compiz.  With dual monitors you can get 1024x768 on each screen, but that is the best that can be done.

If you switch to the binary ATI driver you (might) have a shot, but I don't know if that card is still supported by the binary driver.

You might also have better luck with KDE getting kwin to give you a 3d desktop instead of compiz at that res.

---

### Post by aireq on 2009-01-15
Oh well. .it's not a big deal the Compiz stuff looked cool though. 


Eric

---

### Post by hatorade on 2009-05-02
```
Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc M24 1P [Radeon Mobility X600]
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Your current resolution is too high to run Compiz.
```

Any way I can run Compiz? I have one external monitor at 1920x1200 and my laptop at 1280x800.

Also, does this monitor set-up/graphics card combo have any effect on why I can't run visual effects in normal or extra mode?

Thanks

---

### Post by hatorade on 2009-05-02
Anyone help?

---

### Post by Didius Falco on 2009-05-02
Hi hatorade,

First, just so you know, it's considered rude to "hijack" someone else's thread. Not only that, but a lot of people will just ignore the "hijacker", so as to not reward bad behavior.

 In the future, start a thread of your own for your questions. It also helps to get a response if you make the title of the thread a short description of the problem you are trying to solve, and include as much information as you can in the first post.

That said, your Radeon Mobility x600 card has been made a Legacy card by ATI. This means that you will be unable to use the proprietary driver and will have to use the 2D XORG driver that is installed by default.

You won't be able to use Compiz, and, as you've already found out, you won't be able to use any of the effects either.

The team of developers at Xorg is working on enabling 3d for older cards, but there is no set release date. It'll happen when it happens.


The only way you are going to get 3D in the short-term is to get a newer video card that is supported, or to go back to 8.10. Even if you go back to 8.10, I don't know how well your card will do in 3D mode...

Here is a list of the ATI cards that have been moved to "legacy" cards, direct from ATI:

> ATI Radeon 9500 Series
ATI Radeon 9550 Series
ATI Radeon 9600 Series
ATI Radeon 9700 Series
ATI Radeon 9800 Series
ATI Radeon X300 Series
ATI Radeon X550 Series
ATI Radeon X600 Series
ATI Radeon X700 Series
ATI Radeon X800 Series
ATI Radeon X850 Series
ATI Radeon X1050 Series
ATI Radeon X1300 Series
ATI Radeon X1550 Series
ATI Radeon X1600 Series
ATI Radeon X1650 Series
ATI Radeon X1800 Series
ATI Radeon X1900 Series
ATI Radeon Xpress Series
ATI Radeon X1200 Series
ATI Radeon X1250 Series
ATI Radeon X2100 Series
 
AMD may periodically provide Windows XP and Windows Vista driver updates (for the products listed above) for critical fixes only.  No new features will be provided in future driver updates.  The Linux ATI Catalyst™ driver will only be supported in Linux distributions prior to February 2009 for the legacy products listed above.
 Any customers using a combination of a ATI Radeon™ HD 2000 Series, ATI Radeon™ HD 3000 Series, or ATI Radeon™ HD 4000 Series product with any of the legacy products listed above in a single PC system must use the ATI Catalyst 9.3 or earlier driver.   All future ATI Catalyst™ releases made available past the ATI Catalyst™ 9.3 release will not include support for the legacy products listed above or any of the features associated with those legacy products.


I hope this helps, and welcome to the forums.

---

### Post by george314 on 2009-09-01
There is an open source driver for the ATI Radeon:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

I have it setup with the ATI mobility radeon X600 and I can run Compiz at a resolution of 1680x1050 on an external 22" Dell monitor.


George314

---

