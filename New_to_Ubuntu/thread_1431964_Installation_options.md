---
title: "Installation options"
date: 2010-03-17
forum: New to Ubuntu
---

### Post by SteelCore on 2010-03-17
When manually creating a partition the installer gives the option of either having the partition at the beginning or the end of the volume.  What is the practical benefit of this option? Why would someone choose the partition at the end sectors instead of the beginning.  Thanks.

---

### Post by mikechant on 2010-03-17
I would say that it's unlikely to make any significant difference in performance with modern hardware.

The main difference I can think of is if you don't allocate all the disc space and later want to expand a partition, it's much quicker and less risky to expand a partition by moving the end of the partition than the start - if the start stays fixed and the end moves, none of the data in the partition has to be moved during the operation. If the start of a partition is moved then all the data has to be moved. Also, some partition types don't allow expanding 'backwards' from the start at all (although standard Linux ext2/3/4 filesystems do).

If you place a partition at the end of the disc, you won't have the option to expand it further in that direction.

---

### Post by audiomick on 2010-03-17
> **SteelCore said:**
> Why would someone choose the partition at the end sectors instead of the beginning.  Thanks.
I put my swap at the end to keep it "out of the way" (although I believe this isn't "fastest" place to have it). I did the /  partition first to the size I wanted (15GB) at the start of the drive, then the swap to the size I wanted at the end, then just filled up the rest of the space with the /home partition.

Being able to specify the end of the drive for the swap saved me the trouble of having to work out how big I would have to make the /home to end up with the size I wanted for swap.

---

