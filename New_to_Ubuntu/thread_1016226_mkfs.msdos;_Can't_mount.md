---
title: "mkfs.msdos; Can't mount"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by ok_dr on 2008-12-19
I need help to mount a flash drive. It mounted ok but I think I screwed up writing mkfs.msdos (I think in properties/settings/filesystem) and now it says that "the volume uses mkfs.msdos filesystem which is not supported by your system". 
Is there any way to undo it? (don't ask me why the hell I wrote that in the first place, because it's a long story and I already feel like an idiot).

---

### Post by taurus on 2008-12-19
What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by albinootje on 2008-12-19
> **ok_dr said:**
> I need help to mount a flash drive. It mounted ok but I think I screwed up writing mkfs.msdos (I think in properties/settings/filesystem) and now it says that "the volume uses mkfs.msdos filesystem which is not supported by your system". 
Is there any way to undo it? (don't ask me why the hell I wrote that in the first place, because it's a long story and I already feel like an idiot).

Can you try : ```
 sudo modprobe msdos 
```
And then try mounting it again ?

And is there some important data on it ? Can it be read on a DOS or MS-Windows machine ?
If the data is not important or backed up, you can still use mkfs.vfat for it.

---

### Post by ok_dr on 2008-12-19
The output of fdisk -l:

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2a2f2a2e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4905    39399381   83  Linux
/dev/sda2            4906        4998      747022+   5  Extended
/dev/sda5            4906        4998      746991   82  Linux swap / Solaris

Disk /dev/sdb: 124 MB, 124780544 bytes
255 heads, 63 sectors/track, 15 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1a97e4e8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          15      120456    6  FAT16

---

### Post by ok_dr on 2008-12-19
> **albinootje said:**
> Can you try : ```
 sudo modprobe msdos 
```
And then try mounting it again ?

And is there some important data on it ? Can it be read on a DOS or MS-Windows machine ?
If the data is not important or backed up, you can still use mkfs.vfat for it.

I tried that code but nothing happened. It's read all right in Windows. As for mkfs.vfat how do I use it? Keep in mind I installed ubuntu just 2 days ago so I'm a little lost at times.

---

### Post by taurus on 2008-12-19
What happens if you try to mount it with

```
sudo mkdir /media/sdb1
sudo mount -t vfat /dev/sdb1 /media/sdb1
df -h
```

---

### Post by ok_dr on 2008-12-19
> **taurus said:**
> What happens if you try to mount it with

```
sudo mkdir /media/sdb1
sudo mount -t vfat /dev/sdb1 /media/sdb1
df -h
```

Thanks Taurus. It mounted, I was able to delete the mkfs.msdos (which by the way I had written in the drive settings not the volume settings like reported in the thread). 
Now it mounts ok. Thank you very much.

---

