---
title: "Grub problem in 10.04"
date: 2010-04-22
forum: New to Ubuntu
---

### Post by SpongeBob SquarePants on 2010-04-22
Just upgraded to Ubuntu 10.04. Everything's working fine. Except I can't log into Windows anymore. The entry's there in GRUB. But when I choose "Windows XP" it simply defaults back to the GRUB menu and pretends like nothing has happened. The mistake I made, I think, was upgrading to the package maintainers GRUB settings, instead of keeping what I had previous (which obviously worked).

I had a brief look at grub.cfg and my Windows entry reads....

menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 42ec6cd1ec6cc0b1
	drivemap -s (hd0) ${root}
	chainloader +1

The dev/sda1 part is correct. But the "set root" part, I think, needs to be (hd0,0). It wrongly putting in (hd0,1) is a fairly common fault on my machine. What I usually do is... edit GRUB (that is, the old style GRUB), change the (hd0,1) to (hd0,1)... boot up and then edit GRUB's "menu.lst".

However, in the new GRUB, this doesn't appear to work. Firstly, changing (hd0.1) to (hd0,0) at the GRUB menu (by pressing "e" and then Ctrl+X once I'm done), does nothing. Secondly, I seem to recall that it's not as simple as just editing the grub.cfg any more.

Anyway, can anyone suggest how to fix my problem?

Much obliged, chaps.

---

### Post by Sef on 2010-04-22
Check out Ubuntu's [GRUB 2]("https://help.ubuntu.com/community/Grub2").

---

### Post by oldfred on 2010-04-23
Grub2 counts partitions differently. Where grub legacy counted from 0, grub2 starts at 1, so sda1 will be (hd0,1).

Did you install grub to the partitions also, we have seen many select that while installing Lucid. If so you may have written over the windows boot in the windows partition. If so you need the windows repair disk fro XP and run the fixboot command. Do not run fixMBR or you will have to reinstall grub.

---

