---
title: "Adding space to my ubuntu partition?"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by theair on 2008-12-21
Hi-

I'm a Linux newb running dual-boot between Vista and Ubuntu. My problem is that I've run out of space on the partition I set aside for Ubuntu, and I was wondering if there's a way to expand it? Thanks in advance.

---

### Post by Jengajam2 on 2008-12-21
remember to back up important files before partitioning.
1. get your ubuntu live cd
2. boot it on your computer into live mode
3. go to system>administration>partition editor
4. click on the side of the partition you want space from and make it smaller.
5.then make your ubuntu partition bigger
6.click apply
7 .done
 
EDIT:go to "thread tools" above your post, click it, and click "marked as solved"

---

### Post by theair on 2008-12-21
Does running the cd on my computer in live mode mean putting in the disc I used for installation and running it from in the OS, or going into my bios and booting from CD like I did to install it?

---

### Post by drs305 on 2008-12-21
> **theair said:**
> Does running the cd on my computer in live mode mean putting in the disc I used for installation and running it from in the OS

Yes. For Intrepid, it says "Try Ubuntu without any change to your computer."

---

### Post by theair on 2008-12-21
Thanks a bunch for your help.

I was able to get into the partition editor, but I can't seem to do anything with the unallocated space I set aside in Vista's partition editor. The partition shows up, but there's no option to do anything with it. My only option with the ubuntu partition itself seems to be to shrink. Is my only option to take more space from Vista's partition (even though I've already set some aside) and assign it to ubuntu?

---

### Post by drs305 on 2008-12-21
A picture would be great. If that isn't possible, we can probably figure it out if you will post the results of:
```

sudo fdisk -l

```

You shouldn't have to take any more space from Windows.

If the free space and linux partition are/were both primary partitions, did you remember to highlight the linux partition before trying to select an option from the Partition menu?

If the free space is on the primary partition side and the linux partition is a logical partition (inside the light blue bordered extended partition box), you will first have to increase the size of the extended partition. Once the free space is inside the extended partition you can add it to the linux partition.

Let someone look at the partition table and we'll be able to give you specific instructions.

---

### Post by theair on 2008-12-21
Here's what I got when I ran the code:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x209b4b29

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192       15863   125876224    7  HPFS/NTFS
/dev/sda3           16258       19457    25704000    5  Extended
/dev/sda5           16258       19319    24595483+  83  Linux
/dev/sda6           19320       19457     1108453+  82  Linux swap / Solaris
blake@blake-laptop:~$ 

Let me know if this is enough; I can take a screenshot of the partition editor if I need to. Thanks.

---

