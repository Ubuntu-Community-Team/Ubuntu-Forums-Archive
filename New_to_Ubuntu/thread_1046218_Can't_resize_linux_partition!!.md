---
title: "Can't resize linux partition!!"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by Alfx on 2009-01-21
When I installed ubuntu, I gave it 40 gig of space.

Now I want to add another 40 gig, but somehow I can't!


-I booted ubuntu 8.10 live CD

-I shaved off 40gig off my windows partition

When I try to resize the linux partition it doesnt allow me to get higher than what it currently is.(40gig)

How do I fix this?

---

### Post by boof1988 on 2009-01-21
> **Alfx said:**
> When I installed ubuntu, I gave it 40 gig of space.

Now I want to add another 40 gig, but somehow I can't!


-I booted ubuntu 8.10 live CD

-I shaved off 40gig off my windows partition

When I try to resize the linux partition it doesnt allow me to get higher than what it currently is.(40gig)

How do I fix this?

Is the partition (to be expanded) a logical partition (inside an extended partition)?  If that is the case, if the extended partition is locked (has a key/lock symbol) then the extended partition had to be unmounted so it can expanded before the logical partition can be resized.

If you're able to post a screen-capture of the gparted window, that may help others help you.  Let us know if you don't know how to get the screen-capture.

---

### Post by Alfx on 2009-01-21
> **boof1988 said:**
> Is the partition (to be expanded) a logical partition (inside an extended partition)?  If that is the case, if the extended partition is locked (has a key/lock symbol) then the extended partition had to be unmounted so it can expanded before the logical partition can be resized.

If you're able to post a screen-capture of the gparted window, that may help others help you.  Let us know if you don't know how to get the screen-capture.

That's a screenshot.

[IMG]http://img179.imageshack.us/img179/5019/screenshotzw1.png[/IMG]

---

### Post by taurus on 2009-01-21
You need to unmount your swap partition, /dev/sda6, first.

From a terminal, run

```
sudo swapoff /dev/sda6
-or-
sudo umount /dev/sda6
```
Now, restart gparted again.

---

### Post by Paqman on 2009-01-21
IIRC , Gparted can swapoff for you. Just right-click and "swapoff".

The reason the swap is being a problem is that the LiveCD looks for (and mounts) any existing swap partitions automatically. Normally this is a Good Thing™, it improves performance. However, you can't modify any partitions that are mounted, and if the swap is within an extended partition then mounting it means you can't make changes to that whole extended partition.

---

### Post by Alfx on 2009-01-21
Thank you, Im able to resize it now.

:)

---

