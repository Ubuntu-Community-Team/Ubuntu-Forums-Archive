---
title: "partition help"
date: 2011-01-06
forum: New to Ubuntu
---

### Post by rs87424 on 2011-01-06
I recently had to manually set up partitions and dual boot between windows vista and ubuntu 10.10. I encountered a problem beforehand because for some reason the boot screen said that my internal hard drive wasn't being recognized or wasn't mounting.

So I went ahead and reinstalled ubuntu 10.10 using a cd. When I came to the screen that asks how you would like your partitions to be set up I put one as root but I forgot to use another as home. Long story short I needed to reinstall again, this time making sure I set up a / partition and /home partition.

However, I seem to still have trouble with the data because the original /home partition that I had stored away from the beginning before I even reinstalled is not automatically mounting. I also have three ubuntu grubs(?) when I should only have one. 

I am really confused about what I need to do to make my system work properly. Any help would be much appreciated!

extra info:

```

Found linux image: /boot/vmlinuz-2.6.35-24-generic
Found initrd image: /boot/initrd.img-2.6.35-24-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
Found Windows Recovery Environment (loader) on /dev/sda2
Found Ubuntu 10.10 (10.10) on /dev/sda5
done

```

I seem to be using the sda7 partition now, and there are two of those.

---

### Post by Idefix82 on 2011-01-06
If you want the old /home partition to be used in the new installation, you have to tell Ubuntu during installation to mount that particular partition as /home, rather than to create a new /home partition. But beware: do **not** tick the check box "format" for the reused /home partition, otherwise you will lose the old data.

All the remaining non-windows partitions should be deleted and allocated to / (root), then grub shouldn't give you two Ubuntu installations.

---

### Post by rs87424 on 2011-01-06
I tried to do that before but for some reason the old home partition needs to be mounted as a 20GB file system after I log in. Also, how can I delete all other non-windows partitions? I should reinstall again?

---

### Post by Girya on 2011-01-06
> **rs87424 said:**
> I tried to do that before but for some reason the old home partition needs to be mounted as a 20GB file system after I log in. Also, how can I delete all other non-windows partitions? I should reinstall again?

if I understand right you have / on one partition, and two seperate partitions one with old home and one with new home that mounts on boot? 

why not mount old home and copy data files to new home. then get rid of the old home partition?

---

### Post by rs87424 on 2011-01-06
Well that seems to be a great idea except I have no experience with doing that sort of thing and I am just afraid to really make a mistake.

---

### Post by Bucky Ball on 2011-01-06
> **Girya said:**
> if I understand right you have / on one partition, and two seperate partitions one with old home and one with new home that mounts on boot? 

why not mount old home and copy data files to new home. then get rid of the old home partition?

Good idea. Girya, are you *really* using 7.04??? :-k

---

### Post by rs87424 on 2011-01-06
alright I will try that

---

### Post by Bucky Ball on 2011-01-06
. Duplicate post of my next for some reason! Move on, nothing to see here. ;)

---

### Post by Bucky Ball on 2011-01-06
> **rs87424 said:**
> Well that seems to be a great idea except I have no experience with doing that sort of thing and I am just afraid to really make a mistake.

Back up what you don't want to lose first, if you can.

Copy the data over, open System->Admin->Gparted partition editor, unmount the old and new /home, delete the old /home, expand the new /home into the free space that leaves. ;)

If you boot from a LiveCD and do this, none of the partitions should be mounted as you are running off the CD so a bit more straightforward.

---

### Post by rs87424 on 2011-01-06
I wonder... maybe the 20GB filesystem is the old home? If so, could I just clear that and add it to free space? I know there are some settings stored in the 20GB filesystem but I am not sure exactly what. Anyways, sounds good

---

### Post by Bucky Ball on 2011-01-06
Could you perhaps open a terminal (Applications->Accessories->Terminal) and type or paste this in:

```
sudo blkid
```

You will be asked for your password. Post the output back here so we can see exactly what you have there. ;)

---

### Post by rs87424 on 2011-01-06
```

/dev/sda1: LABEL="PQSERVICE" UUID="EAEE-EB49" TYPE="vfat" 
/dev/sda2: LABEL="ACER" UUID="82FA0C29FA0C1BD3" TYPE="ntfs" 
/dev/sda6: UUID="d037e20f-0d7a-48f4-a598-60b2407e6691" TYPE="swap" 
/dev/sda5: UUID="185ebda4-852f-4061-bfd2-4bf1af1c9a19" TYPE="ext3" 
/dev/sda7: UUID="bf73a271-a4ee-4cf6-a076-729e96935b6f" TYPE="ext4" 
/dev/sdb1: LABEL="FreeAgent Drive" UUID="90C85CAFC85C94F6" TYPE="ntfs" 

```
ok here you go

