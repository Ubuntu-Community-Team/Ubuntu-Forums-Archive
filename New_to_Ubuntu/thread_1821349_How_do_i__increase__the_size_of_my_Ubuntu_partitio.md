---
title: "How do i  increase  the size of my Ubuntu partition?"
date: 2011-08-08
forum: New to Ubuntu
---

### Post by jinjin on 2011-08-08
How do i  increase  the size of my Ubuntu partition? i tripled booted with windows and osx86 and i originally allocate 10gb to my ubuntu partition but i want to make it bigger.   i'm using gparted but the ubuntu partition shows up are an extended partition with an ext4 and linux-swap partition nested.  i'm not sure i increase my partition size, but i know that i shouldn't touch the swap partition.   i tried allocated the extended partition with unallocated space but it didn't increase the size of my ubuntu partition.  am i supposed to allocate the free space to the ext4 partition?

---

### Post by Basher101 on 2011-08-08
Step 1: Free space from a Logical partition
Step 2: Change size of the Extended partition
Step 3: Change size of ext4 filesystem

Step 1 could cause trouble if this makes you *move* partitions.

---

### Post by wildmanne39 on 2011-08-08
Hi, here is a guide for resizing partitions.

Please be careful it can be dangerous to your system to resize partitions.
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

---

### Post by Basher101 on 2011-08-08
i should make bookmarks with those threads to post them to newbies...*sighs*

---

### Post by wildmanne39 on 2011-08-08
Hi, I have a file and I keep everything in it to make it easy to find and post.

---

### Post by jinjin on 2011-08-09
lol in the time i was waiting for responses, i already figured out what i needed to do lol...
but thanks for the replies anyway guys. it was just as i suspected, add free space to the extended partition, move the swap partition, then increase ext4 partition

---

### Post by wildmanne39 on 2011-08-09
Hi, glad you got it done, would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

### Post by jinjin on 2011-08-09
> **wildmanne39 said:**
> Hi, glad you got it done, would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.
done

---

