---
title: "dual booting questions"
date: 2010-07-18
forum: New to Ubuntu
---

### Post by pyrofreak99 on 2010-07-18
I dual booted vista with ubuntu  because the family didnt know how to work ubuntu  but beside the point.

Vista crashed and everytime i try to boot into it  it just restarts  and takes me back to the main boot menu.

So  i was wondering if there is anyway just to delete the vista partion with gpartion without touching the ubuntu os

---

### Post by zeroseven0183 on 2010-07-18
Are Vista and Ubuntu on the same partition or are they separate?

If they're separate, you can use Gparted (install it from the Ubuntu Software Center) and format the partition. You will then have to modify some settings like in fstab so you can use the emptied partition.

---

### Post by TechBeastie on 2010-07-18
As long as you didn't use the Wubi installer, your Windows and Ubuntu installations *should* be on separate partitions.  Running gparted should give you a better sense of what's going on, however.  Make sure that one colored block is labeled as having an NTFS filesystem, and another one has a mountpoint of "/"; if that's the case, you should be able to delete the block formatted as NTFS without harming your Ubuntu install.

---

### Post by Mark Phelps on 2010-07-18
> **pyrofreak99 said:**
> I dual booted vista with ubuntu  because the family didnt know how to work ubuntu  but beside the point.

Vista crashed and everytime i try to boot into it  it just restarts  and takes me back to the main boot menu.

Did you do a side-by-side installation in which you let the Ubuntu installer resize your Vista partition to make room for Ubuntu? If so, you most probably corrupted the Vista OS in the process, rendering it unbootable.

If Ubuntu really IS on its own separate partition, booting from an Ubuntu CD, running Partition Editor, will allow you to delete the Vista partition -- if that's what you really want do.

However, there are also ways to repair the Vista boot loader so you have real dual-boot working.

---

