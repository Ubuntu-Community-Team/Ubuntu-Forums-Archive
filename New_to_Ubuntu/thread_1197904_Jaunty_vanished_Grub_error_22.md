---
title: "Jaunty vanished: Grub error 22"
date: 2009-06-26
forum: New to Ubuntu
---

### Post by ajusco on 2009-06-26
I have Jaunty installed on an Asus EEE 1000HE, dual booted with Windows XP. Each with about half the 160gb hard drive.

Jaunty seems to have vanished suddenly. Grub keeps popping up with an "error 22" message.

A Supergrub disk finds my windows, but not Ubuntu.

Both the Ubuntu 9.04 disk and Knoppix 5.1 find the two windows and two ubuntu partitions: But neither recognizes the Ubuntu file system as any known file system. Won't read them.

Checking the forums, "error 22" usually seems to be when a Windows file system is unreadable. I didn't see any reference to something like this.

Would you know of some way to make the ubuntu partitions readable again?

Failing that, an easy solution would be to reinstall since this is a recent install and I didn't have much saved. But on reinstall I get stuck at the partition. I have to go to manual partitioning since I don't want to partition the whole disk and wipe out windows. But I'm not sure what to put when the process asks for "mount point" and "file system" on the two now mysterious partitions where I'd reinstall Ubuntu.

Any help greatly appreciated.

---

### Post by Azrael3000 on 2009-06-26
Did you try this here: [http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub+livecd](http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub+livecd)

Regarding the ubuntu reinstallation. Normaly you shouldn't have to go to manual partitioning since Ubuntu will keep your Windows installation safe.

---

### Post by ajusco on 2009-06-27
Thanks. Will try the grub mechanics. Tried reinstalling both ubuntu and windows. both installed. but again getting error 22.

it may have been originally a windows error that made jaunty invisible to everything evenwhile windows partitions were visible.

---

### Post by shifty_powers on 2009-06-27
did you use the same cd to reinstall?

if you did, try checking it's integrity.

---

