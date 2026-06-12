---
title: "playing m4a from iTunes."
date: 2009-12-02
forum: New to Ubuntu
---

### Post by jmcgovern on 2009-12-02
I'm feeling like im learning all over again even though I've had Ubuntu as my main OS for over a year.  I've recently been able to rescue music off my iPod and onto my HDD.  However, the iTunes purchased music will not play in any player i've tried (anything i've ripped from my own CD's works perfectly).  According to the  googling i've already done, i need gstreamer0.10-plugins-bad-multiverse installed.   However, Synaptic reports it's already installed.  There has to be something i'm missing.  ubuntu-restricted-extras is also installed, if that makes any difference.

---

### Post by 3rdalbum on 2009-12-02
Ensure that the 'faad' package is installed first.

Secondly, iTunes used to use DRM encryption on its music files. Nothing except iTunes can play the encrypted iTunes files.

I suggest burning them to CD in iTunes and then ripping them again on Linux, into MP3 format.

---

### Post by BandD on 2009-12-02
Chances are the songs have DRM encryption--meaning only iTunes can play them no matter what OS you are using.

If you google you just might be able to find a program that may be able to "fix" the DRM stuff.  I "may" have found a program that does the aforementioned once.

---

