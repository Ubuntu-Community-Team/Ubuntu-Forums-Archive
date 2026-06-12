---
title: "Hard drive"
date: 2009-06-30
forum: New to Ubuntu
---

### Post by noldog0550 on 2009-06-30
So my original plan when installing ubuntu was to dual boot with xp.  I did this and it worked, then windows crashed on me and now willl not boot.  I am wondering if there is a way that i can take the partition that windows was using and add it to my linux partiton?  Is this possible?  I want to get rid of windows all together

---

### Post by stalkier on 2009-06-30
> **noldog0550 said:**
> So my original plan when installing ubuntu was to dual boot with xp.  I did this and it worked, then windows crashed on me and now willl not boot.  I am wondering if there is a way that i can take the partition that windows was using and add it to my linux partiton?  Is this possible?  I want to get rid of windows all together

I would just reformat the partition with Windows on it. Make it the same file system as Ubuntu. You can then use it for data storage. (of course, this is just one suggestion - and easiest)

---

### Post by zeroseven0183 on 2009-07-01
It depends on how you installed Ubuntu. If it's inside Windows (using Wubi) then I think you need to reformat the whole partition to Ubuntu. If not, if Windows and Ubuntu are placed on separate partitions, just delete the partition where Windows is like stalkier suggested and edit your grub.

---

### Post by jrox717 on 2009-07-01
If you have a live cd, boot into that use gparted, which is located under System > Administration (it might be called Partition Manager). From there you can delete your windows partition, which will leave you with a lot of free space on the disk. Then you should be able to resize your ubuntu partition to use that free space. However, like the other posters said, you may not need all that space, so you can also either format the empty space (like stalkier said) or just leave it in case you ever want to dual boot with another OS in the future. Good luck!

---

