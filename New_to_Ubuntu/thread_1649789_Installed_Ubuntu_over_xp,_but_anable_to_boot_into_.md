---
title: "Installed Ubuntu over xp, but anable to boot into ubuntu"
date: 2010-12-20
forum: New to Ubuntu
---

### Post by droidster on 2010-12-20
Hi,
I'll preface this by saying that I am totally new to linux/ubuntu but would really like to adopt it.  I originally installed ubuntu netbook remix (10.10) with windows xp.  The ubuntu worked fine, but I got the BSOD when trying to get windows running (which I need for work).  I then partitioned the hard drive into 2 75GB partitions, one for windows NTSF and one was empty.  I re-installed windows.  I then used the live cd (USB) and divided the partition into 3 sections, root, home and another one which was recommended, but I can't remember.  I then installed Ubuntu as was recommended on the Ubuntu site.

But when I restarted the computer it goes straight to windows without an option for ubuntu.  I might have messed up when I first installed it by setting up the partitions myself.  I wanted to use the option "use largest available free space", but it wasn't an option.  Anyway, I am really a novice.  I don't mind reinstalling ubuntu if that is best, but if someone can give me pretty simple directions that would be great.  Thanks in advance for your help.

BTW, here is the script I got from running the boot info script.  I would have cut it down, but I'm not sure what is important.

Thanks

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *         24,576   154,888,191   154,863,616   7 HPFS/NTFS
/dev/sda2         154,890,238   312,580,095   157,689,858   5 Extended
/dev/sda5         304,769,024   312,580,095     7,811,072  82 Linux swap / Solaris
/dev/sda6         164,143,104   304,769,023   140,625,920  83 Linux
/dev/sda7         154,890,240   164,141,055     9,250,816  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 2004 MB, 2004877312 bytes
255 heads, 63 sectors/track, 243 cylinders, total 3915776 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63     3,915,775     3,915,713   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        4E6C190B6C18F007                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        1b7161f2-56bd-4e35-a866-d546fe642828   swap                                     
/dev/sda6        e062da82-0c49-4495-809e-086a389ef15d   ext3                                     
/dev/sda7        23e8e0bd-d90c-4e8b-915b-018721a08586   ext3                                     
/dev/sda: PTTYPE="dos" 
/dev/sdc1        8862-44BF                              vfat       PENDRIVE                      
/dev/sdc: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdc1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

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
search --no-floppy --fs-uuid --set e062da82-0c49-4495-809e-086a389ef15d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set e062da82-0c49-4495-809e-086a389ef15d
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
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set e062da82-0c49-4495-809e-086a389ef15d
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=e062da82-0c49-4495-809e-086a389ef15d ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set e062da82-0c49-4495-809e-086a389ef15d
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=e062da82-0c49-4495-809e-086a389ef15d ro single 
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
    search --no-floppy --fs-uuid --set e062da82-0c49-4495-809e-086a389ef15d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set e062da82-0c49-4495-809e-086a389ef15d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 4e6c190b6c18f007
    drivemap -s (hd0) ${root}
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
UUID=e062da82-0c49-4495-809e-086a389ef15d /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=23e8e0bd-d90c-4e8b-915b-018721a08586 /home           ext3    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=1b7161f2-56bd-4e35-a866-d546fe642828 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


  89.9GB: boot/grub/core.img
  90.0GB: boot/grub/grub.cfg
  89.9GB: boot/initrd.img-2.6.35-22-generic
  89.9GB: boot/vmlinuz-2.6.35-22-generic
  89.9GB: initrd.img
  89.9GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 40 02 00  |.X.SYSLINUX..@..|
00000010  02 00 02 00 00 f8 ef 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  c1 bf 3b 00 80 00 29 bf  44 62 88 4e 4f 20 4e 41  |..;...).Db.NO NA|
00000030  4d 45 20 20 20 20 46 41  54 31 36 20 20 20 33 c9  |ME    FAT16   3.|
00000040  8e d1 bc f0 7b 8e d9 b8  00 20 8e c0 fc bd 00 7c  |....{.... .....||
00000050  38 4e 24 7d 24 8b c1 99  e8 3c fa fc 31 c9 8e d1  |8N$}$....<..1...|
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
00000100  7d 00 66 b8 80 f0 15 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
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


=======Devices which don't seem to have a corresponding hard drive==============

sdb

---

### Post by sikander3786 on 2010-12-20
Welcome to the forums :-)

Boot an Ubuntu Maverick/Lucid/Karmic Live CD and from Applications > Accessories > Terminal:

```
sudo mount /dev/sda6 /mnt
```

```
sudo grub-install --root-directory=/mnt/ /dev/sd[COLOR="Red"]a[/COLOR]
```

Note, for the second one it is just sda without an integer ;-)

Reboot and boot from you HDD. Hopefully, it would let you boot Ubuntu. If Windows was not listed, from intalled Ubuntu's Terminal,

```
sudo update-grub
```

Good Luck!

---

### Post by droidster on 2010-12-20
> **sikander3786 said:**
> Welcome to the forums :-)

Boot an Ubuntu Maverick/Lucid/Karmic Live CD and from Applications > Accessories > Terminal:

```
sudo mount /dev/sda6 /mnt
```

```
sudo grub-install --root-directory=/mnt/ /dev/sd[COLOR="Red"]a[/COLOR]
```

Note, for the second one it is just sda without an integer ;-)

Reboot and boot from you HDD. Hopefully, it would let you boot Ubuntu. If Windows was not listed, from intalled Ubuntu's Terminal,

```
sudo update-grub
```

Good Luck!

Thanks!!!  That worked perfectly. I really appreciate your help.

---

