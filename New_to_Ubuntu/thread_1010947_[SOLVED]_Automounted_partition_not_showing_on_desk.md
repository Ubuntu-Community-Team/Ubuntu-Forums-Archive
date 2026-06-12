---
title: "[SOLVED] Automounted partition not showing on desktop"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by rv_ on 2008-12-14
Hello,

I'm pretty new to ubuntu and linux in general. A few weeks ago I installed Ubuntu 8.04. Everything runs fine except for just one little problem.

I have one hard disk which has two partitions apart from the linux swap and my partition for ubuntu itself.
I managed to get the two partitions automounted by adjusting my fstab:
/dev/sda1 /media/data1 jfs user,auto 0 0
/dev/sda3 /media/data2 jfs user,auto 0 0

The two partitions are mounted correctly. But only data2 appears on my desktop. Data1 is not. If I only add data1 to the fstab, data1 is shown on the desktop.

When I go to gconf-editor: apps - nautilus - desktop and and unvink volumes_visible and vink it again, both the partitions are shown on the desktop.

I assume this is a bug in nautilus? Is there anything I can do about this or should I look for an other filemapper?


Thanks

---

### Post by nhasian on 2008-12-14
maybe if you specified the options instead of setting everything to auto?  You didnt specify what filesystem you were using so i'll just show you what i have in my fstab as I have one ntfs and one ext3 partition:

```
/dev/sda2	/media/home2	ext3	relatime,errors=remount-ro 0       1
/dev/sdb1	/media/DriveD ntfs defaults,umask=007,gid=46 0 1
```

obviously make a backup copy of your /etc/fstab file first before making any changes ;)

---

### Post by vanadium on 2008-12-14
Drives mounted under /media normally acquire an icon on the desktop indeed. Perhaps the two drives are drawn on top of each other? Try moving the icon to see wether the other one is beneath it. The new position should be remembered. If that is not the case, but your drives are indeed mounted correctly, then you are likely facing a bug.

"Drives" are very much an MS Windows concept. If you would want your partitions not to clutter your desktop, mount them under /mnt instead. I prefer to see icons only for removable drives.

There is no need to change your /etc/fstab options because your issue is not related to that.

---

### Post by rv_ on 2008-12-14
vanadium,

Both icons were indeed drawn on top of each other. I could solve it by making sure 'keep aligned' was selected and choose 'clean up by name'.

When I restarted the icons were on the correct place.

Sometimes problems are much easier as you think.

---

