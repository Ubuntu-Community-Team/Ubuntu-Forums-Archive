---
title: "Grub Error 22"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by SBFree on 2009-02-12
I installed Ubuntu 8.04 in the unpartioned space on a drive with WinXP. I get a grub menu offering to boot Ubuntu but it generates error 22. WinXP doesn't boot either. I used the live cd to look at /boot/grub/menu.lst & the terminal to look at my devices. They appear as:

--------------------------------------------------------------------------------
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80032038912 bytes
255 heads, 63 sectors/track, 9730 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x408549ed

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9729    78148161    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80032038912 bytes
255 heads, 63 sectors/track, 9730 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x408549ed

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9729    78148161    7  HPFS/NTFS

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4ec64ec6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        2611    20972826    7  HPFS/NTFS
/dev/sdc2            2612        9729    57175335    f  W95 Ext'd (LBA)
/dev/sdc5            2612        4421    14538793+   7  HPFS/NTFS
/dev/sdc6            4422        9506    40845231   83  Linux
/dev/sdc7            9507        9729     1791216   82  Linux swap / Solaris

Disk /dev/sdd: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4f064f06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       14593   117218241    7  HPFS/NTFS
ubuntu@ubuntu:~$

## ## End Default Options ##

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic
root        (hd2,5)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=37d5f7e2-fa8d-4722-b0b2-e68b88772e69 ro quiet splash
initrd        /boot/initrd.img-2.6.24-19-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root        (hd2,5)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=37d5f7e2-fa8d-4722-b0b2-e68b88772e69 ro single
initrd        /boot/initrd.img-2.6.24-19-generic

title        Ubuntu 8.04.1, memtest86+
root        (hd2,5)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title        Microsoft Windows XP Professional
root        (hd2,0)
savedefault
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader    +1

----------------------------------------------

/dev/sda & /dev/sdb are a pair of drive in a raid array

/dev/sdc1 is (was) my WinXP boot partion

Any suggestions on how to get either or both partions to boot?

Thanks.
Scott

---

### Post by roshanjose on 2009-02-12
resinstall the grub by placing the cd and selecting the install grub option

---

### Post by caljohnsmith on 2009-02-12
In order to get a clearer picture of your setup, how about booting your Ubuntu Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to the Live CD desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the best solution to your booting problem might be.

---