rsedit: I believe the ext4 partition is the 20GB filesystem if I am not mistaken

---

### Post by Bucky Ball on 2011-01-06
Thanks, good. Yes, the EXT4 would probably be the newest /home. So, you have a Ubuntu install on the same drive as Windows? That would be a good way to go. Why not just delete the old install and put Ubuntu there?

Sure you have your reasons. I see absolutely no reason why you would get the error message when you are wanting to shrink the one big partition on the Freeagent drive (sdb1). I would be tempted to ignore BUT please let us know what the Ubuntu install is on sda.

Incidentally, rule of thumb is to put /swap at the end rather than beginning. OS should go as close to first as they can if poss.

So, Windows is in sda2. (NTFS indicates this), I am a bit confused as to what's on sda5 and 7 ... :confused:

---

### Post by rs87424 on 2011-01-06
> **Bucky Ball said:**
> Thanks, good. Yes, the EXT4 would probably be the newest /home. So, you have a Ubuntu install on the same drive as Windows? That would be a good way to go. Why not just delete the old install and put Ubuntu there?

Sure you have your reasons. I see absolutely no reason why you would get the error message when you are wanting to shrink the one big partition on the Freeagent drive (sdb1). I would be tempted to ignore BUT please let us know what the Ubuntu install is on sda.

Incidentally, rule of thumb is to put /swap at the end rather than beginning. OS should go as close to first as they can if poss.

So, Windows is in sda2. (NTFS indicates this), I am a bit confused as to what's on sda5 and 7 ... :confused:
well the free agent drive is an external hard drive that I have plugged in at the moment. sda7 is ubuntu and I am using that right now and sda5 is also ubuntu which I don't use very often... and mistakenly it is still there... but sda5 has what appears to be the old home...I assume

---

### Post by Bucky Ball on 2011-01-07
Copy your personal data from the old /home to the new one; 
Delete sda5 leaving free space;
Expand your existing install into the free space using Gparted on a LiveCD.

Done. You don't have separate /home partitions so your /home folder(s) are actually in the same partition(s) as your Ubuntu install.

You have two Ubuntu installs both using the same /swap. That's fine but get rid of one of the installs, preferably the older one.

---

### Post by rs87424 on 2011-01-07
> **Bucky Ball said:**
> Copy your personal data from the old /home to the new one; 
Delete sda5 leaving free space;
Expand your existing install into the free space using Gparted on a LiveCD.

Done. You don't have separate /home partitions so your /home folder(s) are actually in the same partition(s) as your Ubuntu install.

You have two Ubuntu installs both using the same /swap. That's fine but get rid of one of the installs, preferably the older one.
Thanks, I will get back to you when I have the time to look at it thoroughly

---

### Post by Bucky Ball on 2011-01-07
Just a note. DON'T copy any hidden folders, files or settings over from your old /home. This could cause a major headache (as you will have two sets of settings!). Just your personal stuff. ;)

---

### Post by rs87424 on 2011-01-07
> **Bucky Ball said:**
> Just a note. DON'T copy any hidden folders, files or settings over from your old /home. This could cause a major headache (as you will have two sets of settings!). Just your personal stuff. ;)
Duly noted

---

### Post by Bucky Ball on 2011-01-07
Press ctl+H to see hidden folders and leave them be. ;)

---

### Post by rs87424 on 2011-01-07
> **Bucky Ball said:**
> Press ctl+H to see hidden folders and leave them be. ;)
ok got you... I see the hidden files

---

### Post by rs87424 on 2011-01-08
Hey guys

I decided to do a full fresh install. I had a little help with my friend on the specifics. I want to put down a list of things to help people if they are having trouble with partitions. I am sure someone has already posted a how to but I wanted to show our methods in hopes that it helps a specific user or users.

**_Fresh Install_**

[LIST]
[*]Free up some blank space (depending on the hard drive and if you want to dual boot with windows)
[*]15-20GB / partition in the free space (must be marked as primary)
[*]create a swap (must be 2x the RAM for your computer ex: 2GB RAM so 4GB swap) may be logical
[*]The rest of the space can be /home-may be logical
[*]For a fresh re-install like the one we performed we clicked "format" for everything but the /home partition.
[*]For the reinstall: set /home as the mount point
[/LIST]

We wanted to do this because we realized that the partitions were so disorganized that things just weren't working right. I appreciated the help and I will take note the information in this thread for future reference.

---

### Post by Bucky Ball on 2011-01-08
> **rs87424 said:**
> Hey guys


