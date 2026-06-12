---
title: "making enough room for ubuntu"
date: 2009-06-29
forum: New to Ubuntu
---

### Post by Earth farmer on 2009-06-29
Hi Ubuntu folks. I'm most impressed with the ubuntu project and I'm keen to get going with using ubuntu. I may have been too keen and hasty to install it without knowing enough about what I was doing!! It seems I have let it install with an absolute minimum partition that leaves it no memory room to move- I couldn't even install a few meg of updates that popped up when I got online. The computer had (and still has) windows XP, so I guess windows is hogging all the disc space. Can anyone help me fix this problem? As you will have already gathered, my computer skills are pretty limited, so please talk in "ubuntu for dummies" language if you can...Much appreciated

---

### Post by Monotoko on 2009-06-29
Hiya Earth farmer :)

This is a rather simple one to fix, the partitions arnt set in stone once you have made them, you can shift them around, all you need is the ubuntu LiveCD (or any other LiveCD will do the trick :P)

put the LiveCD into the drive, boot into it using the "try without installing option"

Then go to System -> Administration -> Partition Manager

From there, you should be able to shrink your Windows XP partition and make your Ubuntu partition bigger.

If you have anymore questions please just ask :)

---

### Post by Mark Phelps on 2009-06-29
From how you described the lack of room, I'm guessing that you installed Ubuntu using Wubi inside XP.  If that is correct, you can't simply resize the partition because it's really a virtual file space.  You would have to check the Wubi Guide for instructions on resizing.

If you installed into a separate partition (outside XP), then the suggestions on resizing partitions apply.

---

