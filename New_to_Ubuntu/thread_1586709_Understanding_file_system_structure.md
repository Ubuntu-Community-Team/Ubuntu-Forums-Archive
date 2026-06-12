---
title: "Understanding file system structure"
date: 2010-10-02
forum: New to Ubuntu
---

### Post by ericstrom on 2010-10-02
I would like to get a better understanding of how the file system root works. I'm getting a warning message that I only have 1.6 GB left on the "file system root". Here's my set up:

Running Lucid Lynx on sda
sda is an IDE drive; size is 40 GB
sdb is an IDE drive that is 40 GB
sdb is mounted automatically under /media
Running Virtual Box OSE
MS Windows XP is setup to run under Virtual Box on sdb

Disk usage analyzer shows the following:
Total file system capacity is 71.8 GB capacity
Used capacity = 31.9 GB , available = 40 GB
/ = 100 % used; 31.5 GB size
/home = 23.2 GB (73%)
/media = 5 GB (16%)
/usr = 2.2 GB (6.9%)

GParted shows:

/dev/sda = 37.27 GB
/dev/sda1 (ext4) = 35.7 GB, 32.27 used, 3.43 unused boot
/dev/sda2 = 1.57

/dev/sdb = 37.28 GB
/dev/sdb1 (ext4) = 37.28 GB, 775.25 MB used , 36.53 GB unused


So why am I getting this message about "file system root" being almost full when I have about 40 GB free ? What dictates the size of root when I mount a second drive under media ? I have about 22.7 GB in data files in a single dropbox folder under /home/dropbox. I could move them over to sdb but would that change the situation with root being full ? 

So what do I do about this ?

---

### Post by surfer on 2010-10-02
> **ericstrom said:**
> 
/ = 100 % used; 31.5 GB size


**that** is your problem. the system needs space in (especially in [FONT="Courier New"]/var[/FONT]) where it can write to. it can not use your [FONT="Courier New"]/media[/FONT] directory for that.

---

### Post by psusi on 2010-10-02
You are getting the message because your / is 100% full.  You need to free up some space there.

---

### Post by ibuclaw on 2010-10-02
The root filesystem is everything inside '/' that isn't on another partition.

So, having a look at your partition layout:
> 
/ = 100 % used; 31.5 GB size
/home = 23.2 GB (73%)
/media = 5 GB (16%)
/usr = 2.2 GB (6.9%)

We can see you have 4 partitions, and '/' is completely full.

Now, as you have all software data on a separate filesystem (/usr), and a separate home filesystem (/home), that leaves not too many reasons why root is filled up.

Are you perhaps running backup software?

---

### Post by waperboy on 2010-10-02
If you issue the command

  df

You see which partitions are mounted where.

---

### Post by ericstrom on 2010-10-02
df shows the following:

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             36843088  33247796   1723728  96% /
none                   1544168       316   1543852   1% /dev
none                   1548512      2136   1546376   1% /dev/shm
none                   1548512       292   1548220   1% /var/run
none                   1548512         0   1548512   0% /var/lock
none                   1548512         0   1548512   0% /lib/init/rw
/dev/sdb1             38480404    180136  36345564   1% /media/Drive-b

I get that / is 100% full. I'm confused why that's the case when I have about 37GB free under /media on sdb.

OK, so if I move /home/dropbox which is about 23 GB over to sdb under /media will that solve the problem ?

---

### Post by psusi on 2010-10-02
> **ibuclaw said:**
> The root filesystem is everything inside '/' that isn't on another partition.

So, having a look at your partition layout:

We can see you have 4 partitions, and '/' is completely full.

Now, as you have all software data on a separate filesystem (/usr), and a separate home filesystem (/home), that leaves not too many reasons why root is filled up.

Are you perhaps running backup software?

I nearly made the same mistake you did since that listing is similar to the output of df, but if you notice, there is no size shown next to anything other than /, so I think it is just reporting how much space is used by those directories, even though they are not separate mount points.

---

