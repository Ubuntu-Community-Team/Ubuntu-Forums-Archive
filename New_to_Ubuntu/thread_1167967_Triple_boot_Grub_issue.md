---
title: "Triple boot Grub issue"
date: 2009-05-23
forum: New to Ubuntu
---

### Post by shabs on 2009-05-23
Hello!
I've checked this forum and the forum on backtrack but have not been able to find a solution to my problem. I was running winxp, and ubuntu 8.04, dual booting with grub without any problems.
I then partitioned my harddrive and installed backtrack 3. I'm able to boot into xp and ubuntu without any trouble. I've edited the grub several times but have not been able to boot into backtrack. I get an 
Error 17:Cannot mount selected partition.

Heres what my grub looks like at the moment:
[I]
title		Ubuntu 8.04.2, kernel 2.6.24-24-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=ef9b2e18-99d5-4282-a2d9-40d2865f34eb ro quiet splash
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-24-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=ef9b2e18-99d5-4282-a2d9-40d2865f34eb ro single
initrd		/boot/initrd.img-2.6.24-24-generic

#Windows based OS
title		Windows XP
root 		(hd0,1)
makeactive	
chainloader +1

#Backtrack 3
title Backtrack 3 
rootnoverify (hd0,2) 
kernel /boot/vmlinuz vga=791 root=/dev/sda4 ro 
boot
[/I]

heres the output of fdisk -lu
[I]
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbc65d858

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1        14683410   121885154    53600872+  83  Linux
/dev/sda2   *   121885155   153340424    15727635    7  HPFS/NTFS
/dev/sda3       153340425   156296384     1477980    5  Extended
/dev/sda4              63    14683409     7341673+  83  Linux
/dev/sda5       153340488   156296384     1477948+  82  Linux swap / Solaris

Partition table entries are not in disk order
[/I]
sda4 is where backtrack is installed. sda1 holds ubuntu. I'm guessing to edit the grub menu in someway to allow me to boot into backtrack. Any help would be appreciated. Thanks.

---

### Post by dnairb on 2009-05-23
I could be wrong (I don't know the disk numbering for extended/logical partitions), but you could try (hd0,3) for the Backtrack.

---

### Post by shabs on 2009-05-23
Thank you so much, it worked. I'm on backtrack as I type. I now see why (hda0,4) worked. I appreciate your time :)

---

