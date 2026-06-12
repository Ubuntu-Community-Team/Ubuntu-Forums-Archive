---
title: "Making a Hot Backup"
date: 2009-06-12
forum: New to Ubuntu
---

### Post by monettsys on 2009-06-12
Hi, I'm in the process of moving over from Windows, and I am running Ubuntu 8.10 (Intrepid). I tried 9.04 but it doesn't seem to like like my ancient PC-AT 84-key keyboard. My question is how do I make a hot backup? I would like to be able to have a complete copy of everything on the backup drive so I can switch over instantly in case anything happens to the main drive, or in case I erase something I shouldn't have.

I have two 500GB Seagate SATA drives, and was able to use GParted to copy everything to the spare drive. It took about 1 1/2 hrs. It boots and runs fine. But now when I try to run GParted again, it will let me select the partition on the main drive, but it won't let me paste it to the spare drive.

Also, I used to be able to see the spare drive after booting into Ubuntu. Now it doesn't show up anymore. Again, both drives work fine and I can boot from either one. But I can't see either drive when it is plugged into the spare SATA slot anymore. GParted sees it but won't let me copy to it.

(I have searched the web and the Ubuntu forums but couldn't find any mention of this particular problem.)

Thanks for your help!

Mike Monett

---

### Post by DGortze380 on 2009-06-12
> **monettsys said:**
> Hi, I'm in the process of moving over from Windows, and I am running Ubuntu 8.10 (Intrepid). I tried 9.04 but it doesn't seem to like like my ancient PC-AT 84-key keyboard. My question is how do I make a hot backup? I would like to be able to have a complete copy of everything on the backup drive so I can switch over instantly in case anything happens to the main drive, or in case I erase something I shouldn't have.

I have two 500GB Seagate SATA drives, and was able to use GParted to copy everything to the spare drive. It took about 1 1/2 hrs. It boots and runs fine. But now when I try to run GParted again, it will let me select the partition on the main drive, but it won't let me paste it to the spare drive.

Also, I used to be able to see the spare drive after booting into Ubuntu. Now it doesn't show up anymore. Again, both drives work fine and I can boot from either one. But I can't see either drive when it is plugged into the spare SATA slot anymore. GParted sees it but won't let me copy to it.

(I have searched the web and the Ubuntu forums but couldn't find any mention of this particular problem.)

Thanks for your help!

Mike Monett

That's not at all what GParted is for...

For backups, look at rsync, very powerful tool.

I don't know what you mean by 'hot backup', but if you're looking for a bit-wise copy of the whole drive, the dd command is what you want.

---

### Post by Hospadar on 2009-06-12
In linux, the way to copy entire drives is to use dd (which is really the backend that gparted uses.  You can have dd overwrite the older backup.

You might also consider, now that you have a complete image, using rsync to just update those files which have changed, this will save you a lot of copy time and hard disk spinning.

Both of these are command line tools which would be easily run from a script or cron job
(if you want to learn more about dd, rsync, or cron, use the googleator)

As to not being able to see the files on the other drive, in linux, drives are identified by a UUID which is a unique identifier for a partition (i.e. only one partition is supposed to have a given uuid) and when you copy a drive or partition completely, it copies the UUID (which is the point of a total drive copy) but the slightly inconvenient downside is that you can't mount 2 drives with the same uuid.

So you can either:
a) just live with it, you can still make direct disk copies, you just need to overwrite the backup drive or clear it before you attempt to copy
b) don't copy the entire partition, make a new partition (or partitions) and use something like rsync to copy the files.  If you have to do a total restoration (or you want to just boot off the backup) you'll need to edit your fstab and possibly re-install grub, neither are particularly rocket science, but can be inconvenient.

---

### Post by iponeverything on 2009-06-12
You could mirror the drives and format them NILFS


[http://www.linux-mag.com/cache/7345/1.html](http://www.linux-mag.com/cache/7345/1.html)

[http://en.wikipedia.org/wiki/NILFS](http://en.wikipedia.org/wiki/NILFS)

---

