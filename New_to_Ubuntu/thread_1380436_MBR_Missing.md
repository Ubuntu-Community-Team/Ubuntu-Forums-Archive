---
title: "MBR Missing"
date: 2010-01-13
forum: New to Ubuntu
---

### Post by cocs on 2010-01-13
Hi everybody,
first of all I'm sorry to post this issue again but I didn't find any post with a situation like mine.
I have a HP xw8200 workstation with three hard drives one on the SCSI controller, one on the SATA controller and, of course, one on the IDE controller.
fdisk -l says:

Disk /dev/sda: 163.9 GB, 163928604672 bytes **/* this one is on SATA*/**
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x184102b9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19178   154047253+  83  Linux
/dev/sda2           19179       19929     6032407+   5  Extended
/dev/sda5           19179       19929     6032376   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes  **/* this one is on IDE*/**
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4bbf3771

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdc: 73.4 GB, 73407865856 bytes  **/* this one is on SCSI*/**
255 heads, 63 sectors/track, 8924 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xec88ec88

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        8924    71681998+   7  HPFS/NTFS

I've installed ubunto on IDE /dev/sda [hd0] and windows on SATA /dev/sdc [hd2]

Grub is installed, of course, on (hd0,0)

Now, I can (or, better, must) choose in the system BIOS which controller must start first.
If I choose SATA: grub starts but if I select Windows I get the message [B]MBR is missing
[/B]If I choose IDE windows (XP 64 Professional) starts.

I've also tried to setup grub on (hd2) and in this case the error I get is [B]"*error 13*:Invalid or unsupported executable file type"
______________________________
[/B]my menu.lst:

title Ubuntu 9.04, kernel 2.6.28-17-generic
kernel /boot/vmlinuz-2.6.28-17-generic root=UUID=a9d1bb4b-74e0-45f0-83b1-e8ce736a017e ro quiet splash
initrd /boot/initrd.img-2.6.28-17-generic

title Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode)
kernel /boot/vmlinuz-2.6.28-17-generic root=UUID=a9d1bb4b-74e0-45f0-83b1-e8ce736a017e ro  single
initrd /boot/initrd.img-2.6.28-17-generic

title Ubuntu 9.04, kernel 2.6.28-11-generic
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=a9d1bb4b-74e0-45f0-83b1-e8ce736a017e ro quiet splash
initrd /boot/initrd.img-2.6.28-11-generic

title Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=a9d1bb4b-74e0-45f0-83b1-e8ce736a017e ro  single
initrd /boot/initrd.img-2.6.28-11-generic

title Ubuntu 9.04, memtest86+
kernel /boot/memtest86+.bin

title windows XP 64bit
root (hd2,0)
map (hd2) (hd0)
map (hd0) (hd2)
chainloader +1
makeactive
_________________________________________ also tried without map

my results file of boot_info is attached.

Thanks a lot!!!

 Massimiliano

---

### Post by JDShu on 2010-01-13
I believe that its because grub is not locating the kernel images because the boot loader is not mounting the ubuntu partitions. I think adding "root (hd0, 0)" under "title Ubuntu 9.04, kernel 2.6.28-17-generic" in your menu.lst should solve the problem.

---

### Post by cocs on 2010-01-14
Thanks, I'm going to test it tonight. Do you think I have to change the setup of grub on (hd2,0) as well? And which controlle must I start first? Now I have IDE (because, if I set SCSI, windows starts bypassing grup).
Thanks again 
 Massimiliano

---

### Post by oldfred on 2010-01-14
Sometimes root works but rootnoverify seems to work better.

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title        Microsoft Windows XP Professional
rootnoverify    (hd2,0)
savedefault
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader    +1

Also you should not get a MBR error chainbooting to windows as grub has bypassed the MBR and jumps to windows PBR just like window MBR code does. Are you sure the drive order is still sdc with windows when you boot Ubuntu. I would think it should work with the map commands especially since the windows boots on its own.

Does you BIOS let you totally control drive order or is it fixed and you just control which drive boots. On my 3 SATA drives they do not change but I actually boot from sdc.  Usually IDE drives end up first. I have seen where IDE drives set to slave will boot windows but not Ubuntu. How is your IDE connected. Old 40 wire with jumpers on drive or newer 80 wire - 3 color connectors and with drive set as cable select?

---

### Post by oldfred on 2010-01-14
Just to agree with jdshu this is my old entry for booting from sdb1.
Remember old grub count partitions from 0.

title        Ubuntu 9.04, kernel 2.6.28-15-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=f9b2a783-78ba-4437-9bc5-9d8cfa86ff0c ro splash quiet 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

---

### Post by JDShu on 2010-01-14
> **cocs said:**
> Thanks, I'm going to test it tonight. Do you think I have to change the setup of grub on (hd2,0) as well? And which controlle must I start first? Now I have IDE (because, if I set SCSI, windows starts bypassing grup).
Thanks again 
 Massimiliano

Your bootloader (grub) is on your SATA drive, so boot that.

---

### Post by cocs on 2010-01-18
Thanks everybody.
It doesn't work :(
My bios let me choose only the controller order and then the order of devices but considering only the first HD. So I can choose from SATA, SCSC or IDE and then I can select "Disc C:" :shock: , USB, CD-ROM, NETWORK.

I've tried to run boot info in different situation (using super grub disk, as well) and my IDE is always sdc....

Any other ideas?
Any test I can do to give you another clue?
Thanks again
Massimiliano

---

### Post by oldfred on 2010-01-18
There should be two places to choose. One for type of device and another for which hard drive if hard drive is the choice. I think on my BIOS it was even a different screen in the BIOS.

---

