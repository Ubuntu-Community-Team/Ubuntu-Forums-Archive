---
title: "Hard drive format"
date: 2010-08-01
forum: New to Ubuntu
---

### Post by L2U2K2E on 2010-08-01
Hi. I am running my desktop with Ubuntu (lucid) on one partition and Vista on another. I plan to set up a third, large partition to hold my data. The trouble is I am not sure how to format it. I have been using the Gparted live CD, so my options are fairly broad. I was thinking about ext4, but I do not think windows can read it. I was thinking about just leaving it as NTFS, but I am not sure how well ubuntu will handle that. Which one should I go with or perhaps another option?

---

### Post by Ocxic on 2010-08-01
FAT32 is the safe choice, but does not allow a file size larger than 4GB, so if you ever think you might run into that issue, go with NTFS.

---

### Post by jerenept on 2010-08-01
Linux NTFS support is really good, so I would definitely recommend NTFS.

---

### Post by Paqman on 2010-08-01
> **Ocxic said:**
> FAT32 is the safe choice, but does not allow a file size larger than 4GB, so if you ever think you might run into that issue, go with NTFS.

FAT is also really nasty for fragmentation. NTFS is a much more modern filesystem all round.

---

### Post by L2U2K2E on 2010-08-02
So I shouldn't run into problems if I stick with NTFS? Super   :]

No love for ext4?

---

### Post by Maverick_Meerkat on 2010-08-02
Greetings,

NTFS works perfectly well for my data partition & I am running a five year old machine with Ubuntu 10.04. NTFS allows Windows to access the data files and it makes backup to an external drive very simple.

---

### Post by howefield on 2010-08-02
> **L2U2K2E said:**
> No love for ext4?

You kind of answered the question yourself.

I don't believe that there are any third party utilities that will read ext4 for you from your windows installation.

If this isn't an issue and you will only access it from Ubuntu, nothing wrong with ext4.

If you want to use the partition from both Windows and Ubuntu, NTFS is probably the best choice. For now :)

---

