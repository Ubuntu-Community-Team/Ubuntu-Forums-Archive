---
title: "grub not working"
date: 2010-09-26
forum: New to Ubuntu
---

### Post by flink.robbie on 2010-09-26
I am currently not at my house, im on a business trip and i need a fast solution before my presentation tomorrow. My grub has decided to stop working, and every time i try booting my computer it gives me the following message:

error: no such partition
grub rescue>

I need a way to fix this within the next two hours if possible. I didn't try deleting anything, but i think the partition may have just gone away

---

### Post by readycarpenter on 2010-09-26
what is the exact grub error you get when booting? what version of ubuntu are you running?

---

### Post by Rubi1200 on 2010-09-26
> I need a way to fix this within the next two hours if possible.How do you expect to achieve this if you are not near the computer?

> I didn't try deleting anything, but i think the partition may have just gone away     Partitions do not just disappear! Human action usually causes such things.

> I didn't try deleting anything
So what did you try?

1. you need to be more specific about what is going on including other operating systems you may have installed, Ubuntu version (as asked above) and so on.

2. if there is someone whom you trust to access the computer for you, they need to be able to do certain things that will give us the information we need to help you fix this.

To that effect, please ask someone to run and then post the results of the bootsscript linked to at the bottom of my post.

Thanks in advance.

---

### Post by inestler on 2010-09-26
I just got the same error message after installing 10.04 from USB stick on Win7 eeePC,

Maybe a problem  with the boot booster

root@asus:~# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done


root@asus:~# fdisk -l

Disk /dev/sda: 32.0 GB, 32017047552 bytes
255 heads, 63 sectors/track, 3892 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcb5bd2b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3890    31245312    7  HPFS/NTFS
/dev/sda2            3890        3892       16154   ef  EFI (FAT-12/16/32)

Disk /dev/sdb: 31.9 GB, 31914983424 bytes
255 heads, 63 sectors/track, 3880 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002ac5b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3391    27230840+   c  W95 FAT32 (LBA)
/dev/sdb2            3391        3881     3931137    5  Extended
/dev/sdb5            3391        3852     3701760   83  Linux
/dev/sdb6            3852        3881      228352   82  Linux swap / Solaris

---

### Post by jtarin on 2010-09-26
> **inestler said:**
> I just got the same error message after installing 10.04 from USB stick on Win7 eeePC,

Maybe a problem  with the _**boot booster**_

Yes no doubt the second-stage.Huh? :P

> Device Boot Start End Blocks Id System
/dev/sdb1 1 3391 27230840+ c W95 FAT32 (LBA)What do you have here at this partition?

---

### Post by inestler on 2010-09-27
[/QUOTE] What do you have here at this partition? [/QUOTE]
 
Disk /dev/sb1 is a fast SDHC drive that was formatted FAT-32 . The ubuntu installation choose this disk.

---

