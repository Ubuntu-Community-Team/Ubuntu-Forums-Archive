---
title: "Desktop Effects: Where to Begin??"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by mpl34 on 2009-02-09
Hey

I have done many installations of various compiz apps and plugins, playedaround with it for a bit, was able to make it as my windiws manager but never had any success enabling desktop effects.

Alot of the time i am reading out-dated posts and getting frustrated that they do not relate to my system.

I am not asking you to go into in incredibly in-depth how-to (unless you wish) but would like some advice on where to start and which programs to use. Does compiz have an advantage over Kwin/KDE or is kwin now a competitive replacement?

Any help would be appreciated, heres an idea of where i eventually want to get ---> [link]("http://farm1.static.flickr.com/106/273011211_f6e654dd2b.jpg?v=0")

---

### Post by billgoldberg on 2009-02-09
Well, I can suggest my guide on Compiz fusion effects.

[http://linuxowns.wordpress.com/2008/06/16/guide-to-customizing-ubuntus-look-and-feel/#5](http://linuxowns.wordpress.com/2008/06/16/guide-to-customizing-ubuntus-look-and-feel/#5)

But that was meant for Ubuntu (I would still read it though).

First you'll have to install Compiz Fusion.

Open up your package manager (Adept?).

And search for "Compiz Fusion" and the "Compiz Fusion Effect Manager".

Also install the "Compiz Fusion Icon".

Once all of that is installed. Open up the "Compiz Fusion Icon" program.

It will sit in the system tray. Set it to use "Compiz Fusion":

[[img]http://xs536.xs.to/xs536/09071/compiz412.png[/img]](http://xs.to)

Your screen will flicker and you'll be using "Compiz Fusion". 

Make the "Compiz Fusion Icon" start on boot, that will make "Compiz Fusion" start on boot.

Then use the guide I've posted to set up the cube and other effects.

---

### Post by HavocXphere on 2009-02-09
Afaik, the cube is only available in KDE 4.2, not in 4.1.X that is shipped on the CD...so you'd have to upgrade it.

Once you've got a working GFX driver with 3d acceleration, its just a matter of enabling it in the menus.

I'm not sure whether Compiz and KDE4 play nice together.

---

### Post by abn91c on 2009-02-09
the desktop effects are integrated in KDE 4.2. Compiz will not play nice in Kubuntu, plus you need a good video card that supports 3D and open GL

---

### Post by SunnyRabbiera on 2009-02-09
> **abn91c said:**
> the desktop effects are integrated in KDE 4.2. Compiz will not play nice in Kubuntu, plus you need a good video card that supports 3D and open GL

Well my card is sort of low end but i seem to be able to run KDE4 effects just fine.
But for the OP the best way to test out effects in kde is to install kde 4.2 and try it out.
Its easy enough to install:
[http://www.kubuntu.org/news/kde-4.2](http://www.kubuntu.org/news/kde-4.2)

Note that even though the page is for the RC the repository it lists has the final release.

---

### Post by mpl34 on 2009-02-09
My graphics card is a NVidia 8600GT. If KDE and compiz-fusion won't play well together should i install the gnome dektop pakage.

Will running gnome with compiz-fusion be a better alternative that KDE/Kwin.

I will try out kde4.2 once i get home, thankyou for the suggestions.

---

### Post by joey-elijah on 2009-02-09
From my experiences  you're bang on the buck : KDE and Compiz-Fusion don't play well together. Certainly nowhere near as seamlessly as Gnome and Compiz.

---

### Post by mpl34 on 2009-02-10
I have now installed kde4.2 and looks great except that i have lost my desktop effects and i can't figure out why!!

The first time i rebooted it worked fine with all the dektop effects, i then updated, upgrade and tried to run kiba dock. (got a few errors when trying to run kib-dock).

After this my desktop effects stop workin!!

Any help would be much appreciated.

---

### Post by wieman01 on 2009-02-10
You need to install the latest NVidia drivers in order for KDE 4.2 to function properly. I am running 4.2 on my legacy NVidia card and performance is great. Desktop effects will be enabled by default provided that you got the hardware and drivers to support it.

Attached a screenshot.

---

### Post by mpl34 on 2009-02-10
```
michael@michael-laptop:~/Apps$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   KDE4
 Graphics chip:         nVidia Corporation GeForce 8600M GT (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: Unable to detect maximum 3D texture size

```

I thought i did have the latest NVidia driver however i will try a reinstall

---

### Post by mpl34 on 2009-02-10
Well it seems that reinstalling the driver fixed all thanks for the advice.

Just one more thing can anyone give me advice on how or whether kiba-dock can work with kde4.2 and if not what dock is a good alternative.

---

