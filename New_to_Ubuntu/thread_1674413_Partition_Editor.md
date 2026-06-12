---
title: "Partition Editor"
date: 2011-01-23
forum: New to Ubuntu
---

### Post by smooth65 on 2011-01-23
I am looking for the partition editor under system-administration but its not there. How can I make that appear. I am attempting to un install ubuntu completely as its not for me at the moment. I dont have windows at all on my PC so I wanna get rid of ubuntu and bring back windows. I am following the instructions to reformat and ran into this problem. Thanks in advance.

---

### Post by dirghrabadia on 2011-01-23
I think you cannot format/change the filesystem while logged into Ubuntu. Running a LIVE CD/DVD of GParted is a likely solution that will allow you to change the filesystem or format it entirely.

---

### Post by cgroza on 2011-01-23
gParted is not installed by default in an Ubuntu install. You can install it by running:

```
sudo apt-get install gparted
```
To edit the partition table, they have to be unmounted.

---

### Post by beew on 2011-01-23
If you want to bring back windoze simply install it into the hard drive and it will automatically reformat it and wipe out Ubuntu.  You don't need to delete Ubuntu first. 

Should ask this in a Windoze forum. :)

---

### Post by Bucky Ball on 2011-01-23
LiveCD, 'Try Ubuntu', away you go. As mentioned, you need to unmount all partitions if you are going to kill them.

---

### Post by Bucky Ball on 2011-01-23
> **beew said:**
> If you want to bring back windoze simply install it into the hard drive and it will automatically reformat it and wipe out Ubuntu.  You don't need to delete Ubuntu first. 

Should ask this in a Windoze forum. :)

Is this from experience? Not sure if that will work as Windows does not recognise EXT file system natively. It will possibly show the partitions as 'Unknown' or some such and won't touch 'em. ;)

---

### Post by beew on 2011-01-23
> **Bucky Ball said:**
> Is this from experience? Not sure if that will work as Windows does not recognise EXT file system natively. It will possibly show the partitions as 'Unknown' or some such and won't touch 'em. ;)

You have a point there. No, not from experience, I wouldn't try to kill Ubuntu in favour of windows under any circumstance. ;)

---

### Post by smooth65 on 2011-01-23
when I put my windows cd in, it says that I need at least 685 MB of space. I assume Gparted is what i need to correct this so that windows will install?

---

### Post by jarvis01123 on 2011-04-25
I have done this several times you need to go in with a live CD and use GParted to delete the previous partitions. Once they are deleted windows will install to fill the unused parts. I've also done it by reformatting a partition to NTFS, as windows will not recognize fat32. Anyways as always back up everything. This has worked for me numerous times but if it doesn't work for you I apologize in advance. Computers are fickle :)

---

### Post by srs5694 on 2011-04-25
If you want to *completely* wipe the hard disk, leaving *none* of your current partitions, a much simpler approach is this:

```

sudo dd if=/dev/zero of=/dev/sda bs=512 count=1

```

This wipes the partition table in a fraction of a second, with no need to boot into an emergency disc. When you shut down and reboot, the computer won't boot from the hard disk, and Windows will see the disk as being completely empty.

A few caveats:


[list]
[*]This assumes that you've got just one physical hard disk. If you've got more than one, you'll need to issue a similar command for each disk, or apply it to just the disk you want to wipe, if you want to wipe one and leave another intact.
[*]This assumes you're using the Master Boot Record (MBR) partitioning system rather than the newer GUID Partition Table (GPT) system. With GPT, you'd need to wipe several sectors at the start of the disk and several more at the end. This task is most easily accomplished with [GPT fdisk (gdisk or sgdisk)](http://www.rodsbooks.com/gdisk/), as in "sudo sgdisk --zap-all /dev/sda". Most computers today use MBR.
[*]When I say that this "completely" wipes the hard disk, I mean that it deletes the partitions. Most of the data on the disk remains intact; it's just rendered inaccessible. For ordinary re-use of a disk yourself, this is fine. If you wanted to sell or give away the disk, you should omit the "count=1" part of the command. This will cause dd to completely erase every sector on the disk, thus erasing passwords, credit card numbers, embarrassing love poems, etc. from your hard disk. Omitting the "count=1" option will, however, cause the command to take much longer (probably several hours) to complete.
[/list]

---

