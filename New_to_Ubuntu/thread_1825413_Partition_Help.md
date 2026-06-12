---
title: "Partition Help"
date: 2011-08-15
forum: New to Ubuntu
---

### Post by n4z1 on 2011-08-15
I have a question regarding partitioning my hard drive for UBuntu. I have the CD for it, and everything works perfectly. What I don't get is this;

1) When it says "Set up a partition" the default size is 310 GB (which is close to my free space, 350 GB). I proceeded to "Okay" and it then took a hell of a lot of time to start, and it was still at 0% after about 20-30 minuets. I tried setting the partition to 20 GB but it came with an error that it was too small. So basically my free space is 350GB right now, and I don't know what to do with the partition space that I have to select. If I choose the default partition space, 310 GB, will it completely remove 310 GB to give to UBuntu, so I only have 40 GB space left on my Windows? What would you recommend?

Thanks for the help guys!

---

### Post by Elfy on 2011-08-15
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

look at the guided resize here [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

Alternatively you can create some partitions before you start the installer and manually choose those.

Whatever you do - make sure you have backups of anything you would not want to lose, I'd make sure I had the disk for windows as well.

---

### Post by Mark Phelps on 2011-08-15
When you say "free space" -- I hope that whay you mean is Unallocated space, NOT space inside an existing partition.

If it's unallocated space, then you're OK; but if it's space inside a partition -- that won't work because you can't install Ubuntu to an existing NTFS partition.  To make space in that situation, use the Win7 Disk Management tool to shrink the Win7 OS partition -- but leave the new space unallocated.  Allow the Ubuntu installer to format that new space.

---

### Post by n4z1 on 2011-08-15
The graphicinstall - is that using Wubi? When I boot my computer to install UBuntu, it shows up nothing like what [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall) shows. Basically what I was asking is I have 350 GB of free space left, without UBuntu. UBuntu wants me to select a partition - the default being 310. If I use 310GB, will it remove that amount of FREE space, and give it to UBuntu, leaving my default system right now, Windows Vista, with 40 GB of free space?

---

