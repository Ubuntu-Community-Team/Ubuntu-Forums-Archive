---
title: "how to delete old versions ?"
date: 2009-12-08
forum: New to Ubuntu
---

### Post by garyed on 2009-12-08
I've got Ubuntu Studio 7.10 standard ext3 & Karmic 9.10 64bit/ext4 on one HD & Windows XP on an second HD. I plan on installing 9.10 32bit/ext3 on the same HD as the other Ubuntu versions & then run some performance tests to decide which version to keep. Is it a simple job to delete the other two versions & enlarge the partition of the version I want to keep so it uses the whole HD? If so how would any of you recommend doing it?

---

### Post by Temposs on 2009-12-08
When you do that next install you mentioned, when it gets to the partition step, choose the Manual Partition setup option, and you will be able to add, resize, and delete whatever partitions you'd like.

---

### Post by garyed on 2009-12-08
I don't really want to delete any partitions until after my new install.
I want to have all three versions working so I can test which one will work best with my hardware for audio production. Afterwards is when I want to delete two out of the three partitions & just have one partition for the whole drive.

---

### Post by Temposs on 2009-12-08
Ah, I understand now.

So, the way to do it is still with the Ubuntu Live CD, but don't do an installation. Just load into the LiveCD Ubuntu desktop and go to System->Administration->Partition Editor. Then, you can similarly do whatever you'd like with your partitions.

Alternatively, you can install the partition editor(also called gparted) on a partition that you know you're not going to mess with. Then you can edit any other partition that you're not currently using.

The important thing is, you **cannot** be using any partitions that you want to mess with. They must be in an unmounted state.

---

### Post by garyed on 2009-12-08
Thanks,
I think I understand.
I guess I'll have to reinstall grub or figure a way to tell it where to find its files since the partition info will be changed especially if I delete a partition that was the last installed version.

---

