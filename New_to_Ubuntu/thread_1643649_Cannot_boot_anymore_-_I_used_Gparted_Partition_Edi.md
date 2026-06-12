---
title: "Cannot boot anymore - I used Gparted Partition Editor"
date: 2010-12-12
forum: New to Ubuntu
---

### Post by umax15 on 2010-12-12
Hi everybody,

I'm a newbie in Linux world.
Please allow me to tell you my crazy adventure.

I installed Ubuntu 10.10 a few weeks ago, on my laptop MSI-M670 (AMD Sempron, 1GB Ram, 120GB HDD, nVidia GeForce Go6100 video - sharing 128MB memory from system RAM).

I had Win XP installed on C: partition on this laptop.

When I installed Ubuntu 10.10, I decided to put Ubuntu on a separate partition, made from shrinking partition D: (extended NFTS partition, that was previously used only by Windows).

So I made a 10GB partition for Ubuntu, and a 512MB partition for swap, reducing accordingly the orignal D: extended partition. Everything worked perfectly, I am amazed of how "Windoz-user-friendly" is Ubuntu.
Actually, I never booted again in Win XP after using Ubuntu !

Anyway, although "curiosity killed the cat", I read about Kubuntu, and how shiny and great looking it is. So I sais to myself: why not?! As such, I downloaded Kubuntu Live CD, and repeated the installation on the same D: drive, again shrinking it to make room for another Linux partition (10GB Kubuntu), and a second 512MB swap partition (both formatted as ext4 file-system).

Grub 2 made all the necessary entries, and I could boot on any of these 3 OS:
- Kubuntu 10.10 (was default choice in Brub2 menu, as it was installed the latest)
- Win XP
- Ubuntu 10.10
 **All worked magically, I could boot into any of these OS and work.**

But using Ubuntu for a few weeks, the 10GB partition used for Ubuntu become too small. Also, the 512MB swap partition did not allow me to use laptop's "suspend" & "hibernate" functions, as the content of 1GB RAM could not fit into the 512MB swap used by Ubuntu.

So, after some reading and downloading, I used Gparted Partition Editor to do the following steps, in this order:
- I shrink again the remaining NTFD D: partition, to make more room for Ubunutu 10GB partition;
- I moved the Kubuntu 10GB partition "to the left", as after shrinking the D: partition, there was room left on this partition;
- I moved the 512MB swap partition used by Kubuntu, "to left", and after that I increased this swap partition to 2GB;
- the I tried to increase the 10GB Ubuntu partition, but it wouldn't let me. I could not unmount it,so I could not move it.

**OK, then I re-booted, Grub2 menu was working, and I loaded Kubuntu.**

In Kubuntu, I used KDE partition editor (or something similar), to increase and move the 10GB partition used by Ubuntu, as described below:
- I increased the originally 10GB Ubuntu partition to about 15GB, and at the same time I moved it a litle "to left", in order to increase the available space for the 512MB swap partition used by Ubuntu;
- and finnaly, I increased the originally 512MB swap partition used by Ubuntu to 2GB, taking up all the remaining space available on disk.

**These modifications appeared to went alright, as there were no error messages.**

After these "nice" changes, I turned of my laptop (as it was 3:00AM in the morning...)... I had a nice sleep thinking about how great will my Ubuntu work next day, having more spare and more swap available...
 
**When I woke up today, guess what?! The laptop is not booting ! The Grub2 menu does not appear, and I cannot do anything.**

Being used to Windoz many instalations (since Win3.1 era), I suspect somehow the boot program is trying to locate the operating systems, but cannot find them where they supposed to be on disk, as I moved al of them during the described procedure (above). So I booted again using LiveCD Ubunut 10.10, and I'm here asking for advice.

**How can I make Grub2 read and use the new location of whatever files he needs in order to show me the bot menu at start-up? **

Below is the result after using "boot_info_script055.sh" to generate info about my HDD partitions.
I hope this helps you better understand what mess I did with Gparted Partition Editor. I wonder why this software did not informed me before applying the changes "hey, you'll not be able to boot again... are you sure you want to move partitions?"
[B]
I'm clueless about what should I do now, in order to teach Grub2 about the changes, and make it read the new locations of boot-"something".[/B]

Waiting for your kind suggestions.
Thank you.


