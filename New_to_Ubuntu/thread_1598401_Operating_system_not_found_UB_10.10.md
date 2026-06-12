---
title: "Operating system not found UB 10.10"
date: 2010-10-16
forum: New to Ubuntu
---

### Post by mlpfw on 2010-10-16
Hello everybody

I'm new to this forum and would appreciate any help I could get.
My computer is HP Pavillion dv5000  Intel Centino Duo with 2g of internal memory.
I have UB installed on a 3g usb thumb drive and it is working perfectly ok. My problem is that the space is limited and I could not add more applications to it hence I decided to install UB on a 30g USB drive.  I've downloaded UB 10.10 ISO and created a bootable CD.  I have installed UB on the new 30g USB drive more than 5 times and after every install and boot attempt, I get "Operating System not found" error. 

Currently, I have the internal SATA HD removed from the laptop to avoid over writing my Windows OS installed in it as a precaution. 

I've searched this forum looking for a method to resolve this problem and have tried some of the recommendations I found but still unable to get it resolved.

Any suggestion(s) would be very highly appreciated

Best Regards

---

### Post by mlpfw on 2010-10-16
BTW I'm currently posting this message using UB on my flash drive. I am not a computer newbie and can follow instructions very well.

Best Regards

---

### Post by rockerphil on 2010-10-16
the first thing that comes to mind is that you may need to have the internal SATA drive connected when you install in order for Ubuntu to install Grub to the MBR properly which is required for a proper dual boot which is what i'm guessing you're trying to achieve. just a thought. hope this helps,

Phil

---

### Post by mlpfw on 2010-10-16
Phil

Thanks for your prompt response.  I was able to install and run UB  with the HD removed on a USB flash drive. That is what I'm using now without  the internal HD. I just reinstalled the internal SATA HD  and reinstalled UB 10.10 and still get the same message when trying to boot from the USB HD.

Best Regards

mlpfw

---

### Post by Quackers on 2010-10-16
What device is your bios set to boot from (first, second etc)?

---

### Post by mlpfw on 2010-10-16
cd
usb
Internal HD is disabled through BIOS


It finds and boot from the USB flash drive ok. When I take it out and attempt to boot on the newly installed USB HD, I get the error message

Best regards

BTW, if I put the CD in, it will boot from it also.

---

