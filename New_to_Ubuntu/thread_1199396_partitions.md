---
title: "partitions"
date: 2009-06-28
forum: New to Ubuntu
---

### Post by WriteGirl on 2009-06-28
I had to uninstall and reinstall ubuntu on my laptop, which I'm dual booting with windows xp. I'm now in the process of reinstalling ubuntu and I'd like to increase the size of the windows partition, since it's running really slow. However, I don't want to accidentally delete the windows part. What I am doing is choosing the manually resize option. I clicked on the windows partition and changed the size, and made sure where it said 'use as' I picked the same name as the windows section. Does this make sense? Do I need to format the partition or change the mount point? Or is this complicated enough that I should just deal with having a slow windows, since I use Ubuntu more anyway?

Thanks.

---

### Post by Ocxic on 2009-06-28
That should work, but I would backup your info before doing this just in case something goes wrong. and you might have to increase the NTFS file system from windows or other 3rd party program to take advantage of the extra space.

---

### Post by candtalan on 2009-06-28
> **WriteGirl said:**
> I had to uninstall and reinstall ubuntu on my laptop, which I'm dual booting with windows xp. I'm now in the process of reinstalling ubuntu

I am curious about you saying 'uninstall ubuntu'. There are two ways to install ubuntu, one can be uninstalled very easily, the other can cause 'uninstall' complications. If you installed ubuntu originally inside windows (using the wubi facility) then the uninstall is easy. However, if you originally installed ubuntu and let it make its own conventional partitions, then an ubuntu uninstall will usually mean a removal of partition/s.

> 
 and I'd like to increase the size of the windows partition, since it's running really slow. However, I don't want to accidentally delete the windows part. What I am doing is choosing the manually resize option.

before doing this I would use the ubuntu live cd partition editor to examine and view (not change) what partitions you have at this stage. then after noting that information, then decide actions and proceed.

---

### Post by raymondh on 2009-06-29
I am assuming Windows and Ubuntu have their own respective partitons (not WUBI).

Gparted can resize.  See attached link ... 'specially about NTSF partitions.

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

Sometimes....sometimes....resizing may cause trouble booting in XP, specially if the partition moved.  For this, you will need the original Xp install disc to do a REPAIR.

Back up your data first.  Have your XP install disc ready just in case.

Good luck.

---

### Post by ahndoruuu on 2009-06-29
all i can say is be careful, you are using an extremely convoluted method to achieve an easy end.

---

### Post by yang925 on 2009-06-29
Use gparted live. boot up and delete the Linux Partition it should be EXT2 or 3. then resize NTFS and it should go fine. I have never had any problems doing that though a backup wouldn't hurt. also might have to reinstall the windows MBR. witch can be done by booting live to a windows install cd going to the recovery console and using the fixmbr command. then like magic ubuntu never existed . thought you lose out on and amazing OS.

---

