---
title: "Toshiba U305-S7448 wifi Ubuntu 8.10"
date: 2008-11-10
forum: Networking &amp; Wireless
---

### Post by laltomar on 2008-11-10
If you have a Toshiba Satelite U305-S7448 and are loading Ubuntu 8.10, the wifi will not work at first but the fix is easy.

Install:  linux-backports-modules-intrepid-generic

Once I loaded this, wifi worked.  I did unload the open source driver. However I do not know if that was necessary or not.

Hope this tip helps fellow Satelite U305 owners who still have issues with the Atheros wifi.  At least support is getting easier.

-lawrence

---

### Post by meditatingfrog on 2009-02-21
Hello fellow U305-S7448 laptop user!  I implemented this fix (glad I don't have to use ndiswrapper anymore!).  

I'm curious, do you have these two problems:

* gnome-settings continuously activates the volume control when increasing/decreasing volume with the volume control on the left side of the laptop?

* odd video "artifacting" during boot ups etc, such as horizontal lines on the screen.  

I found this wiki:  [http://www.linlap.com/wiki/Toshiba+Satellite+U300-U305](http://www.linlap.com/wiki/Toshiba+Satellite+U300-U305) which is pretty good.  It does mention something about a video driver update.

Incidentally, I'm working on this project using Linkwad, an addon for Firefox.  I saved a wad titled "Toshiba u305-s7448:  Streamlining on Ubuntu Linux intrepid".  After the two above issues are resolved, I'm not sure what else can be done to the system that would make it better than previous Windows XP installs.  Perhaps a multithreaded browser a la Chrome would increase productivity for me considerably...maybe.

Edit:  Thought I should add contact info:  
<blog> [http://redrhythmicdragon.blogpost.com](http://redrhythmicdragon.blogpost.com).  
<email> kdemarest [at] gmail [dot] com

---

