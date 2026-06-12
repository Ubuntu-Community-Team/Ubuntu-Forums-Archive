---
title: "Second HDD not mounted, gparted says it is mounted to &quot;/&quot;"
date: 2010-08-27
forum: New to Ubuntu
---

### Post by karatedog on 2010-08-27
I'm working in Virtualbox, but I suppose this is not a VirtualBox specific problem, but when I write "HDD" it means a virtual HDD.

I have two, almost the same, bootable HDDs, they are both attached to one virtual machine (cloned one from the other, but they have different GUIDs)
When I start the system, I expect one of the HDDs to be the boot HDD, and the other to be a simple disk.

My problem is, that the second disk is somehow - automagically - mounted to root "/" as well, along with the perfectly booted disk (well, this is what e2fsck tells me). But the 'mount' command doesn't list the device as mounted, therefore I cannot umount it, and the disk's content is nowhere accessible. It seem that no system utility "knows" about this mount (only e2fsck :-( ).

Is there a way to unmount a such mounted device (anyway what is this "hidden" mount?)
What could be the root cause of this problem (or is it a feature? Does Ubuntu mounts every bootable device?)

First disk is /dev/sda, this is the boot disk. All partitions are mounted, by fstab
Second disk is /dev/sdb. This is a fully bootable general Ubuntu disk (main Ext4 partition, one Extended/Logical partition for swap). When the above problem occurs, only the main partition is mounted, the swap is not.

dmesg has info on mounting the device:
$ dmesg | grep mount
[    6.584564] EXT4-fs (sda1): mounted filesystem with ordered data mode
[ 2434.687134] EXT4-fs (sdb1): mounted filesystem with ordered data mode

/etc/fstab has no extra entries, it only mounts the first HDD (/dev/sda1 and /dev/sda5)

Thanks

---

### Post by elliotn on 2010-08-27
Try using disk utility

System->prefferences->disk utility

---

