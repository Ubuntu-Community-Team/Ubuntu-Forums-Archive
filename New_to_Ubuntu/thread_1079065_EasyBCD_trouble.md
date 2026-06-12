---
title: "EasyBCD trouble"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by hdjunkie on 2009-02-24
Ok, so I installed linux and then windows 7 on top of that. I followed the guide located at:
[http://apcmag.com/how_to_dualboot_vi...led.htm?page=1]("http://apcmag.com/how_to_dualboot_vi...led.htm?page=1")
pretty much exactly. The only thing that was different was I couldn't set the unpartitioned space to "active" in the command prompt, but win7 installed perfectly fine on the unpartitioned space anyways.
The linux partitions are still there, and I backed up the menu.lst file and restored it according to the guide.
I thought everything was fine until I went to boot linux using NeoGrub Bootloader and I received an error:
Windows has failed to start. A recent hardware or software change might be the cause. To fix the problem:

1. Insert your Windows installation disc and restart your computer.
2. Choose your language settings, and then click "Next."
3. Click "Repair your computer."

If you do not have this disc, contact your system administrator or computer manufacturer.

File: /MST/NeoGrub.mbr
Status: 0xc000000f
Info: The selected entry could not be loaded because the application is missing or corrupt.

Here is the text copied from the linux install to the menu.lst file in easybcd

title Ubuntu 8.10, kernel 2.6.27-7-generic
uuid 4780965d-b3ac-4266-a287-2fbb8c456b8e
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=4780965d-b3ac-4266-a287-2fbb8c456b8e ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic
quiet

title Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid 4780965d-b3ac-4266-a287-2fbb8c456b8e
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=4780965d-b3ac-4266-a287-2fbb8c456b8e ro single
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, memtest86+
uuid 4780965d-b3ac-4266-a287-2fbb8c456b8e
kernel /boot/memtest86+.bin
quiet


Any help/suggestions would be greatly appreciated.

---

### Post by bumanie on 2009-02-24
Please post the output of > sudo fdisk -lu This can be done from within ubuntu or off a live ubuntu cd

---

### Post by hdjunkie on 2009-02-24
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7cd17c0c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    51199154    25599546   83  Linux
/dev/sda2   *    51200000    51609599      204800    7  HPFS/NTFS
/dev/sda3        51609600   300849151   124619776    7  HPFS/NTFS
/dev/sda4       300849255   312576704     5863725    5  Extended
/dev/sda5       300849318   312576704     5863693+  82  Linux swap / Solaris
ubuntu@ubuntu:~$



Thanks

---

### Post by hdjunkie on 2009-02-24
I gave up and let grub take over, and edited the menu.lst file to make windows 7 the default option.  It works great!

---

