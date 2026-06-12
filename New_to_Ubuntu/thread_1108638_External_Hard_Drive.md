---
title: "External Hard Drive"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by fknyeah on 2009-03-27
I want to reformat my hard drive.  Really I just can't get it to work well with my system and want to start over.  I've tried using the partition editor, but there is some kind of error.  Please help.  I just want a hard drive that works.

---

### Post by Locutus_of_Borg on 2009-03-27
```

sudo -i
umount -a
fdisk /dev/sdb
{create partitions}
mke2fs -j /dev/sdb1

```

this is assuming the external hard drive is the only other drive connected and is assigned /dev/sdb

you can verify this by plugging in the drive and entering, as root "fdisk -l" without the quotes, and looking at the output for the external drive

let me know i you need help in creating the partitions

---

### Post by Paqman on 2009-03-27
> **fknyeah said:**
> I've tried using the partition editor, but there is some kind of error.

It'd be extremely helpful if you could post what the error was.

---

### Post by fknyeah on 2009-03-27
> **Locutus_of_Borg said:**
> 

you can verify this by plugging in the drive and entering, as root "fdisk -l" without the quotes, and looking at the output for the external drive

let me know i you need help in creating the partitions


/dev/sdb1               1       60801   488384001    7  HPFS/NTFS

I dont care so much if there are partitions.  I just want to be able to use the drive.  It acts as if its read only no matter what I do.  Sometimes it won't mount.  It wont let me put anything on it as if I don't have permission to.

---

### Post by fknyeah on 2009-03-27
when I open the partition editor, the ext HDD has a little picture of keys next to it.  If that helps at all.

---

### Post by Locutus_of_Borg on 2009-03-27
> **fknyeah said:**
> /dev/sdb1               1       60801   488384001    7  HPFS/NTFS

I dont care so much if there are partitions.  I just want to be able to use the drive.  It acts as if its read only no matter what I do.  Sometimes it won't mount.  It wont let me put anything on it as if I don't have permission to.
```

sudo -i
mke2fs -j /dev/sdb1
```
will make an ext3 file system on your external hard drive

there should be no permission errors

---

### Post by Paqman on 2009-03-28
> **fknyeah said:**
> when I open the partition editor, the ext HDD has a little picture of keys next to it.  If that helps at all.

That means those partitions are locked. This is because they are "mounted" (ie: in use). Your solution may be as simple as unmounting them.

However, without knowing more about your partitioning setup that may not be so easy. The bombproof solution is to boot into your LiveCD and run the partition editor. When running off the CD none of your partitions will be mounted and you'll be able to reformat them. If you find you're being stopped by the swap being mounted, just right click on it and "swapoff".

---

