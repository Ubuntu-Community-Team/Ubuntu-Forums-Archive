---
title: "Either Win or GRUB... cannot chainload Ubuntu and XP"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by jdstunner on 2009-09-14
I have 2 partitions on one hard drive [/dev/sdc] for my OS, XP and linux.

I installed XP first, then I installed Ubuntu to the second partition.

Upon reboot, when I select XP in the grub menu, I get: 

[I]Starting up...
This is not a bootable disk. Please enter a bootable floppy and press any key to try again...

[/I]I used the XP disc to go into recovery mode and use

[I]fixmbr

[/I]After doing so, I can only boot into XP.

Using the live CD, I:

```
sudo mkdir /mnt/root
sudo mount -t ext3 /dev/sdc2 /mnt/root
sudo mount -t proc none /mnt/root/proc
sudo mount -o bind /dev /mnt/root/dev
sudo chroot /mnt/root /bin/bash
sudo grub
find /boot/grub/stage1
root (hd2,1)
setup (hd2)
```After this process, GRUB loads, but I get the same error message that I started with when I try to boot XP.

SO!

2 partitions / one drive
XP and Ubuntu
/dev/sdc1 - ntfs - xp
/dev/sdc2 - ext3 - ubuntu

I feel like I'm missing something so incredibly small. I have scoured the forums trying each and every little fix, I haven't gotten anything to work yet.

---

### Post by oldfred on 2009-09-14
Please do not start two threads on the same issue. Answers get mixed and various people that are trying to help do not see the answers in the other thread.

Please also see my suggestion in your other thread.

---

