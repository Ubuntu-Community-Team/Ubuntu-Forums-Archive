---
title: "Terminal command for mounting hdd"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by solian2002 on 2009-03-13
I made a mistake and I can't remember how to mount my hdd via the terminal... Yes, I am made of fail. I can not mount it via the GUI.

sudo mount something isn't it? 

And after that so I don't screw it up again, how do you set a drive to auto mount when Ubuntu starts? Thanks!;)

---

### Post by feelshift on 2009-03-13
```
sudo mount ntfs-3g /dev/sdaX /where/you/want/to/mount/it
```
If the partition is FAT32, replace ntfs-3g with vfat.
For auto mount ```
gksu gedit /etc/fstab
``` and add an entry 
```
/dev/sdaX /where/you/want/to/mount/it ntfs-3g umask=000 0 0
```
Again, substitute ntfs-3g with vfat if necesary.

Note: in /dev/sdaX, the X is replaced with the partition number. If you don't know it, ```
sudo fdisk -l
```

Example:```
sudo mount -t ntfs-3g /dev/sda1 /mnt/win
```
and the fstab entry
```
/dev/sda1 /mnt/win ntfs-3g umask=000 0 0
```

---

### Post by solian2002 on 2009-03-13
Okay, it's mounted, now umount won't let me unmount it... I gues I wasn't suppose to mount it in my home folder... I'm so full of fail... lol

---

### Post by feelshift on 2009-03-13
Try with the force argument. I think you add --force at the end of the command but I'm not sure.

---

### Post by solian2002 on 2009-03-13
Used the windows method of probleming sloving (and it worked!), restart the computer and hope it fixes itself. This time I made a folder and all is good, thank you for your help.

---

### Post by RetchingRabbit on 2009-03-13
> **solian2002 said:**
> Okay, it's mounted, now umount won't let me unmount it... I gues I wasn't suppose to mount it in my home folder... I'm so full of fail... lol

My guess is that this situation may require a reboot to unmount. In the future, use a dedicated mount point. For example, do ```
sudo mkdir /mnt/win
```Then ```
sudo mount /dev/sdX /mnt/win
```

Hope this helps!

---

