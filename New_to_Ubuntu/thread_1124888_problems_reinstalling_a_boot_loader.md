---
title: "problems reinstalling a boot loader"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by vtownterryo on 2009-04-13
windows xp wiped out my boot loader (LILO) when I had to reinstall . I know this sounds like I'm 'tarded but is the a way to just install ANY boot loader
without doing a full install and wiping out my linux partition.
   I'm running on a live cd right now and can't find ANY of my hard drives or partitions any where on the desktop 
   If anyone could help me ;I'd be forever in debt to them ;) Thank you very much

---

### Post by Shazaam on 2009-04-13
Hmm. Open terminal and run this code...
```
sudo fdisk -lu
```
(lower case L)
If you can, post the output here.

---

### Post by Vrekk on 2009-04-13
This think might help.
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by steve101101 on 2009-04-13
if you can't find your partions use a live os called testdisk. i used this to find my partitions after vista messed them up. worked great. also if you need a boot loader back use the super grub disk

---

