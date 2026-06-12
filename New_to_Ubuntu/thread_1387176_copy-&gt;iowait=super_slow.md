---
title: "copy-&gt;iowait=super slow"
date: 2010-01-21
forum: New to Ubuntu
---

### Post by xieu90 on 2010-01-21
hi
I am trying to copy some files to memory card.
when i copy then the iowait will go up and I have to wait so long. are there any way to make it copy faster ?
it is like my computer just idle and doesnt copy at all
what is the cause of this iowait ?
it is so annoying.

---

### Post by 73ckn797 on 2010-02-05
File operations to a USB device, I have found, are slower than between internal drives or partitions.

I back-up my documents to a Windows drive and larger files are even very slow to complete.

I use "grsync" to make it a simple procedure but I sometimes have to walk away and let it run.

---

### Post by llamabr on 2010-02-05
I don't know what iowait is.  but how are you copying?  with like drag and drop?  or on the cli?  And how big is the file?

---

### Post by ibuclaw on 2010-02-05
You can't really *speed up* the actual speed of transaction, but you can make it *appear* to move quicker, at the cost of a little overhead (and possible overall system slowdown).

Memory Cards/SSD devices may actually benefit from a noop IO scheduler, as other schedulers tend to treat the block device as a rotational drive. (I can also note that quite a few users of swear by using deadline over cfq on disk storage devices too).

```
echo noop | sudo tee /sys/block/sdb/queue/scheduler
```
Change accordingly.

Regards
Iain

---