### Post by Quackers on 2010-10-16
May I suggest that you try booting with ONLY the usb HDD connected (no internal HDD and no usb thumb). Do you get the same message?
I would then suggest that you boot from the 10.10 cd and then go to the site below and download the file to your desktop then run the command as shown. This will create a Results.txt file on your desktop. If you will copy the contents of the file and paste them into your next post using code tags (click on # in New Reply) it will give a clearer idea of what is where.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Quackers on 2010-10-16
In my bios boot options I have 3 usb choices
USB optical drive
USB flash
USB drive
Is your similar? For instance if it is set to USB flash it won't boot from USB hard drive unless that is enabled.

---

### Post by mlpfw on 2010-10-16
Boot Order:
1. USB Hard Drive
2. ATAPI cd/dvd rom drive
3. Notebook hard drive
4. USB diskette on key
5. USB floppy
!6. Network adapter

---

### Post by mlpfw on 2010-10-16
```

```                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders, total 58605120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    56,094,719    56,092,672  83 Linux
/dev/sda2          56,096,766    58,603,519     2,506,754   5 Extended
/dev/sda5          56,096,768    58,603,519     2,506,752  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        d5f059de-26cb-4274-9bc5-7e73a44c4229   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        b1c65945-02f3-433b-9dbc-b017217563df   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set d5f059de-26cb-4274-9bc5-7e73a44c4229
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set d5f059de-26cb-4274-9bc5-7e73a44c4229
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set d5f059de-26cb-4274-9bc5-7e73a44c4229
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=d5f059de-26cb-4274-9bc5-7e73a44c4229 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set d5f059de-26cb-4274-9bc5-7e73a44c4229
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=d5f059de-26cb-4274-9bc5-7e73a44c4229 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set d5f059de-26cb-4274-9bc5-7e73a44c4229
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set d5f059de-26cb-4274-9bc5-7e73a44c4229
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=d5f059de-26cb-4274-9bc5-7e73a44c4229 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b1c65945-02f3-433b-9dbc-b017217563df none            swap    sw              0       0
/dev/sda        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  17.5GB: boot/grub/core.img
   8.7GB: boot/grub/grub.cfg
    .8GB: boot/initrd.img-2.6.35-22-generic
  17.5GB: boot/vmlinuz-2.6.35-22-generic
    .8GB: initrd.img
  17.5GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  4b 4f 1d 23 f2 c0 f8 cc  21 a2 c3 89 dc 81 6c 86  |KO.#....!.....l.|
00000010  41 31 07 e3 49 f5 9d d6  99 02 3c 8c e6 80 6d 25  |A1..I.....<...m%|
00000020  85 00 71 3f 55 b6 a0 66  70 e9 3c e3 02 b4 19 d1  |..q?U..fp.<.....|
00000030  c7 11 a5 28 80 a2 2c 1a  30 06 a0 03 08 26 dd ba  |...(..,.0....&..|
00000040  76 e9 82 85 4b 78 d8 98  75 ba 14 28 68 f0 b8 e9  |v...Kx..u..(h...|
00000050  96 af 04 22 26 0d 06 00  01 b6 44 c9 13 08 b3 0f  |..."&.....D.....|
00000060  9c 66 5e 22 56 43 1c 4e  79 fa 76 7c 83 07 72 04  |.f^"VC.Ny.v|..r.|
00000070  8d 6e 8d 1b 24 7f c9 4e  a4 96 01 dc 57 0d 18 6a  |.n..$..N....W..j|
00000080  42 c8 30 0c f4 c3 6d 99  b1 43 45 c4 77 0e a7 41  |B.0...m..CE.w..A|
00000090  c3 03 fd 1e 65 61 82 fd  5b d0 b1 82 c9 0e 8a cd  |....ea..[.......|
000000a0  4a 9b 30 10 b7 67 b1 98  52 a4 08 90 fb 81 f2 7d  |J.0..g..R......}|
000000b0  1c 6c 4e 27 5b 5b 84 88  f4 2f 47 4c 48 0a 71 fa  |.lN'[[.../GLH.q.|
000000c0  00 ad 09 2c 31 28 59 c2  e2 f2 7b c0 07 fb 86 a1  |...,1(Y...{.....|
000000d0  27 f0 81 71 35 a1 b7 43  58 19 c2 03 03 00 c0 62  |'..q5..CX......b|
000000e0  1e 21 10 91 d0 80 99 05  39 eb 00 ee 44 00 00 01  |.!......9...D...|
000000f0  07 32 c8 bb b0 8b 3a d8  a4 e6 f2 00 1f 80 37 49  |.2....:.......7I|
00000100  2c 03 10 18 86 92 c9 21  a7 0e 3e 67 02 7b 87 40  |,......!..>g.{.@|
00000110  26 2c 04 c4 d0 32 34 ec  c7 50 0d c0 76 4c cc 57  |&,...24..P..vL.W|
00000120  29 a9 0c 04 08 03 2d 90  e4 ce 18 78 a8 ef 00 cb  |).....-....x....|
00000130  4b 30 80 f7 da 6b 66 12  46 8c b3 c7 8e 88 f1 e3  |K0...kf.F.......|
00000140  a2 c0 65 a0 63 00 1b 6d  81 be 1f 7f 80 fe 1f 16  |..e.c..m........|
00000150  03 2b f6 dd b2 40 57 dc  f6 97 f8 ed 00 47 6d c0  |.+...@W......Gm.|
00000160  7b 56 cc 64 ad 18 9c bb  38 dd 37 98 d7 69 60 34  |{V.d....8.7..i`4|
00000170  20 55 b2 1b 32 68 39 72  14 3a 28 63 c0 c6 00 31  | U..2h9r.:(c...1|
00000180  d6 db 31 0b de bc 82 57  12 15 4b 15 61 61 6d 76  |..1....W..K.aamv|
00000190  cc 36 a9 18 77 31 62 1b  48 6f 80 dc e1 54 71 f2  |.6..w1b.Ho...Tq.|
000001a0  b3 81 18 9e 4f 20 5b 20  92 b4 0d 1e 24 4c 85 75  |....O [ ....$L.u|
000001b0  b4 d2 9a dd aa 2d 0b 1f  38 a9 51 f3 83 08 00 fe  |.....-..8.Q.....|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 40 26 00 00 00  |...........@&...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by mlpfw on 2010-10-16
Above you will find information as requested

Best Regards

mlpfw

---

### Post by Quackers on 2010-10-16
It's actually 2-20am here so that's the excuses out of the way :-)
I have looked at your boot script and I can't see anything out of place or missing at all. It is entirely possible that I have missed something, but if I have I cant' see it.
Hopefully somebody more experienced than me will come along and offer suggestions.
I'm sorry I can't offer better news.

---

### Post by mlpfw on 2010-10-16
Thanks for all your help and have a wonderful evening/night.

Best regards

mlpfw

---

### Post by mlpfw on 2010-10-17
Any takers? Would appreciate any help I could get.

Thanks in advance  for your help.

Best Regards
mlpfw

---

### Post by mlpfw on 2010-10-18
Could anybody out there help me plz. Need to get this going as I've ran out of space on my flash drive.

Best Regards

MLPFW

---

### Post by mrnelson1986 on 2010-10-18
> **mlpfw said:**
> Could anybody out there help me plz. Need to get this going as I've ran out of space on my flash drive.

Best Regards

MLPFW

I literally just achieved this (installing Ubuntu on a USB thumb drive (16 GB)).  I tried a couple of times and it didn't work, same as you.  Are you making sure that you install the boot loader to the thumb drive? If you don't, you will always have errors of "no OS."  During install, advanced partition setup, at the bottom of the menu there is a choice of where to install the bootloader, make sure you are choosing the same USB thumb drive that you want the OS installed on.  I didn't notice this dropdown box the first couple of times.

I also had the same problem creating my bootable live USB drive (I don't like to use the live CD, so I use unetbootin to create a bootable usb live drive) and the linux version of the program was having issues, so I tried out the Universal USB installer that Ubuntu links to on its website using my windows 7 partition [http://www.pendrivelinux.com/downloads/Universal-USB-Installer/Universal-USB-Installer.exe](http://www.pendrivelinux.com/downloads/Universal-USB-Installer/Universal-USB-Installer.exe)
and it worked for creating the bootable media correctly.  using unetbootin it would work as a live usb drive but it would forget to install the capability to install grub during a real install.

---

### Post by mlpfw on 2010-10-18
Thanks for th information. My problem is not installing UB to a thumb drive but USB Hard Drive.

I'm currently running UB off my 3G thumb drive but I'm beginning to run out of space hence my attempt to use a 30G USB hard-drive I have laying around.  I would hate to go purchase a larger capacity of a thumb drive if I could install and run UB off an external USB hard-drive.

Best Regards

---

### Post by mrnelson1986 on 2010-10-18
> **mlpfw said:**
> Thanks for th information. My problem is not installing UB to a thumb drive but USB Hard Drive.

I'm currently running UB off my 3G thumb drive but I'm beginning to run out of space hence my attempt to use a 30G USB hard-drive I have laying around.  I would hate to go purchase a larger capacity of a thumb drive if I could install and run UB off an external USB hard-drive.

Best Regards

I understand, but a USB device is a USB device, the same process should follow.  Also, I found this: [http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html](http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html)
maybe it will help you?

---

### Post by Quackers on 2010-10-18
mlpfw, I've just had a look in my bios settings and I see that the option to boot from USB hard drive has a * next to it. This means that it is not enabled by default and must be enabled manually. Yours wouldn't be the same would it?

---

### Post by mlpfw on 2010-10-20
Thanks everybody for your help. I solved the problem.  This is what I did. I have another 120G external USB HD  so I removed the SATA USB adapter from it and  used it on the 30G and bingo!!!!, it booted into UB without any problems. Please note that what I swapped was the adapter and not the cable. 

Again, thanks each and every one of you for the help rendered. 

Best Regards

Mlpfw.

---

