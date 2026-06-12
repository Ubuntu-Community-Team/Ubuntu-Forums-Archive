---
title: "Can not find Boot Option to boot Windows XP"
date: 2009-12-19
forum: New to Ubuntu
---

### Post by sarayuvijay on 2009-12-19
I very new to linux. I upgraded from Jaunty to Karmic recently. After much struggle I was able to get the sound working in Karmic thanks to the ubuntu forums, by installing Grub2. After installation when I re booted the windows option disappeared from the boot menu list.
I am including the results of following commands.  just thought it might help
 sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd439d439

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9767488+  83  Linux
/dev/sda2            1217        9728    68372640    f  W95 Ext'd (LBA)
/dev/sda5            2551        3825    10241406    7  HPFS/NTFS
/dev/sda6            3826        5100    10241406    7  HPFS/NTFS
/dev/sda7            5101        9728    37174378+   7  HPFS/NTFS
/dev/sda8            1217        1824     4883697   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x72ff1c78

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       19130   153653692+   f  W95 Ext'd (LBA)
/dev/sdb2           19457       21888    19535040   82  Linux swap / Solaris
/dev/sdb3           21889       24320    19535040   83  Linux
/dev/sdb4   *       24321       26870    20482875    7  HPFS/NTFS
/dev/sdb5               2       19130   153653661    7  HPFS/NTFS

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0dcb3c60

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       15200   122093968+   7  HPFS/NTFS
/dev/sdc2           15201       30401   122102032+   7  HPFS/NTFS

Results of sudo update-grub  
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found linux image: /boot/vmlinuz-2.6.28-11-generic
Found initrd image: /boot/initrd.img-2.6.28-11-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /media/EXT: No such file or directory
ls: cannot access /media/EXT: No such file or directory
Found Ubuntu 9.04 (9.04) on /dev/sda1
Found Microsoft Windows XP Home Edition on /dev/sdb4
done

My search results recommended many solutions but I am unable to fix this. Can somebody please help in restoring my windows XP
Thanks
Sarayuvijay

---

### Post by Temposs on 2009-12-19
OK, I did a little research into how to do this, because I haven't done any editing of grub2 yet. But, here's what you should do. Open a terminal, and type:

```
sudo update-grub
```

This supposedly will automatically detect all the operating systems you have installed, including Windows. Then simply try restarting your computer, and see if Windows appears as an option in the Grub boot list :-)

Let me know how it goes.

---

### Post by Temposs on 2009-12-19
Oh, and to put you at ease, here's what it looks like when I run the update-grub command:

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
done
```

---

### Post by sarayuvijay on 2009-12-19
Thanks for the message Temposs. I have already tried all that and I have even posted the result of the Sudo-update grub which is basically the generated grub.cfg. Windows Xp was found in /dev/sd4 but the boot menu does not contain this option. During the course of my search I figured that a menu entry is missing and needs to be re instated. Not having the confidence to mess with Grub I have not attempted it. Would appreciate a 'how to re-configure Grub for dummies' to fix this.
thanks
Sarayuvijay

---

### Post by joes7 on 2009-12-19
Update grub. Open a new terminal and write:
```

update-grub

```

---

