---
title: "Firefox flashplayer, no sound problem."
date: 2008-12-12
forum: New to Ubuntu
---

### Post by Yarp on 2008-12-12
I can't get any flash videos to play sound under firefox.  I've googled this till I'm blue.  Either the solution I try jacks up my sound or is so asinine I debate going back to windows.  Does anyone have a working solution for the 64bit version of the Unbuntu 8.10 client?

---

### Post by ajcham on 2008-12-12
I'm not sure of all the details but the 64bit Flash client for Linux is currently an Alpha release, so a number of bugs are to be expected.  It's worth keeping this in mind before messing with your system in any way.

That said, whenever I've had sound problems reloading ALSA seemed to rectify it, so that's worth a shot:
```
sudo alsa force-reload
```

---

### Post by kansasnoob on 2008-12-12
I would post here:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

I've not messed with 64 bit Intrepid, but psyke83 will be able to answer your questions.

---

### Post by 2hot6ft2 on 2008-12-12
> **Yarp said:**
> I can't get any flash videos to play sound under firefox.  I've googled this till I'm blue.  Either the solution I try jacks up my sound or is so asinine I debate going back to windows.  Does anyone have a working solution for the 64bit version of the Unbuntu 8.10 client?
Well it's 2 part. First to install everything you need for multimedia start here [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Then the second part getting Pulse Audio configured properly for any sound issues here [http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

Between the 2 you should have it working great.

---

