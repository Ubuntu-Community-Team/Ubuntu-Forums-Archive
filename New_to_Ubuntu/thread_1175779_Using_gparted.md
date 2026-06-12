---
title: "Using gparted"
date: 2009-06-01
forum: New to Ubuntu
---

### Post by mesmith on 2009-06-01
I have a 20gb hard drive.  I wanted to increase the size of my swap partition, so I shrank the main partition by 1gb using gparted off my system rescue cd.  All went well, and I now have about 1gb of unallocated space between my main partition and the swap partition (which is the last partition on the disk.  I thought I could just resize the swap partition to to fill to the left and use the unallocated space.  Can't figure out how to do that, as space preceding and following the swap partition are zero, and I can't seem to change that.  What am I not understanding?

---

### Post by LewRockwell on 2009-06-01
I usually just delete the original swap area and then select the unallocated area(which will include the new part you created by shrinking the other partition) and make it a swap partition again.  hope that helps!

---

### Post by mesmith on 2009-06-01
That seemed to work, but I notice after removing the old swap I had to delete an extended partition in order to free space behind the new swap area before expanding it.  That seemed to work okay.  Now I have two partitions, sda1 and sda3.  I took a look at fstab and it shows the swap area as sda5 (the old number system before deleting the extended partition).  Should I edit fstab and change the swap area to sda3?

---

### Post by ajgreeny on 2009-06-01
I suspect the swap area was mounted and being by the System Rescue CD.  Right click on it in gparted and choose unmount (or swapoff, I can't remember the way it is done at the moment) and see if that helps you move/enlarge it.

EDIT:  Sorry I was called away half way through writing this post and didn't see the last poster's entry.

---

### Post by egalvan on 2009-06-01
Post a screen-shot of gparted.

Let us see the actual partition lay-out.

---

### Post by louieb on 2009-06-01
> **mesmith said:**
>   Should I edit fstab and change the swap area to sda3?
Yes. 
Use 
```
sudo blkid
```
to list the swap partitions UUID. Change /etc/fstab entry for swap to match.

---

### Post by mesmith on 2009-06-02
I edited fstab, and changed the uuid to match that shown by blkid.  Then changed the designation sda5 to sda3.  All looks okay, but when I rerun blkid the old sda5 partition shows up in the output of blkid.  Looks like this:

mike@mike-desktop:~$ sudo blkid
[sudo] password for mike: 
/dev/ramzswap0: TYPE="swap" 
/dev/sda1: UUID="c3dc2164-0e80-4dd7-908e-390eb3733b6f" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="a798242f-7e2-44f8-9c63-720967a73cee" 
/dev/sdb1: UUID="954c5b76-5f4b-4205-aabc-048fc7f4a6a0" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: TYPE="swap" UUID="917260b7-9ce3-4038-ad3e-338bcabc0062" 
mike@mike-desktop:~$ 

Why does sda5 show up?  It shouldn't exist.  Also, what is /dev/ramzswap0?

I have a second hard drive sdb1 which is in the list.

---

### Post by mesmith on 2009-06-02
One more question.  As a result of this exercise, my swap partition is no longer part of an extended partition, but is now a partition in its own right.  My extended partition is gone and now I have a primary linux partition and a separate swap partition.  I assume that is okay, but something weird happened:  my xubuntu boot splash screen lights up, moves the progress bar back and forth, then drops into a text screen titled something like "Reading files necessary to boot...".  Have I broken something?  System does boot and works okay.

---

### Post by mesmith on 2009-06-02
Update:  I found and fixed the problem of dropping out of the boot splash screen.  Googled it and found a fix:

[http://ggts.net/2008/05/13/reading-files-needed-to-boot/](http://ggts.net/2008/05/13/reading-files-needed-to-boot/)

Still can't explain the invalid swap file listed by blkid, but the incorrect swap file appears in blkid.tab.  Shouldn't running blkid update the tab file?  Can the tab file be edited, e.g. just delete the invalid entry?

---

### Post by louieb on 2009-06-02
> **mesmith said:**
>  but when I rerun blkid the old sda5 partition shows up.

Haven't seen a non-existent partition show up before. Can't help but just out curiosity what does 

```
ls -l /dev/disk/by-uuid/
``` show?

---

### Post by mesmith on 2009-06-02
Looks like this:

mike@mike-desktop:~$ ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2009-06-02 08:25 917260b7-9ce3-4038-ad3e-338bcabc0062 -> ../../sda3
lrwxrwxrwx 1 root root 10 2009-06-02 08:25 954c5b76-5f4b-4205-aabc-048fc7f4a6a0 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2009-06-02 08:25 c3dc2164-0e80-4dd7-908e-390eb3733b6f -> ../../sda1
mike@mike-desktop:~$ 

Some googling shows that there are bugs associated with blkid regarding its cache file blkid.tab, with some fixes.  Haven't picked one yet, but safest seems to be a rename of blkid.tab and blkid.old, then a rerun of blkid which rebuilds the cache.  Will post if it works.

---

### Post by mesmith on 2009-06-04
Some Googling reveals that blkid does not automatically purge old partitions, and the garbage removal option is spotty, so just screwed up my courage and edited out the offending bad line in the blkid.tab cache.  Everything seems to work okay.

---

