---
title: "Ubuntu will not boot"
date: 2011-03-24
forum: New to Ubuntu
---

### Post by deckerry on 2011-03-24
_Problem Background_:
I tried to install Ubuntu on my laptop. It seemed to work the first couple times. Now it won't work. The error message is below but first I will give more information.

My computer has always been running Windows Vista. I just heard of Ubuntu and it seems very fascinating so I figured I would try it.

First I went to ubuntu.com, clicked the "download ubuntu" link and followed the 4 steps listed on that page. Step 1: I downloaded the 32-bit Ubuntu 10.10 the filename is ubuntu-10.10-desktop-i386. I also downloaded wubi for some reason but I don't remember when or why.

Step 2: Since my disc drive is completely broken and non-functional, I created a usb drive to get Ubuntu started. I used the universal usb installer the filename for that program is Universal-USB-Installer-1.8.3.7.

Step 3: I restarted my computer with the usb as the first in the boot order. I chose the first option in that menu which I think just ran Ubuntu from the usb drive. I ran the installation after enabling a wireless internet connection and restarted the computer.

I removed the usb drive and Ubuntu started and had me login my username and password. I tried to connect to the internet but couldn't figure it out so I restarted the computer.

_The problem._
Now here's the problem. This time Ubuntu didn't work. I get an error message and this is what I see on the screen...


```
Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
 - Check rootdelay= (did the system wait long enough?)
 - Check root= (did the system wait for the right device?)
- Missing modules (cat/proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/0696b9a1-0116-4dd8-bee6-9156394da148 does not exist. Dropping to a shell!
 
Busybox v1.15.3 (Ubuntu1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-in commands.
 
(initramfs) _
```

I know very, very, very little about linux or computers in general but I am very very willing to learn.

Does anybody know what to do?

---

### Post by Hippytaff on 2011-03-24
Hi and welcome to the forums

What graphics card do you have? and can you boot from that usb again and choose [COLOR=Red]try[/COLOR] rather than install? if so post the results.txt genereated by downloading and running [this script]("http://sourceforge.net/projects/bootinfoscript/") whilst in the ubuntu usb live environment

If that usb doesn't let you [COLOR=Red]try[/COLOR] ubuntu then the iso is probably corrupt...if so then download another one :-)

---

### Post by deconstrained on 2011-03-24
You should try using the "USB Startup Disk Creator" instead. Booting from USB requires special hooks/modules and a filesystem that Linux can use; FAT32, a common FS on USB sticks, just doesn't cut it, and NTFS support is still a bit glitchy for use as root. The startup disk creator takes care of all of this, and should be available to you if you install it (if it isn't already available) while booted to the CD (the package will be copied to and unpacked in memory). You may, however, need another external drive to store the ISO to use for creating the startup disk.

---

### Post by deckerry on 2011-03-24
> **Hippytaff said:**
> Hi and welcome to the forums

What graphics card do you have? and can you boot from that usb again and choose [COLOR=Red]try[/COLOR] rather than install? if so post the results.txt genereated by downloading and running [this script]("http://sourceforge.net/projects/bootinfoscript/") whilst in the ubuntu usb live environment

If that usb doesn't let you [COLOR=Red]try[/COLOR] ubuntu then the iso is probably corrupt...if so then download another one :-)
Wow that was a really quick response thanks.

I don't know which graphics card I have. I think it's [COLOR=Red]nvidia[/COLOR]. I hope that answers that question.

I think I figured out how to post the [COLOR=Red]results.txt[/COLOR] as an attachment but it seems to be too large.
It is 21.5 and it seems that the limit is 19.5.

---

### Post by deckerry on 2011-03-24
> **deconstrained said:**
> You should try using the "USB Startup Disk Creator" instead. Booting from USB requires special hooks/modules and a filesystem that Linux can use; FAT32, a common FS on USB sticks, just doesn't cut it, and NTFS support is still a bit glitchy for use as root. The startup disk creator takes care of all of this, and should be available to you if you install it (if it isn't already available) while booted to the CD (the package will be copied to and unpacked in memory). You may, however, need another external drive to store the ISO to use for creating the startup disk.
Thanks a lot for the tip. I am going to try _Hippytaff_'s advice first. If that doesn't work, I'll try yours next.

---

### Post by Hippytaff on 2011-03-24
> **deckerry said:**
> Thanks a lot for the tip. I am going to try _Hippytaff_'s advice first. If that doesn't work, I'll try yours next.

To post the results.txt file...click the New Reply icon (the grey one) paste the results.txt.  Then highlight the text you pasted and click the # icon at the top of  the window. That should put it in tags...and deconstrained probaly knows more that me :?

---

### Post by deckerry on 2011-03-24
I'm sorry, but do you delete a reply by the way? I know I can edit it but don't know how to delete it.

---

### Post by Hippytaff on 2011-03-24
> **deckerry said:**
> There's the results.txt.

```
 file:///home/ubuntu/Desktop/RESULTS.txt
```

The contents of that file is what  is useful :-D

---

### Post by deckerry on 2011-03-24
Ha ha ha! Wow. You're absolutely right.
Can you tell I'm a complete noob!

Thanks for being so patient.
I edited some of my posts if you want to take another look above.

---

### Post by Hippytaff on 2011-03-24
> **deckerry said:**
> Ha ha ha! Wow. You're absolutely right.
Can you tell I'm a complete noob!

Thanks for being so patient.
I edited some of my posts if you want to take another look above.

it's probably best if you post it again for the lazy people..like me

---

### Post by deckerry on 2011-03-24
Here are the results:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #7 for (,msdos7)/boot/grub.
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7856127 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             38     7,839,719     7,839,682   c W95 FAT32 (LBA)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   150,328,426   150,328,364   7 HPFS/NTFS
/dev/sdb2         216,781,110   234,436,544    17,655,435   7 HPFS/NTFS
/dev/sdb3         150,329,342   216,780,799    66,451,458   5 Extended
/dev/sdb5         183,619,584   215,298,047    31,678,464  83 Linux
/dev/sdb6         215,300,096   216,780,799     1,480,704  82 Linux swap / Solaris
/dev/sdb7         150,329,344   182,132,735    31,803,392  83 Linux
/dev/sdb8         182,134,784   183,607,295     1,472,512  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   234,436,544   234,436,482   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       0d8062ba-1bad-f948-bc58-4fd99ec0f0c9   ext2       casper-rw                     
/dev/sda1        16ED-345D                              vfat       PENDRIVE                      
/dev/sda: PTTYPE="dos" 
/dev/sdb1        EC8AF1E38AF1A9EA                       ntfs       OS                            
/dev/sdb2        2C88743C8874071C                       ntfs       HP_RECOVERY                   
/dev/sdb3: PTTYPE="dos" 
/dev/sdb5        f787b0b3-f28c-4b89-9e6b-086b5007e48f   ext4                                     
/dev/sdb6        32f1c54d-01d7-46c9-92c2-11ebf87de29d   swap                                     
/dev/sdb7        0696b9a1-0116-4dd8-bee6-9156394da148   ext4                                     
/dev/sdb8        29855466-8fa6-4477-8969-d5a93e68db6a   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        F248CE0448CDC815                       ntfs       DATA                          
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sda1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set f787b0b3-f28c-4b89-9e6b-086b5007e48f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set f787b0b3-f28c-4b89-9e6b-086b5007e48f
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
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set f787b0b3-f28c-4b89-9e6b-086b5007e48f
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=f787b0b3-f28c-4b89-9e6b-086b5007e48f ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set f787b0b3-f28c-4b89-9e6b-086b5007e48f
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=f787b0b3-f28c-4b89-9e6b-086b5007e48f ro single 
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
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set f787b0b3-f28c-4b89-9e6b-086b5007e48f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set f787b0b3-f28c-4b89-9e6b-086b5007e48f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 7c5e70b95e706db0
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sdb2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set 2c88743c8874071c
    chainloader +1
}
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

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=f787b0b3-f28c-4b89-9e6b-086b5007e48f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=32f1c54d-01d7-46c9-92c2-11ebf87de29d none            swap    sw              0       0

=================== sdb5: Location of files loaded by Grub: ===================


 103.4GB: boot/grub/core.img
  98.5GB: boot/grub/grub.cfg
  94.5GB: boot/initrd.img-2.6.35-22-generic
 103.4GB: boot/vmlinuz-2.6.35-22-generic
  94.5GB: initrd.img
 103.4GB: vmlinuz

