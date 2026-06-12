---
title: "DVD burning"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by Sheneron on 2008-12-26
Hi
I am trying to burn a video (avi) file to a dvd that will play on a dvd player.  I used to use nero in windows which worked well and I had no problems.

I downloaded the program DeVeDe, and it seemed like it was going to work.  I picked Video DVD and it created an iso file (which took forever).  Then with that iso file I used Brasero Disc Burning to burn that image to a disc.

I went to play it in the DVD player and it wouldn't work.  If I put it in my computer it would work.  If I put it in my brothers windows computer it wouldn't work.

How can I burn this avi to a disc so that it will work in a tv?

---

### Post by northern lights on 2008-12-26
Use *tovid* to convert source video to readable formats.

If you're running either Hardy or Intrepid, it's available from the repositories:```
sudo apt-get install tovid
```

If you prefer a GUI, use *tovidgui* or *todiscgui*. Alternatively check out bink's GUI from [here]("http://ubuntuforums.org/showthread.php?t=311936").

For command line conversion and further info, check the [tovid manual]("http://tovid.sourceforge.net/manpages/tovid.html").

---

