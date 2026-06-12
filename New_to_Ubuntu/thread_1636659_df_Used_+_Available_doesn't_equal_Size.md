---
title: "df: Used + Available doesn't equal Size"
date: 2010-12-03
forum: New to Ubuntu
---

### Post by Stephen Morgan on 2010-12-03
This is quite a minor problem of long standing but when I run "df -h" I get this:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             448G  363G   63G  86% /
none                  1.9G  300K  1.9G   1% /dev
none                  2.0G  408K  2.0G   1% /dev/shm
none                  2.0G  104K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock

Now 363 and 63 is 426, not 448. That's quite a lot of missing space. This has been the case since I was using 8.10. Back then it was only about half as much space missing, on a partition about half the size. I assumed this was a normal thing, but I notice other people don't have it. When I had a Windows NTFS partition the two figures for that added up, even when the ext3 partition didn't. Since then I've done a clean install, Ubuntu using the whole hard disk. 

GPartEd lists the size of the partition as 454.62 GiB, used 369.54, available 85.08. Those figures seem to add up. What might be causing this?

---

### Post by plucky on 2010-12-03
> **Stephen Morgan said:**
> This is quite a minor problem of long standing but when I run "df -h" I get this:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             448G  363G   63G  86% /
none                  1.9G  300K  1.9G   1% /dev
none                  2.0G  408K  2.0G   1% /dev/shm
none                  2.0G  104K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock

Now 363 and 63 is 426, not 448. That's quite a lot of missing space. This has been the case since I was using 8.10. Back then it was only about half as much space missing, on a partition about half the size. I assumed this was a normal thing, but I notice other people don't have it. When I had a Windows NTFS partition the two figures for that added up, even when the ext3 partition didn't. Since then I've done a clean install, Ubuntu using the whole hard disk. 

GPartEd lists the size of the partition as 454.62 GiB, used 369.54, available 85.08. Those figures seem to add up. What might be causing this?

(448 x 5)/100= 22.4 is 5% of 448 which is reserved system space.

363 + 63 + 22 = 448

From [Here](http://lxr.linux.no/#linux+v2.6.29/Documentation/filesystems/ext2.txt)

> Reserved Space
 --------------
 
 In ext2, there is a mechanism for reserving a certain number of blocks
 for a particular user (normally the super-user).  This is intended to
 allow for the system to continue functioning even if non-privileged users
 fill up all the space available to them (this is independent of filesystem quotas).
It also keeps the filesystem from filling up entirely which helps combat fragmentation.

Good Luck


Good Luck

---

