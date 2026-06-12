---
title: "Trouble upgrading to 10.04"
date: 2010-06-30
forum: New to Ubuntu
---

### Post by Drjim on 2010-06-30
I've been running 8.04 for several months with not too many problems. I tried upgrading to 10.04 this week. After having my internet connection cut out a few times (problem with my isp, not ubuntu) I finally finished the upgrade download from within 8.04 via the update manager. Unfortunately the install then failed (forgot to write down the error message). I've run update manager a few times since but have not gotten any upgrade options. 

I have 10.04 downloaded and on CD. Can I try upgrading from the CD? How? I looked aro und the help sections of the website but couldn't find anything that applied. 

BTW, I'm running a primary Windows laptop with Ubuntu via Wubi. 

On a similar subject, how buggy is 10.04. 8.04 works, should I wait longer to get more bugs out before trying to upgrade?

Thanks,

Jim

---

### Post by wilee-nilee on 2010-06-30
Wubi is for trying it out it is not for long term use or upgrading. Pull out what you need with the live cd, delete the wubi and do a real dualboot use the W7 disk manager to shrink W7 not anything else.

---

### Post by Drjim on 2010-06-30
Can I shrink win xp as described above even if I've been using win xp for several years on this HD?

---

### Post by wilee-nilee on 2010-07-01
> **Drjim said:**
> Can I shrink win xp as described above even if I've been using win xp for several years on this HD?

First I don't know how much stuff is on XP, or how big the HD is. If you do decide to shrink it though use this defragger with the optimize mode set in preferences first to move everything to the front of the HD.
[http://www.auslogics.com/en/software/disk-defrag/download/](http://www.auslogics.com/en/software/disk-defrag/download/)

Shrink it if needed then reboot it to make sure it runs the chkdsk and is running okay. The defragger will show you the unmovable part in the XP partition so note that it will probably be in about the middle of the HD at the least, so you don't shrink it to far.

You could also just backup whats on the hardy install by using the Lucid cd to get to the Ubuntu folder in XP, and then delete the hardy using the delete option in the Ubuntu folder then just install Lucid as a wubi again, remembering that upgrading and saving lots of stuff to it is not advised. Get a external HD to save stuff.

**No matter what though you should be backed up anyway.**

---

