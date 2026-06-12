---
title: "Video freezes during high CPU usage"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by abhiroopb on 2009-05-25
So, I am downloading some files in Firefox. I can see in conky that my cpu usage is constantly quite higher than normal.

While running a video under these conditions the video (whether it is in vlc or smplayer) freezes over and over again. It will freeze for 3s, then restart, and then some time later freeze again and restart. The audio continues but the video freezes. 

This is very annoying. I assume this is happening because of the high CPU cycles. But downloading in Firefox is something I am constantly doing, and a number of other things that take up CPU cycles.

Are there any settings to change to ensure that this does not happen?

---

### Post by Keithhed on 2009-05-25
I encountered the same problem.  Sadly I couldn't fix it, I downgraded to 8.04 for now.  It seems to happen with less frequency now.  But, I don't feel any better because I haven't found a solution either.  (when my video freezes, it doesn't unfreeze)

---

### Post by abhiroopb on 2009-05-25
seems it might be related to "downthemall", I am trying standard download.

---

### Post by Keithhed on 2009-05-25
I use Deluge for downloads, and this problem only happens while downloading.  So, it could be Deluge? Too much download? It doesn't happen without pushing the system.  Running Deluge, watching a video and web browsing usually does it.  Sometimes I have to run a VM also to push it over the edge. Most threads with this subject lead to Intel drivers but that doesn't apply to me. Sorry I'm not more helpful, just sharing my experience with the issue.

---

### Post by lovinglinux on 2009-05-25
> **Keithhed said:**
> I use Deluge for downloads, and this problem only happens while downloading.  So, it could be Deluge? Too much download? It doesn't happen without pushing the system.  Running Deluge, watching a video and web browsing usually does it.  Sometimes I have to run a VM also to push it over the edge. Most threads with this subject lead to Intel drivers but that doesn't apply to me. Sorry I'm not more helpful, just sharing my experience with the issue.

I'm not sure if it is deluge, but from time to time there is some activity that makes the CPU usage spike and video freezes for less than a second. Is not very frequent tho.

I have nVidia.

---

### Post by abhiroopb on 2009-05-25
I turned of DownThemAll! and there is now no problem :). It may have also been the fact that Firefox was running for a long time.

---

### Post by Noah_Kapiolani on 2009-05-25
Glad you found the culprit!  Downthemall ?

I was going to suggest opening the terminal and typing:

top


It will tell you which app is using how much % CPU time

For example, 

Xorg is using 11%

Firefox is using 5%

etc

---

### Post by abhiroopb on 2009-05-25
I always knew it was firefox related, I had top running. but couldn't figure out why it was using so much CPU!

---

