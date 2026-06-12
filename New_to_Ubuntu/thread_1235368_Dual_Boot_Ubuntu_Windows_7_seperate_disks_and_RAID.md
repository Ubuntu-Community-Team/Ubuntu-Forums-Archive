---
title: "Dual Boot Ubuntu Windows 7 seperate disks and RAID 0"
date: 2009-08-09
forum: New to Ubuntu
---

### Post by derNome on 2009-08-09
Having spent a good chunk of this afternoon digging around for a solution to my dual boot woes I have been unable to find a clear solution for my problem. This is my first stab at linux.


If this question has already been answered I'm sorry for not seeing it.

Setup:

On 2 x250 GB hdd's in  RAID0  I have installed Windows 7.

On the single 150 GB drive I have installed Ubuntu.

I have seen how to point GRUB at the separate hard disks, however Grub gives me a "Partition Table Invalid" when I have tried searching for the partition type using root (hdX,Y).
 

 I tried to force my bios to boot from the hard disks with Windows on them but I get a GRUB error 21.
 

 I don't know where to go from here. Any help would be greatly appreciated.

---

### Post by gabry79Italy on 2009-08-09
please post
sudo fdisk -l
cat /boot/grub/menu.lst

---

### Post by derNome on 2009-08-09
> **gabry79Italy said:**
> please post
sudo fdisk -l
cat /boot/grub/menu.lst
title        Ubuntu 9.04, kernel 2.6.28-14-generic
uuid        159f22ab-904d-4762-a357-9f0e599d641c
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=159f22ab-904d-4762-a357-9f0e599d641c ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid        159f22ab-904d-4762-a357-9f0e599d641c
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=159f22ab-904d-4762-a357-9f0e599d641c ro  single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        159f22ab-904d-4762-a357-9f0e599d641c
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=159f22ab-904d-4762-a357-9f0e599d641c ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        159f22ab-904d-4762-a357-9f0e599d641c
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=159f22ab-904d-4762-a357-9f0e599d641c ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        159f22ab-904d-4762-a357-9f0e599d641c
kernel        /boot/memtest86+.bin
quiet

This is without the commented section.

---

### Post by gabry79Italy on 2009-08-10
Please post 
sudo fdisk -l

---

