---
title: "GRUB: moving to bigger hard drive with gparted and clonezilla"
date: 2010-02-22
forum: New to Ubuntu
---

### Post by tadcan on 2010-02-22
I have cloned my laptop HD with clonezilla and put i the new HD. I went through the advanced options which stated it would try and expand to the new size. Which it didn't.

So it put in gparted. To use the unallocated space I had to copy and expand into the blank space, then I deleted the original partitions. Which allows me to expand the window partition to fill up the space left. 

This however makes a mess of grub. Is there a way to build Grub/MBR to make this work. Or do I have to use another method.

---

### Post by jimreynold2nd on 2010-02-22
Yes. Are you comfortable with GrUB and your partitioning scheme? If so, recovering from that is easy. I'm assuming GrUB 1. GrUB 2 should have similar commands.
1) Recover GrUB's MBR so that the computer boots.
- Boot into partedmagic (or clonezilla), make sure you're root, run "grub" from command line and you should have a grub prompt.
- Run "root (hdX,Y)" where X is your (grub) hard drive number, Y is your (grub) partition number. You can use double-tab-completion in case you forget. Remember that those numbers started at 0, and that your first extended partition is (hdX,5). No space after the comma.
- Run "setup (hdX)" to install GrUB into MBR. Alternatively you can install GrUB into boot sector of partition Z by doing "setup (hdX,Z)".

2) Edit GrUB config file (menu.lst or grub.conf, try one, if doesn't work, rename to the other one) to reflect the new partitioning scheme.

---

### Post by tadcan on 2010-02-22
No I'm new to all this and working it out as I'm going along. I'll have a go at your advice and post any questions that come up.

---

### Post by louieb on 2010-02-22
Did the same thing a while back. After using Gparted you will need to reinstall GRUB - you really need to know if you have Grub or GRUB2. Reinstall method is different. Look in /boot/grub - menu.lst = grub legacy . grub.conf = GRUB2.

With Karmic it could be either, my guess is you have GRUB2 but you need to be sure. [Grub 2 Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1195275")

---

### Post by tadcan on 2010-02-23
I have grub 2.

I'll have a go when i get home this evening. Thanks for the link.

---

### Post by tadcan on 2010-02-23
In gparted I opened the terminal put in grub and grub.conf

grub-install -v gave grub 1.98

However I have a bigger problem, I get a error when I expand the windows partition. When I boot into a live cd I can't find root. 

I may just back up /home and documents and settings and just reinstall from scratch. At least I know how to do that. :D

---

### Post by louieb on 2010-02-23
Believe there is a check box for aligning the copy to cylinder boundary - For XP and Linux you want to align to cylinder boundary - for Vista and Win7 it just the opposite you want the box unchecked. 

To find which partition is your / (root) boot to the hard drive install and run the **mount** command

---

### Post by tadcan on 2010-02-23
I unticked the box for round cylinder's. It still didn't work.

I had a look at the log. It seems the ntfs file system itself has an error. 

The ntfs drive I saved the image to had errors that I had to fix. But I don't see how that could have had an impact. 

Maybe their was an error on the original hard drive.

---

