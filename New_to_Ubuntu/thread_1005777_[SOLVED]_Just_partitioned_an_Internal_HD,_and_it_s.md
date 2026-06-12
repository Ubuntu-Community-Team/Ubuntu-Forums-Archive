---
title: "[SOLVED] Just partitioned an Internal HD, and it says it has 7GB used on it already."
date: 2008-12-08
forum: New to Ubuntu
---

### Post by Orange_Ribbon on 2008-12-08
Okay,  I had to install Ubuntu on my Slave drive, because there was a problem with my Master Drive.  Since all the information was just backed up (How often does that happen.) I didn't care about it, and used GParted to make a 9GB FAT32 partition to reinstall XP on in case I can't get Fuppes or Ushare working with my xbox360.  and the rest of the drive as a 140 GB Ext3 partition.  

The 140GB partition says it has 7ish GB used when I am in Gnome, XFce when nothing is on the drive.  

Thanks in advance.

---

### Post by perlluver on 2008-12-08
So you have Gnome and XFCE installed on the drive?  Also ext3 uses room for the file system.  For example with Ubuntu installed, on an ext3 partition it uses about 10 GB.  And about 1GB for swap.

---

### Post by Addiction2Code on 2008-12-08
The same thing happened to my 500Gig drive, you never get the full amount of space, its always a little less due to the partition scheme and type. However 7Gig seems like a bit much for a 140Gig HD, you may have bad sectors on your drive. Hope this helps.

---

### Post by jame86 on 2008-12-08
depending on the number of partitions and their type (ntfs for the windows parti) 7gb loss isnt too much for the multipal file tables.

---

### Post by Orange_Ribbon on 2008-12-08
> **perlluver said:**
> So you have Gnome and XFCE installed on the drive?  Also ext3 uses room for the file system.  For example with Ubuntu installed, on an ext3 partition it uses about 10 GB.  And about 1GB for swap.

Well that explains why my 40 GB drive because a 30GB drive,  but the 160 (what the box said) GB drive doesn't have my OS on it.  before I start moving my stuff back, should go with a different file system so I don't lose as much space since it is just for my movies/music?  

Yeah I like XFce better because this is an older machine, and it was easier to set up like windows since everyone likes what they used first.  I use Gnome though because most of the tutorials are written for Gnome.  Learn it there, and make the translation to the different environment.  

Oh well,  thanks for all the answers everyone.

---

### Post by drs305 on 2008-12-08
By default, ubuntu reserves 5% of the partition for system use (journaling, etc). So 7GB on a 150GB drive is just about right. This is in addition to the normal occurence of a hard drive advertising one size but having a smaller usable one.

Although I don't recommend it, you can alter the reserved percentage if you *really* need the space with "tune2fs" and the "-m" switch. You can read about it on the man page ( man tune2fs ).

---

### Post by Orange_Ribbon on 2008-12-08
Ahhh,  okay.  So that is set aside for the operating system.  The space isn't a biggie since you can buy a TB for about 100 to 150 now.  It was more of a curiosity.

---

