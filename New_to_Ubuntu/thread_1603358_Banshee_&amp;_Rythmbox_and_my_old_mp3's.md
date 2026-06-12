---
title: "Banshee &amp; Rythmbox and my old mp3's"
date: 2010-10-22
forum: New to Ubuntu
---

### Post by Stylesmarino on 2010-10-22
I have googled around and have not had a good solution.

I have recently started with Ubuntu due to a failed hdd and a lost windows disk. 
I have music on an external drive.

VLC is installed as I used it on Windoze. 
I installed Banshee cos RhythmBox would only show the one album and its the only one that was not on the EHDD.

Here is the problem. While Banshee will actually list the tracks I have, it will not play them.
They are mp3's. 
They all play from the EHDD and my onboard HDD through VLC (of course) but get a little x next to the track when I try to play in Banshee.  (RhythmBox won't do anything.)

I have installed gstreamer good, bad and ugly.
Any ideas?
I would have thought there are adequat codecs at this stage...
Even a fix for RB would do.

---

### Post by Grenage on 2010-10-22
It may well be that the mp3 codecs aren't installed; they aren't by default due to licensing.  Try installing the restricted extras package:

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Stylesmarino on 2010-10-22
Awesome.

That Worked.

---