### Post by psusi on 2010-10-02
> **ericstrom said:**
> 
I get that / is 100% full. I'm confused why that's the case when I have about 37GB free under /media on sdb.

Because / and /media/Drive-b are different disks.

> **ericstrom said:**
> OK, so if I move /home/dropbox which is about 23 GB over to sdb under /media will that solve the problem ?

You need to move it to /media/Drive-b/.

---

### Post by srs5694 on 2010-10-02
More broadly speaking: When you've got two physical disks, you've got to find some way to allocate space between them so that you don't run into problems from filling one disk too quickly. There are basically two ways to do this:


[list]
[*]**Careful partition planning** -- Under Linux, partitions are *mounted* at specific directories known as *mount points.* In your case, /media/Drive-b is your second disk's mount point, meaning that it's accessed there. You can plan your layout in other ways, though. For instance, you could mount the second disk as /home, or split it into parts and mount it in multiple locations. To do this, you'd edit /etc/fstab to reflect your desired configuration. (The Ubuntu installer will do this when you use the advanced partitioning options.) In some cases, careful planning of your partitions and mount points can head off problems like what you've encountered. In other cases, moving files around manually after the fact can do the job. This is likely to be the quickest solution in your case, but it might not be the best solution in the long term.
[*]**Device recombinations** -- Linux's RAID and LVM subsystems enable you to recombine multiple devices into a single virtual device, which can then be carved up in any way that's convenient. RAID offers speed and/or reliability benefits, whereas LVM offers speed and/or flexibility benefits. For instance, your two 40 GB disks could be combined into an 80 GB storage space and then split up into a 15 GB part for root (/), a 4 GB part for swap, and a 61 GB part for /home. This 61 GB /home would be impossible using conventional partitioning; the best you could do there would be to use 40 GB for /home and 21 GB for something mounted under /home (or vice-versa).
[/list]


Unfortunately, optimal planning and setup of partitions requires a certain amount of experience, particularly in cases like yours, with two relatively small disks. The good news is that you're gaining that experience right now.

