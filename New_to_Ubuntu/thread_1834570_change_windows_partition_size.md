---
title: "change windows partition size?"
date: 2011-08-27
forum: New to Ubuntu
---

### Post by NattyNoobCake on 2011-08-27
im dual booting windows/ubuntu (not wubi) and i want to resize my windows partition. from windows, it only lets me shrink the windows partition by 400 MB. from ubuntu, it says i cannot b/c i have bad sectors. Can i somehow shrink the windows partition/enlarge ubuntu partition?

---

### Post by androssofer on 2011-08-27
> **NattyNoobCake said:**
> im dual booting windows/ubuntu (not wubi) and i want to resize my windows partition. from windows, it only lets me shrink the windows partition by 400 MB. from ubuntu, it says i cannot b/c i have bad sectors. Can i somehow shrink the windows partition/enlarge ubuntu partition?

found this on fixin bad sectors:

[http://ubuntuforums.org/showthread.php?t=81565](http://ubuntuforums.org/showthread.php?t=81565)

then defrag and scan disk on windows. then gparted shud work...

---

### Post by Mark Phelps on 2011-08-28
If you're running Win7, using GParted to shrink your OS partition runs the risk of corrupting it and rendering it unbootable.  If that happens, you won't be able to boot back into Win7 to repair it -- so, you'll lose the use of Win7.

So BEFORE you do that, do yourself a favor and run the Win7 backup feature to create and burn a Win7 Repair CD.  This way, if your Win7 OS does get corrupted, you will be able to boot using this CD and run repairs.

---

### Post by Gone fishing on 2011-08-28
First I'd let windows check the disk - if you do a full check it will mark any bad sectors - I'd be worried by too many bad sectors they are not common on modern hard drives and may indicate th drive is failing.

Resize from inside windows if you can - if not gparted (I use the parted magic CD) [http://partedmagic.com/doku.php](http://partedmagic.com/doku.php) also have a look at [http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)

---

