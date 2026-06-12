---
title: "Unable to mount Vista partition after 9.04 upgrade"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by ubntufan on 2009-04-25
I've upgraded my copy of 8.10 to 9.04 and its enjoyable...a bit buggy but great nonetheless. I have an immediate problem mounting my Windows partition. Before I took the plunge in upgrading, I was hesitant. I went as far as letting the Update Manager carry out setting the new software channels and cancelled. I'm speculating that this may have messed up my access to my files on the Vista side as I'd thought I could access it before I decided to fool around with the Update Manager.  

Anyhow, I'd read on the net about a program called pysdm and installed that. After starting pysdm, I noticed that I'm missing sda3 and sda4 as available partitions to mount. Despite the missing partitions, I have sda1, 2, 5, 6 and 7. I opened a terminal and typed the command sudo fdisk -l and got this

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2               6        1280    10240000    7  HPFS/NTFS
/dev/sda3   *        1280       22426   169855148    7  HPFS/NTFS
/dev/sda4           22427       30402    64060500+   f  W95 Ext'd (LBA)
/dev/sda5           30076       30402     2619392   dd  Unknown
/dev/sda6           22427       29757    58886226   83  Linux
/dev/sda7           29758       30075     2554303+  82  Linux swap / Solaris
```



Also before the upgrade, the folder (OS) bridging the gap to my Vista side (sda3) in /media/ has now vanished?

:confused:

---

### Post by cariboo on 2009-04-26
You would probably be better off installing ntfsprogs, it is in the repositiories, and you can use Add/Remove Programs or Synaptic Package Manager to install the package.

---

### Post by ubntufan on 2009-04-26
Alright, I downloaded ntfsprogs. I tried using ntfsmount to mount sda3 but here is what happened; 
```
sudo mount /dev/sda3 /mnt/windows -t ntfs -o umask=0002,nls=utf8

``````
NTFS signature is missing.
Failed to mount '/dev/sda3': Invalid argument
The device '/dev/sda3' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
``` I also downloaded gParted and didn't carry out anything, but I'd noticed sda3 was in black stated as "unknown" and had an exclamation mark to its left while everything else had a label such as ext3, linux-swap, etc.

---

### Post by Mark Phelps on 2009-04-27
Would strongly recommend using ntfs-3g for mounting Vista volumes, as follows: "mount -t ntfs-3g /dev/sda3 /mnt/windows"

---

