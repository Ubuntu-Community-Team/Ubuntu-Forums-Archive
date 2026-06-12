---
title: "will data be erased if i re partition?"
date: 2011-01-27
forum: New to Ubuntu
---

### Post by StuSchu on 2011-01-27
I'm (relatively) new to Ubuntu and I use 10.04 on a Dell Inspiron mini.

I currently use dual boot, and the person who originally installed Ubuntu for me left way too much memory on the Windows side. So I'd like to re partition and give more memory to Ubuntu.

Question: If I re partition, will this delete the data I have saved in Windows and Ubuntu?

Thanks.

---

### Post by CharlesA on 2011-01-27
Yes. Be sure to back up any data you want to keep before messing with partitioning.

---

### Post by Mark Phelps on 2011-01-28
> **StuSchu said:**
> I'm (relatively) new to Ubuntu and I use 10.04 on a Dell Inspiron mini.

I currently use dual boot, and the person who originally installed Ubuntu for me left way too much memory on the Windows side. So I'd like to re partition and give more memory to Ubuntu.
I think you mean disk space -- not memory, right?

> Question: If I re partition, will this delete the data I have saved in Windows and Ubuntu?

Depends on HOW you do it.

IF the PC is running Vista or Win7, do NOT use Ubuntu or GParted to shrink its OS partition; instead, use the Windows Disk Management utility to do that.  Afterward, boot back into Windows a couple of times to let it adjust the filesystem info.

Then, boot from an Ubuntu LiveCD and use Partition Editor to expand the Ubuntu partition.  Make sure that NONE of the partitions are mounted, otherwise, it won't let you make any changes.

Also, you didn't mention if Ubuntu is on its own partition. Be sure to confirm that in the Partition Editor; otherwise, you won't be able to change the partition size.

---