[LIST]
[*]15-20GB / partition in the free space **(must be marked as primary)**
[/LIST]
The part in bold is wrong. For your purposes making it a primary partition ... why not? But Ubuntu _DOES NOT_ need to exist on a primary partition. It will happily exist in a logical partition inside an extended partition. ;)

Meaning ... if you already have 3 primary partitions on your hard drive, for instance containing Windows stuff, and free space at the end,_*you could create an extended partition the size of the free space and create /, /home, /swap and whatever else you can fit in it.*_ You could put a whole Ubuntu setup inside an extended partition in other words. Primary or Logical. Non-issue.

Also, four primary partitions on a drive is it. You can have no more. *BUT*, you can have three primarys and an extended with up to 99 logical drives inside it. The system sees this as the four partition maximum regardless. 

Also: you can put /swap anywhere but it would generally be put at the end. /, /home. /swap, in that order. Thinking being? You then have your OS on the fastest part of the drive and /swap, which is rarely used, on the slowest. Why clag up a fast part of the drive with a 2-4Gb blob of nothing? This is a rule of thumb computing convention.

> For a fresh re-install like the one we performed we clicked "format" for everything but the /home partition.
For the reinstall: set /home as the mount point. 

These two lines don't make sense. Please explain. For a fresh install why wouldn't you format /home? If you were installing just the OS on / this would be the case.
For reinstall 'Set /home as the mountpoint'??? What mountpoint? I don't get it. For reinstall you would do as you suggest for a fresh install, don't format /home. You missed out the fact that you also don't need to format or change /swap. 

Take note. I would read some of the existing howto's and edit. This is a bit of a dog's breakfast and not easy to understand. ;)

---

### Post by rs87424 on 2011-01-08
> **Bucky Ball said:**
> The part in bold is wrong. For your purposes making it a primary partition ... why not? But Ubuntu _DOES NOT_ need to exist on a primary partition. It will happily exist in a logical partition inside an extended partition. ;)

Meaning ... if you already have 3 primary partitions on your hard drive, for instance containing Windows stuff, and free space at the end,_*you could create an extended partition the size of the free space and create /, /home, /swap and whatever else you can fit in it.*_

Also, four primary partitions on a drive is it. You can have no more. *BUT*, you can have three primarys and an extended with up to 99 logical drives inside it. The system sees this as the four partition maximum regardless. 

Take note. I would read some of the howto's. ;)
Again, thanks for the additional information. I want to make sure I know what I am doing so that the next time I reinstall ubuntu or try to use arc linux sometime in the future I will be confident that I am organizing everything neatly and efficiently. :popcorn:

---

### Post by Bucky Ball on 2011-01-08
Please reread my last post, I have edited it. There are more errors. ;)

---

### Post by rs87424 on 2011-01-08
well I am just going by what was noted from my friend. Its not very clear and all of the facts aren't there but surely it works. 

and what we meant by reinstall is after you have already done a fresh install and something goes wrong for whatever reason. Of course, you seem to have clarified that... Thanks

---

### Post by srs5694 on 2011-01-08
> **Bucky Ball said:**
> Also, four primary partitions on a drive is it. You can have no more. *BUT*, you can have three primarys and an extended with up to 99 logical drives inside it. The system sees this as the four partition maximum regardless.

A minor correction: From a data structures point of view, the number of logical partitions can be about 2 billion. This is because logical partitions are defined in what's called a "linked list" data structure, in which the definition of one logical partition points to another. Each definition consumes one sector of disk space, and the partition itself must consume another one. MBR uses 32-bit sector pointers, for a total of 2^32 = 4.29 billion sectors, so if you were to max out the number of partitions, you'd have half that, or slightly over 2 billion partitions. Of course, this would be ridiculous -- why would anybody want 2 billion 1-sector partitions? That is the theoretical limit, though.

The theoretical limit on most real disks is lower than this, since most disks don't have 4 billion sectors, but it's still pretty huge. As an example, an 80 GB disk has about 160 million sectors, so you could theoretically create about 80 million logical partitions on it.

In practice, the kernel and udev may impose lower limits, but if so, I don't know what they are. I just tried, and I created a disk with 120 partitions (1 primary and 119 logical), and Linux handled it just fine. Linux's fdisk stopped displaying partitions at /dev/sdb60, but GNU Parted displayed them all, and appropriate device nodes were created on my test system. FWIW, I did this on a USB flash drive, and it took several seconds to seek through the linked list when I inserted the disk or used a disk utility like fdisk or GNU Parted. I've seen posts from people who have problems with more than 16 partitions per disk. I suspect this is an issue with udev configuration, but I've not looked into the issue in detail.

---

### Post by Bucky Ball on 2011-01-08
Happily stand corrected and will keep that in mind when I'm going for a thousand partitions on the one drive in five or ten years time. Cheers. ;)

---

