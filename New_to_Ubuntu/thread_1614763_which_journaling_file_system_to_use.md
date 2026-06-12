---
title: "which journaling file system to use"
date: 2010-11-06
forum: New to Ubuntu
---

### Post by wstay on 2010-11-06
After changing my Computer Processor from Intel Pentium 2.6 to Intel celerom 2.6, my Ubuntu 9.10 cannot start.
I would like to reinstall with Ubuntu 10.04.
Can someone please advise which is a better file system to use: Ext4 or ReiserFS or JFS or XFS journaling file system?

---

### Post by Rubi1200 on 2010-11-06
The default file-system for Ubuntu 10.04 is Ext4; I would probably go with that unless you have a reason not to.

---

### Post by sikander3786 on 2010-11-06
As Rubi mentioned, ext4 is the default and therefore I assume the better one foor Ubuntu.

If you are curious, you can can use Google. Need to do a bit of research yourself :-)

[http://www.google.com.pk/search?q=ext4+vs+reiserfs&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com.pk/search?q=ext4+vs+reiserfs&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

---

### Post by bioterror on 2010-11-06
I would go for the Ext4 as root partition.
And depends what you're going to do.
MurderFS (ReiserFS ;) has it's benefits when we go to like databases. JFS is slow, so that's dropped any how from this. XFS is okay when you deal with huge files (let's say like 1080p movies with mkv as a container).

The ext4 is a golden middle path. 
[http://www.phoronix.com/scan.php?page=article&item=intel_x25e_filesystems&num=2]("http://www.phoronix.com/scan.php?page=article&item=intel_x25e_filesystems&num=2")

---

### Post by HermanAB on 2010-11-06
Howdy,

In my experience, Ext3 is wasteful of disk space (it uses 15% for the journal).  Ext4 is still rather new, so I'd avoid it for another year or two.  ReiserFS is unmaintained.  JFS and XFS are mature and are very efficient with disk usage (They use about 0.5% for the journal) - so these two are my favourites.  However, if you want to encrypt the file system, where a single bit error can frack it all up, Ext3 is more robust thanks to the large journal.

---

### Post by bioterror on 2010-11-06
> **HermanAB said:**
> Howdy,

In my experience, Ext3 is wasteful of disk space (it uses 15% for the journal).  Ext4 is still rather new, so I'd avoid it for another year or two.  ReiserFS is unmaintained.  JFS and XFS are mature and are very efficient with disk usage (They use about 0.5% for the journal) - so these two are my favourites.  However, if you want to encrypt the file system, where a single bit error can frack it all up, Ext3 is more robust thanks to the large journal.

If Ext4 is new, how about BtrFS?

---

