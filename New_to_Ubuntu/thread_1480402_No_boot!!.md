---
title: "No boot!!"
date: 2010-05-11
forum: New to Ubuntu
---

### Post by monkeyyking on 2010-05-11
Hi ):P

SOOO I finally decided to ditch winblows and go full time ubuntu:guitar::guitar:

First I got exited ,downloaded,booted into the live CD environment, choose to install fully, played some solitaire while it installs, reboot 3..2..1.. nothing but blank screen with a blinking underscore in top left corner, downed and burned 3CDs now, no success :confused:

PLEASE help me :-({|= [-o<

SYSTEM:
# AMD Phenom II X4 955 Black Edition 3.2 GHz Socket AM3 8MB Processor
# Samsung EcoGreen F2 1TB 32MB Cache Hard Drive
# Maxtor 80GB 7200rpm 8MB Cache Hard Drive
# Sony 24x DVD±RW DL & RAM Internal SATA Drive 
# MSI 770-C45 ATX Motherboard
# Corsair 550W VX Series PSU
# Evga e-GeForce 8800 GT SSC 512mb (G92 chip)=same as 9800gt 
# Crucial 2GB DDR3 1333MHz/PC3-10600 Memory CL9 1.5 V Unbuffered Non-ECC (X2 sticks )

---

### Post by Kafubie on 2010-05-11
So...  You are saying you didn't actually test it out?
You just installed it?

---

### Post by spydeyrch on 2010-05-11
> **monkeyyking said:**
> Hi ):P

SOOO I finally decided to ditch winblows and go full time ubuntu:guitar::guitar:

First I got exited ,downloaded,booted into the live CD environment, choose to install fully, played some solitaire while it installs, reboot 3..2..1.. nothing but blank screen with a blinking underscore in top left corner, downed and burned 3CDs now, no success :confused:

PLEASE help me :-({|= [-o<

SYSTEM:
# AMD Phenom II X4 955 Black Edition 3.2 GHz Socket AM3 8MB Processor
# Samsung EcoGreen F2 1TB 32MB Cache Hard Drive
# Maxtor 80GB 7200rpm 8MB Cache Hard Drive
# Sony 24x DVD±RW DL & RAM Internal SATA Drive 
# MSI 770-C45 ATX Motherboard
# Corsair 550W VX Series PSU
# Evga e-GeForce 8800 GT SSC 512mb (G92 chip)=same as 9800gt 
# Crucial 2GB DDR3 1333MHz/PC3-10600 Memory CL9 1.5 V Unbuffered Non-ECC (X2 sticks )

Are your HDD SATA or IDE?

Also, have you updated your BIOS lately? I would start there.

Try the live CD if you haven't already done so, that will give you an idea of if it will work on your hardware setup.

How did you partition your system? Do you still have windows on any of the partitions? If so, windows xp, vista, or 7?

-Spydey :guitar:

---

### Post by monkeyyking on 2010-05-11
been dual-booting for ages, the problems with 10.04 , karmic worked fine, drives are sata, it was full automatic  install ubuntu is only os ond rive.

---

### Post by philinux on 2010-05-11
Boot the live cd and press any key at first graphic. Select check cd for defects.

---

### Post by monkeyyking on 2010-05-11
checking..

---

### Post by monkeyyking on 2010-05-11
checking finished: no errors found

---

### Post by philinux on 2010-05-11
boot the system and press the shift key pronto to get the grub menu. Choose the recovery mode option. Then at the menu choose resume normal boot

---

### Post by monkeyyking on 2010-05-11
nothings happening

---

### Post by spydeyrch on 2010-05-11
Are you using the x64 or x32 flavor?

-Spydey :guitar:

---

### Post by monkeyyking on 2010-05-11
x64 already tried x32 same thing

---

### Post by spydeyrch on 2010-05-11
> **monkeyyking said:**
> x64 already tried x86 same thing

Strange, I had some very similar issues with the x32 (x86) flavor but went to the x64 (x86-64) flavor and those issues went away. Interesting ....... :confused:

It probably won't make a difference but have you tried installing from a live pen drive? Like I said, I don't see why or how it would make a difference but it is something that I would personally try. I am assuming your system can boot from a USB pen drive. Just a thought. :KS

-Spydey :guitar:

---

### Post by monkeyyking on 2010-05-11
tried aswell, nothing :(

---

### Post by philinux on 2010-05-11
> **monkeyyking said:**
> nothings happening

Did you run the live cd to the desktop and did it run ok?

---

### Post by monkeyyking on 2010-05-11
yes Live cd runs fine, after the install first reboot there's nothing

---

### Post by monkeyyking on 2010-05-12
anyone? 8-[

---

### Post by kansasnoob on 2010-05-12
When you said "nothing happened" when you tried booting into Recovery Mode what did you mean?

Were you even able to select Recovery Mode?

If so did it complete to where you saw a list of options like:

resume
clean
dpkg
failsafeX
grub
netroot
root

If it gets that far you might try "failsafeX" which is like Safe Graphics mode.

Otherwise, since you can run the Live CD, it might help to see the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Ozymandias_117 on 2010-05-12
It sounds like a GRUB issue... try following the steps [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") to reinstall it.


Edit: Unless I misunderstood what you meant by "Nothing Happens" if you DID get to the Recovery Console part, ignore my post.

---

### Post by monkeyyking on 2010-05-12
No what I meant was no matter what I press shift etc I't goes straight from post messeges to a blank screen

---

### Post by kansasnoob on 2010-05-12
> **monkeyyking said:**
> No what I meant was no matter what I press shift etc I't goes straight from post messeges to a blank screen

So you've tried holding down the shift key right after the System/BIOS screen passes?

If so, and if you don't even get the boot menu please use the Live CD and post the output of the Boot Info Script:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

It provides a lot of info regarding the boot process.

---

### Post by monkeyyking on 2010-05-12
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => No known boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048 1,929,746,431 1,929,744,384  83 Linux
/dev/sda2       1,929,748,478 1,953,523,711    23,775,234   5 Extended
/dev/sda5       1,929,748,480 1,953,523,711    23,775,232  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   149,843,967   149,841,920  83 Linux
/dev/sdb2         149,846,014   156,301,311     6,455,298   5 Extended
/dev/sdb5         149,846,016   156,301,311     6,455,296  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1028 MB, 1028653056 bytes
255 heads, 63 sectors/track, 125 cylinders, total 2009088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63     2,008,124     2,008,062   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        4e881d11-8cf6-4f63-b050-04a53146536a   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        f689feb6-8359-4e74-b8fc-d0af8e3859e9   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        359c893f-cfc8-43c2-b52d-d6a17eaf26eb   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        ed739bbf-e70a-4c42-bd36-fb6a6fe5dc6b   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        DE6E-61CC                              vfat                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/DE6E-61CC         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 4e881d11-8cf6-4f63-b050-04a53146536a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 4e881d11-8cf6-4f63-b050-04a53146536a
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4e881d11-8cf6-4f63-b050-04a53146536a
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=4e881d11-8cf6-4f63-b050-04a53146536a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4e881d11-8cf6-4f63-b050-04a53146536a
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=4e881d11-8cf6-4f63-b050-04a53146536a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4e881d11-8cf6-4f63-b050-04a53146536a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4e881d11-8cf6-4f63-b050-04a53146536a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 1d75eb8c-67c3-4dc2-9b21-984350fb97fb
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=1d75eb8c-67c3-4dc2-9b21-984350fb97fb ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 1d75eb8c-67c3-4dc2-9b21-984350fb97fb
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=1d75eb8c-67c3-4dc2-9b21-984350fb97fb ro single
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f689feb6-8359-4e74-b8fc-d0af8e3859e9 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 195.5GB: boot/grub/core.img
 814.0GB: boot/grub/grub.cfg
 195.5GB: boot/initrd.img-2.6.32-21-generic
 195.5GB: boot/vmlinuz-2.6.32-21-generic
 195.5GB: initrd.img
 195.5GB: vmlinuz

=========================== sdb1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 359c893f-cfc8-43c2-b52d-d6a17eaf26eb
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 359c893f-cfc8-43c2-b52d-d6a17eaf26eb
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 359c893f-cfc8-43c2-b52d-d6a17eaf26eb
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=359c893f-cfc8-43c2-b52d-d6a17eaf26eb ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 359c893f-cfc8-43c2-b52d-d6a17eaf26eb
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=359c893f-cfc8-43c2-b52d-d6a17eaf26eb ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 359c893f-cfc8-43c2-b52d-d6a17eaf26eb
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 359c893f-cfc8-43c2-b52d-d6a17eaf26eb
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4e881d11-8cf6-4f63-b050-04a53146536a
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=4e881d11-8cf6-4f63-b050-04a53146536a ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4e881d11-8cf6-4f63-b050-04a53146536a
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=4e881d11-8cf6-4f63-b050-04a53146536a ro single
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=359c893f-cfc8-43c2-b52d-d6a17eaf26eb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=ed739bbf-e70a-4c42-bd36-fb6a6fe5dc6b none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


  51.6GB: boot/grub/core.img
  30.2GB: boot/grub/grub.cfg
  51.6GB: boot/initrd.img-2.6.32-21-generic
  51.6GB: boot/vmlinuz-2.6.32-21-generic
  51.6GB: initrd.img
  51.6GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdc

00000000  eb 06 00 00 00 00 00 00  33 c0 fa 8e d0 bc 00 7c  |........3......||
00000010  fb 8e d8 8b f4 8e c0 bf  26 7e 06 57 bf 00 7e b9  |........&~.W..~.|
00000020  00 02 fc f3 a4 cb be 02  7e ad 8b c8 66 ad bb 00  |........~...f...|
00000030  80 83 f9 00 75 2e be be  7f ac 3c 80 74 1b 83 c6  |....u.....<.t...|
00000040  0f 81 fe fe 7f 75 f2 be  44 7f e8 33 00 be 92 7f  |.....u..D..3....|
00000050  e8 2d 00 33 c0 cd 16 cd  19 83 c6 07 66 ad b9 01  |.-.3........f...|
00000060  00 bb 00 7c 32 f6 e8 24  00 be 62 7f 72 dc 8b f3  |...|2..$..b.r...|
00000070  81 c6 fe 01 ad be 7f 7f  3d 55 aa 75 cd 06 53 cb  |........=U.u..S.|
00000080  b4 0e fc ac 3c 00 74 04  cd 10 eb f7 c3 66 60 1e  |....<.t......f`.|
00000090  06 66 50 53 51 52 8b ec  b4 41 bb aa 55 8a 56 00  |.fPSQR...A..U.V.|
000000a0  cd 13 72 39 81 fb 55 aa  75 33 f6 c1 01 74 2e 66  |..r9..U.u3...t.f|
000000b0  33 c0 66 50 66 8b 46 06  66 50 8b 46 0a 50 8b 46  |3.fPf.F.fP.F.P.F|
000000c0  04 50 66 b8 10 00 01 00  66 50 16 1f 8b f4 8b 56  |.Pf.....fP.....V|
000000d0  00 b8 00 42 02 e6 cd 13  83 c4 10 eb 50 b4 08 8a  |...B........P...|
000000e0  56 00 33 ff 8e c7 cd 13  72 43 66 83 e1 3f fe c6  |V.3.....rCf..?..|
000000f0  8a de 66 8b 46 06 66 33  d2 66 f7 f1 42 52 8a cb  |..f.F.f3.f..BR..|
00000100  66 33 d2 66 f7 f1 8a f2  59 66 3d ff 03 00 00 77  |f3.f....Yf=....w|
00000110  1b 86 e0 c0 e0 06 03 c8  8e 46 0a 8b 5e 04 8b 46  |.........F..^..F|
00000120  00 8a d0 80 c4 02 b0 01  cd 13 eb 01 f9 5a 59 5b  |.............ZY[|
00000130  66 58 72 0b 81 c3 00 02  66 40 49 0f 85 52 ff 07  |fXr.....f@I..R..|
00000140  1f 66 61 c3 0d 0a 41 63  74 69 76 65 20 70 61 72  |.fa...Active par|
00000150  74 69 74 69 6f 6e 20 6e  6f 74 20 66 6f 75 6e 64  |tition not found|
00000160  21 00 0d 0a 45 72 72 6f  72 20 72 65 61 64 69 6e  |!...Error readin|
00000170  67 20 62 6f 6f 74 20 73  65 63 74 6f 72 21 00 0d  |g boot sector!..|
00000180  0a 42 61 64 20 62 6f 6f  74 20 73 65 63 74 6f 72  |.Bad boot sector|
00000190  21 00 0d 0a 50 72 65 73  73 20 61 6e 79 20 6b 65  |!...Press any ke|
000001a0  79 2e 2e 2e 0d 0a 00 00  00 00 00 00 00 00 00 00  |y...............|
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 80 00  |................|
000001c0  01 00 0b fe 3f 7c 3f 00  00 00 fe a3 1e 00 00 00  |....?|?.........|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sda2

00000000  12 36 42 5f 3a 47 b2 6f  2b 4d 58 90 ce 99 17 ad  |.6B_:G.o+MX.....|
00000010  ab a2 56 1e 0c 9e 48 da  5f 4f 71 e8 dd 20 66 17  |..V...H._Oq.. f.|
00000020  69 70 d4 ef bb 2e c3 e7  bd a6 1c d9 35 9a 69 b2  |ip..........5.i.|
00000030  a5 95 dd 6e 6f 7c 94 44  3d 66 1b 1d a0 ad 33 4b  |...no|.D=f....3K|
00000040  f8 46 d2 78 93 4d 6b dc  19 e4 6f b4 27 3e 14 ef  |.F.x.Mk...o.'>..|
00000050  3a f7 55 2a cf a7 3a de  c8 b6 59 d8 12 72 9d ea  |:.U*..:...Y..r..|
00000060  85 5e 46 e1 0b cd 31 b6  05 b0 5a 09 ea ad 9f ca  |.^F...1...Z.....|
00000070  31 71 c7 3a 72 46 c2 12  c8 e8 32 01 79 94 2b 5c  |1q.:rF....2.y.+\|
00000080  d9 63 37 12 6b d6 9e de  4a b2 e4 c0 c7 0e 92 ad  |.c7.k...J.......|
00000090  54 aa 3a 86 a1 82 b5 47  04 a3 af 81 1e 3e 66 0a  |T.:....G.....>f.|
000000a0  bc fb ae f2 fb 8f 39 ba  b0 91 15 c1 06 89 76 ff  |......9.......v.|
000000b0  69 4b b6 f5 a3 83 9a e4  45 90 d7 3e 49 96 d4 5a  |iK......E..>I..Z|
000000c0  f5 ce b2 6b 03 21 8a b3  fe f6 f5 f4 ef 48 d2 28  |...k.!.......H.(|
000000d0  39 fb 43 71 c2 70 f9 53  53 57 b2 21 42 c4 ff b5  |9.Cq.p.SSW.!B...|
000000e0  4e 85 4b 64 ca b4 19 32  fe 88 8d 41 ca 70 2e 90  |N.Kd...2...A.p..|
000000f0  8c 63 ea e2 44 71 5b fb  f6 9f 48 12 50 f1 6f 84  |.c..Dq[...H.P.o.|
00000100  8d c8 81 c6 99 6e 6f 9d  76 f0 e4 91 de 2c 12 9f  |.....no.v....,..|
00000110  2a 2a b2 2e 72 b0 46 44  f6 10 a2 fa bc 45 aa 2d  |**..r.FD.....E.-|
00000120  7b 3e 5d 77 b8 7a 13 5d  2f d5 02 ca 74 a2 07 bd  |{>]w.z.]/...t...|
00000130  da f9 a4 3e 94 52 45 96  1a 53 c7 bf cf e7 3a 1a  |...>.RE..S....:.|
00000140  e0 90 e6 60 6f fe 8d db  f1 e0 f0 d6 d4 fa 94 52  |...`o..........R|
00000150  65 78 c6 fa f2 82 dd 59  2b 10 bf 4b ce 00 a7 b1  |ex.....Y+..K....|
00000160  84 66 25 69 06 23 66 7e  83 b9 b5 9b 46 5d 42 c6  |.f%i.#f~....F]B.|
00000170  94 4e 22 4a d3 66 98 f5  f2 ee 93 84 04 b7 77 5c  |.N"J.f........w\|
00000180  2e 66 20 7b c4 10 25 ad  af 07 59 03 12 f3 98 81  |.f {..%...Y.....|
00000190  2d 24 c0 17 81 26 fd d3  34 96 4a 54 b8 35 34 82  |-$...&..4.JT.54.|
000001a0  a8 3b e1 7c f2 ee 52 d2  3b 72 e5 f5 7f e3 1e eb  |.;.|..R.;r......|
000001b0  f8 a1 a6 47 42 eb 94 59  bc b0 ec a2 31 a1 00 fe  |...GB..Y....1...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 c8 6a 01 00 00  |............j...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb2

00000000  38 aa 30 be a5 6e 05 1f  24 4a aa c2 bf 2d 22 34  |8.0..n..$J...-"4|
00000010  1e 30 f4 6c ac 27 74 00  f5 76 43 99 52 27 19 a5  |.0.l.'t..vC.R'..|
00000020  c9 39 c2 4b 2f 3a 67 a4  8f 18 0f 28 d0 34 65 66  |.9.K/:g....(.4ef|
00000030  91 b8 bc f9 58 2b 50 b7  ec 42 cf 2b ff f9 18 46  |....X+P..B.+...F|
00000040  10 e3 42 51 90 be e0 26  44 4b 83 a0 ea 5d 81 50  |..BQ...&DK...].P|
00000050  1f 2f f5 71 80 fa 07 1e  10 c7 6e c3 da 82 33 d2  |./.q......n...3.|
00000060  d7 51 b7 b7 11 24 f7 0d  09 8c 0f 12 56 d0 fd 58  |.Q...$......V..X|
00000070  90 3e a8 be 6c bf 21 9f  28 ae 28 49 2a ea f2 b1  |.>..l.!.(.(I*...|
00000080  e4 2a 29 65 fa 91 35 c1  a7 83 ba 66 5d b6 61 e8  |.*)e..5....f].a.|
00000090  ab 8c dc c7 64 a0 24 a1  fe 9e 05 a5 38 59 dd 4b  |....d.$.....8Y.K|
000000a0  ff 17 a1 42 93 2f 20 aa  e6 d7 8c 84 45 37 36 67  |...B./ .....E76g|
000000b0  39 c2 99 74 b0 c5 9a 8c  58 40 0e c0 4c f6 7d 08  |9..t....X@..L.}.|
000000c0  f2 c0 25 38 23 26 42 31  8d 30 8d 54 56 7a 03 3d  |..%8#&B1.0.TVz.=|
000000d0  02 87 e7 ad 97 57 0a c7  ff 3c 4a 80 ad e9 59 51  |.....W...<J...YQ|
000000e0  84 cc c0 2e f4 9e 23 bc  66 38 c6 bf da a8 50 d1  |......#.f8....P.|
000000f0  ce 84 cf 5a 62 7e fd bc  bb 39 c2 ce a5 5b f9 8c  |...Zb~...9...[..|
00000100  7c e4 77 0d 4c be 49 b5  37 94 3e ab 17 e8 a6 8d  ||.w.L.I.7.>.....|
00000110  65 60 58 63 5a 61 fa d2  53 df 7c 93 7a 74 e6 23  |e`XcZa..S.|.zt.#|
00000120  a3 af 54 bb 74 ae 3e 82  c9 ef fd 02 56 63 8b d8  |..T.t.>.....Vc..|
00000130  8f c4 8b b0 c4 29 89 71  91 d8 82 b5 75 5b a7 7c  |.....).q....u[.||
00000140  c1 d6 5e 21 b4 97 8a 8d  e4 ef 0c aa df 40 8a 1a  |..^!.........@..|
00000150  13 58 6e 2a eb fd 32 01  3b c9 dc 1e de 39 c4 01  |.Xn*..2.;....9..|
00000160  9e 00 9d 27 53 a1 b3 3c  4f 3c 72 8d fa a8 28 bc  |...'S..<O<r...(.|
00000170  ba c3 0c b7 16 06 7e ea  1a 5d 90 b4 fd 35 c6 18  |......~..]...5..|
00000180  01 d6 1a b6 9b f3 43 f9  d4 7f 37 91 ef c3 ef 24  |......C...7....$|
00000190  4c ae 6a 40 8c 6c f4 95  f6 3a a8 61 19 78 34 2b  |L.j@.l...:.a.x4+|
000001a0  b3 ff dc b4 d2 b6 c2 2b  39 60 64 a0 05 b8 66 bb  |.......+9`d...f.|
000001b0  91 c0 92 ae 96 56 1d 68  97 08 2b 0b 7c 29 00 fe  |.....V.h..+.|)..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 80 62 00 00 00  |............b...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by kansasnoob on 2010-05-12
This is going to take a bit as I need to compare UUID's, etc.

You are aware that you have Ubuntu installed twice aren't you?

All of drive sda and all of drive sdb are 100% Ubuntu.

The only thing that really jumps out at me otherwise is this:

> =================== sda1: Location of files loaded by Grub: ===================


195.5GB: boot/grub/core.img
814.0GB: boot/grub/grub.cfg
195.5GB: boot/initrd.img-2.6.32-21-generic
195.5GB: boot/vmlinuz-2.6.32-21-generic
195.5GB: initrd.img
195.5GB: vmlinuz

Compared to this:

> =================== sdb1: Location of files loaded by Grub: ===================


51.6GB: boot/grub/core.img
30.2GB: boot/grub/grub.cfg
51.6GB: boot/initrd.img-2.6.32-21-generic
51.6GB: boot/vmlinuz-2.6.32-21-generic
51.6GB: initrd.img
51.6GB: vmlinuz

Notice the numbers? Now that's supposed to indicate size of files, and I'm aware that the script doesn't get that 100% right yet, I'm sure Meierfra is working towards fixing that, but those numbers for the Ubuntu on sda look very high.

Give me a bit to do a more thorough of parsing all that info and I'll be back.

---

### Post by kansasnoob on 2010-05-12
Well, that all looks fine, but before we go any further I want you to verify that you know you have Ubuntu installed both to all of drive sda (the 1TB drive), and also to all of drive sdb (the 80GB drive).

---

### Post by monkeyyking on 2010-05-12
Didn't know that, should I try formating both my drives using disk tool before installing again? BTW pclinuxos, opensuse, sabayon all work it just lucid givin me this problem , just thought it would help.

---

### Post by kansasnoob on 2010-05-12
> **monkeyyking said:**
> Didn't know that, should I try formating both my drives using disk tool before installing again? BTW pclinuxos, opensuse, sabayon all work it just lucid givin me this problem , just thought it would help.

I just wanted to be sure that you knew what was up with your drives, just in case one was a mistake ;)

My first thought is that you might still have the 80GB drive set to boot first in BIOS. Have you checked?

Or you could install the sdb1 Lucid's grub2 to the mbr of sdb if that's what you want to do?

My second thought is that having basically just one large partition (+ SWAP) on that 1TB drive won't work. It's odd to see that, I have a 500GB and look at it:

[ATTACH]156646[/ATTACH]

You can see that I have several operating systems, each with a small separate /home, and 4 separate data partitions that I symlink to each OS so they easily share data. Now not many people would care to go to the trouble of symlinking the separate data partitions so they'd want much larger /home partitions.

Do you plan on multi-booting with other operating systems? Or maybe running other OS's in a vm? I mean it's kind of hard to plan partitioning for someone else because we all have different wants and needs.

Something very basic though - you can only have a total of 4 primary partitions - that's why I have 3 primaries and one extended. The extended partition can hold a lot of logical partitions. I'm sure there's a limit to the number of logical partitions but I've never reached it yet.

Anyway I'd recommend reinstalling to the 1TB drive using a pre-partitioning approach like this:

[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

Of course there he's dual-booting with Windows and you're not, he's also not creating a separate /home which I consider almost a must have! Having a separate /home means you can retain most of your settings, data, etc. when you end up having to reinstall. (Just be sure NOT to reformat the /home when reinstalling)

Actually this one shows the Lucid installer and creating a separate /home (but the /home is on a different drive):

[http://members.iinet.net/~herman546/p28.html](http://members.iinet.net/~herman546/p28.html)

Of course you'll want to skip the part about creating a Live USB, and you'd want your /home on the same drive, he also skipped creating a SWAP and don't do that!

Those are just some nice illustrated guides to give you an idea what to expect from the installer. As I said it's hard to plan someone else's partitioning.

What are your future plans?

---

### Post by monkeyyking on 2010-05-12
IT's the other way round I installed to the 80gb and intended to use the 1tb for files incase something happened to the OS I've tried disconnecting the one drive and just installing fully on the other and both freshly formatted with only one containing anything at all still no joy:(

---

### Post by kansasnoob on 2010-05-12
> **monkeyyking said:**
> IT's the other way round I installed to the 80gb and intended to use the 1tb for files incase something happened to the OS I've tried disconnecting the one drive and just installing fully on the other and both freshly formatted with only one containing anything at all still no joy:(

OK, that makes sense, and the Lucid on sdb does not have it's grub installed to any drives mbr!

Give me just a few minutes to review your info again (I get to working on so many of these I get confused sometimes).

This should be a piece of cake but I do need to know which drive is set to boot first in the BIOS.

---

### Post by kansasnoob on 2010-05-12
Well to hand boot off to the Lucid on sdb1 copy-n-paste the following commands (NOTE: I'm assuming you'll set sdb - the 80GB drive - to boot first in BIOS):

```
sudo mount /dev/sdb1 /mnt && sudo mount --bind /dev /mnt/dev &&sudo mount --bind /proc /mnt/proc && sudo chroot /mnt
```

```
grub-install /dev/sdb
```

If that returns any errors run:

```
grub-install --recheck /dev/sdb
```

Then just exit the chroot and unmount:

```
exit
```

```
sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

---

### Post by monkeyyking on 2010-05-12
OH-MY-GOD IT WORKED!!! 

you rock [kansasnoob]("http://ubuntuforums.org/member.php?u=554595") :guitar:

Why did it work?

---

### Post by kansasnoob on 2010-05-12
> **monkeyyking said:**
> OH-MY-GOD IT WORKED!!! 

you rock [kansasnoob]("http://ubuntuforums.org/member.php?u=554595") :guitar:

Why did it work?

Because I know what I'm doing ........ most of the time :lolflag:

There are some boot issues I don't understand well, like if someone uses a separate /boot partition I'm fairly lost.

I just multi-boot a lot so I've had to learn this stuff :)

---

### Post by monkeyyking on 2010-05-12
So what was the problem?

---

### Post by kansasnoob on 2010-05-12
Just what I said:

> OK, that makes sense, and the Lucid on sdb does not have it's grub installed to any drives mbr!

But that Lucid on sda I think is somehow hosed, remember when I pointed out the large size of the boot files. It just doesn't look right. I'm guessing because it's such an incredibly large partition, that's unusual.

Using the large drive for data makes much more sense. Most of my data goes on external drives that get sealed in Tupperware and locked up in my gun safe. I've lost data due to fire, theft, flood, and a malicious Ex so I'm paranoid :)

---

### Post by monkeyyking on 2010-05-12
I'm not sure I understand but inn any cast thanks. ):P

---

### Post by kansasnoob on 2010-05-12
Oh and one other thing! With more than one drive you must tell the installer where to install grub:

[http://members.iinet.net.au/%7Eherman546/p22/036.png](http://members.iinet.net.au/%7Eherman546/p22/036.png)

That's a shot of the final installation screen. There's an advanced button in the lower right hand corner. When you click on it that new window appears.

By now you probably know that drives end in letters like sda, sdb, sdc. And partitions end in numbers like sda1, sdb3, sda2, etc. It's almost never a good idea to install grub to a partition!!!!!!!!!!

And unless you make a selection the default is always drive #1 (/dev/sda).

---

### Post by monkeyyking on 2010-05-12
will remember thanks a bunch :KS

---