```
                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks at sector 206273248 
    of the same hard drive for core.img, but core.img can not be found at this 
    location.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr /wubildr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 8. But according to the info from fdisk, 
                       sda5 starts at sector 81920024.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
6 heads, 8 sectors/track, 4884201 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                   8    81,920,015    81,920,008   7 HPFS/NTFS
/dev/sda2          81,920,022   234,440,703   152,520,682   f W95 Ext d (LBA)
/dev/sda5          81,920,024   174,079,999    92,159,976   7 HPFS/NTFS
/dev/sda6    *    199,575,558   230,243,579    30,668,022  83 Linux
/dev/sda7         230,243,643   234,436,607     4,192,965  82 Linux swap / Solaris
/dev/sda8         174,082,048   195,469,311    21,387,264  83 Linux
/dev/sda9         195,471,360   199,573,503     4,102,144  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        F628C2DC28C29B4F                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        3014974214970A4C                       ntfs                                     
/dev/sda6        e5ba4b0f-a684-4af0-9c84-714102711d96   ext4                                     
/dev/sda7        f1a0870a-1b52-46da-bc56-a986a819bbc9   swap                                     
/dev/sda8        367605fd-6df2-4b25-9bf4-53c0904e8cd4   ext4                                     
/dev/sda9        41eb0f9c-ef43-44e0-8413-b86d6594ce91   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=0 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer 
C:\wubildr.mbr = "Ubuntu" 
 

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set e5ba4b0f-a684-4af0-9c84-714102711d96
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=800x600
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set e5ba4b0f-a684-4af0-9c84-714102711d96
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=30
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set e5ba4b0f-a684-4af0-9c84-714102711d96
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=e5ba4b0f-a684-4af0-9c84-714102711d96 ro  vga=788  quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set e5ba4b0f-a684-4af0-9c84-714102711d96
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=e5ba4b0f-a684-4af0-9c84-714102711d96 ro single  vga=788
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set e5ba4b0f-a684-4af0-9c84-714102711d96
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=e5ba4b0f-a684-4af0-9c84-714102711d96 ro  vga=788  quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set e5ba4b0f-a684-4af0-9c84-714102711d96
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=e5ba4b0f-a684-4af0-9c84-714102711d96 ro single  vga=788
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
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set e5ba4b0f-a684-4af0-9c84-714102711d96
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set e5ba4b0f-a684-4af0-9c84-714102711d96
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set f628c2dc28c29b4f
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda8)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 367605fd-6df2-4b25-9bf4-53c0904e8cd4
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=367605fd-6df2-4b25-9bf4-53c0904e8cd4 ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda8)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 367605fd-6df2-4b25-9bf4-53c0904e8cd4
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=367605fd-6df2-4b25-9bf4-53c0904e8cd4 ro single
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=e5ba4b0f-a684-4af0-9c84-714102711d96 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=f1a0870a-1b52-46da-bc56-a986a819bbc9 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 106.9GB: boot/grub/core.img
 103.0GB: boot/grub/grub.cfg
 111.1GB: boot/initrd.img-2.6.35-22-generic
 110.6GB: boot/initrd.img-2.6.35-23-generic
 107.5GB: boot/vmlinuz-2.6.35-22-generic
 108.7GB: boot/vmlinuz-2.6.35-23-generic
 110.6GB: initrd.img
 111.1GB: initrd.img.old
 108.7GB: vmlinuz
 107.5GB: vmlinuz.old

=========================== sda8/boot/grub/grub.cfg: ===========================

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
set default="5"
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
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set 367605fd-6df2-4b25-9bf4-53c0904e8cd4
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set 367605fd-6df2-4b25-9bf4-53c0904e8cd4
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=30
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
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 367605fd-6df2-4b25-9bf4-53c0904e8cd4
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=367605fd-6df2-4b25-9bf4-53c0904e8cd4 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 367605fd-6df2-4b25-9bf4-53c0904e8cd4
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=367605fd-6df2-4b25-9bf4-53c0904e8cd4 ro single 
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
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 367605fd-6df2-4b25-9bf4-53c0904e8cd4
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 367605fd-6df2-4b25-9bf4-53c0904e8cd4
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set f628c2dc28c29b4f
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set e5ba4b0f-a684-4af0-9c84-714102711d96
    linux /boot/vmlinuz-2.6.35-23-generic root=UUID=e5ba4b0f-a684-4af0-9c84-714102711d96 ro vga=788 quiet splash
    initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (recovery mode) (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set e5ba4b0f-a684-4af0-9c84-714102711d96
    linux /boot/vmlinuz-2.6.35-23-generic root=UUID=e5ba4b0f-a684-4af0-9c84-714102711d96 ro single vga=788
    initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set e5ba4b0f-a684-4af0-9c84-714102711d96
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=e5ba4b0f-a684-4af0-9c84-714102711d96 ro vga=788 quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set e5ba4b0f-a684-4af0-9c84-714102711d96
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=e5ba4b0f-a684-4af0-9c84-714102711d96 ro single vga=788
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

=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=367605fd-6df2-4b25-9bf4-53c0904e8cd4 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=41eb0f9c-ef43-44e0-8413-b86d6594ce91 none            swap    sw              0       0

=================== sda8: Location of files loaded by Grub: ===================


  98.1GB: boot/grub/core.img
  94.7GB: boot/grub/grub.cfg
  90.1GB: boot/initrd.img-2.6.35-22-generic
  89.5GB: boot/vmlinuz-2.6.35-22-generic
  90.1GB: initrd.img
  89.5GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

---

### Post by warfacegod on 2010-12-12
I would start by reinstalling GRUB2. Section 13 here: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by germanix on 2010-12-12
I believe you may need to update grub. Try the following:
Open the terminal (from the live cd) and type the following:
sudo update-grub
then press enter
I am not sure if this also works while using the live disk, if not you may have to boot in recovery mode and then update grub as explained above.

---

### Post by ajgreeny on 2010-12-12
I think in your situation the easiest thing *could* be to start again with which ever of the ubuntu family you want to keep, but there are a number of comments to make before you decide one way or another.

1.  You never need more than one swap, no matter how many Linux OSs you have on a machine; they will all find the one you have and use it.  Even a live CD will find it and use it.  You can certainly therefore delete of one of the two swaps you have, but make sure the one you keep is large enough; 2GB should be fine.

2.  You could have added kubuntu-desktop package to your installed Ubuntu which would have added the equivalent of Kubuntu to your existing Ubuntu OS.  This is the way I always used my system when I first started with Ubuntu, though now I stick with gnome, ie Ubuntu.  You then choose which to use from the login screen.

3.  I assume the NTFS partition sda5 is a data partition, not an OS partition.  If this is so, you can set it to mount at boot time of Ubuntu, and make sure all your Ubuntu apps save their data files to folders in that, rather than into folders in Ubuntu's home folders.

4.  I think it may be worth restoring an XP MBR first either with your XP install CD, or if you do not have one using the Ubuntu live CD.  Come back again if you need more detail on either procedure.

5.  Having hopefully now got XP booting again, backup all your data files from Ubuntu using the Ubuntu live CD, copying the files to an external drive.  If all your data was already on the NTFS partition you can ignore this bit, though it is always good to have backups on an external drive.

6.  Now using the live CD delete all your ubuntu/kubuntu partitions with gparted, and then install your new chosen primary ubuntu family member to the unallocated space.  You could make a separate /home partition, but if you are keeping most, if not all your data on the NTFS partition, that is probably not needed.  Let ubuntu put its grub onto the default /dev/sda.

This should give you a disk with your XP OS on one primary partition with data on the second, but logical NTFS partition.  Ubuntu will then be on a third, again logical partition, and swap on the final logical partition.  Sorry if this all seems very complicated, but you have got into a bit of a pickle by adding and moving partitions, and I think it may save you a lot of time, and give you a cleaner system to start again with Ubuntu.

---

### Post by warfacegod on 2010-12-12
Surprised I missed that. ajgreeny is right. Two swaps is totally unnecessary.

---

### Post by umax15 on 2010-12-12
Thank you.
I tried that, and it says:

```
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
/usr/sbin/grub-setup: warn: Your embedding area is unusually small.  core.img won't fit in it..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.
ubuntu@ubuntu:~$
```

I don't know what "embedding" means.
I do not understand why it says "not enouh space", when there are 6.6GB free on that partition "sda6"

Any ideas?

---

### Post by umax15 on 2010-12-12
> **germanix said:**
> I believe you may need to update grub. Try the following:
Open the terminal (from the live cd) and type the following:
sudo update-grub
then press enter
I am not sure if this also works while using the live disk, if not you may have to boot in recovery mode and then update grub as explained above.

I tried that too.
Please check below.

```
ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
ubuntu@ubuntu:~$ 

