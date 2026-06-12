---
title: "Partitioning my Ubuntu drive"
date: 2009-08-11
forum: New to Ubuntu
---

### Post by tesseract1 on 2009-08-11
I have two separate drives.  One for Ubuntu and one for WindowsXP.  I can't seem to resize my Ubuntu partition for a new partition.

I went through Partition Magic in WinXP and it sees the drive as completely full, so it won't resize it.

I booted Ubuntu Jaunty OS from the drive and tried to work on it there with GParted.  It wouldn't let me do a thing.

I booted the Live CD and got a little further.  But it would never complete the process.  I'd always get some error telling me to go to the GParted website for support.  I don't remember the error.

Why is this so difficult?  What else could I be trying?

---

### Post by Aweyer2 on 2009-08-11
There could be a few problems affecting your partitions. One, be sue that the drive you are trying to partition is not mounted. The GParted live disk could be corrupted, try downloading a fresh copy. Also, if you could post a copy of the error code that would help me direct you in the correct direction. Another possible problem could be the actual hard disk is corrupted, although this is unlikely because the disk does boot, right?

---

### Post by nhasian on 2009-08-11
Shouldnt be too difficult.  you cannot resize a volume while its mounted so you must use the liveCD.  you should also run a chkdsk on the volume to make sure there are no issues.  also if you can give us the gparted error message you receive it may help us resolve the problem for you.  

Note: try launching gparted from the terminal instead of the menu so you can see any error messages output.

```
gksu gparted
```

also you can try the latest gparted from this liveCD:

[http://sourceforge.net/projects/gparted/files/gparted-live-testing/0.4.6-1/gparted-live-0.4.6-1.iso/download](http://sourceforge.net/projects/gparted/files/gparted-live-testing/0.4.6-1/gparted-live-0.4.6-1.iso/download)

> **tesseract1 said:**
> I booted Ubuntu Jaunty OS from the drive and tried to work on it there with GParted.  It wouldn't let me do a thing.

I booted the Live CD and got a little further.  But it would never complete the process.  I'd always get some error telling me to go to the GParted website for support.  I don't remember the error.

Why is this so difficult?  What else could I be trying?

---

