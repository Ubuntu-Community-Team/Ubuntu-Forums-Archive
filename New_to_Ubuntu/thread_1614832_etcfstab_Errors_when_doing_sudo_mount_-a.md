---
title: "/etc/fstab Errors when doing sudo mount -a"
date: 2010-11-06
forum: New to Ubuntu
---

### Post by Joshwaa on 2010-11-06
When I attempt
```
sudo mount -a
```
in Terminal it'll give me errors for lines 10 and 12 of my /etc/fstab.
Heres the file:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=5f1df4ea-be09-480e-ab2f-4a8dc7ba19e0 /               ext4    errors=remount-ro 0       1&#8206;
/mnt/4096Mb.swap  none  swap  sw  0 0
/dev/sda3      /media/Windows 7 ntfs-3g    default  0   0
```

---

### Post by zer010 on 2010-11-06
Is it even possible to mount the swap area?

---

### Post by Verbeck on 2010-11-06
try replacing line 10 with 
```
UUID=5f1df4ea-be09-480e-ab2f-4a8dc7ba19e0 / ext4 errors=remount-ro 0 1
```for line 12, put /media/windows 7 in quotes "" so it reads
```
"/media/windows 7"
```

---

### Post by Joshwaa on 2010-11-06
> **zer010 said:**
> Is it even possible to mount the swap area?

No idea.. bit of a linux newb. It's a swap file not a swap partition so I think it has to be mounted.

---

### Post by Joshwaa on 2010-11-06
> **Verbeck said:**
> try replacing line 10 with 
```
UUID=5f1df4ea-be09-480e-ab2f-4a8dc7ba19e0 / ext4 errors=remount-ro 0 1
```for line 12, put /media/windows 7 in quotes "" so it reads
```
"/media/windows 7"
```

Line 10 works now, whilst Line 12 doesnt..

---

### Post by coffeecat on 2010-11-06
Someone else has picked up the problem with the space in your label "Windows 7" for sda3, but field 4 needs changing from 'default' to 'defaults'.

---

### Post by Ant59 on 2010-11-06
Can you post the output of:

```
ls /media
```

---

### Post by Joshwaa on 2010-11-06
> **coffeecat said:**
> Someone else has picked up the problem with the space in your label "Windows 7" for sda3, but field 4 needs changing from 'default' to 'defaults'.

Hm.. explain further?


> **Ant59 said:**
> Can you post the output of:

```
ls /media
```

```
josh@JoshsUbuntu:~$ ls /media
disk  Windows 7

```

---

### Post by Ant59 on 2010-11-06
Ok, make this Line 12:

```
/dev/sda3 "/media/Windows 7" ntfs-3g defaults 0 0
```

---

### Post by Joshwaa on 2010-11-06
> **Ant59 said:**
> Ok, make this Line 12:

```
/dev/sda3 "/media/Windows 7" ntfs-3g defaults 0 0
```

Still getting that line 12 is bad..

---

### Post by coffeecat on 2010-11-06
> **Joshwaa said:**
> Hm.. explain further?

Ah, forget it. I've always used 'defaults' for the option in ntfs fstab lines and I thought that 'default' wouldn't work, but I've just tried it and it does.

Saves a keypress, I suppose. :|

---

### Post by Joshwaa on 2010-11-06
> **coffeecat said:**
> Ah, forget it. I've always used 'defaults' for the option in ntfs fstab lines and I thought that 'default' wouldn't work, but I've just tried it and it does.

Saves a keypress, I suppose. :|


I've tried what you've said, and it still doesn't work.. im confused as to why this isn't working..

---

### Post by Ant59 on 2010-11-06
Does it give any details on the error?

Out of curiosity, what does "sudo fdisk -l" output?

---

### Post by Verbeck on 2010-11-06
could you try mounting it to a directory without a space?
```
sudo mkdir /media/windows-7
```then in fstab - line 12
```
/dev/sda3 /media/Windows-7 ntfs-3g defaults 0 0
```EDIT:
also post the output of 
```
sudo blkid -c /dev/null
```

---

### Post by Joshwaa on 2010-11-06
> **Ant59 said:**
> Does it give any details on the error?

Out of curiosity, what does "sudo fdisk -l" output?

It just says that line 12 is bad..
hm..

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xdc82dc82

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1530    12288000   27  Unknown
/dev/sda2   *        1530        1543      102400    7  HPFS/NTFS
/dev/sda3            1543       35089   269457752    7  HPFS/NTFS
/dev/sda4           35089       38914    30718977    f  W95 Ext'd (LBA)
/dev/sda5           35089       38914    30718976   83  Linux

Disk /dev/sdb: 3965 MB, 3965190144 bytes
49 heads, 48 sectors/track, 3292 cylinders
Units = cylinders of 2352 * 512 = 1204224 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           4        3293     3868160    b  W95 FAT32

```

