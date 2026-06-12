---
title: "Can't Create a new file system on my SDHC card"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by hanzj on 2009-11-18
Trying to creat Linux Ext2 system on a freshly erased SDHC memory card.

The error message I'm getting when using Palimpsest Disk Utility is

> Error creating file system: helper exited with exit code 1: helper failed with:
mke2fs 1.41.9 (22-Aug-2009)



Please help.

---

### Post by Astrogeek on 2009-11-25
Having the same issue here with a 250G IDE. It doesn't seem to matter what format I select either. EXT4 and EXT3 both give the error.

Any solutions out there yet?

---

### Post by jamesisin on 2009-11-29
Same problem on two 1.5 TB drives.

---

### Post by jamesisin on 2009-11-29
Ok, this is just a bad GUI problem...

Here is how to make this happen:

Locate your drive.  Mine is called 1500 GB Hard Disk.  Below that is an entry called 1500 GB Unrecognized (Unknown or Unused).

Select that Unrecognized entry and create a partition table (under Create Partition Table -- I chose Master Boot Record).  After this is done the sub-entry will be called 1500 GB Free (Unallocated Space).

You may then label and format that unallocated space as you see fit.

---

### Post by dukeofkent on 2010-05-10
I bumped into this thread by googling. I have this 1.5TB seagate hard drive that wont be detected by windows. Ubuntu could read it but it threw up a warning "disk failure is imminent". I backed up all my data so that I could format. i tried formatting using NTFS. 
It gives me an error that reads something like "error creating filesystem:helper exited error calling fsync (2)"
What is the fix? Is my disk salvagable?
Any help would be appreciated.

---