```

:confused:

---

### Post by QLee on 2010-12-12
With separate swaps for each OS, and only the specific one listed in each fstab, in a multi-boot situation you have the ability to hibernate a system and next time it is selected from the GRUB menu it can resume. With a single swap, the hibernate file from one will be overwritten when you boot to a different OS.

Not a very important or useful feature for most people. And the live cd could muck with it.

---

### Post by umax15 on 2010-12-12
> **ajgreeny said:**
> I think in your situation the easiest thing could be to start again with whichevert of the ubuntu family you want to keep, but there are a number of comments to make before you decide one way or another.

1.  You never need more than one swap, no matter how many Linux OSs you have on a machine; they will all find the one you have and use it.  Even a live CD will find it and use it.  You can certainly therefore delete of one of the two swaps you have, but make sure the one you keep is large enough; 2GB should be fine.

2.  You could have added kubuntu-desktop package to your installed Ubuntu which would have added the equivalent of Kubuntu to your existing Ubuntu OS.  This is the way I always used my system when I first started with Ubuntu, though now I stick with gnome, ie Ubuntu.  You then choose which to use from the login screen.

3.  I assume the NTFS partition sda5 is a data partition, not an OS partition.  If this is so, you can set it to mount at boot time of Ubuntu, and make sure all your Ubuntu apps save their data files to folders in that, rather than into folders in Ubuntu's home folders.

4.  I think it may be worth restoring an XP MBR first either with your XP install CD, or if you do not have one using the Ubuntu live CD.  Come back again if you need more detail on either procedure.

5.  Having hopefully now got XP booting again, backup all your data files from Ubuntu using the Ubuntu live CD, copying the files to an external drive.  If all your data was already on the NTFS partition you can ignore this bit, though it is always good to have backups on an external drive.

6.  Now using the live CD delete all your ubuntu/kubuntu partitions with gparted, and then install your new chosen primary ubuntu family member to the unallocated space.  You could make a separate /home partition, but if you are keeping most, if not all your data on the NTFS partition, that is probably not needed.  Let ubuntu put its grub onto the default /dev/sda.

This should give you a disk with your XP OS on one primary partition with data on the second, but logical NTFS partition.  Ubuntu will then be on a third, again logical partition, and swap on the final logical partition.  Sorry if this all seems very complicated, but you have got into a bit of a pickle by adding and moving partitions, and I think it may save you a lot of time, and give you a cleaner system to start again with Ubuntu.


Thank you very much for your long reply. I appreciate your coherent and systematic, detailed approach.

**How could I save my current Ubuntu setup? I changed themes,I installed and used Evolution email (and I have a lot of email in Ubuntu), etc. **

I have no problem erasing Kubuntu partition (and it's no longer necessary swap)... but starting over with Ubuntu installation will eat so many hours (Ubuntu I shall keep).

> 3.  I assume the NTFS partition sda5 is a data partition, not an OS  partition.  If this is so, you can set it to mount at boot time of  Ubuntu, and make sure all your Ubuntu apps save their data files to  folders in that, rather than into folders in Ubuntu's home folders.

**You are right, sda5 is "data partition", WinXP OS system is on sda1.**


> 4.  I think it may be worth restoring an XP MBR first either with your  XP install CD, or if you do not have one using the Ubuntu live CD.  Come  back again if you need more detail on either procedure.

Please guide me through this. I would try to reanimate my laptop, before trying to reinstall Ubuntu. **Unfortnatelly, my WinXP CD is not at hand, so I should do it using Ubunu LiveCD (which is running right now).**

Thank you.

---

### Post by Pritamsng on 2010-12-12
update grub

---

### Post by QLee on 2010-12-12
umax15,

See if this thread by forum moderator drs305, about restoring GRUB from the live CD helps:
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by ajgreeny on 2010-12-12
OK, if you want to keep your current Ubuntu system but uninstall the Kubuntu partition, you can do that from the live CD currently running, using gparted.

If you are going to keep Ubuntu there is really no need to restore the  XP MBR, so forget that unless you want to try it.  If so, from the live  CD you can install a Windows equivalent MBR to your sda drive by doing  the following:-
```
sudo apt-get install lilo
```Ignore the warning then 
 ```
