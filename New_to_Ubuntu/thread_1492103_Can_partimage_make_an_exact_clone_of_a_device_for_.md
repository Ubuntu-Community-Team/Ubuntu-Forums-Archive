---
title: "Can partimage make an exact clone of a device for later recovery?"
date: 2010-05-24
forum: New to Ubuntu
---

### Post by frenchn00b on 2010-05-24
Can partimage make an exact clone of a device for later recovery?

I made an image *.000 of my CF disk, with partimage, and restored it, but photorec/testdisk do not find anything. It is weird because they were still on teh disk before I do partimage.

It seems that partimage does NOT close the bits like they are...

best regards

---

### Post by Mark Phelps on 2010-05-24
My experience in personally using Partimage was for backing up and restoring full Ext3 partitions.  Have not tried using it to backup full device (drive).

Also, know that it does NOT work for Ext4 filesystems, and what I read, is that it is NOT going to be updated to do that.

---

### Post by nhasian on 2010-05-24
i put clonezilla on a usb-thumbdrive and boot from it to back up partitions or entire images or hard disks.  Also it *does* work with EXT4 filesystems

---

### Post by srs5694 on 2010-05-24
From the [partimage main page:](http://www.partimage.org/Main_Page)

[quote=http://www.partimage.org/Main_Page]**Partimage will only copy data from the used portions of the  partition.** (This is why it only works for [**supported filesystem**]("http://www.partimage.org/Supported-Filesystems")).  For  speed and efficiency, free blocks are not written to the image file.[/quote]

Partimage *does* do a byte-level copy, but it ignores those bytes  that it believes are not currently in use. Because of this, if your disk is damaged (lost partitions, accidentally deleted files, filesystem corruption, etc.), partimage will *not* reliably back up anything that's not already reliably readable in more conventional ways, and tools like testdisk or photorec will be unlikely to recover anything from the source disk when using the backup disk.

For low-level data recovery using testdisk/photorec or similar tools, you *must* work on a *complete* low-level copy. In Linux, the usual way to create such a copy is with dd, as in:

```

sudo dd if=/dev/sda of=/dev/sdb

```

This command copies all of /dev/sda onto /dev/sdb. (To be reliable, /dev/sdb must be at least as large as /dev/sda.) It copies even unused sectors (or sectors which the filesystems or partition table says are unused), so it can take quite a while to complete -- much longer than partimage would take on a little-used disk. OTOH, the backup should be useful for recovery operations with testdisk/photorec or similar tools.

---

### Post by jerome1232 on 2010-05-24
You can make dd go a bit faster if you toss some options at it.

```
dd if=/dev/sdx of=~/sdx.img bs=1M conv=notrunc
```

Actually if your working with a damaged disk you may want to use ddrescue.Check the man pages and really know what your doing when using these tools.

```
ddrescue /dev/sdx ~/sdx.img
```

---

### Post by frenchn00b on 2010-05-24
Thank you very very much guys for so much talented and experienced replies !!!

I shall have used dd or ddrescue :(

---

