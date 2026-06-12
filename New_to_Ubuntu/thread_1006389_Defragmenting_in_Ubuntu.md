---
title: "Defragmenting in Ubuntu"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by bradthewanderer on 2008-12-09
Hi all, is there a program or command line for defragging the hard disk? I want to be able to set it up for every week.

Thanks for any help.

---

### Post by Eisenwinter on 2008-12-09
Linux doesn't really need defragmenting, it organizes files in order on the disk.

---

### Post by kgas on 2008-12-09
For Linux installation there is no need for de-fragmentation. Still interested following are the links to see yourself.
[http://polishlinux.org/apps/cli/defragmentation-of-linux-filesystems/](http://polishlinux.org/apps/cli/defragmentation-of-linux-filesystems/)

[http://www.linuxquestions.org/questions/linux-general-1/defrag-on-linux-331862/](http://www.linuxquestions.org/questions/linux-general-1/defrag-on-linux-331862/)

---

### Post by Zzl1xndd on 2008-12-09
As was stated above defragmenting isn't really need in the ext3 file system.

its all explained here: [http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

---

### Post by phidia on 2008-12-09
Also the Ubuntu wiki gives a detailed explanation on the [linux filesystem]("https://help.ubuntu.com/community/LinuxFilesystemsExplained").

---

### Post by Kevbert on 2008-12-09
It's not required. After a number of boots I believe a file system check/repair is made during bootup (fsck), so that is sufficient.

---

### Post by Lusse on 2008-12-09
> **Kevbert said:**
> It's not required. After a number of boots I believe a file system check/repair is made during bootup (fsck), so that is sufficient.
Does the check/repair fix fragmented drives? I don't think so but I may be wrong... (No offense, just wanted to check)

---

### Post by jpmelos on 2008-12-09
Nice thing how Linux file system works! Didn't know why it didn't need to defrag, even though I always had the doubt! :)

---

### Post by brainac0cult on 2008-12-09
in windows, you have to "fix" the hard disc all the time but in linux it never breaks in the first place...

you all to used to windows my friend....

---

### Post by kpkeerthi on 2008-12-09
Here is what you could do to defragment:
1. Backup your partition as a TAR archive
2. Delete and reformat the partition
3. Untar the archive back to the partition

---

### Post by kpkeerthi on 2008-12-09
> **Lusse said:**
> Does the check/repair fix fragmented drives? I don't think so but I may be wrong... (No offense, just wanted to check)

No. It does not defragment, if that is what you are asking.

---

### Post by linux_tech on 2008-12-09
fidefrag-- similar to  pyFragTools 
[http://linux.softpedia.com/get/System/Filesystems/fiDefrag-39829.shtml](http://linux.softpedia.com/get/System/Filesystems/fiDefrag-39829.shtml)

---

### Post by oldsoundguy on 2008-12-09
Linux is NOT a sloppy Windows, de-fragmenting a drive is not needed.  The simple act of re-booting on occasion will keep all your ducks in a row.

Since the system is so much more stable. it will automatically run a pass about once in every 30 or so re-boots.

The only clean up I run .. once a month I run: sudo apt-get auto clean 
to remove fragments left from the updates.

---

### Post by oldos2er on 2008-12-09
> **bradthewanderer said:**
> Hi all, is there a program or command line for defragging the hard disk? I want to be able to set it up for every week.
 

 Which file system are you using?

---

### Post by jrusso2 on 2008-12-09
Yes Linux does fragment just like any other OS especially if you do a lot of media work and add and delete a large number of files.  The previous post is still the best way to defragment it if it really needs it.

---

### Post by Tatty on 2008-12-09
Ext4 will come with a a defragmenter.  It will be a couple of years till that is considered stable though.

---

### Post by hyper_ch on 2008-12-09
if you use less than 95% of your diskspace your system will only only slightly become fragmented. It can't be avoided. However it is not nearly as bad as on windows and generally defragementation is way lower than on windows after 10 times defragging.

If you don't believe me, here's a quote from TLDP
> 
None of these habits should be carried over to Linux and ext2. Linux native file systems do not need defragmentation under normal use and this includes any condition with at least 5% of free space on a disk. There is a defragmentation tool for ext2 called defrag, but users are cautioned against casual use. A power outage during such an operation can trash your file system. Since you need to back up your data anyway, simply writing back from your copy will do the job. 
[http://tldp.org/HOWTO/Partition/appendix.html](http://tldp.org/HOWTO/Partition/appendix.html)

---

### Post by Kevbert on 2008-12-09
> **Lusse said:**
> Does the check/repair fix fragmented drives? I don't think so but I may be wrong... (No offense, just wanted to check)

fsck is the linux equivalent of scandisk and defrag. If your drive is ext3 you shouldn't need to manually defrag the hard disk. You should not use fsck on a mounted disk.

---

### Post by Tatty on 2008-12-09
> **Kevbert said:**
> fsck is the linux equivalent of scandisk and defrag. If your drive is ext3 you shouldn't need to manually defrag the hard disk. You should not use fsck on a mounted disk.

[http://en.wikipedia.org/wiki/Fsck](http://en.wikipedia.org/wiki/Fsck)  Fsck will not defragment an ext3 drive.

Ext3 drives can fragment, but it is very difficult to do and the chance of it getting to the stage of decreasing performance noticeably is very small.

There are a few tools available to defrag an ext3 drive, although none of these seem to be popular.

---

### Post by Kevbert on 2008-12-09
> **Tatty said:**
> [http://en.wikipedia.org/wiki/Fsck](http://en.wikipedia.org/wiki/Fsck)  Fsck will not defragment an ext3 drive.

Ext3 drives can fragment, but it is very difficult to do and the chance of it getting to the stage of decreasing performance noticeably is very small.

There are a few tools available to defrag an ext3 drive, although none of these seem to be popular.

Thanks for the link. I stand corrected, I based the information on posts found elsewhere.

---

### Post by hyper_ch on 2008-12-10
In conclusion one can say that ext3 does normally not fragment.

---

