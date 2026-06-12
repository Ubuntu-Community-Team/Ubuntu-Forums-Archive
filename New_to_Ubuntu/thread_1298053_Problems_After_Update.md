---
title: "Problems After Update"
date: 2009-10-22
forum: New to Ubuntu
---

### Post by lordofthedice on 2009-10-22
About an hour ago, I got a notice from my update manager that there were some new updates for my system. If I remember correctly, it was mostly security things, which is important. So, I downloaded and installed the various files. I could be more specific if I could find a place where what was installed is recorded, but so far the update manager just tells me when the last time I updated was.

On to the problems. After the update, I restarted my system when prompted and then left idling for about an hour while I went to class. I doubt this had anything to do with it, but I add it to be thorough. I come back and try to start up World of Warcraft. The launch menu starts, but the program itself will not start, even when I execute the .exe file itself. I'm using Wine to run it and for the past few days it has been working rather well, give or take a few minor glitches. On top of that, the refresh rate for my screen appears to be affected, too. For example, when I scroll in Firefox, the page takes a moment to refresh causing it to move jaggedly rather than the smooth scroll I experienced before the update.

All other programs seem to work satisfactorally it's just these two problems so far. I'm running Ubuntu ver. 9.04.

I appreciate any help. Thanks.

---

### Post by LewRockwell on 2009-10-22
yep, depending on your hardware...

latest round of updates is breaking stuff...

.

---

### Post by lordofthedice on 2009-10-22
I thought that might be the case. Is there a way to fix this?

---

### Post by aroach31291 on 2009-10-22
Seems like a driver issue if games won't launch and you have choppy response on scrolling. Which graphics card are you using?

---

### Post by MarkStarCrashes on 2009-10-22
> **LewRockwell said:**
> yep, depending on your hardware...

latest round of updates is breaking stuff...

.

I have no sound since the updates this morning. Only a static/crackling sound when a sound tries to play.

---

### Post by lordofthedice on 2009-10-22
I'm using a Radeon HD 4670 card. I was thinking this was the problem as well and I've been working on reinstalling the drivers to see if that might fix it. I'll post again if this fixes it.

---

### Post by Dullstar on 2009-10-22
Hmmm, interesting issues.  I was about to pop in and say to do a fresh install, but then I realized that it had nothing to do with upgrading from one version to another.

---

### Post by lordofthedice on 2009-10-22
Reinstalling the driver worked. Everything it running again.

Thanks for the comments and help.

---

### Post by fsando on 2009-10-22
> **lordofthedice said:**
> ...if I could find a place where what was installed is recorded, but so far the update manager just tells me when the last time I updated was.
...

Try in synaptic:

File > History

---

