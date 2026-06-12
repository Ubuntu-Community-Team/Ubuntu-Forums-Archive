---
title: "Add a software RAID to an existing install."
date: 2009-10-18
forum: New to Ubuntu
---

### Post by novus22 on 2009-10-18
How do I add a software RAID to an existing install?
 
I'm just getting started, I'm trying to setup a computer that dual boots to XP Pro. I have Ubuntu 9.04 installed and I'm in the process of configuring it to run Bacula over a home network. It has a Via VT6421 RAID board with 2 500gb hard drives. I would like to configure them as a RAID 1 and store backups on them and boot from another drive that I already have Ubuntu installed on. I can see both drives and mount them right now. 
 
I've found several threads discussing how to install to a software RAID, but how do I add a software RAID to an existing install?

---

### Post by noway2 on 2009-10-18
I have been doing some reading on this subject, and came across your post.  There are a few how-to documents out there that discuss this.  Of particular interest may be the following link:[http://www.tek-tips.com/viewthread.cfm?qid=1318503&page=1](http://www.tek-tips.com/viewthread.cfm?qid=1318503&page=1)


Basically, from what I can tell the procedure goes something like this:
1 - install a second (blank) drive that will be one of the raid drives.
2 - create a raid file system on it and declare it to in a degraded state where the second drive is missing
3 - copy the old drive to the new raid drive
4 - remove the old drive and put in the second new raid drive and configure the partitions so that it mirrors the first raid drive.

It also appears that you will run into a little trouble with GRUB when creating the raid system.  You will need to rerun the grub utility and create the boot loader on both drives.  Again, the how-to documents on this subject describe the procedure.

I personally am wanting to do this very same thing, but I DON'T want to loose the data on my existing drive.  I am planning on using one of the drives that I plan to make a raid to create a copy of my existing drive and then initially work with that one as the non-raid drive.

---

### Post by BikeHelmet on 2009-10-18
So in short, he needs a third new drive to get software RAID working?

I'd look into RSYNC. Set it to backup all the contents of the first drive onto the second sometime at night when it doesn't matter.

There's plenty of articles about it - search google.

[http://www.arsgeek.com/2006/10/18/how-to-back-up-and-restore-your-ubuntu-machine/](http://www.arsgeek.com/2006/10/18/how-to-back-up-and-restore-your-ubuntu-machine/)

---

