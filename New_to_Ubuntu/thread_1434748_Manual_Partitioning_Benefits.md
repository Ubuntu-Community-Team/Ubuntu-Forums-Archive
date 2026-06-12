---
title: "Manual Partitioning Benefits"
date: 2010-03-20
forum: New to Ubuntu
---

### Post by EmanuelO on 2010-03-20
What are the benefits of dedicating a partition to each directory (/,/boot,/tmp,/usr/var,etc.)? So, let's say I wanted to do this, what type of partition and filesystem would I use for each directory?

Thank you.

---

### Post by twright on 2010-03-20
> **EmanuelO said:**
> What are the benefits of dedicating a partition to each directory (/,/boot,/tmp,/usr/var,etc.)? So, let's say I wanted to do this, what type of partition and filesystem would I use for each directory?

Thank you.

It is only worth it if you want to separate home and the rest of the filesystem. Also, you should generally just use ext4 for everything (it is usually faster).

---

### Post by EmanuelO on 2010-03-20
> **twright said:**
> It is only worth it if you want to separate home and the rest of the filesystem. Also, you should generally just use ext4 for everything (it is usually faster).
So, there is no reason to give each directory its own partition? I was under the impression it would give things a performance boost of some sort.

---

### Post by coldfusion1313 on 2010-03-20
But if you wanted to give your computer a fresh install of Ubuntu you can just install it on the / directory and the /home directory will be left alone.

---

### Post by twright on 2010-03-20
> **EmanuelO said:**
> So, there is no reason to give each directory it's own partition? I was under the impression it would give things a performance boost of some sort.

Most probably it won't make a difference performance wise, the main reason is flexibility.

---

### Post by EmanuelO on 2010-03-20
Alright, thank you. I will just keep things simple then and just make separate /swap and /home directories.

---

### Post by 2hot6ft2 on 2010-03-20
> **EmanuelO said:**
> What are the benefits of dedicating a partition to each directory (/,/boot,/tmp,/usr/var,etc.)? So, let's say I wanted to do this, what type of partition and filesystem would I use for each directory?

Thank you.
None as far as I know. It would sure make for a lot of partitions on your drive. Maybe one for "/" and one for "/home" like was already mentioned.
I still use ext3 for my file system (since I want cross compatibility between 9.10 and my BT4 OS) but ext4 is going to be the future.

---

### Post by ajgreeny on 2010-03-20
I agree with most who have posted here.  Use a separate /home partition, but keep everything else on /.  Also go with ext4 for all partitions.  It is much faster than ext3, in my opinion, seen most obviously on my setup when new packages are being installed; this is much quicker than jaunty was on ext3.

---

### Post by lavinog on 2010-03-20
I have a couple of partitions:
boot
root
home
storage
backups

The main reasons why I do this has more to do with the way things used to be:
Occasionally ubuntu will do a disk check.  a single 500gb partition takes a long time to check, but having smaller partitions I can spread out the disk check across multiple boots...also partitions that don't change often, don't need to get checked as frequently (like the storage partition for music and videos)
Now Ubuntu only waits for checking root and home.  My storage and backup partitions can be checked after login...so this improves the boot time for me.

Another reason is for stability.  When ext4 was first used in ubuntu, there was a critical bug that caused data loss if you manipulate large files such as videos, and archives.  For this reason, I keep my storage, and backup partition as ext3.
Ext4 is not readable in windows, but ext3 is...so keeping my videos and music on an ext3 partition helps also.

I keep a separate boot partition because in the past I used to dual boot different versions of ubuntu, and it was simpler to maintain that way...I also kept it as ext3 so I can modifiy the boot menu from windows if I wanted.

The other advantage of multiple partitions is that it can be easier to move partitions around...shrinking a 50g partition is quicker than shrinking a 500g partition.
The limited space also keeps me on top of keeping files organized and paying attention to junk files.

On the other side of that...the limited space increases the fragmentation.  Once you have less than 10% free, files can become pretty fragmented.

---

### Post by srs5694 on 2010-03-20
For advanced users, there are definite security, flexibility, and even performance benefits to creating multiple partitions, but you've got to know what you're doing to do it right. I wrote [a piece for IBM developerWorks](http://www.ibm.com/developerworks/aix/library/au-unixfilesys/index.html) on the topic a while back, so refer to it for the details -- it's got far more information than I could reasonably provide in a single post. You'll get the single biggest benefit from splitting off /home from root (/), but there are benefits to separating certain other directories, too, particularly if you have specific needs. For instance, if you compile many local programs or otherwise make use of /usr/local, putting it on its own partition can keep the programs and other data there safe when you re-install or upgrade your OS.

I also disagree with a blanket recommendation to use ext4fs. Although ext4fs has its advantages and is a perfectly reasonable filesystem in many cases, I've seen reports that it still has a few reliability issues. Personally, I wouldn't yet use it on truly critical systems; I'd use ext3fs, ReiserFS, or XFS instead. This is likely to change in the not-too-distant future (say, 6 to 12 months), but not yet. Looking a year or two after that, ext4fs is likely to be eclipsed by Btrfs, but Btrfs is still considered experimental, so it's even less suitable for truly critical data than is ext4fs.

---

