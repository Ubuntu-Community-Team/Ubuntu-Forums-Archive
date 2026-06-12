---
title: "Full drive + left over space from another drive = LVM?"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by Meph1st0 on 2009-01-20
I think this might be a hard one.  I have two hard drives, they're both 320 GB drives.  Drive one, (I'm assuming would be /dev/sda) has two partitions, a 1 GB swap partition, and then a 40 GB partition for root /.  I would like to add the remaining space of this first hard drive to the entirety of my second hard drive in an LVM configuration.  

So I should have a total of 3 partitions.  Swap, root, and then my LVM which will make up my second 320 GB drive and the left over space from drive 1.  Is this possible?

I installed system-config-lvm (*I think that was the name) and it seems I can only "initialize" an entire drive (drive 2) and I can't do anything with the remaining empty space of my first drive.

Would anyone know how to do this?

---

### Post by Meph1st0 on 2009-04-02
This thread was solved by following [this]("http://ubuntuforums.org/showthread.php?t=584473") how-to.

---

