---
title: "confused on how much Mib for partitions"
date: 2009-12-17
forum: New to Ubuntu
---

### Post by manny43 on 2009-12-17
Hello friends

How much MiB for logical partition?
How much MiB for Primary partition?
How much MiB for Extended partitio?
I have 107GB of unallocated space and would like to partition space to install second linux os.I am using GParted.Thanks

---

### Post by k3lt01 on 2009-12-17
> **manny43 said:**
> Hello friends

How much MiB for logical partition?
How much MiB for Primary partition?
How much MiB for Extended partitio?
I have 107GB of unallocated space and would like to partition space to install second linux os.I am using GParted.Thanks1st question is what else do you have on the hdd already? Once we know that the answers you get will be better.

Generally for Ubuntu I do 10 gb for /, 2 gb for SWAP, and the rest for /home. As far as logical etc go I just use the first option presented in the partition manager and it always works.

---

### Post by mvalviar on 2009-12-17
> **k3lt01 said:**
> 
Generally for Ubuntu I do 10 gb for /, 2 gb for SWAP, and the rest for /home. As far as logical etc go I just use the first option presented in the partition manager and it always works.

Exactly the same partitions as mine. I think I got it from psychocat's guide. :)

---

### Post by atomizer on 2009-12-17
You can only have 4 primary partitions.
If you need more, you will have to create one of them as an extended partition, where you put your secondary partitions (so an extended partition is a partition wich contains partitions)

see [the wiki ]("http://en.wikipedia.org/wiki/Disk_partitioning")for more info

---

### Post by plusnplus on 2009-12-17
sorry to ask in this thread.
how about minimum size for / partition?

---

### Post by atomizer on 2009-12-17
Size of / partition depends on how much you are going to install.
I always use 20Gb for my /, but you can do with 10Gb

---

### Post by k3lt01 on 2009-12-17
> **plusnplus said:**
> sorry to ask in this thread.
how about minimum size for / partition?Read my post above, it answer that question before you even asked it :lolflag:

---

### Post by Paqman on 2009-12-17
> **plusnplus said:**
> sorry to ask in this thread.
how about minimum size for / partition?

Absolute minimum for the standard desktop I would say about 6GB, but 10GB would be better. If you're going to be doing anything that creates huge temp files (like authoring DVDs) then you might want to push that out to 15-20GB.

---

### Post by audiomick on 2009-12-17
> **plusnplus said:**
> sorry to ask in this thread.
how about minimum size for / partition?

On a recent fresh install of 9.10, I noticed that / had about 2.7 GB in it. On that computer, I had to re-size because the / had got up to 4.8GB in a 5 GB partition.
My machine, with Ubuntu Studio and a number of extra programs, has been updated 3 times with the updater and is up to almost 6GB in /.

Both machines are set up with a separate /home, swap, and everything else in the / partition.

Between 10 - 15 GB should be good for a few years.

---

### Post by manny43 on 2009-12-18
Thanks

---

