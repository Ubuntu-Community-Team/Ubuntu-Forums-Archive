---
title: "Partitioning for dual boot OS...."
date: 2009-01-20
forum: New to Ubuntu
---

### Post by ozark_hillbilly on 2009-01-20
Hello,

After installing MS XP on drive I now want to partition remainder for Linux.

For proper dual OS boot up do I select Beginning or End for
Location of new partition?

Use as:  ext3   ?   
Mount point:    ?

Tks,

ED

---

### Post by Archmage on 2009-01-20
You need at least one partition. It should be named / and I would suggest ext3 as a filesystem.

Furthermore a swap-partition is highly suggested. (size memory x 1.5)

A medium suggestion would be a seperate /home partition and I would also suggest ext3, because it seems to be the most stable, although it might be slow under some cirstiumance.

If you put this on the beginning or end, this dosn't matter that much.

---

### Post by 2hot6ft2 on 2009-01-20
> **Archmage said:**
> You need at least one partition. It should be named / and I would suggest ext3 as a filesystem.

Furthermore a swap-partition is highly suggested. (size memory x 1.5)

A medium suggestion would be a seperate /home partition and I would also suggest ext3, because it seems to be the most stable, although it might be slow under some cirstiumance.

If you put this on the beginning or end, this dosn't matter that much.
I agree. Archmage covered it all. I don't give mine that much swap since I have a lot of RAM and swappiness is set to 0.

---

