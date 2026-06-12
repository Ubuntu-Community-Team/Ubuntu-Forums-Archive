---
title: "[SOLVED] SD card suddenly mounting as read only filesystem, help with fsck.vfat and/o"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by earthpigg on 2008-12-10
I didn't change anything that i can think of.

ive tried this:
tail -f /var/log/syslog

which returns a 'filesystem panic'. google tells me this means the filesystem is corrupted, and that to fix it i should:

> Please run 'sudo dosfsck -v -a /dev/mmcblk0p1' after unmounting the device (do not do this whilst it is mounted).

when i unmount (sudo umount /media/disk) the device and try running the command, it simply tells me it is not found. (i am positive it is mounted at /media/disk).


so... yeah.

is there a "sudo stfu-i-dont-care-if-its-corrupted remount right now" command?

and whats up with all the google results telling me to unmount it and then try running dosfck or fsck.vfat... if its unmounted, wtf do i put in place of /media/disk - that directory doesn't exist unless its mounted!

(tried on a 8.04 system, where it mounts at /media/disk, and an 8.10 system where it mounts at /media/disk-2... both to no avail)

edit: yes, ive tried moving the little slider on the side of the SD card both ways :)

---

### Post by tech9 on 2008-12-10
If you are sure the device is mounted at /media/disk,

then you could try something like this....

```
sudo mkfs.vfat /media/disk
```

be careful, this will format the disk, but if you do not have any data on it - it's worth a shot to see if your media will mount automatically and be both read/writable.

Good Luck,

T9

---

### Post by earthpigg on 2008-12-10
```
sudo mkfs.vfat /media/disk
mkfs.vfat 2.11 (12 Mar 2005)
mkfs.vfat: unable to open /media/disk

```

when i go to computer -> file system -> media -> disk... there it is. thats the stuff on that sd card.

other ideas?

:(

---

### Post by tech9 on 2008-12-10
> **earthpigg said:**
> ```
sudo mkfs.vfat /media/disk
mkfs.vfat 2.11 (12 Mar 2005)
mkfs.vfat: unable to open /media/disk

```when i go to computer -> file system -> media -> disk... there it is. thats the stuff on that sd card.

other ideas?

:(

with your media disk plugged into your computer

try opening gnome-terminal

and type

```
sudo fdisk -l
```This should list all of your partitions / mounted devices.

Please post your output & we'll take it from there.

---

### Post by achase79 on 2008-12-10
The device is most likely not mounted at all when you get your error.  You will have to use the device file (located in the /dev director) when calling fsck.vfat or mksf.vfat.
Such as the error you recieved showed

---

### Post by earthpigg on 2008-12-10
well what in the hell, lol.

can something be mounted at two places at once?

the significant output from sudo fdisk -l:
```

/dev/mmcblk3p1         1         2861    2011014+  6   FAT16

```

---

### Post by tech9 on 2008-12-10
> **earthpigg said:**
> well what in the hell, lol.

can something be mounted at two places at once?

the significant output from sudo fdisk -l:
```

/dev/mmcblk3p1         1         2861    2011014+  6   FAT16

```

There it is....

```
 /dev/mmcblk3p1
```

now you can format it as vfat so that you can save both your Linux and Windows files to the Disk

Glad it showed up ;)

T9

---

### Post by earthpigg on 2008-12-10
woot, thanks!

---

### Post by tech9 on 2008-12-10
> **earthpigg said:**
> woot, thanks!

no problem earthpigg :D

Take Care,

T9

---

