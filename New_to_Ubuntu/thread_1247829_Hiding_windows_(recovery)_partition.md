---
title: "Hiding windows (recovery) partition ?"
date: 2009-08-23
forum: New to Ubuntu
---

### Post by simransingh on 2009-08-23
How can i completely remove a windows (recovery) partition on the sidebar (UNR), places, file explorer etc

Thanks

ps the drive doesnt show (or my other windows drive) in fstab - only linux partitions show (btw this partition im trying to hide is a fat32 recovery partition)

---

### Post by TheLions on 2009-08-23
> **simransingh said:**
> How can i hide a windows (recovery partition) on the sidebar (and from panel/file explorer in the traditional view mode) ??

Thanks

look here:
[http://ubuntuforums.org/showthread.php?t=99086](http://ubuntuforums.org/showthread.php?t=99086)

---

### Post by simransingh on 2009-08-23
> **TheLions said:**
> look here:
[http://ubuntuforums.org/showthread.php?t=99086](http://ubuntuforums.org/showthread.php?t=99086)

its a fat32 drive (sda3) and isnt listed in fstab (only linux partitions are) but of course it lists in fdisk

check out the file logs

[Http://pastebin.ubuntu.com/258177](Http://pastebin.ubuntu.com/258177)  (my fstab)
[http://paste.ubuntu.com/258174](http://paste.ubuntu.com/258174) (fdisk)

I want Ubuntu to not even FIND the recovery drive

---

### Post by rbc on 2009-08-23
Open GParted, then right click on the Recovery partition, then select Manage Flags. From the available options, check "hidden". Close GParted. See if that doesn't accomplish what you want

---

### Post by simransingh on 2009-08-23
> **rbc said:**
> Open GParted, then right click on the Recovery partition, then select Manage Flags. From the available options, check "hidden". Close GParted. See if that doesn't accomplish what you want

Thanks very much for your input - The only flag that was checked on the Recovery partition was "lba", so i checked "hidden" - 
However the Drive still shows on the right side bar, panels etc and it can be mounted...

here is a short summary of the scenario:

[FONT=verdana, arial, helvetica][SIZE=2][SIZE=1]i bought an eee pc, it had 1 HDD divided into C:/ and D:/ ....but there was also an option to boot from a recovery partition which WAS hidden (it used to showed on partition magic as "hidden on the far right".

I recently installed ubuntu, created several partitions using Gparted live, moved sectors about etc...now the recovery partition is no longer hidden. it shows in UBUNTU as a fat32 partition which i can mount. Because the partition isnt assigned a drive letter, it wouldnt show in windows/explorer

So what i would like to know is...How can i make it a hidden partition once again? (i dont want to hide a partition from an OS...i want to make it hidden)

GRUB (linux boot system), now shows 3 booting options ...linux, xp AND this recovery partition --> which takes you to the eeepc system recovery...

I have tried using partition magic..but the "hide partition" option is greyed out.. No point using a util like powertools xp (tweakui) as that requires the partition to have a drive letter, and thus just hides that DRIVE from window and not the part[/SIZE]ition.[/SIZE][/FONT]

---

