---
title: "ext 4 install of 9.04"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by loyaleagle on 2009-04-23
i am trying to do a fresh install of 9.04 using the ext4.
I am in the partition manager changing /dev/sda2 to ext 4 (I set that one to root. It is 146 gigs.) No what do I do with /dev/sda1. When I change it to ext 4, it asks me where I want to mount it? I do not know what to do...

Thanks

---

### Post by ugriffin on 2009-04-23
Don't use ext4 yet. It's still unstable and you might lose data.

On the other hand, just format your ubuntu partition as ext4, give it a use "/", which will be your root folder, and check the "format?" box.

---

### Post by utnubuuser on 2009-04-23
What is sda1?  An existing partition?  Is there another OS on this disk?

If you're doing a clean install, that is, no other OSs on the disk. You only need the root / partition and a swap partition approx 1.5x the amount of ram.
You can have a separate /home partition, (which is a really good idea), and seperate /temp /var etc if you like.
But usually, on a clean install, your / root partiton is sda1, then a swap, then /home as sda2, etc.

---