=========================== sdb7/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos7)'
search --no-floppy --fs-uuid --set 0696b9a1-0116-4dd8-bee6-9156394da148
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos7)'
search --no-floppy --fs-uuid --set 0696b9a1-0116-4dd8-bee6-9156394da148
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
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set 0696b9a1-0116-4dd8-bee6-9156394da148
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=0696b9a1-0116-4dd8-bee6-9156394da148 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set 0696b9a1-0116-4dd8-bee6-9156394da148
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=0696b9a1-0116-4dd8-bee6-9156394da148 ro single 
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
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set 0696b9a1-0116-4dd8-bee6-9156394da148
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set 0696b9a1-0116-4dd8-bee6-9156394da148
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set ec8af1e38af1a9ea
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sdb2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set 2c88743c8874071c
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sdb5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set f787b0b3-f28c-4b89-9e6b-086b5007e48f
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=f787b0b3-f28c-4b89-9e6b-086b5007e48f ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sdb5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set f787b0b3-f28c-4b89-9e6b-086b5007e48f
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=f787b0b3-f28c-4b89-9e6b-086b5007e48f ro single
    initrd /boot/initrd.img-2.6.35-22-generic
}
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

=============================== sdb7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb7 during installation
UUID=0696b9a1-0116-4dd8-bee6-9156394da148 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb8 during installation
UUID=29855466-8fa6-4477-8969-d5a93e68db6a none            swap    sw              0       0

=================== sdb7: Location of files loaded by Grub: ===================


  81.7GB: boot/grub/core.img
  85.6GB: boot/grub/grub.cfg
  78.7GB: boot/initrd.img-2.6.35-22-generic
  81.7GB: boot/vmlinuz-2.6.35-22-generic
  78.7GB: initrd.img
  81.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 04 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 26 00 00 00  |........?...&...|
00000020  c2 9f 77 00 95 3b 00 00  00 00 00 00 02 00 00 00  |..w..;..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 5d 34 ed 16 4e  4f 20 4e 41 4d 45 20 20  |..)]4..NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 1e 56  8e c1 b1 26 bf 78 7b f3  |.v{R.W.V...&.x{.|
00000070  a5 8e d9 bb 78 00 0f b4  37 0f a0 56 20 d2 78 1b  |....x...7..V .x.|
00000080  31 c0 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |1....?.G..d....||
00000090  88 4d bc 50 50 50 50 cd  13 eb 5c 8b 55 aa 8b 75  |.M.PPPP...\.U..u|
000000a0  a8 c1 ee 04 01 f2 81 fa  b7 07 73 2b f6 45 b4 7f  |..........s+.E..|
000000b0  75 25 38 4d b8 74 20 66  3d 21 47 50 54 75 10 80  |u%8M.t f=!GPTu..|
000000c0  7d b8 ed 75 0a 66 ff 75  ec 66 ff 75 e8 eb 0f 51  |}..u.f.u.f.u...Q|
000000d0  51 66 ff 75 bc eb 07 51  51 66 ff 36 1c 7c b4 08  |Qf.u...QQf.6.|..|
000000e0  cd 13 72 13 20 e4 75 0f  c1 ea 08 42 89 16 1a 7c  |..r. .u....B...||
000000f0  83 e1 3f 89 0e 18 7c fb  bb aa 55 b4 41 8a 16 74  |..?...|...U.A..t|
00000100  7b cd 13 72 10 81 fb 55  aa 75 0a f6 c1 01 74 05  |{..r...U.u....t.|
00000110  c6 06 45 7d 00 66 b8 4e  77 00 00 66 ba 00 00 00  |..E}.f.Nw..f....|
00000120  00 bb 00 7e e8 10 00 66  81 3e 24 7e d4 ff 73 72  |...~...f.>$~..sr|
00000130  75 76 ea 38 7e 00 00 66  03 06 60 7b 66 13 16 64  |uv.8~..f..`{f..d|
00000140  7b b9 10 00 eb 2b 66 52  66 50 06 53 6a 01 6a 10  |{....+fRfP.Sj.j.|
00000150  89 e6 66 60 b4 42 e8 7f  00 66 61 8d 64 10 72 01  |..f`.B...fa.d.r.|
00000160  c3 66 60 31 c0 e8 70 00  66 61 e2 da c6 06 45 7d  |.f`1..p.fa....E}|
00000170  2b 66 60 66 0f b7 36 18  7c 66 0f b7 3e 1a 7c 66  |+f`f..6.|f..>.|f|
00000180  f7 f6 31 c9 87 ca 66 f7  f7 66 3d ff 03 00 00 77  |..1...f..f=....w|
00000190  17 c0 e4 06 41 08 e1 88  c5 88 d6 b8 01 02 e8 37  |....A..........7|
000001a0  00 66 61 72 01 c3 e2 c9  31 f6 8e d6 bc 68 7b 8e  |.far....1....h{.|
000001b0  de 66 8f 06 78 00 be df  7d e8 09 00 31 c0 cd 16  |.f..x...}...1...|
000001c0  cd 19 f4 eb fd 66 60 ac  20 c0 74 09 b4 0e bb 07  |.....f`. .t.....|
000001d0  00 cd 10 eb f2 66 61 c3  8a 16 74 7b cd 13 c3 42  |.....fa...t{...B|
000001e0  6f 6f 74 20 65 72 72 6f  72 0d 0a 00 00 00 00 00  |oot error.......|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb3

00000000  1d 2c 45 ff 1e 2c 43 ff  1e 2b 42 ff 19 27 43 ff  |.,E..,C..+B..'C.|
00000010  1d 2a 44 ff 1c 2c 44 ff  1c 2a 43 ff 19 28 43 ff  |.*D..,D..*C..(C.|
00000020  19 29 43 ff 17 27 43 ff  18 26 42 ff 18 25 42 ff  |.)C..'C..&B..%B.|
00000030  17 27 42 ff 18 25 40 ff  1a 28 3f ff 19 27 3f ff  |.'B..%@..(?..'?.|
00000040  19 28 40 ff 18 26 3e ff  19 27 3f ff 19 28 40 ff  |.(@..&>..'?..(@.|
00000050  19 28 40 ff 1a 28 3e ff  1a 28 3f ff 1c 29 3e ff  |.(@..(>..(?..)>.|
00000060  1b 27 3f ff 1a 28 3f ff  1f 2f 43 ff 1f 24 2c ff  |.'?..(?../C..$,.|
00000070  ae b9 c1 ff af b9 c2 ff  af b9 c1 ff b0 ba c2 ff  |................|
00000080  af ba c2 ff b0 ba c2 ff  b0 bb c3 ff a6 b2 ba ff  |................|
00000090  1f 28 38 ff 18 20 33 ff  1b 2a 42 ff 22 3a 58 ff  |.(8.. 3..*B.":X.|
000000a0  1e 38 55 ff 1d 34 51 ff  1d 33 50 ff 1c 2e 48 ff  |.8U..4Q..3P...H.|
000000b0  1e 36 53 ff 23 3f 61 ff  26 3e 5d ff 26 3d 5d ff  |.6S.#?a.&>].&=].|
000000c0  2f 43 61 ff 27 3c 5b ff  24 36 52 ff 47 52 62 ff  |/Ca.'<[.$6R.GRb.|
000000d0  49 57 69 ff 4d 5b 6c ff  4c 5a 6b ff 4c 5b 6c ff  |IWi.M[l.LZk.L[l.|
000000e0  4e 5d 6d ff 65 71 7e ff  6d 79 85 ff 6c 78 83 ff  |N]m.eq~.my..lx..|
000000f0  6c 77 82 ff 6a 76 81 ff  41 4c 5c ff 1e 2c 44 ff  |lw..jv..AL\..,D.|
00000100  1d 2c 43 ff 1d 2a 41 ff  1c 2b 41 ff 1d 2b 42 ff  |.,C..*A..+A..+B.|
00000110  1c 29 44 ff 1c 2b 43 ff  1b 2a 43 ff 19 28 43 ff  |.)D..+C..*C..(C.|
00000120  19 28 43 ff 19 28 42 ff  1a 28 41 ff 18 26 40 ff  |.(C..(B..(A..&@.|
00000130  1b 2a 42 ff 18 24 3e ff  1b 28 40 ff 19 27 3f ff  |.*B..$>..(@..'?.|
00000140  19 27 3f ff 19 26 3e ff  19 27 3f ff 18 26 40 ff  |.'?..&>..'?..&@.|
00000150  19 28 40 ff 19 27 3d ff  1a 28 3e ff 1a 28 3d ff  |.(@..'=..(>..(=.|
00000160  1a 27 3e ff 1b 29 3f ff  1a 24 33 ff 1e 21 27 ff  |.'>..)?..$3..!'.|
00000170  ae b7 c0 ff ae b9 c0 ff  ae b9 c1 ff af b9 c1 ff  |................|
00000180  ae b9 c1 ff ae ba c1 ff  af b9 c1 ff a1 ad b6 ff  |................|
00000190  1b 24 35 ff 17 20 34 ff  1b 2a 43 ff 20 38 56 ff  |.$5.. 4..*C. 8V.|
000001a0  1e 37 54 ff 1d 35 51 ff  1c 35 54 ff 1c 2f 4a ff  |.7T..5Q..5T../J.|
000001b0  1e 38 57 ff 22 3d 5d ff  25 3e 5e ff 26 3d 00 fe  |.8W."=].%>^.&=..|
000001c0  ff ff 83 fe ff ff 02 f8  fb 01 00 60 e3 01 00 fe  |...........`....|
000001d0  ff ff 05 fe ff ff 02 58  df 03 00 a0 16 00 00 00  |.......X........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by deckerry on 2011-03-24
**Hippytaff**,
I have to leave for now but when are the best times for me to come back and check for your replies?

---

### Post by Hippytaff on 2011-03-24
> **deckerry said:**
> **hippytaff**,
i have to leave for now but when are the best times for me to come back and check for your replies?

:?

---

### Post by deckerry on 2011-03-24
> **Hippytaff said:**
> :?
That confused smiley leads me to believe that you are not comfortable answering that question. That's perfectly fine. Privacy is an important thing. I will just check back later.

You have been very helpful this far and I hope you can help me get to the bottom of this problem. If at any point you feel like your sick of trying to solve this problem just let me know. Then I will know when to move on to another strategy.

I know you have a life outside of answering forum questions. You have been very helpful this far and I hope you can help me get to the bottom of this problem.

---

### Post by Hedgehog1 on 2011-03-24
**deckerry,**

Now that you have successfully posted the scripts results (we let Hippytaff do the hard work!) :D

It appears you have installed Ubuntu twice:

/dev/sdb3
[COLOR="Green"]__/dev/sdb5        f787b0b3-f28c-4b89-9e6b-086b5007e48f   ext4                                     
__/dev/sdb6        32f1c54d-01d7-46c9-92c2-11ebf87de29d   swap[/COLOR]                                     
[COLOR="Blue"]__/dev/sdb7        0696b9a1-0116-4dd8-bee6-9156394da148   ext4                                     
__/dev/sdb8        29855466-8fa6-4477-8969-d5a93e68db6a   swap [/COLOR]

Ubuntu created an extended partition (called /dev/sd**b3**)
* b= Second Hard drive (first one is 'a' - and 'a' is your USB stick you had to boot from)
* 3= Third partition on that drive.

sdb5 & sdb6 are from the first install (in green)
sdb7 & sdb8 are from the second install (in blue)

You original error message was:```
- Missing modules (cat/proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/[COLOR="Blue"]0696b9a1-0116-4dd8-bee6-9156394da148[/COLOR] does not exist. Dropping to a shell!

```

[COLOR="Blue"]__/dev/sdb7        0696b9a1-0116-4dd8-bee6-9156394da148   ext4[/COLOR]

What this all means is the fstab (**F**ile **S**ystem **TAB**le) of the second install got confused because of the first install and the second fstab is referencing itself.

**Note: We are seeing the /dev/sda5 fstab in the script results, not the /dev/sda7 fstab**.

I think your best bet is to remove the two Ubuntu installs, and then reinstall Ubuntu in a controlled fashion.

We can guide you through this process.

[B]Here is a link from a few days ago where this situation also happened:  [http://ubuntuforums.org/showthread.php?t=1711146]("http://ubuntuforums.org/showthread.php?t=1711146")

Starting at post 12, you will see lots of pictures that help explain the removal and reinstall process.[/B]


***The Hedge***

:KS

---

### Post by jtarin on 2011-03-24
Edited for redundancy.

---

### Post by samcot on 2011-03-24
Hi, deckerry. I like your scroll box! How do you do it?

---

### Post by deckerry on 2011-03-25
> **samcot said:**
> Hi, deckerry. I like your scroll box! How do you do it?
[U][B]
Hey Samcot[/B][/U],

For a scroll box:
1) Put in some text into a reply box.
2) Highlight the text you want to be in a scroll box.
3) At the top of the reply box click on the [COLOR=Red]#[/COLOR] button. If you don't see it, click [COLOR=Red]Go Advanced[/COLOR] at the bottom of the reply box.

