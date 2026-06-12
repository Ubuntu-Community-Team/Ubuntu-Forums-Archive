---
title: "Non destructive read/write test on XFS"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by athena_acq on 2010-05-09
I have an Hard disk which has XFS on it. I want to conduct a non destructive read/write test on it. 
Earlier I have used "e2fsck -c -c" for an ext2 file system. 
Can anyone tell me what is the appropriate tool/command for this test for XFS?

---

### Post by QLee on 2010-05-09
[QUOTE=athena_acq]I have an Hard disk which has XFS on it. I want to conduct a non destructive read/write test on it. 
Earlier I have used "e2fsck -c -c" for an ext2 file system. 
Can anyone tell me what is the appropriate tool/command for this test for XFS?[/QUOTE]

I can only offer a partial answer, since I don't use XFS filesystems, I don't have any experience on how well the tool works so I can't say "appropriate" except in theory. What you probably want is xfs_check. It's part of the xfsprogs package.

---

### Post by athena_acq on 2010-05-09
xfs_check man page indicates that the file system must ideally be read only. So, this indicates that xfs_check performs only read test. 
I am looking for a (non-destructive) write test.

---

### Post by QLee on 2010-05-09
> **athena_acq said:**
> xfs_check man page indicates that the file system must ideally be read only. So, this indicates that xfs_check performs only read test. 
I am looking for a (non-destructive) write test.

Are you sure that it indicates unsuitability, you don't want to run any fscks on mounted partitions, that's always the recommendation as far as I can tell, unmounted or RO for fscks. 

Do you believe that there some is possibility that it could pass the test and still not be useable for whatever purpose you have in mind?

As I mentioned, I have no experience with XFS, perhaps you should just bump this post from time-to-time (once a day) until someone comes along who can give a definitive answer.

---

### Post by quadproc on 2010-05-09
> **athena_acq said:**
> I have an Hard disk which has XFS on it. I want to conduct a non destructive read/write test on it. 

A write test that checks the entire disk is a very difficult thing to do on a running system.  Much better to physically put the drive into another system and to test it there.

The problem with doing a write test is that you have to arrange things so that the system cannot do anything which would alter the data that it puts on the disk during the time that the portion of disk being tested is actually being tested.  Since you cannot predict when disk write events will occur (for example, a cron job might start something, the system might make a log entry, etc.), you have to do a software lock on the drive during this time.  That capability probably does not exist in the linux kernel by default.  And then you have to unlock the drive just after you restore the original data back to the disk.

If you want to write test the unused portions of the disk which are located in partitions then you could write a small program which would fill up the disk with an algorithmic pattern and then read it back and compare the output with the original pattern.  No special tricks are required for this approach, but you might touch some system bugs - it is wise to never completely fill a disk.

If the disk is relatively new then it may have SMART capability.  If so, the disk does a lot of self testing during normal operations and it remembers the results of those tests.  See smartctl and smartmontools.  Note that in Ubuntu 9.10 these tools have been crippled because they could damage SSDs.

quadproc

---

### Post by QLee on 2010-05-10
Good explanation quadproc, however the OP is looking for something for the XFS filesystem that is equivalent or similar to the issuing of e2fsck with -c -c , which is claimed to be a non-destructive R-W scan for bad blocks.


athena_acq, it occurred to me that one of the people who hang out in the Server Platforms sub forum might have a server with a partition or two using XFS filesystem and thus have the experience to answer your question. You might consider marking this thread solved and post your question over there (solved just to indicate closed so you don't have two posts with the same question going at one time).

---

