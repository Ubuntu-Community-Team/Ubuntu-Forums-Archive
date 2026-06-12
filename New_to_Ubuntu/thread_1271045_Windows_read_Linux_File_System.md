---
title: "Windows read Linux File System?"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by stoppage on 2009-09-20
Hi, is there an app. for 8.04 on dual boot, preferably GUI,  that can read from WindowsXP to my Ubuntu files (need to read both reiserfs and ext3) please?

---

### Post by astrakhan on 2009-09-20
hi 
i've used explore2fs before. it's quite nice and pretty straight forward to use. it's read ext2 and ext3 but there is apparently beta version that can also read reiserfs:

[http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)

why not give that a try

---

### Post by erilidon on 2009-09-20
I've used EXT2 IFS for Vista and EXT2Fsd in XP. They allow you to mount it as a local drive with a letter, not just browse it. However I have had problems with the newest releases of the programs

I've used EXT2IFS 1.10c for Vista

And EXT2Fsd 0.46 in XP

EXT2IFS:
[http://www.fs-driver.org/extendeddl.html](http://www.fs-driver.org/extendeddl.html)

EXT2Fsd:
[http://sourceforge.net/projects/ext2fsd/files/](http://sourceforge.net/projects/ext2fsd/files/)

---

### Post by stoppage on 2009-09-22
I installed EXT2Fsd 0.46, it mounted my Ubuntu /home partition but with unknown file system and only option present was a format. So I wound up with "LTools"..[http://www.it.fht-esslingen.de/~zimmerma/cgi-bin/counter.php?upload=../software/ltools-6.12.zip&page=ltools&logit=1]("http://www.it.fht-esslingen.de/~zimmerma/cgi-bin/counter.php?upload=../software/ltools-6.12.zip&page=ltools&logit=1") but with only read support for reiserfs. An impressive application and obliged for the help

---

### Post by erilidon on 2009-09-22
yeah, that happened to me a lot I just had to keep trying different versions until I got one that worked...

But once I did it works great. I dual boot XP and ubuntu and they share the configuration for thunderbird and firefox.

---