---

### Post by deckerry on 2011-03-25
> **Hedgehog1 said:**
> **deckerry,**

Now that you have successfully posted the scripts results (we let Hippytaff do the hard work!) :D

It appears you have installed Ubuntu twice:

/dev/sdb3
[COLOR="Green"]__/dev/sdb5        f787b0b3-f28c-4b89-9e6b-086b5007e48f   ext4                                     
__/dev/sdb6        32f1c54d-01d7-46c9-92c2-11ebf87de29d   swap[/COLOR]                                     
[COLOR="Blue"]__/dev/sdb7        0696b9a1-0116-4dd8-bee6-9156394da148   ext4                                     
__/dev/sdb8        29855466-8fa6-4477-8969-d5a93e68db6a   swap [/COLOR]

Ubuntu created an extended partition (called /dev/sd**b3**)
* b= Second Hard drive (first one is 'a' - and 'a' is your USB stick you had to boot from)
* 3= Third partition on that drive.

sdb5 & sdb6 are from the first install (in green)
sdb7 & sdb8 are from the second install (in blue)

You original error message was:```
- Missing modules (cat/proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/[COLOR="Blue"]0696b9a1-0116-4dd8-bee6-9156394da148[/COLOR] does not exist. Dropping to a shell!

```

[COLOR="Blue"]__/dev/sdb7        0696b9a1-0116-4dd8-bee6-9156394da148   ext4[/COLOR]

What this all means is the fstab (**F**ile **S**ystem **TAB**le) of the second install got confused because of the first install and the second fstab is referencing itself.

**Note: We are seeing the /dev/sda5 fstab in the script results, not the /dev/sda7 fstab**.

I think your best bet is to remove the two Ubuntu installs, and then reinstall Ubuntu in a controlled fashion.

We can guide you through this process.

[B]Here is a link from a few days ago where this situation also happened:  [http://ubuntuforums.org/showthread.php?t=1711146]("http://ubuntuforums.org/showthread.php?t=1711146")

Starting at post 12, you will see lots of pictures that help explain the removal and reinstall process.[/B]


***The Hedge***

:KS
Thanks a lot Hedgehog1 it seems like you really understand this stuff well.

I looked at step 12 from [http://ubuntuforums.org/showthread.php?t=1711146](http://ubuntuforums.org/showthread.php?t=1711146) and noticed that I am supposed to create a system repair disc. Before I go and do that, I have 2 issues.

1) I looked in Vista and can't figure out how to even make the repair disc.
2) I don't think the repair disc could help me because my disc drive is completely broken(trust me, even its tech support told me I would have to replace it and its not covered under warranty and I don't have money to buy a replacement.)

Could I use a usb as a repair disc if I can figure out how to make a "repair disc?"

---

### Post by Hedgehog1 on 2011-03-25
The system repair disk is hard coded in Windows to burn a CD only.  MS assumes a minimum level of hardware, and for Win7 a working CD burning is a requirement.

If you are not able to burn a repair CD, this severely limits the options.

