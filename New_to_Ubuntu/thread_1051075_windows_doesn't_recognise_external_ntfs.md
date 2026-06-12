---
title: "windows doesn't recognise external ntfs"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by jalirious on 2009-01-26
Hi, I have partitioned my 8gb flash into 2 bits using gparted.

Both primary, 1st = fat32, second = ntfs.

The whole point was for windoze to recognise the ntfs partition to be able to move >4gb files, but xp only sees the fat32 partition.

Is there a flag necessary to set for the ntfs partition to be recognised?

Cheers, Ben.

---

### Post by Sjeti on 2009-01-26
You could probably try downloading the ntfs-config tool and running that.  Check the external drives option and that should make it show up.  If it doesn't show up immediately you might need to reboot.

---

### Post by Hospadar on 2009-01-26
what happens when the entire thing is ntfs, or when ntfs is first

---

### Post by Rolcol on 2009-01-26
I've heard that windows can only handle one partition on a flash drive.  See what happens when you switch the partitons and put NTFS in front of FAT32.

---

### Post by mkvnmtr on 2009-01-26
I almost never start my windows os but I have found a number of cross platform apps in the package manager to make writing and reading possible. I think I read that one was needed for Gparted and I think it was something like nfftprogs. Take this with a grain of salt I may be misremembering. I am more interested in cross platform for my mac os. Just thought it might help yoou.

---

### Post by Arylon on 2009-01-26
Why not just use the Windows tools to partition the drive? That way you won't need to guess about what the problem might be.

---

### Post by jalirious on 2009-03-17
Used gparted to convert the flash drive into 1 ntfs partition. Already had ntfsprogs installed, that may matter.

Now recognised by ubuntu & xp, cheers for all your help!

---

