---
title: "Boot into grub rescue with no such device error"
date: 2011-03-03
forum: New to Ubuntu
---

### Post by beew on 2011-03-03
Hi,

I don't know what has happened, this is pretty weired. I was trying to install Natty on an external drive for testing. So I booted into a Natty live usb on a laptop, plug in the target external drive and installed Natty. Install was successful according to the installer but afterwards not only could I not boot from the external drive where natty is supposed to be installed (just a black screen with a little flashing cursor like thing on the upper left corner forever) Somehow I couldn't boot from the laptop at all!

This is an older computer with Lucid installed. When attempted to boot into Lucid (just switching power on) I got this message

> error: no such device: xxxxxxxxxxxxxx
and a prompt 

grub rescue>

I have done this operation (install into an external hard drive) many many times, I made sure that I installed grub in the correct drive( /dev/sdc in this case whereas the Lucid install is in the internal drive sda) This should not be happening!

There is an empty partition on the pc after I removed XP, I tried to install Maverick in the empty partition so I could at least boot into Lucid to fix thing, but Mav's installer kept crashing with I/O error, don't know if that indicates that some hard drive problem just happened coincidentally or just the Mav's live usb is corrupted.

Thanks for any help in advance.

---

### Post by wilee-nilee on 2011-03-03
Post the boot script in my signature in code tags.

---

### Post by beew on 2011-03-03
Sorry, how do I run the boot script now that I cannot boot?

---

### Post by wilee-nilee on 2011-03-03
> **beew said:**
> Sorry, how do I run the boot script now that I cannot boot?

You can boot a live cd and run it.:)

---

### Post by beew on 2011-03-03
Of course,  :) well but the damn thing just shut down right now because of overheating, I will let it cool for a bit and then do that.

Thanks in advance.

---

### Post by beew on 2011-03-03
Hi,

Here is the output

