---
title: "can no longer mount iPod"
date: 2009-06-30
forum: New to Ubuntu
---

### Post by wgardne on 2009-06-30
At first my ipod worked great with Ubuntu. I was able to copy all my music from the iPod. But when I tried to transfer music to the iPod through Rhythmbox, Ubuntu was no longer able to see the ipod. Trying to explore the actual iPod device (it's listed as "USB Device" in the GUI), I always get "Unable to mount location."

I've tried mounting it manually through the terminal with "matt@ubuntu-fox:~$ sudo mount /dev/sda1 /media/iPod/" but I always get "mount: mount point /media/iPod/ does not exist"

So I figured that maybe I'm assuming Ubuntu is naming it something else:

> [SIZE=1]matt@ubuntu-fox:~$ sudo fdisk -l

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x18af18ae

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       58147   467065746    7  HPFS/NTFS
/dev/sda2           58148       77825   158063535    5  Extended
/dev/sda5           58148       77262   153541206   83  Linux
/dev/sda6           77263       77825     4522266   82  Linux swap / Solaris
Note: sector size is 4096 (not 512)

Disk /dev/sdj: 3892 MB, 3892056064 bytes
38 heads, 42 sectors/track, 595 cylinders
Units = cylinders of 1596 * 4096 = 6537216 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdj1               1         596     3800580    b  W95 FAT32
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 1, 1) logical=(0, 1, 22)
Partition 1 has different physical/logical endings:
     phys=(59, 37, 42) logical=(595, 13, 42)[/SIZE]    
> [SIZE=1]matt@ubuntu-fox:~$ dmesg | tail
[30591.834814] sd 11:0:0:0: [sdj] Write Protect is off
[30591.834819] sd 11:0:0:0: [sdj] Mode Sense: 68 00 00 08
[30591.834821] sd 11:0:0:0: [sdj] Assuming drive cache: write through
[30591.838176] sd 11:0:0:0: [sdj] 950209 4096-byte hardware sectors: (3.89 GB/3.62 GiB)
[30591.838662] sd 11:0:0:0: [sdj] Write Protect is off
[30591.838664] sd 11:0:0:0: [sdj] Mode Sense: 68 00 00 08
[30591.838666] sd 11:0:0:0: [sdj] Assuming drive cache: write through
[30591.838673]  sdj: sdj1
[30591.839984] sd 11:0:0:0: [sdj] Attached SCSI removable disk
[30591.840733] sd 11:0:0:0: Attached scsi generic sg6 type 0[/SIZE]
But I'm still receiving the same error:
matt@ubuntu-fox:~$ sudo mount /dev/sdj1/ /media/iPod/
mount: mount point /media/iPod/ does not exist

I'm not sure what I should try next to get it to mount. It's a 4GB iPod nano (the square ones)

---

### Post by Roadbloc on 2009-06-30
ive never had this problem. the only thing i can recommend is possible using alternative software found in add/remove, like gtkpod or amarok.

good luck

---

