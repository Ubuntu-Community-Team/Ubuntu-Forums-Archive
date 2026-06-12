---
title: "Cannot See Second Hard Drive"
date: 2010-10-04
forum: New to Ubuntu
---

### Post by AThree on 2010-10-04
I apologise if this has been answered recently, but I struggled to find any answers via the forum search.

I've just installed Ubuntu on another PC and while most of the process went smoothly, I cannot find the second hard drive anywhere inside Ubuntu. Not in places or anywhere else.

I can see it in BIOS and I saw it in Windows before I removed the drive Windows was installed on and put a new one in for the Ubuntu install (so there is no dual booting - fresh new drive for fresh new Ubuntu install).

The file system on the missing second drive is NTFS but only because Windows wouldn't format the drive as anything else. I really would not prefer to reformat as there is so much data now on that drive. But if I have to, I understand.

I've already read some posts here in the forum so I've tried typing ```
fdisk -l
``` into terminal and nothing came up, but looking at more posts, do I need to put sudo at the start for the list to appear?

I'm still a right noob when it comes to Ubuntu so I do apologise in advance if I'm a bit slow.

Thanks for any help you can give :)

EDIT: Yeah, turns out I did need sudo *face palm* this is what came up:

> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9e874813

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19457   156288321    7  HPFS/NTFS

Disk /dev/sdb: 60.0 GB, 60040544256 bytes
255 heads, 63 sectors/track, 7299 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000dd42b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6996    56192000   83  Linux
/dev/sdb2            6996        7300     2439169    5  Extended
/dev/sdb5            6996        7300     2439168   82  Linux swap / Solaris

Disk /dev/sdc: 4018 MB, 4018143232 bytes
256 heads, 32 sectors/track, 958 cylinders
Units = cylinders of 8192 * 512 = 4194304 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd03ed03e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         957     3918848    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(958, 255, 32) logical=(956, 193, 4)


Not sure what any of it means though O_o

---

### Post by viralmeme on 2010-10-04
> **AThree said:**
> I've just installed Ubuntu on another PC and while most of the process went smoothly, I cannot find the second hard drive anywhere inside Ubuntu

See if this works ..

$sudo -i
$mkdir /mnt/sda1
$mount /dev/sda1 /mnt/sda1

If so, then to make permanent, you need to put an entry in /etc/fstab .. [Mounting Windows Partitions in Ubuntu]("http://www.psychocats.net/ubuntu/mountwindowsfstab")

---

### Post by AThree on 2010-10-04
Thanks for your reply :)

Followed instructions above and got this in Terminal:

> The disk contains an unclean file system (0, 1).
The file system wasn't safely closed on Windows. Fixing.

Good to hear it is being fixed, but I cannot exit Terminal because it is still fixing - any idea how long this might take or should I just let it run as long as it wants?

---

### Post by robsoles on 2010-10-04
> **AThree said:**
> ...

Good to hear it is being fixed, but I cannot exit Terminal because it is still fixing - any idea how long this might take or should I just let it run as long as it wants?

Best leave it run till finished.

When it finishes you will possibly find it in 'places', if not immediately then perhaps after a restart.

'System'->'Administration'->'Disk Utility' will be listing the drive and would have allowed you to do a neater 'GUI' file-system check of the drive.

---

### Post by AThree on 2010-10-04
Thank you :)

Although I cannot see or hear anything to suggest it is fixing, the Terminal still isn't letting me exit, so I shall just have to have faith it is working!

---

### Post by muteXe on 2010-10-04
If that doesn't work, try plugging it into a mate's windows machine, then make sure you select the "safely remove USB device" option. 
Then try it again on your linux machine.

---

### Post by robsoles on 2010-10-05
> **AThree said:**
> Thank you :)

Although I cannot see or hear anything to suggest it is fixing, the Terminal still isn't letting me exit, so I shall just have to have faith it is working!

So surely it finished? Has it the files you hoped to get back off it?

---

### Post by muteXe on 2010-10-05
He said "the Terminal still isn't letting me exit", which to me means it's hanging.

---

