---
title: "Embarrasingly noobish question about graphics card"
date: 2011-02-05
forum: New to Ubuntu
---

### Post by frutavana on 2011-02-05
I recently bought a new Intel 2.8 Core I5 with 4 Gb of RAM (onboard graphics), and after some consideration decided to load it with Ubuntu 10.10, as I remember the stellar performace I got from crappy laptop with Hardy a couple years ago.

Alas, I've noticed several problems, the most frustrating one being a rather sluggish performance (with no processes to lay the blame on, according to top). As that particular problem is covered elsewhere in the forums, I'll deal with another thing I've noticed.

I don't seem to be able to enable visual effects (not that I care much about those, but I think I should be able to), which leads me to think my graphic chipset is not properly configured. (The "Additional drivers" thing lists absolutely nothing). Anyway, in order to find out what I need to do, I'd reckon I must know what the device is called, and I haven't been able to do that. I installed this GNOME device manager, which only says "Sandy Bridge Integrated Graphics Controller", which sounds kind of vague.

Anyway, if someone could tell me how to find out at least what's the proper name of this thing that isn't working, I'd very much appreciate it.

---

### Post by DiSTORT3D on 2011-02-05
sandy bridge is the onboard intel HD driver, the intel driver that comes with xorg works good.

---

### Post by frutavana on 2011-02-05
Hey, thanks! I can't say I totally understood your reply, but I did search for "Sandy bridge" in the forums, and THINK I managed to install the Xorg drivers based on [this]("http://ubuntuforums.org/showpost.php?p=10358709&postcount=3") post. However cringeworthy my installing something without knowing what it'll do may seem, everything seems to run much smoother now, although I am still unable to enable effects AND youtube freezes my computer in fullscreen mode. 

So, thanks again. If someone else happens to have an idea about what I may try now, go ahead.

---

### Post by PhilGil on 2011-02-05
The sandy bridge graphics architecture is too new to be fully supported in Ubuntu 10.10 without pulling in a newer kernel and several not fully stable graphics packages: [http://www.phoronix.com/scan.php?page=news_item&px=ODk2OA](http://www.phoronix.com/scan.php?page=news_item&px=ODk2OA) .

This seems pretty typical for Linux releases. My observation is that graphics support can be problematic if your hardware is either very new or very old. 

Unless I had to have desktop effects I'd wait. 3D support will probably be available in Natty, although nothing is certain until release.

---

### Post by frutavana on 2011-02-05
Ah, I see now. Well, I'd reckon I'll have to make do for the time being, then. I gather this particular problem is not Ubuntu-specific, right?

At least things seem much smoother after installing the Xorg driver. No effects or fullscreen Youtube, but still.

Thanks a lot, guys.

---

### Post by PhilGil on 2011-02-05
> **frutavana said:**
> Ah, I see now. Well, I'd reckon I'll have to make do for the time being, then. I gather this particular problem is not Ubuntu-specific, right?
It's not Ubuntu specific; you'd likely have the same problems (or worse) with most current Linux releases.

---

### Post by PhilGil on 2011-02-05
Forgot a couple of things...

Disabling hardware acceleration in Flash may help with your youtbe crashes:
[http://www.macromedia.com/support/documentation/en/flashplayer/help/help01.html](http://www.macromedia.com/support/documentation/en/flashplayer/help/help01.html)

[]("http://www.nvnews.net/vbulletin/showthread.php?p=1997651")

---

### Post by frutavana on 2011-02-05
Thanks! I'll check those up.

---

