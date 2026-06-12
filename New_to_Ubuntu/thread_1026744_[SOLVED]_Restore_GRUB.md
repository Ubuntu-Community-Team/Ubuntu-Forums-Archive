---
title: "[SOLVED] Restore GRUB"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by The_Shady_1 on 2008-12-31
I made the mistake of giving Vista a try recently and am trying to restore GRUB on my multi boot machine. I want to get rid of Vista and restore GRUB without messing up XP that I have on my other drive. When I boot now it gives me the option of Vista or earlier version of Windows. From a live CD I have already tried:
sudo grub
find /boot/grub/stage1
root (hd0)
etc....

It gives me a successful message but when I went to reboot it was back to the Windows Boot screen. 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x32f932f8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x79907b78

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       32548   261441778+  83  Linux
/dev/sdb2           60052       60801     6024375    5  Extended
/dev/sdb3           32549       60051   220917847+   7  HPFS/NTFS
/dev/sdb5           60052       60801     6024343+  82  Linux swap / Solaris

sda1=XP
sdb3=Vista

---

### Post by gn2 on 2008-12-31
[This should help]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD")

---

### Post by caljohnsmith on 2008-12-31
Do you know which drive you boot on start up? Is it the sda Windows drive or your sdb Ubuntu drive? To restore Grub to the MBR of either drive, you could do:
```
sudo grub
grub> root (hd1,0)
```
And then if you want to install Grub to the MBR of your Windows drive do:
```
grub> setup (hd0)
```
Or if you are booting your Ubuntu drive and want to install Grub to its MBR:
```
grub> setup (hd1)
```
And then you should get Grub on start up again. Let me know how it goes or if you run into problems.

---

