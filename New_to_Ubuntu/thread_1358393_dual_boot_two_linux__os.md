---
title: "dual boot two linux  os"
date: 2009-12-18
forum: New to Ubuntu
---

### Post by manny43 on 2009-12-18
Hello friends

Can i dual boot two different distros of Linux?Ubuntu pre-installed and then adding maybe
simplymepis.No windows installed in hard drive only Ubuntu.I'm just worry that i'm going
to run into problems with GRUB.IF you have done this before maybe you couold help me
on how to dual boot both Linux os.Thanks.

---

### Post by tacantara on 2009-12-18
I have done dual-boots successfully with Ubuntu and Linux Mint, and Ubuntu and Fedora 12.  The only problem I had with GRUB was when I deleted the Mint partition to make room for another distro.  I had to use the Ubuntu Live CD to fix GRUB.  Otherwise, no problems with dual-booting.  Good luck :)

---

### Post by kansasnoob on 2009-12-18
I multi-boot a lot:

```
Model: ATA WDC WD1600AAJB-0 (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  22.0GB  22.0GB  primary   ntfs            boot
 3      22.0GB  31.0GB  8933MB  primary   ext3
 2      31.0GB  160GB   129GB   extended
 5      31.0GB  39.5GB  8521MB  logical   ext3
 6      39.5GB  76.4GB  36.9GB  logical   ext3
 7      76.4GB  84.7GB  8365MB  logical   ext3
 8      84.7GB  100GB   15.7GB  logical   ext3
13      100GB   107GB   6835MB  logical   ext4
14      107GB   122GB   15.1GB  logical   ext4
 9      122GB   124GB   1258MB  logical   linux-swap(v1)
10      124GB   141GB   17.0GB  logical   ext3
11      141GB   147GB   6309MB  logical   ext3
12      147GB   160GB   13.1GB  logical   ext3

```

Currently Win XP, Ubuntu 10.04, 9.10 & 9.04, and Mint 7 & 8.

But I have had Mepis in the mix, however I've not tried adding it to grub2 as yet.

Anyway the bootloader has been the major hitch with any distro I've tried. In the case of Mepis I simply chose not to install it's bootloader:

[ATTACH]140430[/ATTACH]

I then added Mepis to Ubuntu's legacy grub. Since Mepis is Debian based I'd bet there's a good chance grub2 would pick it up with a simple "sudo update-grub" but I can't be sure.

Anyway the major catch is almost always with the bootloader so I'd do some pre-planning regarding that.

As far as adding most OS's to an existing legacy grub I generally find this type of syntax works best:

title Ubuntu 9.10, kernel 2.6.31-11-generic (on /dev/sda3)
root (hd0,2)
kernel /boot/vmlinuz-2.6.31-11-generic root=UUID=d3d589c9-29e6-463e-9c99-806ec3646dea ro quiet splash
initrd /boot/initrd.img-2.6.31-11-generic
savedefault
boot

title Ubuntu 9.10, kernel 2.6.31-11-generic (recovery mode) (on /dev/sda3)
root (hd0,2)
kernel /boot/vmlinuz-2.6.31-11-generic root=UUID=d3d589c9-29e6-463e-9c99-806ec3646dea ro single
initrd /boot/initrd.img-2.6.31-11-generic
savedefault
boot

Rather than this:

&#65279;title Ubuntu karmic (development branch), kernel 2.6.31-11-generic
uuid d3d589c9-29e6-463e-9c99-806ec3646dea
kernel /boot/vmlinuz-2.6.31-11-generic root=UUID=d3d589c9-29e6-463e-9c99-806ec3646dea ro quiet splash
initrd /boot/initrd.img-2.6.31-11-generic

title Ubuntu karmic (development branch), kernel 2.6.31-11-generic (recovery mode)
uuid d3d589c9-29e6-463e-9c99-806ec3646dea
kernel /boot/vmlinuz-2.6.31-11-generic root=UUID=d3d589c9-29e6-463e-9c99-806ec3646dea ro single
initrd /boot/initrd.img-2.6.31-11-generic 

Of course the titles would be different as would the actual locations (ie: sda3 (hd0,2)) and of course the UUID's. It's all great fun to me :lolflag:

---

### Post by gorgon on 2009-12-18
which version of grub are you running? If you have installed 9.10 karmic from scratch you got grub2.

if you do have grub2, this has actually gotten a lot easier and should just be a matter of running 'sudo update-grub' in a terminal of your ubuntu installation after installing the other linux distro. Or, if the new linux distro overwrites grub so that you cannot see your ubuntu from grub, run 'sudo update-grub' from the new distro --- hoping that it also has grub2 :)

what update-grub does is to look for other os'es and adds them to the grub menu.

I have recently done this and its very smooth.

---

### Post by coffeecat on 2009-12-18
Most Linux distros are good at detecting another Linux installation and setting up the grub menu so that you can boot into either (or all, if you have more than two). From memory, Ubuntu, Mint (which is based on Ubuntu), Mepis, Mandriva and openSUSE you can rely on. Although you don't mention Fedora, the big exception is Fedora. It will detect Windows and set up a dual-boot Windows and Fedora menu, but it completely ignores other pre-installed Linux distros.

So if you want to include Fedora in your dual-boot, either install Fedora first, or you'll have to learn how to edit the grub menu. :wink: Which adds another complication: since Karmic, Ubuntu is using grub 2 whereas most other distros are still using legacy grub and the process for modifying the grub menu is different.

Good luck with your dual-booting!

---

### Post by jerrrys on 2009-12-18
i have three different versions loaded on a just ubuntu machine.  quirk is file transfer between ext3 and 4 at times can be a problem...

---

### Post by manny43 on 2009-12-18
Thank you very much.GREAT HELP

---

### Post by manny43 on 2009-12-18
Thank you very very much

---

### Post by joes7 on 2009-12-18
Yes. You can also use Virtual Box to run another one from one of the two OS's

---

