---
title: "Stuck at grub rescue prompt"
date: 2010-11-01
forum: New to Ubuntu
---

### Post by MagicalPony on 2010-11-01
I foolishly deleted a bunch of partitions on my laptop. Now when I boot up, all I have is a grub rescue prompt:

```
Unknown Filesystem.
grub rescue> 
```The only commands I've found that work are ls, set, set root=, and set prefix=. I'm new to linux, and from what I've read, I need to set the prefix to point to /boot/grub, but I just keep getting an unknown filesystem message if I do something like ls (hd0,3)/boot/grub.

If I just ls, it returns: (hd0), (hd0,1), (hd0,3), (hd0,6).
I've tried setting the root and prefix to all of these but still get unknown filessytem error.

set command shows this configuration when I first boot up the computer:
```
prefix=(hd0,6)/boot/grub
root=(hd0,6)
```My biggest problem is the fact that the laptop has no CD drive, so live disks aren't really an option. And to make matters worse, The system just hangs if a flash drive is plugged in when booting up. I don't see anything useful in the BIOS setup either.

The laptop has (had?) XP, and Kubuntu.

What are my options?

Thanks.

---

### Post by drs305 on 2010-11-01
I wrote a guide on how to access the LiveCD ISO if you can get to a grub prompt. You have to be able to download the ISO and access it via the Grub menu. Here is the link if you can do those two things:
[http://ubuntuforums.org/showthread.php?t=1599293]("http://ubuntuforums.org/showthread.php?t=1599293")

Also, have you tried the "insmod" command?  It might be that you have to "insmod (hd0,6)/boot/grub/linux.mod" ...
Added:  Also "insmod (hd0,6)/boot/grub/ext2.mod".

---

### Post by MagicalPony on 2010-11-01
Thank you for the quick reply. It looks like it does recognize the insmod comand, although I'm not sure how to use it. I will try what you suggested and read your HOWTO, hopefully I can figure things out.
EDIT: insmod (hd0,6)/boot/grub/linux.mod retuned the same "error: unknown filesystem"

---

### Post by drs305 on 2010-11-01
If you are able to boot to the LiveCD desktop, by whatever means, posting the RESULTS.txt output of the boot info script found here may help us [http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by MagicalPony on 2010-11-01
Thanks for the help, I finally got the computer to boot from my flash drive which has Linux Mint 9. I'm now in the process of installing it. I don't really need anthing that was on the partitions that I got rid of, do I need to do anything else to make sure they have been correctly deleted?

---

### Post by drs305 on 2010-11-01
> **MagicalPony said:**
> Thanks for the help, I finally got the computer to boot from my flash drive which has Linux Mint 9. I'm now in the process of installing it. I don't really need anthing that was on the partitions that I got rid of, do I need to do anything else to make sure they have been correctly deleted?

If you are about to install a linux OS, you might open GParted to inspect the partition structure just to make sure the disk is partitioned the way you think it is. 

Before installing, it would also be a good time to decide whether you want to set up a separate /home or data partition. I generally find it easier to create these before I start the installation, and then choose manual partitioning during the install so I can choose where things go. But these are just personal preferences....

---