It is possible to do this without the repair disk; however if any little thing goes wrong, you will be left with a PC that does not boot (We don't want you to be in this situation!)

All is not lost, however.

We can still get your Ubuntu working and reclaim the disk space, but the steps are more convoluted.

The first thing we will need to for you to copy the fstab file from /dev/sda7 into your next post.  Don't change anything on it yet, just copy and paste it into the post.

Here is how to get to it:

Please boot off your LiveCD/LiveUSB, select TRY

In the Terminal (Menu to: Applications >> Accessories >> Terminal), copy and paste these one at a time:

```
sudo mount /dev/sdb7 /mnt
```
```
gedit /mnt/etc/fstab
```

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-03-25
As an outline for you and a note to others who will help while I am gone, here are the steps I am proposing:

1) Get a copy of the /etc/fstab in /dev/sdb7

2) Give you a functional fstab to be placed back into /dev/sdb7 (to get Ubuntu to boot) using these command off the LiveCD/LiveUSB:

```
sudo mount /dev/sdb1 /mnt
```
```
gksudo gedit /mnt/etc/fstab
```

**Once Ubuntu boots** from /sda/sdb7 and things look good:

3) From LiveCD/LiveUSB, use gparted to delete /dev/sdb5 & /dev/sdb6

4) From LiveCD/LiveUSB, use gparted to move/resize /dev/sdb7 to fill the open space in /dev/sdb3

***The Hedge***

:KS

---

### Post by deckerry on 2011-03-25
> **Hedgehog1 said:**
> The system repair disk is hard coded in Windows to burn a CD only.  MS assumes a minimum level of hardware, and for Win7 a working CD burning is a requirement.

If you are not able to burn a repair CD, this severely limits the options.

