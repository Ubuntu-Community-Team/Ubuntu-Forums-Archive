---
title: "Hard Drive problems in Ubuntu!"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by Zorlee on 2009-09-14
Hi everyone!
I've just installed Ubuntu on my Asus EEE PC. I have a 160 GB hard-drive installed in my computer. My problem is that Ubuntu somehow acts as if the internal drive was external. I have to mount the drive everytime I log on, and the system drive has no more space what-so-ever. Is there a possiblity to merge these drives?
I can't install any updates or anything, because of this issue. I'm very new to Ubuntu, so I'm sorry if this is a common quesiton, I tried searching, but no luck.

I also have some problems installing some software - do you guys think it's because of this issue, or?

Thank you guys so much!
Sincerely,
Zorlee...

---

### Post by Wim Sturkenboom on 2009-09-14
You probably installed next to existing OS or gave Ubuntu the freedom to partition to its liking (in which case it uses an absolutely stupid minimum).
Reinstall and use the manual partitioner.

I'm not sure if this solves your funny mounting issue as I don't have any idea where it comes from.

---

### Post by LowSky on 2009-09-14
I'm guessing your dual booting with Windows XP?

What you need to do is boot into wndows, defrag the hard drive. then boot the ubuntu live cd, use the partition editor and increase the space of the linux partition by first shrinking the XP partition.

---

