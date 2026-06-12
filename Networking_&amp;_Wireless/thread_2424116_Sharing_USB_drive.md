---
title: "Sharing USB drive"
date: 2019-08-03
forum: Networking &amp; Wireless
---

### Post by bobbych on 2019-08-03
i have installed Ubuntu 18, and have a USB drive attached .  I want to share that drive on my home network on Win 10 PCs

I have set the sharing on local network, and can see the drive on my win 10 PC but when i try to open it i get an error saying I do not have permission.  this only happens on a USB drive, if I share a folder on my internal HDD it works fine

what am I doing wrong?

---

### Post by TheFu on 2019-08-03
Which file system does the USB partition have?
Which file system does the internal HDD have?

What are the permissions on each?

How best to share USB storage is an area full of poor choices.  Windows prefers the SMB protocol that Samba provides.  Did you setup a samba server?
Linux prefers native Linux file systems, not NTFS or vfat or exfat, so if the USB partition has the one of those file systems, there will be permissions challenges which have to be addressed, assuming you don't/won't change to ext4 on the USB storage.

---

### Post by Morbius1 on 2019-08-03
Does the usb drive mount to /media/         bobbych/XXX ?

If it does then the issue isn't samba it's Linux permissions. Linux sets /media/bobbych with special permissions that allows only bobbych access to what is under it. So if you shared XXX allowing guest access guest isn't you so access will be denied.

One way to fix this is to edit /etc/samba/smb.conf and right under the "workgroup = WORKGROUP" line add this one:
```
force user = bobbych
```
Then restart smbd:
```
sudo service smbd restart
```

If this usb drive is mounted someplace else we need to see how the share is set up so please post the output of the following commands:
```
testparm -s
```
```
net usershare info --long
```

---

### Post by bobbych on 2019-08-04
Thanks for the responses. I am totally new to ubuntu so please bear with me. The answers above are quite alien to me as a normal Windows user

The USB drive is formatted as WIndows drive so is probably nfts. I assume the internal drive is formatted as per Linux and it shares fine.

If I were to format the external drive within ubuntu would that solve the issue?

---

### Post by bobbych on 2019-08-04
hopefully the issue is resolved thanks to the advice above.

I edited the smb.conf and added my as a forced user, and now i can see my share on on my windows network

thanks for the help

---

### Post by TheFu on 2019-08-04
> **bobbych said:**
> Thanks for the responses. I am totally new to ubuntu so please bear with me. The answers above are quite alien to me as a normal Windows user

The USB drive is formatted as WIndows drive so is probably nfts. I assume the internal drive is formatted as per Linux and it shares fine.

If I were to format the external drive within ubuntu would that solve the issue?

Happy to hear that you got it working. Thanks a bunch for taking the time to let us know that it is solved AND how you got it working.  THAT is very helpful.  Can you do 1 more thing to help the community, please?  Near the top of the this page is a "Thread Tools" button, mark this thread as "SOLVED".

Morbius1's solution is elegant for a  home environment.  I cannot think of any shorter answer.

You asked a few questions above.  The answers aren't THAT important anymore.

"USB drive" could be either a flash drive, which might be formatted with FAT32 or exFAT
or it could be an external USB drive with an SSD or spinning HDD which would most likely have 1 partition that was formatted with NTFS.  Any of these file systems are accessed by Linux using what is known as FUSE drivers, not kernel drivers.  That means that access is a little slower than when native Linux file systems are used.  With flash drives, the speed of the storage is slower than the FUSE file system so much, that it isn't noticed. Doesn't matter.  With an SSD or spinning disk using NTFS, the performance slowdown will be noticeable.  There are some mount options to make them faster, but they will never be as fast as ext3, ext4, zfs, xfs, or one of the other native Linux file systems.

There is also the file and directory permissions problem.  Unix systems have a native permissions model that is extremely important for system security. In a home environment where samba with a "forced user" and Guest allowed setting, that probably doesn't matter much, if at all.  If you use Linux for anything more than what you are doing here, you'll need to learn and understand Unix permissions.  The reason your original attempt at sharing this partition (it wasn't a drive, it was a partition you were trying to share) failed was because of Unix file and directory permissions.  It will come up again and again.  Permissions on all the popular OSes used in the world work this way, so learning it wouldn't be a waste of time. Android, iOS, OSX, all Linux, all Unix use the same permissions models.  Search for a tutorial with "Ubuntu file permissions" and spend about 45 min learning it the next time you see any permissions denied error.

You specifically asked if formatting the drive within Ubuntu would solved it?  No. The location where the drive was automatically mounted has permissions that only allow 1 userid to see it. That wouldn't have changed.  I'm not a fan of letting the OS use it's defaults to automatically mount storage for a number of reasons, including this one.  Don't forget to look for that tutorial if you want to understand more.

Also the question has misconceptions which weren't important under Windows, but are very important for all Linux and Unix systems.
"drive" is different from "partition."  Windows called C: a drive and D: a drive, though they were really partitions inside different HDDs, almost always.
In Linux, 
/dev/sda is the entire internal drive in your system (probably, I'm guessing).
/dev/sda**1** is the 1st partition on the internal drive in your systems (probably, I'm guessing).
/dev/sda**2** is the 2nd partition on the internal drive in your systems (probably, I'm guessing).
See the difference?  With GPT, you can have over 100 partitions on each drive.  Linux will let you format the drive and it will be really bad.  We almost always want to have partitions and be cautious to format a partition.   
Additionally, there are 20-30 popular file systems available in Linux, so you'll have to select/choose which with which to format.  If you don't have a good reason to choose any specific file system, then ext4 is a good, general purpose, file system for SSD and spinning disks.  Linux has some extremely advanced file systems and volume management capabilities which are used by professionals.  You have access to those on your box, if you like, but most normal end-users don't use them.  LVM, ZFS, and BTRFS are some of the more popular advanced storage tools.  If you are planning to have many TBs of storage, it could be useful to learn about ZFS or using LVM+ext4.  Those are thoughts for the future.

BTW, when I say "Linux", I mean any of the the different flavors, not just Ubuntu.  Desktop or server doesn't matter.  Intel or ARM CPU doesn't matter.  When I say "Unix", I mean any of the Unix-like OSes, which includes all the Linux flavors too.

---

