---
title: "gparted"
date: 2011-08-04
forum: New to Ubuntu
---

### Post by Aitashan on 2011-08-04
i am unable to move move partitions what i need to do is increase the size of ntfs that is sda1 with the unallocated space is this possible here is screenshot and is it normal to have three Linux-swap

---

### Post by psusi on 2011-08-04
No, it is not normal to have 3 swap partitions.  Delete the 3 swap partitions ( you will need to unmount them first so the little lock icon goes away ), then move the ext4 partition to the right.  Then slide the start of the extended partition to the right so you get some free space after the ntfs partition, then you can extend the ntfs partition into that free space.  Then if you want, you can set up a single swap partition, and you will need to edit your /etc/fstab to mount it.

Note: you need to do this from the livecd so that the ext4 partition is not mounted.

---

### Post by Aitashan on 2011-08-04
why can it not be done without a live cd cause cd rom is having a lot of problem is there a alternative

---

### Post by wildmanne39 on 2011-08-04
Hi, it can not be done because the partitions will be mounted and in use.

If you try you will mess up your system and it will not work any more.

You can also create a liveusb stick and use it.

---

### Post by Basher101 on 2011-08-04
You should be able to do it from your linux partition, as long as you do not move itself. But as wildmanne39 stated, it could mess up. Is your liveCD scratched or why does it not work?

---

### Post by Aitashan on 2011-08-04
cd rom itself is not functional anyways is there a way that i could use the unallocated space with sda1 without merging to it

---

### Post by Basher101 on 2011-08-04
What do you mean CD rom is not functional? Is your optical drive broken or the Live CD?

---

### Post by wildmanne39 on 2011-08-04
Hi, do you have a usb stick called a jump drive?

---

### Post by Aitashan on 2011-08-04
yes i have a usb drive i have a pc dvd rom which is not rewriteable so i can not even burn cds on on it

---

### Post by wildmanne39 on 2011-08-04
Hi, download ubuntu then use startup disk creator to make a bootable usb stick, then you can change your partitions using the usb stick.

Here is a guide you should read before you try to change them, it is a risky task.

You should always back up everything first.
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

---

### Post by Aitashan on 2011-08-05
> **wildmanne39 said:**
> Hi, download ubuntu then use startup disk creator to make a bootable usb stick, then you can change your partitions using the usb stick.

Here is a guide you should read before you try to change them, it is a risky task.

You should always back up everything first.
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

ive got one thing more  i am running windows xp dual boot with ubuntu so if i boot to windows xp ubuntus partition gets unmounted so then by using gparted could i achieve my desirable task

---

### Post by wildmanne39 on 2011-08-05
Hi, that is true but gparted is not on windows, only ubuntu so you still need to use jump drive.

---