In the short term, your best bet is probably to move some files from /home into /media/Drive-b. This will move the files from your full disk to your nearly empty disk. In the long term, you may want to consider repartitioning, and possibly using a RAID or LVM configuration to increase flexibility. (I'd go for LVM in your position.) Alternatively, you could buy a new and much bigger hard disk, which will give you a lot more wiggle room. Such a disk might be more reliable, too -- a 40 GB disk is likely to be several years old, and could therefore be nearing the end of its useful life.

---

### Post by ericstrom on 2010-10-02
This still doesn't make sense to me. I followed the advice here and moved my dropbox folder (which was under /home) to /media/drive-b. That was about 22 GB. 

Now GParted tells me I have 9.52 used and about 26.2 GB unused on sda. On sdb I have 23.3 GB used and 13.8 GB unused.

So that seems like a reasonable amount of free space on both drives. The confusion is that Disk Usage Analyzer (DUA) is still telling me that root is 100% used. The specifics are :
/ 100% usage , 31.5 GB
/media 88.2% usage , 27.8 GB
/usr 6.9% usage , 2.2 GB

Disk Usage Analyzer also says total file system capacity is 71.8 GB (used 31.9 GB, available 40 GB).

Should I be concerned that DUA is saying root is 100% usage ? It's like root size is set by the size of the boot drive. And it doesn't matter that another drive is mounted. And if that's the case, what's the value of mounting a second drive if root is the only thing that matters and it's size is ONLY dictated by the size of the single boot drive ?

I know I need a bigger drive. I'm just trying to limp along for a few more months when I'll get a new PC with a larger drive. I'm not overly concerned about drive integrity since everything is backed up through DropBox. 

Please explain how root works and if 100% usage is of concern when GParted is showing space on both drives.

---

### Post by The Cog on 2010-10-02
In your case, /dev/sda1 holds everything in the filesystem except for what's in /media/Drive-B. anything you put in /media/Drive-B goes on /dev/sdb1 instead. Stuff you put anywhere other than /media/Drive-B goes on the first disk. You can't use the second disk as an overflow for other folders - they all go on the first disk. It's not so different to having C: and D: in windows. You have problems if the root disk gets full because the OS needs a little space for working files. It won't try and use the second drive because that's only providing storage for /media/Drive-B.

Have you re-scanned the filesystem in disk usage analyser since you made the changes? I think you may be looking at old scan results.

---

### Post by ericstrom on 2010-10-02
I not only rescanned the drive after making the changes, I also did a restart to make sure the scan was correct. 

So do I have a problem and if so, what do I do ? I have a decent amount of free space on both drives after I've made the change and yet root is at 100%.

---

### Post by SeijiSensei on 2010-10-02
> **ericstrom said:**
> I not only rescanned the drive after making the changes, I also did a restart to make sure the scan was correct.

Does "restart" mean you rebooted?  I've sometimes had problems getting the OS to recognize that I deleted things from the root partition when it was at or near 100% usage.  Rebooting forces the OS to mount the root partition afresh which usually cures the problem.

Here's a simple way to see how big each top-level directory is:

```
sudo cd /
sudo du -s *
```
will print back a list of all the directories with their associated sizes.  Pay special attention to /home and /var, which grow over time.  You'll see that /usr commands a lot of space as well, but those files are largely programs and documentation.  On my newly-installed 10.10 system, about 3.6 GB of the root filesystem is in use including /usr and /var.  (I have /home on a separate partition.)

---

### Post by ericstrom on 2010-10-02
Yes, restart means I rebooted. I hit the red shutdown button and then selected restart.

I tried the commands suggested in the last post and here's the output. Still wondering why I am showing the root at 100 % usage


6568	bin
47424	boot
4	cdrom
1200	dev
14712	etc
du: cannot access `home/eric/.gvfs': Permission denied
538380	home
0	initrd.img
0	initrd.img.old
321200	lib
16	lost+found
29140888	media
12	mnt
72724	opt
du: cannot access `proc/2295/task/2295/fd/3': No such file or directory
du: cannot access `proc/2295/task/2295/fdinfo/3': No such file or directory
du: cannot access `proc/2295/fd/3': No such file or directory
du: cannot access `proc/2295/fdinfo/3': No such file or directory
0	proc
292	root
7748	sbin
4	selinux
4	srv
0	sys
56	tmp
2281508	usr
652900	var
0	vmlinuz
0	vmlinuz.old

---

### Post by srs5694 on 2010-10-02
I'm not familiar with Disk Usage Analyzer, so I won't speculate about what it may be doing. Instead, I'll suggest you use df with its -h option (which just converts units to use sensible suffixes), which produces output like this:

```

$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              30G  4.2G   24G  15% /
/dev/sda5             151M   19M  125M  13% /boot
/dev/sdb4              80G  200M   80G   1% /home
/dev/sdb5              12G  6.2G  5.4G  54% /other/shared

```

If this shows reasonable values, you're set.

---

### Post by The Cog on 2010-10-04
I agree entirely. I'm not sure how Disk Usage Analyzer works, and if it disagrees with what df -h says, I would choose to believe df.

This might give more believable figures - it only counts stuff on the / filesystem.
> cd /
sudo du -hx --max-depth=1

---

### Post by waperboy on 2010-10-06
> **ericstrom said:**
> The confusion is that Disk Usage Analyzer (DUA) is still telling me that root is 100% used. The specifics are :
/ 100% usage , 31.5 GB
/media 88.2% usage , 27.8 GB
/usr 6.9% usage , 2.2 GB

Disk Usage Analyzer also says total file system capacity is 71.8 GB (used 31.9 GB, available 40 GB).



Disk Usage analyzer just tells you that / contains 100% of your total data, of which /media is 88.2% and /usr is 6.9%.

Note that this says nothing about the usage of any particular physical disks, just how usage is distributed across the logical directory structure.

---

