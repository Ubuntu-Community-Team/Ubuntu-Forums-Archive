---
title: "External HDD 1 TB slows down ubuntu"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by Captainflowers91 on 2010-01-03
This is probably really stupid, but I recently purchased an HP 1TB external hard drive. Anyway, whenever I plug it in, my computers speed slows waaaaaaaaay down and the harddrive usage jumps to like 98 to 100% until I unplug it and it also makes Cairo Dock crash the minute its plugged in. Any ideas or has anyone else ever had this problem?

---

### Post by markjensen on 2010-01-03
I don't have any clues on this, but if you open a terminal, and type in the following:
**tail -f /var/log/dmesg**

then once the screen settles down, plug in your drive.  What the kernel sees should be written to the terminal.

Tolerate the maddening slowdown for a bit, then unplug it and post in here what was written to the screen after you plugged in the drive.

It will probably be too technical for me, but someone else here might be able to make sense of it.

---

