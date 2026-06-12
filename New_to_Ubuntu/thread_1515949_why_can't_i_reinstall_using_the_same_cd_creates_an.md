---
title: "why can't i reinstall using the same cd? creates another ubuntu rather than replacing"
date: 2010-06-23
forum: New to Ubuntu
---

### Post by izangeek on 2010-06-23
i've been using ubuntu as my secondary os for close to a month and find  it great.
but lately i find that after familiarization with the terminals, etc...
i could use a fresh installation so as to eliminate those unused items i  might have downloaded.

but when i tried to reinstall ubuntu from the cd, it seems to create  another partition for itself apart from the current os's(ubuntu &  win 7).

is there a way that while reinstalling, it overrides the current ubuntu  and this making it only one instead of two?

thanks... (new to ubuntu) :)

---

### Post by jeffymarts on 2010-06-23
Ok, so the thing is that you have to actually manually delete the Ubuntu partition that's installed. That's not as simple as it sounds though because that's where the MBR (Master Boot Record: Thingie that loads the OS's if you weren't aware.) resides and if that's deleted... well, it's not good. So follow this tutorial ([http://ubuntuforums.org/showthread.php?t=113630](http://ubuntuforums.org/showthread.php?t=113630)) to delete the partition with Ubuntu in it without getting rid of the MBR. After that you can reinstall to your content.

If you have any questions you can PM me.

---

### Post by izangeek on 2010-06-23
ouh thz! been searching for that...
n will do...

---

