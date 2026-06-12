---
title: "need help with grub!"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by robbo130 on 2009-05-01
hey all

recently installed ubuntu 8.04 hh on external media( sdb3, hd1,2 by the menu.lst) and now grub wont find fedora 10 on my internal hd. which is kinda irritating seeing as it found xp on the very same hard drive that fedora is on. 

this is the xp part of grub, and the fedora 10 part i tried to add:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Microsoft Windows XP Home Edition
root        (hd0,1)
savedefault
makeactive
chainloader    +1

# This entry is a guess. Fedora Core 10, kernel 56
# possibly on /dev/sda3
title        Fedora Core 10, kernel 56
root        (hd0,2)
map (hd0,1)
savedefault
makeactive
chainloader    +1

```the fedora entry is a work in progress, accumulated from what i could find on the net. but it gives me all sorts of errors during boot. namely, 13, and a few others that ive forgotten (with diff config of course).

this is my drive arrangement, as ```
sudo fdisk -l
``` found out for me:

```
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x34fe34fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63     6554519     3277228+  12  Compaq diagnostics
/dev/sda2         6554520    41961779    17703630    7  HPFS/NTFS
/dev/sda3   *    41961780    42363404      200812+  83  Linux
/dev/sda4        42363405    78140159    17888377+   5  Extended
/dev/sda5        42363468    78140159    17888346   8e  Linux LVM

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000b1c62

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   202756364   101378151    b  W95 FAT32
/dev/sdb2       202756365   222291404     9767520   82  Linux swap / Solaris
/dev/sdb3   *   222291405   312576704    45142650   83  Linux
```sdb2 is ubuntu, and sda2 is xp (i believe).

can anyone please help me get my fedora into grub? i havent yet found any help anywhere else on the net, and as im just getting used to linux, ive got no clue as to how i would go about fixing this.

thanks in advance 

-xavier.

---

### Post by Eisenwinter on 2009-05-01
Your entry for Fedora is wrong.

It needs to be

title Fedora
root hd(0,2) #/dev/sda3
kernel /something root=/dev/<where fedora is installed>
initrd /kernel_image

Get into a live environment, chroot into the fedora root partition, and check out the info in /boot/grub/menu.lst, copy the stuff from there into your Ubuntu one.

---

### Post by robbo130 on 2009-05-01
thanks mate, ill give it a shot now

-xavier

---

### Post by robbo130 on 2009-05-01
okay, ive got the live environment up, now how do i chroot there? the fedora partition isnt listed as mounted media, though the xp partition is

thanks

-xavier

---

### Post by robbo130 on 2009-05-01
not to worry, managed to bypass needing chroot by forcing the mount of sda3, where fedora boot manager is apparently.

problem was, it was a hidden folder :evil:

but its all worked out now, thanks for your help champ, i really appreciate it hey.

-xavier

---

