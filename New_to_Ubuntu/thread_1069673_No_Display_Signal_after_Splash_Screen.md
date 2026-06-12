---
title: "No Display Signal after Splash Screen"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by EKLittleTree on 2009-02-14
I just intalled Ubuntu on my computer about last week.  Everything was going fine until I activated the "ati/amd proprietary FGLRX graphics driver."  I have an old crappy graphics card and so the nice effects that the drivers enabled were somewhat choppy.  Anyway, I decided to deactivate the drivers and after I restarted the computer, the splash screen comes up, but then the display signal turns off.  I can hear the login chime, but no visuals.

Any help would be appreciated.

---

### Post by EKLittleTree on 2009-02-14
Well, I think I fixed it.  I went into xorg.conf and changed the driver to "vesa".  However, now, the resolution is 800x600 and my screen is about twice as big, and I have no idea how to make the resolution bigger.

---