---

### Post by Ant59 on 2010-11-06
What details does it give if you try it manually?

```
sudo mount /dev/sda3 "/media/Windows 7"
```

---

### Post by Joshwaa on 2010-11-06
> **Ant59 said:**
> What details does it give if you try it manually?

```
sudo mount /dev/sda3 "/media/Windows 7"
```


```
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.

```

---

### Post by Ant59 on 2010-11-06
I think I've got it! Did you correctly shut down Windows before booting Ubuntu? If you hibernated or didn't shut down, you won't be able to mount the Windows partition.

---

### Post by Joshwaa on 2010-11-06
> **Ant59 said:**
> I think I've got it! Did you correctly shut down Windows before booting Ubuntu? If you hibernated or didn't shut down, you won't be able to mount the Windows partition.
It was shut down properly.. haha.
The thing is, it shows up in my the sidebar of Nautilus and I click it and it mounts.. it's weird because my music on Rhythmbox is being pulled from my Win7 partition and I have to open the partition for the music to load, I'm trying to make the partition automatically load.

---

### Post by Verbeck on 2010-11-06
also. before you try sudo mount -a, unmount the device first if its already mounted

```
sudo umount /dev/sda3
```

---

### Post by Joshwaa on 2010-11-06
> **Verbeck said:**
> also. before you try sudo mount -a, unmount the device first if its already mounted

```
sudo umount /dev/sda3
```


Still giving line 12 is bad error.

---

### Post by Verbeck on 2010-11-06
> **Joshwaa said:**
> Still giving line 12 is bad error.
have you tried what i said in the previous post? it could work 

```
sudo mkdir /media/windows-7
```then in fstab - line 12
```
/dev/sda3 /media/windows-7 ntfs-3g defaults 0 0
```

---

### Post by Joshwaa on 2010-11-06
> **Verbeck said:**
> have you tried what i said in the previous post? it could work 

```
sudo mkdir /media/windows-7
```then in fstab - line 12
```
/dev/sda3 /media/windows-7 ntfs-3g defaults 0 0
```


I must have missed that post, that worked perfectly!
This will not affect how my Windows 7 boots will it, since I've renamed the /media/Windows 7 to /media/Windows-7?

---

### Post by Verbeck on 2010-11-06
yep, fstab handles how the device is mounted in ubuntu. its got nothing to do with windows

---

### Post by nitstorm on 2010-11-06
+1 for Windows-7 solution

Also could you try using the UUID of /dev/sda3 ?
u can get the UUID by typing
```

sudo blkid

```

then ur line would read something like this
```


UUID=06C00DB5C00DAC4D "/media/Windows 7" ntfs defaults 0 0


```

P.S: Try replacing ntfs-3g with ntfs

---

### Post by Joshwaa on 2010-11-06
> **Verbeck said:**
> yep, fstab handles how the device is mounted in ubuntu. its got nothing to do with windows

Thanks for the help :) That works perfectly now.
I'll set the thread as Solved, but if I boot into Windows and it won't work properly I'll unmark it :)

---

### Post by Ant59 on 2010-11-06
Glad it's working now :)

I'll have to make a note of this: "fstab does not play well with spaces" haha

---

### Post by Crusty Old Fart on 2010-11-06
Spaces in mount points written in fstab need to be specified as: \040

If you'd rather not use the UUID, this would have worked:
```

/dev/sda3 /media/Windows\0407 ntfs defaults 0 0

```Then in /media:
```

sudo mkdir /media/"Windows 7"

```Just another way to skin the same cat.

---

