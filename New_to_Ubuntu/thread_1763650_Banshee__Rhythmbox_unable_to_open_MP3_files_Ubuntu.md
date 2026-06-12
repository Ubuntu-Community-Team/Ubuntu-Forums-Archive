---
title: "Banshee / Rhythmbox unable to open MP3 files Ubuntu 11.04"
date: 2011-05-20
forum: New to Ubuntu
---

### Post by Betaroad on 2011-05-20
I've recently install Ubuntu 11.04 on a spare desktop for my daughter - wanted to play MP3 files but try as I might and cannot get Banshee or Rhythmbox to import the files.

I have downloaded the appropriate libraries (previously I couldn't even see the files) and when opening directly the file the Movie player opens them.

When I try and import in Banshee or RB the files appear but greyed out.

I'm sure I'm missing something obvious but can't find out what. Any suggestions?

---

### Post by Mr. Shannon on 2011-05-20
Open a terminal using **Ctrl+Alt+t** and then type
```
dpgk -l | grep gstreamer0.10
```
and hit enter.  Then copy and past the result on this thread.  This will show us what gstreamer plugins you have.

---

### Post by wildmanne39 on 2011-05-20
> **Betaroad said:**
> I've recently install Ubuntu 11.04 on a spare desktop for my daughter - wanted to play MP3 files but try as I might and cannot get Banshee or Rhythmbox to import the files.

I have downloaded the appropriate libraries (previously I couldn't even see the files) and when opening directly the file the Movie player opens them.

When I try and import in Banshee or RB the files appear but greyed out.

I'm sure I'm missing something obvious but can't find out what. Any suggestions?

Hi, go here and follow the instructions carefully and mp3 will play, plus dvd, flash videos, be able to make dvd and cd, make sure you follow the instructions for the version of ubuntu you are using, and go all the way down the page. [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

