---
title: "Vista partition won't extend after deleting Ubuntu?"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by Noise... on 2009-05-07
I needed to uninstall Ubuntu, and now that I'm back to Vista, I'm having trouble resizing the disk partition back to the full size.

I'm using Vista's partitioner, and it's not letting me extend the partition that Vista is on - the only option is to shrink it, despite there being 150GB of free space just sitting there.

How do I solve this?

---

### Post by fornix on 2009-05-07
> **Noise... said:**
> I needed to uninstall Ubuntu, and now that I'm back to Vista, I'm having trouble resizing the disk partition back to the full size.

I'm using Vista's partitioner, and it's not letting me extend the partition that Vista is on - the only option is to shrink it, despite there being 150GB of free space just sitting there.

How do I solve this?

You can use the ubuntu live CD to boot and use the partition editor (Gparted) for your purposes.

---

### Post by Noise... on 2009-05-07
> **fornix said:**
> You can use the ubuntu live CD to boot and use the partition editor (Gparted) for your purposes.

My disk is an Ubuntu Studio disk - which lacks the live CD feature.

---

### Post by lindsay7 on 2009-05-07
Download and burn the ISO image of Gparted to a cd or dvd and use that.  Just look for their web site. It is free.

---

### Post by Didius Falco on 2009-05-07
Take a look at the partitions again in Windows. Usually when this happens, it's because the empty space is inside an extended partition.

If that is the case, you'll need to resize the extended partition before you resize the other partition. If the extended partition is empty, you could just delete it.

If you can take a screen shot and post it, we can see what is going on more easily.

I hope this helps...

Regards,

Didius

---

### Post by freeman2000 on 2009-05-07
It's been awhile, and I'm not in Vista right now, but I believe that Vista will only work on and extend partitions that are formatted as NTFS.  So I believe you have to go into Administrative Tools and then Disk Management to reformat the old Ubuntu partition to NTFS, then Vista should let you work with it.  This is off ancient memory - the light is dim.  Good luck.

---

