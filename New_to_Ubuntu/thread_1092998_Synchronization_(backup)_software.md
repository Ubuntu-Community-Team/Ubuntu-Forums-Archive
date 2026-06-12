---
title: "Synchronization (backup) software"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by SteelCore on 2009-03-11
Is there any software in Ubuntu that can help synchronize 2 folders, for example one on the desktop and other on a USB flash memory.
Thank you for your help.

---

### Post by Kareeser on 2009-03-11
Learn to use rsync and crontab, it's nice, quick, and lightweight. It even interfaces with ssh if need be! :)

man rsync

man crontab

---

### Post by ad_267 on 2009-03-11
If you're only working on the desktop and just using the USB for backup then rsync is a good idea. 

If you use two desktops like me (one at home and one at uni) and a USB drive for synchronising the two then you might want to try Unison. There's also a graphical version of Unison available.

---

### Post by tea for one on 2009-03-11
There is also another application called Grsync (available via Synaptic) which features a reasonably intuitive GUI.

---

### Post by binbash on 2009-03-11
+1 for Grsync, it s a good frontend to rsync

---