sudo lilo -M  /dev/sda mbr
```Then you should be able to boot  directly into Windows again if all goes well, but don't forget that  restoring grub will again remove that XP MBR.
 
To restore grub, run ```
sudo fdisk -l
``` just to ensure we know which partition is which, and finally, restore grub using the live CD with the following:-

From that last *fdisk* command you can find the device name of your Ubuntu drive, something like &#8220;/dev/sda6&#8243;.
Still in the terminal, type:
    sudo mkdir /media/sda6
    sudo mount /dev/sda6 /media/sda6
To reinstall grub:
    sudo grub-install --root-directory=/media/sda6 /dev/sda
Press enter and you&#8217;re done! Of course you need to replace &#8220;/dev/sda6&#8243; and &#8220;/dev/sda&#8221; with what you found in the fdisk output, but if things have not changed, I think that is where they are.

To mount the NTFS data partition at boot, install and use ntfs-config in your Ubuntu installation.

All your emails etc etc in evolution should be in the hidden **~/.evolution** folder in your Ubuntu home.  You can check that from the live CD by double clicking on the ubuntu partition in Places of nautilus (or the menu) and showing hidden files and folders with Ctrl+H.  All of your customisation and configuration of Ubuntu will be in other hidden folders in that home.

---

### Post by sunmake on 2010-12-12
To restore win MBR you can use also WindowsLiveCdXP.iso (less than 60MB).

---

