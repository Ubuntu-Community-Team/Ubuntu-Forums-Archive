---
title: "Creating Partition and installing XP with ubuntu"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by tekne on 2009-01-23
Hello

My computer originaly with Windows Vista.
As it is not a good computer i was hopping to try linux a while ago i decided to put ubuntu 8.10. I deleted everything in my hard drive through Ubuntu Live CD and now i have only the basic partitions for ubuntu to work.
Now, i want to make a new partition so i can install windows XP but i can't find a SIMPLE and efficient program that can help me make the partition i need for windows and, still, live the partitions for linux to run and installed with all the documents, music, videos, **** i have in it.
I tried GParted but i can only creat a new partition by deleting everything in the one that already exists. Anyone know a better and simple way? Thank you for your time.

---

### Post by Locke_99GS on 2009-01-23
Use gparted to size a partition smaller, then let Windows have the unused space.

Note that after installing Windows, you will have to reinstall GRUB.

---

### Post by kestrel1 on 2009-01-23
To use Gparted to resize your partitions you need to be running the Live CD, because the partitions cannot be mounted at the same time as you are trying to resize them.

---

### Post by tekne on 2009-01-23
what is GRUB and why is that?
the button for "resizing" /dev/sda1 are locked, i can not resize. any ideas why?

---

### Post by kestrel1 on 2009-01-23
See my first post.
Grub is the linux boot loader.
Additionally see here to restore GRUB: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by tekne on 2009-01-23
thank you, will try

---

