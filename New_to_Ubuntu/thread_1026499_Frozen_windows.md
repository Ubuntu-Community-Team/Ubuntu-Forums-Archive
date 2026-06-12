---
title: "Frozen windows"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by mkvnmtr on 2008-12-31
I just had the strangest thing happen and wonder if anyone can shed some light on it. I had Firefox open with a few tabs. I also had Epipany browser open with Evolution. I had some torrents going.  This is normal and have never had a problem in months of running 8.04. Suddenly I could not move my Evolution window. I went to use the force quit and could not click on the icon.My cpu usage at the time was about 30%. I could close windows and exit programs. I closed the torrents first. I use KTorrents. I closed Firefox and then I could move my windows. I have since opened Firefox and things are normal. I guess my question is is this just a glich that can happen sometimes or is it something I should seek to deal with.

---

### Post by flanagan on 2008-12-31
I had a similar problem with a combination of Firefox 3.0.5 (and 3.0.4) with Adobe's flash player version 10.0 r12. Apps would freeze, windows controls ceased to work, and, if I could kill Firefox at all, the symptoms would go away. Most of the time I had to Ctl-Alt-Backspace to reload.

The issue finally went away after Adobe came out with release 15. I installed using the .deb for Ubuntu 8.04+ available at [http://get.adobe.com/flashplayer/?promoid=BUIGP](http://get.adobe.com/flashplayer/?promoid=BUIGP).

Your problem may be different, but this might be worth looking into. I chalked it up to Adobe developers not testing properly with Firefox and Mozilla developers not testing properly with Adobe Flash Player. The two products have had a flurry of releases lately and they pretty clearly don't work together very well (if at all). (The development teams that is.)

---