```
2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for gnak.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 247.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     7,999,487     7,997,440  83 Linux
/dev/sda2          76,324,864   105,621,503    29,296,640  83 Linux
/dev/sda3         105,623,550   156,299,263    50,675,714   5 Extended
/dev/sda5         105,623,552   152,395,775    46,772,224  83 Linux
/dev/sda6         152,397,824   156,299,263     3,901,440  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2045 MB, 2045247488 bytes
47 heads, 46 sectors/track, 1847 cylinders, total 3994624 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *            247     3,994,623     3,994,377   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       424154b6-db53-4559-bc6c-37494f20d841   ext3                                     
/dev/sda1        e812e19a-409e-4dd4-8ce4-041eb56e4cb8   ext4                                     
/dev/sda2        23a71713-5de6-455b-98dc-d28675c25c46   ext3                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        f09c7e78-0011-4048-ad9b-cfa34daed283   ext3                                     
/dev/sda6        c5fb6ab0-b621-49f3-9584-e9f8d396ce09   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        E78A-6E11                              vfat       ubuntu                        
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
UUID=e812e19a-409e-4dd4-8ce4-041eb56e4cb8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=c5fb6ab0-b621-49f3-9584-e9f8d396ce09 none            swap    sw              0       0

=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 23a71713-5de6-455b-98dc-d28675c25c46
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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 23a71713-5de6-455b-98dc-d28675c25c46
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
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 23a71713-5de6-455b-98dc-d28675c25c46
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=23a71713-5de6-455b-98dc-d28675c25c46 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 23a71713-5de6-455b-98dc-d28675c25c46
    echo    'Loading Linux 2.6.32-29-generic ...'
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=23a71713-5de6-455b-98dc-d28675c25c46 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 23a71713-5de6-455b-98dc-d28675c25c46
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=23a71713-5de6-455b-98dc-d28675c25c46 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 23a71713-5de6-455b-98dc-d28675c25c46
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=23a71713-5de6-455b-98dc-d28675c25c46 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 23a71713-5de6-455b-98dc-d28675c25c46
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=23a71713-5de6-455b-98dc-d28675c25c46 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 23a71713-5de6-455b-98dc-d28675c25c46
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=23a71713-5de6-455b-98dc-d28675c25c46 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 23a71713-5de6-455b-98dc-d28675c25c46
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 23a71713-5de6-455b-98dc-d28675c25c46
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set aa0c1fa30c1f6a19
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-26-generic (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set f3638d96-742e-45ce-96bd-afaf522a94c9
    linux /boot/vmlinuz-2.6.35-26-generic root=UUID=f3638d96-742e-45ce-96bd-afaf522a94c9 ro splash quiet splash
    initrd /boot/initrd.img-2.6.35-26-generic
}
menuentry "Ubuntu, with Linux 2.6.35-26-generic (recovery mode) (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set f3638d96-742e-45ce-96bd-afaf522a94c9
    linux /boot/vmlinuz-2.6.35-26-generic root=UUID=f3638d96-742e-45ce-96bd-afaf522a94c9 ro single splash
    initrd /boot/initrd.img-2.6.35-26-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set f3638d96-742e-45ce-96bd-afaf522a94c9
    linux /boot/vmlinuz-2.6.35-25-generic root=UUID=f3638d96-742e-45ce-96bd-afaf522a94c9 ro splash quiet splash
    initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (recovery mode) (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set f3638d96-742e-45ce-96bd-afaf522a94c9
    linux /boot/vmlinuz-2.6.35-25-generic root=UUID=f3638d96-742e-45ce-96bd-afaf522a94c9 ro single splash
    initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set f3638d96-742e-45ce-96bd-afaf522a94c9
    linux /boot/vmlinuz-2.6.35-24-generic root=UUID=f3638d96-742e-45ce-96bd-afaf522a94c9 ro splash quiet splash
    initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (recovery mode) (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set f3638d96-742e-45ce-96bd-afaf522a94c9
    linux /boot/vmlinuz-2.6.35-24-generic root=UUID=f3638d96-742e-45ce-96bd-afaf522a94c9 ro single splash
    initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set f3638d96-742e-45ce-96bd-afaf522a94c9
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=f3638d96-742e-45ce-96bd-afaf522a94c9 ro splash quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set f3638d96-742e-45ce-96bd-afaf522a94c9
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=f3638d96-742e-45ce-96bd-afaf522a94c9 ro single splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "unknown Linux distribution (on /dev/sdb10)" {
    insmod ext2
    set root='(hd1,10)'
    search --no-floppy --fs-uuid --set 7a2132ec-3542-11e0-91ec-08107463b348
    linux /boot/vmlinuz-2.6.35-1_10BOOT root=/dev/sdb10
}
menuentry "Fedora release 14 (Laughlin) (on /dev/sdb7)" {
    insmod ext2
    set root='(hd1,7)'
    search --no-floppy --fs-uuid --set c1a33d44-8ffc-4a87-8b85-791c71d9b435
    linux /boot/vmlinuz-2.6.35.10-74.fc14.i686 root=/dev/sdb7
}
menuentry "Fedora release 14 (Laughlin) (on /dev/sdb7)" {
    insmod ext2
    set root='(hd1,7)'
    search --no-floppy --fs-uuid --set c1a33d44-8ffc-4a87-8b85-791c71d9b435
    linux /boot/vmlinuz-2.6.35.11-83.fc14.i686 root=/dev/sdb7
}
menuentry "Fedora release 14 (Laughlin) (on /dev/sdb7)" {
    insmod ext2
    set root='(hd1,7)'
    search --no-floppy --fs-uuid --set c1a33d44-8ffc-4a87-8b85-791c71d9b435
    linux /boot/vmlinuz-2.6.35.6-45.fc14.i686 root=/dev/sdb7
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=23a71713-5de6-455b-98dc-d28675c25c46 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=f09c7e78-0011-4048-ad9b-cfa34daed283 /home           ext3    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=c5fb6ab0-b621-49f3-9584-e9f8d396ce09 none            swap    sw              0       0

=================== sda2: Location of files loaded by Grub: ===================


  48.1GB: boot/grub/core.img
  48.1GB: boot/grub/grub.cfg
  48.5GB: boot/initrd.img-2.6.32-25-generic
  48.7GB: boot/initrd.img-2.6.32-28-generic
  48.2GB: boot/initrd.img-2.6.32-29-generic
  48.5GB: boot/vmlinuz-2.6.32-25-generic
  48.3GB: boot/vmlinuz-2.6.32-28-generic
  48.2GB: boot/vmlinuz-2.6.32-29-generic
  48.2GB: initrd.img
  48.7GB: initrd.img.old
  48.2GB: vmlinuz
  48.3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3e 00 3f 00 00 00 00 00  |........>.?.....|
00000020  08 f3 3c 00 38 0f 00 00  00 00 00 00 02 00 00 00  |..<.8...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 11 6e 8a e7 75  62 75 6e 74 75 20 20 20  |..).n..ubuntu   |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 70 c6 15 00  66 ba 00 00 00 00 bb 00  |}.f.p...f.......|
00000110  7e e8 10 00 66 81 3e 2c  7e cd c2 8f 72 75 76 ea  |~...f.>,~...ruv.|
00000120  40 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |@~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

The 10.10 partition is sda1 is the result of an arborted Maverick installation as explained in  my first post.

Thanks.

---

### Post by wilee-nilee on 2011-03-03
Your grub script shows some changes a former fedora on a non existent partition. Lets just try reloading the mbr from the live 10.04 cd. From the booted live cd run these two commands.
```
sudo mount /dev/sda2 /mnt
```
then
```
sudo grub-install --root-directory=/mnt /dev/sda
```
reboot to the grub menu then to the install and run sudo update-grub.

---

### Post by beew on 2011-03-03
Hi,

I am now able to boot back into Lucid. Thanks a lot!

But as you can see there is a Maverick installation in sda1, that is the remnant of an abortive installation (explained in first post) in my panic attempt to boot back to lucid, now if I want to delete that partition but I am afraid that would delete grub as well.
 
My thinking is that I should delete the partition and than run in Lucid > sudo grub-install   /dev/sda and then run  > sudo update-grub  

Does it make any sense?

The Fedora partition doesn't exist on this drive, i have installed Fedora in an external drive using this computer,--which was several months ago,-- I guess that information is stored.

By the way, do you have an idea what might have happened?

Thanks again!

---

### Post by wilee-nilee on 2011-03-03
> **beew said:**
> Hi,

I am now able to boot back into Lucid. Thanks a lot!

But as you can see there is a Maverick installation in sda1, that is the remnant of an abortive installation (explained in first post) in my panic attempt to boot back to lucid, now if I want to delete that partition but I am afraid that would delete grub as well.
 
My thinking is that I should delete the partition and than run in Lucid  and then run    

Does it make any sense?

The Fedora partition doesn't exist on this drive, i have installed Fedora in an external drive using this computer,--which was several months ago,-- I guess that information is stored.

By the way, do you have an idea what might have happened?

Thanks again!

Lucid should be the controlling grub now but your correct with the commands I just assign the grub control first. I think sda1 will go now without a problem.

I have been using supergrub lately to get back in like we did with the 2 commands, then running the commands you have posted

---

### Post by beew on 2011-03-03
Hi,

Everything is working now, I really appreciate the help.

Since you are here I am wondering if  you would be able to take a look at this thread which is kind of related.
[http://ubuntuforums.org/showthread.php?t=1698582](http://ubuntuforums.org/showthread.php?t=1698582)

Sorry for being greedy, just think you may be a good person to ask that kind of question.  A  big  thanks again.

---

### Post by beew on 2011-03-04
Well I figured out what went wrong after a second attempt. 

Normally when I do an install I would manually create the partition table but since this time I am using a 4 G external drive I figured I might as well tell it to erase the whole disk and thought that it would be ok as long as I specified correctly which disk to install into. It turns out that while Natty was installed in the correct drive grub was installed in sda (the Lucid partition) instead (from the progress bar I am now seeing "running grub-install /dev/sda") 

This is a very curious behaviour that I am not aware of (like I said in all installations I have done I created the partition manually and there was an option to pick where to install grub and while I always double checked the default offered was always correct once the drive to install into is identified correctly) So maybe this is a bug?

So Natty's version of grub was injected into Lucid which somehow made it not bootable (backward incompatibility? ) and the external disk had no bootloader, so not bootable either.

---

### Post by MrGammaRay on 2011-03-11
Hi all,

New to Ubuntu and hoping to get some help.

I have an Acer Aspire One (AOD255) loaded with Win7. Wanted to give Ubuntu a try so loaded Ubuntu Netbook Remix 10.10 into a partition. All was happy until I messed something up (didn't someone say it was best to learn from mistakes? 8-) ).

So my bright idea was to just reinstall Ubuntu. Only I didn't know it would make a new partition and not overwrite the old one. So having 2 Linux OSs (one working one not) and Win7 I decided to start over. Booting into Win7 recovery I wanted to reformat the entire drive and start over. While preparing to do this I noticed that it only seemed to notice the current Windows partition and maybe wasn't going to wipe out the whole drive. So I aborted the Windows reinstall. (In retrospect that makes sense as formatting the whole drive would wipe out the protected section with Windows backup. But maybe I'm wrong.)

Unfortunately the damage was done. Got the blank screen, no such device error.

I am trying to fix the MBR/grub (still not clear how these are fitting together) but running into roadblocks. I've got the live USB running but not sure how to proceed. I've downloaded the boot.info.script to the desktop of the live USB but I get an error after typing
```
sudo bash ~desktop/boot_info_script*.sh
```.

It returns:
```
bash: ~desktop/boot_info_script*.sh: No such file or directory
```

Would definitely appreciated some help.

Thanks,

-steve-

---

### Post by lake54 on 2011-03-13
Hi Steve,

The * means swap it out for the version, in our case '055', so, the whole command should be:

~Desktop/boot_info_script055.sh

James

---

### Post by MrGammaRay on 2011-03-13
> **lake54 said:**
> Hi Steve,

The * means swap it out for the version, in our case '055', so, the whole command should be:

~Desktop/boot_info_script055.sh

James

Thanks for the response James. I did try to insert the 055 instead of *. But no luck.

Anyways, decided that my "best" course would be to boot with the live USB Ubuntu and use Gparted to delete the Ubuntu partition that contained the 2 Ubuntu systems. Then I continued to use Gparted to expand the Windows partition to take up the whole hard-drive (well almost, I left the protected Windows partition alone for future Windows recovery if needed). Then used the live USB to partition/install Ubuntu 10.10 Netbook Remix. As a byproduct it reinstalled/fixed the MBR and now it is a dual-boot machine once again.

Not sure if this was an optimal solution, but things seem to be working properly over the last couple of days. Fingers crossed.

I'll still take any advice people can throw my way as I learn the Ubuntu operating system.

cheers,

-steve-

---

