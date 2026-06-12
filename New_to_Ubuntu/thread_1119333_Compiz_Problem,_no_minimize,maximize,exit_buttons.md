---
title: "Compiz Problem, no minimize,maximize,exit buttons"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by DracoJesi on 2009-04-07
I installed Compiz,all the effects I've tried work, with no slugishness at all, but this has come at a cost, the minimize, maximize and exit buttons have disappeared on all of my windows...

I have turned of all the plugins and nothing has changed..

I tried disabling legacy  support, as suggested, no good, 

it seems allot of people have had this problem according to google,but I cant find an answer, any suggestions?

I've managed to revert back using metacity --replace untill this gets solved so thats a good thing...

---

### Post by Zeedok on 2009-04-08
Have you tried [CompizFusionicon]("http://wiki.compiz-fusion.org/CompizFusionIcon")?

This allows you to select the window manager and window decorator you want to use.  There is some more information [here]("http://tombuntu.com/index.php/2008/03/25/toggle-compiz-with-fusion-icon-in-ubuntu-804/").

Incidentally, is [Emerald]("http://wiki.compiz-fusion.org/Decorators/Emerald") working?

Good luck.

---

### Post by DracoJesi on 2009-04-08
thanks for the link but how will that help me when compiz is on?

Emerald installed but it doesn't seem to be doing anything, theres no themes in there...

thanks

---

### Post by Therion on 2009-04-08
> **DracoJesi said:**
> thanks for the link but how will that help me when compiz is on?

Emerald installed but it doesn't seem to be doing anything, theres no themes in there...

thanks
Try installing the Fusion Icon and then switch between Compiz and Metacity a time or two.  For whatever reason this has solved this (common) issue for some people permanently.  It's like a kick-start or something.

If that's a no-go we'll look at kicking Emerald in the Family Jewel's, because I suspect it's the real culprit here.  Typically, if you have both Compiz AND Emerald installed, Compiz is going to WANT to use Emerald to decorate your windows...  But you have no themes for Emerald to use so... POOF!  Away go your window decorations altogether.

---

### Post by Jakey_TheSnake on 2009-04-08
Try:

```
gnome-wm --replace
``` 

In the terminal.

edit: unless he's specified wanting to use emerald as the window manager somewhere surely Ubuntu should be using the default gnome-wm? 

All the same, if gnome-wm doesn't work, download an .emerald theme and install it via Emerald Theme Manager, then try:

```
emerald --replace
```

If that works, add it to your start up scripts: System > Preferences > Sessions > Add, in the command box type the code above.

---

### Post by kimberlite on 2009-06-11
Thanks, switching to Metacity and back to Compiz helped me using Fusion Icon (right-click).

---

### Post by 4Orbs on 2009-06-11
In my case the disappearing window frame happened because I had changed my screen resolution before activating the nVidia driver for my graphics card. Setting the resolution (as root) and refresh rate back to Auto made the window borders reappear. I now adjust resolution by editing the xorg.conf and adding a display subsection defining the preferred resolutions.

---

### Post by Guanglin.Du on 2010-02-18
I had this problem with Ubuntu 9.10. From System -> Preferences -> Appearance -> Visual Effects, I switched the default option from **Normal** to **None**, the min, max and exit buttons resumed on the windows, including the **Terminal** window.

---

### Post by $p00ky on 2010-05-17
I actually like the "bug" when the top window bar with the title, minimize/maximize/close buttons disappears.

Thanks to this bug, I actually noticed this bar is useless if we have other ways to maximize/unmaximize/minimize the windows.
I tried the "Maximumizer" plugin in compiz, but it just doesn't do anything (or I can't make it do anything).

Do you know any simple way, using or not compiz to maximize/unmaximize/minimize the windows?

---

