---
title: "Wine isn't working"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by mmitt on 2009-01-30
I wanted to download the new trackmania game, and I installed it and everything went fine, but I can't actually access the game. It installed to the C:/Program Files but wine won't let me browse the C: because it "doesn't exist"... Is there any way to play the game now?

---

### Post by ibuclaw on 2009-01-30
Could you show hidden files in your file browser, and locate the folder "**.wine**" in your home directory?

Enter it and ensure that the folder **drive_c** is present.

If it is, then run **winecfg** and click the "Drives" tab.
Ensure that drive C: is exists and is pointing to the right location.

Regards
Iain

---

### Post by mmitt on 2009-01-30
> **tinivole said:**
> Could you show hidden files in your file browser, and locate the folder "**.wine**" in your home directory?

Enter it and ensure that the folder **drive_c** is present.

If it is, then run **winecfg** and click the "Drives" tab.
Ensure that drive C: is exists and is pointing to the right location.

Regards
Iain
Nevermind, its wine is working. TrackMania isn't. It works perfect on vista on the same computer, but on ubuntu + wine, if I try to run it, it say that something is outdated and makes me log back in... Any ideas?

---

### Post by mmitt on 2009-01-30
Ok it says my video card is outdated... Do I need drivers for my AVi card?

---