It is possible to do this without the repair disk; however if any little thing goes wrong, you will be left with a PC that does not boot (We don't want you to be in this situation!)

All is not lost, however.

We can still get your Ubuntu working and reclaim the disk space, but the steps are more convoluted.

The first thing we will need to for you to copy the fstab file from /dev/sda7 into your next post.  Don't change anything on it yet, just copy and paste it into the post.

Here is how to get to it:

Please boot off your LiveCD/LiveUSB, select TRY

In the Terminal (Menu to: Applications >> Accessories >> Terminal), copy and paste these one at a time:

```
sudo mount /dev/sdb7 /mnt
```
```
gedit /mnt/etc/fstab
```

***The Hedge***

:KS
I am running vista. I do not have windows 7. (Just double checking that we're on the same page.)

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb7 during installation
UUID=0696b9a1-0116-4dd8-bee6-9156394da148 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb8 during installation
UUID=29855466-8fa6-4477-8969-d5a93e68db6a none            swap    sw              0       0
```

---

### Post by Hedgehog1 on 2011-03-25
> **deckerry said:**
> I am running vista. I do not have windows 7. (Just double checking that we're on the same page.)
 
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb7 during installation
UUID=0696b9a1-0116-4dd8-bee6-9156394da148 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb8 during installation
UUID=29855466-8fa6-4477-8969-d5a93e68db6a none            swap    sw              0       0
```
 
OK - Vista it is. Fortunately, the steps are identical for Vista and Win7.
 
The fstab file from /dev/sdb7 looks correct (matches the blue numbers):
 
/dev/sdb3
[COLOR=green]__/dev/sdb5 f787b0b3-f28c-4b89-9e6b-086b5007e48f ext4 [/COLOR]
[COLOR=green]__/dev/sdb6 32f1c54d-01d7-46c9-92c2-11ebf87de29d swap[/COLOR] 
[COLOR=blue]__/dev/sdb7 0696b9a1-0116-4dd8-bee6-9156394da148 ext4 [/COLOR]
[COLOR=blue]__/dev/sdb8 29855466-8fa6-4477-8969-d5a93e68db6a swap [/COLOR]
 
Which makes your error message:
 
```
- Missing modules (cat/proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/[COLOR=blue]0696b9a1-0116-4dd8-bee6-9156394da148[/COLOR] does not exist. Dropping to a shell!
```
 
Very confusing. The line for root ('/') refences the partiton correctly, and no additional lines refenrence it again.
 
This will alter the plan a little.
 
-------
 
Please boot off your LiveCD/LiveUSB, select TRY
 
Using gparted, go ahead and delete paritions:
 
[COLOR=#008000]__/dev/sdb5 f787b0b3-f28c-4b89-9e6b-086b5007e48f ext4 [/COLOR]
[COLOR=#008000]__/dev/sdb6 32f1c54d-01d7-46c9-92c2-11ebf87de29d swap[/COLOR] 
 
Be aware you **may** have to unmount** /dev/sdb5**, and select 'swapof' for **/dev/sdb6**
 
**----**
 
Once they are deleted, ***do the next steps right away before rebooting***:
 
In the Terminal (Menu to: Applications >> Accessories >> Terminal), _copy and paste these one at a time (they have **your** drive IDs in them already):_
 
```
sudo mount /dev/sdb7 /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /proc /mnt/proc && sudo mount -o bind /sys /mnt/sys && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
``` ```
grub-install /dev/sdb
``````
update-grub
``````
exit
``` ```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt/sys && sudo umount /mnt
``````
sudo shutdown -r now
```
 
Hopefully, when you reboot normally after this, Ubuntu will come up OK when you select it in the grub menu.
 
Please let me know the results...
 
***The Hedge***
 
:KS

---

### Post by deckerry on 2011-03-25
Gee willikers man! This thing is biting and scratching every single step of the way!

I can't get gparted to run. At first I tired to open it and it gave me an error message. I tried to report it and it said that it couldn't be reported. So I restarted the computer and booted from the usb again and now it tries to open and just disappears without completely opening right when you think its going to work. After restarting it doesn't produce an error message anymore. It just doesn't completely start.

You said "Be aware you may have to unmount /dev/sdb5, and select 'swapof' for /dev/sdb6." That's cool with me except I don't know how or when to do that. Would that make gparted work? Is that why you said that?

Thanks for being so patient with me by the way.

---

### Post by Hedgehog1 on 2011-03-25
I was posting during a quick break for lunch, so things were a bit hurried.

You have to use gparted to "unmount /dev/sdb5, and select 'swapof' for /dev/sdb6.", by right clicking on those partitions and using the options show in the right-click menu.

I am concerned that gparted is not running.

So we can see whatever error message is coming up when it crashes, please do the from the LiveCD/LiveUSB:

In the Terminal (Menu to: Applications >> Accessories >> Terminal):
```
sudo gparted
```

When it dies, the error that caused it should display in the terminal.  Please copy and paste that error into your next post.

***The Hedge***

:KS

p.s. There is something screwy going on here....  But my Hedgie-Sense isn't giving me any clues...

---

### Post by deckerry on 2011-03-26
> **Hedgehog1 said:**
> I was posting during a quick break for lunch, so things were a bit hurried.

You have to use gparted to "unmount /dev/sdb5, and select 'swapof' for /dev/sdb6.", by right clicking on those partitions and using the options show in the right-click menu.

I am concerned that gparted is not running.

So we can see whatever error message is coming up when it crashes, please do the from the LiveCD/LiveUSB:

In the Terminal (Menu to: Applications >> Accessories >> Terminal):
```
sudo gparted
```

When it dies, the error that caused it should display in the terminal.  Please copy and paste that error into your next post.

***The Hedge***

:KS

p.s. There is something screwy going on here....  But my Hedgie-Sense isn't giving me any clues...

Here's what it says:

```

ubuntu@ubuntu:~$ sudo gparted
======================
libparted : 2.3
======================

glibmm-ERROR **:
unhandled exception (type std::exception) in signal handler:
what: basic_string::_S_create

aborting...
ubuntu@ubuntu:~$

```

---

### Post by Hedgehog1 on 2011-03-26
I am going to ask you to rebuild the LiveUSB, please.

Then reboot off of it and see if gparted will run as expected. 

Otherwise, we may have to take more radical measures *(Lets see, we will need Duct-tape, a bag of Lemon balls, two Hamsters and a yard stick...)*


***The Hedge***

:KS

---

### Post by samcot on 2011-03-26
Thank you, deckerry! I'm amazed at how much there is to learn in a forum like this, and everyone is so helpful. I hope to start returning the favor once I'm no longer a noobie. :smile: I assume that "CODE" in brackets are HTML tags that I can use elsewhere?
 
```
 
This is a test to see if I can create a scroll box. I'll insert a link to a song and post the lyrics:
 
[I Have A Song To Sing, O! - Gilbert and Sullivan]("http://www.youtube.com/watch?v=aQh04-STjmU&feature=related")
 
I have a song to sing, O! (Sing me your song, O!)
It is sung to the moon by a love-lorn loon who fled from the mocking throng-o
It's the song of a merry man moping mum whose soul was sad and whose glance was glum
Who sipped no sup and who craved no crumb as he sighed for the love of a lady 
Hey-di, hey-di, misery me, lack-a-day-de
He sipped no sup and he craved no crumb as he sighed for the love of a lady 
 
I have a song to sing, O! (What is your song, O?)
It is sung with the ring of the songs maids sing who loved with a love life-long-o
It's a song of a merry maid peerly proud who loved a lord and who laughed aloud
At the moan of the merry man moping mum whose soul was sad and whose glance was glum
Who sipped no sup and who craved no crumb as he sighed for the love of a lady 
Hey-di, hey-di, misery me, lack-a-day-de
He sipped no sup and he craved no crumb as he sighed for the love of a lady
 
I have a song to sing,O! (Sing me your song, O!)
It is sung to the knell of a church-yard bell and a doleful dirge ding-dong-o
It's a song of a popinjay bravely born who turned up his noble nose with scorn
At the humble merry maid peerly proud who loved a lord and who laughed aloud
At the moan of a merry man moping mum whose soul was sad and whose glance was glum
Who sipped no sup and who craved no crumb as he sighed for the love of a lady
Hey-di, hey-di, misery me, lack-a-day-de
He sipped no sup and he craved no crumb as he sighed for the love of a lady 
 
I have a song to sing, O! (Sing me your song, O!)
It is sung with a sigh and a tear in the eye for it tells of a righted wrong-o
It's a song of the merry maid once so gay who turned on her heel and tripped away
From the peacock popinjay bravely born who turned up his noble nose with scorn
At the humble heart that he did not prize so she begged on her knees with downcast eyes
For the love of the merry man moping mum whose soul was sad and whose glance was glum
Who sipped no sup and who craved no crumb as he sighed for the love of a lady 
Hey-di, hey-di, misery me, lack-a-day-de
His pains were o'er and he sighed no more for he lived in the love of a lady 
Hey-di, hey-di, misery me, lack-a-day-de
His pains were o'er and he sighed no more for he lived in the love of a lady

```

---

### Post by deckerry on 2011-03-26
> **Hedgehog1 said:**
> I am going to ask you to rebuild the LiveUSB, please.

Then reboot off of it and see if gparted will run as expected. 

Otherwise, we may have to take more radical measures *(Lets see, we will need Duct-tape, a bag of Lemon balls, two Hamsters and a yard stick...)*


***The Hedge***

:KS

Dang, still doesn't work. But I went to Walmart and got some lemon balls, I went to Staples and got a yard stick, got duct-tape from Home Depot, bought a hamster from the petstore and stole the other one from my neighbor because I ran out of money.

Plus I got these cool neat error messages along the way for free:

```

Sorry, the package "bcmwl-kernel-source 5.60.48.36+bdcom-0ubuntu5" failed to install or upgrade.

```
```

Sorry, the package "initramfs-tools 0.98.1ubuntu6" failed to install or upgrade.

```

---

### Post by Hedgehog1 on 2011-03-26
> **deckerry said:**
> But I went to Walmart and got some lemon balls, I went to Staples and got a yard stick, got duct-tape from Home Depot, bought a hamster from the petstore and stole the other one from my neighbor because I ran out of money.

**That's the spirit!**  *As a side note, Gerbils will work when Hamsters are not available.* :D

These error messages are quite new to me:

```

Sorry, the package "bcmwl-kernel-source 5.60.48.36+bdcom-0ubuntu5" failed to install or upgrade.

```
```

Sorry, the package "initramfs-tools 0.98.1ubuntu6" failed to install or upgrade.

```

I am going to request some folks take a look at this and see if it is something they are familiar with. 


***The 'stumped' Hedge***

:KS

---

### Post by Dutch70 on 2011-03-26
Hello Hedge :D

I almost hate to ask this question, this far into the battle, but have you checked the md5sum of the downloaded .iso? 
[[COLOR="Red"]https://help.ubuntu.com/community/HowToMD5SUM[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM")

---

### Post by oldfred on 2011-03-26
Where did you get the error message. Just after the grub install?

Two choices, One we keep trying to fix this which I always like to do even if it takes days (it is good learning for all of us). 
Two reinstall. If you do not have saved data or a lot of configuration work invested then repair may not make sense. You can usually reinstall in about an hour.

To repair I think we need to chroot into your system again and do a full refresh.
To reinstall be sure to use manual install and choose the same partitions you have.

this was the chroot command you ran before:
```
sudo mount /dev/sdb7 /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /proc /mnt/proc && sudo mount -o bind /sys /mnt/sys && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```

Then run all of these:
Commands once in chroot:
if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

exit

Then copy the umount commands & shutdown commands you had before.

---

### Post by Hedgehog1 on 2011-03-26
> I almost hate to ask this question, this far into the battle, but have you checked the md5sum of the downloaded .iso? 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

See - that is something that is so obvious that it never occurred to me that a damaged download of the ISO would then make any install attempts from it fail...

***The Hedge***

---

### Post by Hedgehog1 on 2011-03-26
> **oldfred said:**
> Two choices, One we keep trying to fix this which I always like to do even if it takes days (it is good learning for all of us). 
**Two reinstall. If you do not have saved data or a lot of configuration work invested then repair may not make sense. You can usually reinstall in about an hour.**


Thanks oldfred!

Deckerry,

I am thinking the checking of the ISO is the first place to start.

***The Hedge***

p.s. I am always amazed at just how much oldfred knows.  He is a gold-mine of Linux/Ubuntu info.

---

### Post by Dutch70 on 2011-03-26
> **Hedgehog1 said:**
> See - that is something that is so obvious that it never occurred to me that a damaged download of the ISO would then make any install attempts from it fail...

***The Hedge***

LOL, Quackers got me on that the other day, but hey...
**We got back up!** ;)

---

### Post by deckerry on 2011-03-26
Ok there are alot of messages up there and I'm getting overwhelmed so what's the very next thing I should do? I really don't care how we do this as long as I don't erase vista. So the quickest easiest way is the best for me but then again I have no idea what's going on so I'm up for anything.

---

### Post by tushar maroo on 2011-03-26
i think other than all mentioned above you have losted your grub so try to fix it and update it

---

### Post by Hedgehog1 on 2011-03-26
> **deckerry said:**
> Ok there are alot of messages up there and I'm getting overwhelmed so what's the very next thing I should do? I really don't care how we do this as long as I don't erase vista. So the quickest easiest way is the best for me but then again I have no idea what's going on so I'm up for anything.

Fair enough.

The Next step is to check that the .iso file you downloaded is not damaged.  We nerds call it: Checking the md5sum of the .iso

[https://help.ubuntu.com/community/HowToMD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM")

You can also re-download the .iso using a bit-torrent client, as bit-torrent downloaders always check the integrity of whatever they download.

What sounds good to you?

***The Hedge***

:KS

---

### Post by deckerry on 2011-03-26
> **Hedgehog1 said:**
> Fair enough.

The Next step is to check that the .iso file you downloaded is not damaged.  We nerds call it: Checking the md5sum of the .iso

[https://help.ubuntu.com/community/HowToMD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM")

You can also re-download the .iso using a bit-torrent client, as bit-torrent downloaders always check the integrity of whatever they download.

What sounds good to you?

***The Hedge***

:KS
What sounds good to me?
Whatever is the quickest and most painless way to get Ubuntu to work. I don't really care what version. If there is a version easier to install than 10.10 I'm cool with just doing that.

I copied the iso [COLOR="Red"]ubuntu-10.10-desktop-i386.iso[/COLOR] into the directory [COLOR="Red"]ubuntu[/COLOR].

I opened a terminal and put this in there:
```

md5sum ubuntu-8.10-desktop-i386.iso

```

I clicked enter and the terminal told me this:
```

md5sum: ubuntu-8.10-desktop-i386.iso: No such file or directory

```

I must surely be doing something wrong.

---

### Post by Dutch70 on 2011-03-26
It's 10.10, not 8.10. You have to change that to the exact name of your .iso.

You may be able to just right click the .iso & select "md5sum" and it should give you the numbers to check.

---

### Post by Hedgehog1 on 2011-03-26
OK - lets try the Long Term Support version of Ubuntu.

The iso is on this web page:

[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download]("http://www.ubuntu.com/desktop/get-ubuntu/alternative-download")

You want to download and install:

**ubuntu-10.04.2-desktop-i386.iso.torrent**

***The Hedge***

:KS

---

### Post by deckerry on 2011-03-26
Dutch70:
Ok I know I'm a noob but there's no excuse for me being stupid lol! Sorry about that. I put in the command with the 10 instead of 8 and it seems to like that better. I'll keep workin' at it. Thanks for that.

Hedgehog:
I'm downloading that iso you told me about. It looks like it should be done at about 1:45pm central.

If I'm downloading 10.04, should I even worry about m5ing my 10.10 iso?

---

### Post by Dutch70 on 2011-03-26
No, but just for kicks & giggles, right click the .iso you have & select "md5sum" compare the numbers to these.
59d15a16ce90c8ee97fa7c211b7673a8

and btw, nobody's stupid here. When you get caught up in something, it's all too easy to miss the little things.

---

### Post by Hedgehog1 on 2011-03-26
> **deckerry said:**
> 
If I'm downloading 10.04, should I even worry about m5ing my 10.10 iso?

It would be good to know if the 10.10 .iso is damaged or OK; however that is an optional step.  It is a learning experience (although you have had a few too many of those in this effort :D )

***The Hedge***

:KS

---

### Post by deckerry on 2011-03-26
> **Dutch70 said:**
> No, but just for kicks & giggles, right click the .iso you have & select "md5sum" compare the numbers to these.
59d15a16ce90c8ee97fa7c211b7673a8

and btw, nobody's stupid here. When you get caught up in something, it's all too easy to miss the little things.
I got a perfect match.
59d15a16ce90c8ee97fa7c211b7673a8

---

### Post by Hedgehog1 on 2011-03-26
> **deckerry said:**
> I got a perfect match.
59d15a16ce90c8ee97fa7c211b7673a8

Hmmm... If the 10.04.2 doesn't install, this could be a VERY long thread....


***The Hedge***

:KS

---

### Post by deckerry on 2011-03-26
Yes do you think this might be a Guinness world record breaker? 

Ok the 10.04 iso is here finally.

We will be taking the other 2 installs of 10.10 off before or after installing 10.04, right?

Hey if you're having fun helping me slay this Godzilla, I'm sure that I'll need help getting my internet and graphics cards to work after installing Ubuntu 10.04.

---

### Post by Hedgehog1 on 2011-03-26
Yes, please remove all your 10.10 installs first.

You can repeat the install steps for 10.04.02, they are the same as far as you are concerned.

***The Hedge***

:KS

---

### Post by deckerry on 2011-03-26
> **Hedgehog1 said:**
> Yes, please remove all your 10.10 installs first.

You can repeat the install steps for 10.04.02, they are the same as far as you are concerned.

***The Hedge***

:KS
I'm sorry about this but I don't know how to remove my 10.10 installs.

---

### Post by Dutch70 on 2011-03-26
re-post the output of "sudo fdisk -lu"

---

### Post by deckerry on 2011-03-26
> **Dutch70 said:**
> re-post the output of "sudo fdisk -lu"

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   976768064   488384001    c  W95 FAT32 (LBA)

Disk /dev/sdb: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7856127 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          38     7839719     3919841    c  W95 FAT32 (LBA)

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1f29dfaf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   150328426    75164182    7  HPFS/NTFS
/dev/sdc2       216781110   234436544     8827717+   7  HPFS/NTFS
/dev/sdc3       150329342   216780799    33225729    5  Extended
/dev/sdc5       183619584   215298047    15839232   83  Linux
/dev/sdc6       215300096   216780799      740352   82  Linux swap / Solaris
/dev/sdc7       150329344   182132735    15901696   83  Linux
/dev/sdc8       182134784   183607295      736256   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdd: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x478a8f3f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63   234436544   117218241    7  HPFS/NTFS
ubuntu@ubuntu:~$ 

```

---

### Post by Hedgehog1 on 2011-03-26
I did not realize you did not delete the original installs before doing 10.10 again.

From the LiveCD, use gparted to delete these partitons 

[B]/dev/sdc5       183619584   215298047    15839232   83  Linux
/dev/sdc6       215300096   216780799      740352   82  Linux swap / Solaris
/dev/sdc7       150329344   182132735    15901696   83  Linux
/dev/sdc8       1[/B]82134784   183607295      736256   82  Linux swap / Solari

You right click on the partition to get the 'delete':

[IMG]http://img856.imageshack.us/img856/2164/hp4partitions03.png[/IMG]

Once all four are deleted, press the check-mark button to make the change real.

This also explains why the new 10.10 install failed, these old partitions were still there and confusing the install.

---

### Post by deckerry on 2011-03-26
Gparted doesn't run. It says this:

```
ubuntu@ubuntu:~$ sudo gparted
======================
libparted : 2.3
======================

glibmm-ERROR **: 
unhandled exception (type std::exception) in signal handler:
what: basic_string::_S_create

aborting...
ubuntu@ubuntu:~$ 
```

Is there a way to delete them in Vista?

---

### Post by Hedgehog1 on 2011-03-26
-deleted-

---

### Post by Hedgehog1 on 2011-03-26
> **deckerry said:**
> Gparted doesn't run. It says this:

```
ubuntu@ubuntu:~$ sudo gparted
======================
libparted : 2.3
======================

glibmm-ERROR **: 
unhandled exception (type std::exception) in signal handler:
what: basic_string::_S_create

aborting...
ubuntu@ubuntu:~$ 
```

Is there a way to delete them in Vista?

Yes:

[IMG]http://img718.imageshack.us/img718/7687/small55diskmanagement.png[/IMG]
Remove Swap Partiton
[IMG]http://img97.imageshack.us/img97/4905/small56deleteswap.png[/IMG]
[IMG]http://img231.imageshack.us/img231/2992/small57freespace.png[/IMG]
Remove Ubuntu Partition
[IMG]http://img96.imageshack.us/img96/5986/small58deleteubuntu.png[/IMG]

You will need to delete 4 partitions - do not delete anything that says **NTFS**

---

### Post by Hedgehog1 on 2011-03-26
Then make a new LiveUSB from Ubuntu 10.04.02 and see that gparted will run for you...

We hope so...

***The Hedge***

:KS

---

### Post by Dutch70 on 2011-03-26
[[COLOR="Red"]BUG[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/parted/+bug/558431") ...Looks like it may have something to do with your particular geek stick. :P

---

### Post by deckerry on 2011-03-26
Before I go deleting stuff I want to show you my screen and make absolutely sure I'm getting the right stuff because I know I could really mess things up here.

Keep in mind that my cd drive is broken with no hope of fixing.

I'm gonna delete the partitions that are:
15.17GB
719MB
15.11GB
723MB

Am I supposed to "reclaim stuff for vista" or something or just delete these?

---

### Post by Hedgehog1 on 2011-03-26
Yes - the four partitions in the 'middle' that do not say 'NTFS' are the ones to delete.

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-03-26
Also - Dutch70 found that some USB sticks and gparted do not get along **[gparted-usb-bug]("https://bugs.launchpad.net/ubuntu/+source/parted/+bug/558431")**

Do you have a different USB stick you could use? Can you boot off a CD?  I forget how can and can't after a few hours....

***The Hedge***

:KS

---

### Post by deckerry on 2011-03-26
I deleted those 4 and one gave me an error and made me restart the disc management. Here is the error screen and also the disc management screen after the deletions. I have not restarted my computer (and am kind of afraid to) but everything seems fine.

---

### Post by deckerry on 2011-03-26
> **Dutch70 said:**
> [[COLOR="Red"]BUG[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/parted/+bug/558431") ...Looks like it may have something to do with your particular geek stick. :P
I can't boot off a cd (disc drive broken) and I don't have another usb drive on me. So I have to either buy a new one or try one more time with ubuntu 10.04.2

---

### Post by Hedgehog1 on 2011-03-26
Ahh - the 'Unexpected error' message.  Like there were errors you were expecting?!?!

You have to reboot sometime...

BUT make a new LiveUSB of 10.04.02 first... Then reboot...

***The Hedge***

:KS

Right - you had the busted CD...  I cannot keep this straight some days...

---

### Post by deckerry on 2011-03-26
> **Hedgehog1 said:**
> Ahh - the 'Unexpected error' message.  Like there were errors you were expecting?!?!

You have to reboot sometime...

BUT make a new LiveUSB of 10.04.02 first... Then reboot...

***The Hedge***

:KS

Right - you had the busted CD...  I cannot keep this straight some days...
Well usually I don't expect them but I've been having so many obstacles I can't honestly say that I'm suprised. Lol.

Anyways, what should I expect after rebooting. Do I boot off my new usb thing? If yes, what should I do after booting off the usb and what should I not to while booting off the usb?

---

### Post by Hedgehog1 on 2011-03-26
Boot of the new USB thing, select 'try', then fire up fire-fox and get onto this forum.

Next, try gparted and see if it starts up.  If it does, we can create the two partitions you need and keep moving along.  Post what happens...

***The Hedge***

:KS

---

### Post by laerub18 on 2011-03-26
hey,

i've been reading since the beginning but i'm kind of lost:
if a partition has been freed, why not installing ubuntu on it instead of clicking on try ?

also, deckerry, maybe one of your friends has an external usb disc drive ?

---

### Post by Hedgehog1 on 2011-03-26
> **laerub18 said:**
> hey,

i've been reading since the beginning but i'm kind of lost:
if a partition has been freed, why not installing ubuntu on it instead of clicking on try ?

also, deckerry, maybe one of your friends has an external usb disc drive ?

The idea here is to control the install - that means creating the partitions manually.  deckerry is trying to accomplish a disk layout like this:

[IMG]http://img269.imageshack.us/img269/2134/hp4partitions15o.png[/IMG]

However, the deck has been stacked against him/her...

***The Hedge***

:KS

---

### Post by deckerry on 2011-03-26
GPARTED WORKS!!!!!!!! :)
Now what should I do?

---

### Post by Hedgehog1 on 2011-03-26
Cool!

Pictures will follow in a moment!!  HAPPY DANCE TIME!!!!!

---

### Post by Hedgehog1 on 2011-03-26
[SIZE="4"][COLOR="DarkOrange"]Create your sd**b**5 (the pictures have sda) Ubuntu partition by right clicking on the area- you will see a menu of options.  Leave a little room for swap later (Format this ext4 - and press that check mark button):[/COLOR][/SIZE]
[IMG]http://img863.imageshack.us/img863/4839/hp4partitions06.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Create sd**b**6 and make it swap space:[/COLOR][/SIZE]
[IMG]http://img855.imageshack.us/img855/3999/hp4partitions07.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Press the check mark button again[/COLOR][/SIZE]

---

### Post by Dutch70 on 2011-03-26
> **Hedgehog1 said:**
> Cool!

Pictures will follow in a moment!!  HAPPY DANCE TIME!!!!!

[[COLOR="Red"]http://www.youtube.com/watch?v=JAMkggHmRUw[/COLOR]]("http://www.youtube.com/watch?v=JAMkggHmRUw")

---

### Post by Hedgehog1 on 2011-03-26
[SIZE="4"][COLOR="DarkOrange"]You are ready to install Ubuntu:[/COLOR][/SIZE]
[IMG]http://img864.imageshack.us/img864/2449/hp4partitions08d.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Select this during the install:[/COLOR][/SIZE]
[IMG]http://img705.imageshack.us/img705/2588/hp4partitions09.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]And you will get to here:[/COLOR][/SIZE]
[IMG]http://img849.imageshack.us/img849/9937/hp4partitions10.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]We will add some extra data to sd**b**5 and sd**b**6.  With sd**b**5 highlighted, press the [CHANGE] button:[/COLOR][/SIZE]
[IMG]http://img861.imageshack.us/img861/5274/hp4partitions11.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]These settings prepare the partition to be ext4, '/'.[/COLOR][/SIZE]
[SIZE="4"][COLOR="DarkOrange"]Repeat the steps for the swap area (This usually set itself up OK) :[/COLOR][/SIZE]
[IMG]http://img26.imageshack.us/img26/4934/hp4partitions12.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]You are ready to install.  Press [Install Now].[/COLOR][/SIZE]


[SIZE="4"]EDIT: Your Boot Loader goes on **/dev/sdb** - (sda is your USB stick)...[/SIZE]
Don't use sdb1 or sdb3 - just **sdb**


[IMG]http://img857.imageshack.us/img857/6342/hp4partitions13.png[/IMG] 
[SIZE="4"][COLOR="DarkOrange"]This is (Close) to what your drive looks like in the 'Disk Utility' in Ubuntu after the load is complete:[/COLOR][/SIZE]
[IMG]http://img852.imageshack.us/img852/3987/hp4partitions14.png[/IMG]  

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-03-26
> **Dutch70 said:**
> [[COLOR="Red"]http://www.youtube.com/watch?v=JAMkggHmRUw[/COLOR]]("http://www.youtube.com/watch?v=JAMkggHmRUw")

Your are just too funny!  :lolflag:  A dancing penguin, of course!


***The 'dancing' Hedge***

:KS

---

### Post by deckerry on 2011-03-26
I'm having trouble changing the settings. It says minimum is 8MB and so is the max. I'm very confused.

How are you putting those images right in the post instead of thumbnails like I have?

---

### Post by Dutch70 on 2011-03-26
That's your usb stick bruh...lol. Click the dropdown box in the upper right hand corner to select your hdd. 

sdc, was it?

---

### Post by Hedgehog1 on 2011-03-26
The pictures were for an install on the sd**a** drive, your are installing on the sd**b** drive.

The only thing you will install in /dev/sd**a** is the boot loader - everything else is sd*b*

I store these picture on an outside web server:

[http://img269.imageshack.us/img269/2134/hp4partitions15o.png](http://img269.imageshack.us/img269/2134/hp4partitions15o.png)

That is how I get around the limit.

**[SIZE="3"]EDIT: Your Boot Loader goes on /dev/sdb - sda is your USB stick[/SIZE]**

---

### Post by deckerry on 2011-03-26
> **Dutch70 said:**
> That's your usb stick bruh...lol. Click the dropdown box in the upper right hand corner to select your hdd. 

sdc, was it?

Is this the right place? Click on the unallocated 31.69GB one?

---

### Post by Hedgehog1 on 2011-03-26
> **deckerry said:**
> Is this the right place? Click on the unallocated 31.69GB one?

That is it!  Perfect!

---

### Post by deckerry on 2011-03-26
Here's what I have now. So now do I look at installation and follow post #72?

---

### Post by Hedgehog1 on 2011-03-26
First press the check mark button to make the changes 'real'.

It will "do it's thing" for a little bit.

And then you are ready for #72.

***The 'getting excited this might work' Hedge***

:KS

---

### Post by deckerry on 2011-03-26
before I checkmark the checkmark...

is it a problem that it says "New partition #1" and "New Partition #2" instead of "/dev/sdb5" and "/dev/sdb6"?

Plus there's still the unallocated part.

---

### Post by Hedgehog1 on 2011-03-26
> **deckerry said:**
> before I checkmark the checkmark...

is it a problem that it says "New partition #1" and "New Partition #2" instead of "/dev/sdb5" and "/dev/sdb6"?

Plus there's still the unallocated part.

Checking the checkmark is what makes it /dev/sdb5 & 6.

Please ignore that little bit of unused space.

---

### Post by rbjordan on 2011-03-26
Count me in with that bunch too!:(

---

### Post by Hedgehog1 on 2011-03-26
> **rbjordan said:**
> Count me in with that bunch too!:(

Hey there!

Please create a new thread, and explain your issue.

That way others will see it too and can help you.

***The Hedge***

:KS

---

### Post by deckerry on 2011-03-26
What does this mean? Should I just click continue?

---

### Post by Hedgehog1 on 2011-03-26
You want to format /dev/sdb5.  Please go back and check that box.

***The Hedge***

:KS

---

### Post by deckerry on 2011-03-26
What's this?

---

### Post by Hedgehog1 on 2011-03-26
Select nothing and go on past it.  You are keeping Windows, so you don't need to migrate anything into Ubuntu.

---

### Post by deckerry on 2011-03-26
Here's the last 2 windows before I click install. is /dev/sda good or should it be /dev/sdb or sdc?

---

### Post by Hedgehog1 on 2011-03-26
> **deckerry said:**
> Here's the last 2 windows before I click install. is /dev/sda good or should it be /dev/sdb or sdc?

sda is the USB stick, so please install the boot loader on **/dev/sdb**

---

### Post by deckerry on 2011-03-26
Its installing. So after it's done I'm assuming I have to reboot. What should I expect. Will I be able to use Ubuntu without the usb now? Is this supposed to be the final step for installation?

---

### Post by Dutch70 on 2011-03-26
It's looking good. Cross your fingers. [-o<

---

### Post by Hedgehog1 on 2011-03-26
> **deckerry said:**
> Its installing. So after it's done I'm assuming I have to reboot. What should I expect. Will I be able to use Ubuntu without the usb now? Is this supposed to be the final step for installation?

It will tell you when it needs to reboot, and ask you to remove the CD/USB.

Then it will reboot and load a series of updates to get you current.

Once you can boot OK into 10.04.02, THEN you can reuse the USB stick for whatever.

By the way: ***Your screen shots were EXCELLENT!***

Also; what do you think about the ability to surf the web ***during*** the install process?  Handy, huh?


***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-03-26
> **Dutch70 said:**
> It's looking good. Cross your fingers. [-o<

I tried crossing them - and I broke a nail... :D

***The Hedge***

:KS

---

### Post by deckerry on 2011-03-26
Very nice. I am very optimistic. Thanks everybody for helping. Especially you Hedgehog. You people are extreeeeeeeemely patient. I'm gonna restart now. Here it goes!

---

### Post by Dutch70 on 2011-03-26
> **Hedgehog1 said:**
> I tried crossing them - and I broke a nail... :D

***The Hedge***

:KS

Ouch! At least you've got some Extra Foam Sugar Free Ubuntu to help soothe you now. ;)

---

### Post by Hedgehog1 on 2011-03-26
> **Dutch70 said:**
> Ouch! At least you've got some Extra Foam Sugar Free Ubuntu to help soothe you now. ;)

I may have the sugar free stuff, yeah.  But **you** are ***100% Pure Ubuntu***.

These little titles are the silliest things (but fun).


I do hope deckerry's PC boots  OK...

---

### Post by Dutch70 on 2011-03-26
> **Hedgehog1 said:**
> I may have the sugar free stuff, yeah.  But you are 100% Pure Ubuntu.

These little titles are the silliest things (but fun).

I do hope deckerry's PC boots  OK...

Yeah, so do I. I'm sitting here refreshing the screen every min or so...lol. 
We know it was installed correctly though. As long as their are no hardware issues, he should be fine.

---

### Post by Hedgehog1 on 2011-03-26
> **Dutch70 said:**
> I wonder how people like Quackers for example set their own title. 
His says "Please feed the ducks" LOL

I am guessing it is based on the number of beans...

I want mine to say: **Hedgehogs Prefer Hardware RAID**

---

### Post by Dutch70 on 2011-03-26
> **Hedgehog1 said:**
> I am guessing it is based on the number of beans...

I want mine to say: **Hedgehogs Prefer Hardware RAID**


Hedgehogs Prefer Hardware (Redundant Array of Inexpensive Disks) ...:-k LOL

I know nothing about RAID btw

---

### Post by deckerry on 2011-03-26
Ok everybody. I am late picking up somebody and I have to leave my computer which SUCKS. but I'll be back on here eventually. I don't know if it worked. I restarted the computer with the usb in and it went to the option menu. The first option is "run from usb" or something so I chose it and it went into ubuntu. The internet wouldn't work 'cause I think it couldn't find the drivers for my wireless and I don't have the ability to plug in ethernet 'cause i'm in an apartment.

So I rebooted without the usb and I stared at a blank screen for like 10-15min then gave up and hard-restarted and booted to Vista so I could send this message before I go. I'll be back in a few hours and maybe not until tomorrow. But thanks for hangin in there for me.

See you later.

---

### Post by Hedgehog1 on 2011-03-26
> **deckerry said:**
> Ok everybody. I am late picking up somebody and I have to leave my computer which SUCKS. but I'll be back on here eventually. I don't know if it worked. I restarted the computer with the usb in and it went to the option menu. The first option is "run from usb" or something so I chose it and it went into ubuntu. The internet wouldn't work 'cause I think it couldn't find the drivers for my wireless and I don't have the ability to plug in ethernet 'cause i'm in an apartment.

So I rebooted without the usb and I stared at a blank screen for like 10-15min then gave up and hard-restarted and booted to Vista so I could send this message before I go. I'll be back in a few hours and maybe not until tomorrow. But thanks for hangin in there for me.

See you later.

You are now in the run-of-the-mill issues.

Please read and follow the 'blank screen problems' thread below. 

You will be changing the 'nomodeset' boot parameter.

[http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html](http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html)

You might need to to enter other boot parameters There are 6 of them. You may have to do them one-by-one until you get video.

[https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options](https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options)  (Common Kernel Options Section)

***The Hedge***

:KS

---

### Post by Dutch70 on 2011-03-26
In the future to avoid doing a hard reboot on your computer. 
Press & hold (Alt + prt scrn) 

Obviously with the other hand. Press the following keys with a short pause between each one.
R-E-I-S-U-B (you may have to let off the (alt+prt scrn) keys before letting off the "B"
That will reboot your computer safely without damaging your hdd.

A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.

The order of the keys doesn't matter as long as it is REISUB or RSEIUB.
This is one of the first things you should learn & remember. You'll be glad you did.

---

### Post by deckerry on 2011-03-26
Ok so now I guess I need to configure "nomodeset". I'll follow the steps on the links and see if I can figure it out before I start asking a bunch more questions.

But one question I will ask is which problem of the following two should I fix first:

1) nomodeset
2) I managed to boot into Ubuntu without the usb and without fixing my nomodeset problem, but I can't get the internet to work. Here's an error message I got when I tried to enable the wireless driver. Maybe I could just download the file in Vista, save it to an external hard drive, boot to Ubuntu, and then try to get it in that way?

P.S. As of now, since I can't get the internet to work, I have to switch to Vista every time I want to look at this thread. Just letting you know.

---

### Post by Hedgehog1 on 2011-03-26
> **deckerry said:**
> Ok so now I guess I need to configure "nomodeset". I'll follow the steps on the links and see if I can figure it out before I start asking a bunch more questions.

But one question I will ask is which problem of the following two should I fix first:

1) nomodeset
2) I managed to boot into Ubuntu without the usb and without fixing my nomodeset problem, but I can't get the internet to work. Here's an error message I got when I tried to enable the wireless driver. Maybe I could just download the file in Vista, save it to an external hard drive, boot to Ubuntu, and then try to get it in that way?

P.S. As of now, since I can't get the internet to work, I have to switch to Vista every time I want to look at this thread. Just letting you know.

May I suggest creating a new thread.  We have managed to get Ubuntu installed.  A new thread about getting the network running is better as I know very little about that...  But others do...

***The Hedge***

:KS

---

### Post by samcot on 2011-03-26
Congratulations are in order! I was on the edge of my seat . . . :-)

---

### Post by deckerry on 2011-03-26
Ok. I'm gonna start a new thread about getting the internet to work. Does that mean that I should classify this as "SOLVED"? How do I do that?

---

### Post by deckerry on 2011-03-26
> **samcot said:**
> Congratulations are in order! I was on the edge of my seat . . . :-)
Yea me too!

---

### Post by Hedgehog1 on 2011-03-26
Please use the thread tools in the top right hand of the web page to set the thread to 'solved'.

I look forward to having you in the forums!

***The Hedge***

:KS

---

### Post by deckerry on 2011-03-26
> **Hedgehog1 said:**
> May I suggest creating a new thread.  We have managed to get Ubuntu installed.  A new thread about getting the network running is better as I know very little about that...  But others do...

***The Hedge***

:KS
The new thread is titled:
Internet Does Not Work Ubuntu 10.04.2 LTS

[Here's the link.]("http://ubuntuforums.org/showthread.php?t=1715445")

---

### Post by deckerry on 2011-03-27
> **deckerry said:**
> The new thread is titled:
Internet Does Not Work Ubuntu 10.04.2 LTS

[Here's the link.]("http://ubuntuforums.org/showthread.php?t=1715445")
Thanks everybody I am very very grateful to have such smart people helping me out.

Thanks A LOT _Hedgehog1_ [COLOR="Red"]YOU FREAKIN ROCK!!!!!!!!!!!!!!!!!!!!!![/COLOR]

---

