---
title: "Start up  problem"
date: 2011-06-15
forum: New to Ubuntu
---

### Post by Mccfuzz on 2011-06-15
Until yesterday my Ubuntu 10.10 was booting perfectly.  Today I was greeted with the message:
"An error occurred while mounting /media/drive
Press S skip mounting or M for manual recovery.

I press S and it then boots normally.

Anyone know the fix for this?

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  nodev,noexec,nosuid       0  0  
# / was on /dev/sdb2 during installation
UUID=2e65e39b-c9c9-4627-814a-077d6ae24fa1  /               ext4  defaults         0  1  
# swap was on /dev/sdb7 during installation
UUID=1bdb7a63-b579-4d6e-be10-304962df81f4  none            swap  sw                        0  0  
/dev/fd0                                   /media/floppy0  auto  rw,user,noauto,exec,utf8  0  0  
/dev/sdc1                                  /media/Drive Two  vfat  defaults                  0  0  
/dev/sdc1                                  /media/Drive Two  vfat  users                     0  0  
/dev/sdc1                                  /media/sda2     vfat  defaults                  0  0

---

### Post by jtarin on 2011-06-15
Do you have an external drive uplugged?

---

### Post by Mccfuzz on 2011-06-15
Hi there

I don't have an external drive just a USB although simultaneously I did have a problem with a second internal hard drive.

It was functioning fine and then today it appeared to have unformatted itself.
I've since re formatted and it is now functioning normally.
The only other thing I did prior to the problem was to download 'Storage Device Manager'.
Whether any of the above ids related I can't say!

---

### Post by jtarin on 2011-06-15
[Run boot info script and post results.]("http://sourceforge.net/projects/bootinfoscript/")

---

### Post by pqwoerituytrueiwoq on 2011-06-15
```
/dev/sdc1                                  /media/Drive Two  vfat  defaults                  0  0  
/dev/sdc1                                  /media/Drive Two  vfat  users                     0  0  
```
i don't know if you can use-spaces in folders paths in fstab

---

### Post by Mccfuzz on 2011-06-16
Hi there,

Excuse my novice ignorance but how to I obtain the 'Boot Info Script"?

Re not knowing about spaces: neither do I!

Thanks...all

---

### Post by wildmanne39 on 2011-06-16
> **Mccfuzz said:**
> Hi there,

Excuse my novice ignorance but how to I obtain the 'Boot Info Script"?

Re not knowing about spaces: neither do I!

Thanks...allHi, click on the script link that jtarin posted, I know took me awhile to realize the words he types are links a lot of time like in this case, I thinks it is because he is such a jokester. He make me laugh at the things he posts.

---

### Post by jtarin on 2011-06-16
> **wildmanne39 said:**
> Hi, click on the script link that jtarin posted, I know took me awhile to realize the words he types are links a lot of time like in this case, I thinks it is because he is such a jokester. He make me laugh at the things he posts.
Actually I have always done it this way. I don't like links in plain site......goes back to the days of link spamming.

---

### Post by jtarin on 2011-06-16
> **Mccfuzz said:**
> 
Re not knowing about spaces: neither do I!

Thanks...all
I wouldn't recommend spaces. You should use UUID.
[Info FSTAB]("https://help.ubuntu.com/community/Fstab")
[Converting to UUID.]("https://help.ubuntu.com/community/UsingUUID")

---

### Post by Mccfuzz on 2011-06-16
Hi there'
I think this is what you requested.
Took me some time to figure out how it works.
Too used to windows and click on 'setup' methodology.
Someone suggested delving into the UUID .  What!
Is Ubuntu supposed to give one a headache!!:lolflag:           


     Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 2 for .
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 2 for (,msdos2)/boot/grub.
 => Windows is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63. But according to the info from fdisk, 
                       sda5 starts at sector 16128. "63" and "2048" are quite 
                       common values for the starting sector of a logical 
                       partition and they only need to be fixed when you want 
                       to boot Windows from a logical partition.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdb2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdb4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: FAT32
    Boot sector info:   According to the info in the boot sector, sdb5 starts 
                       at sector 63. But according to the info from fdisk, 
                       sdb5 starts at sector 240220008. "63" and "2048" are 
                       quite common values for the starting sector of a 
                       logical partition and they only need to be fixed when 
                       you want to boot Windows from a logical partition.
    Operating System:  
    Boot files:        

sdb6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sdb6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sdb7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1              16,065    80,292,869    80,276,805   f W95 Extended (LBA)
/dev/sda5              16,128    80,292,869    80,276,742   b W95 FAT32


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63    84,983,849    84,983,787  1c Hidden W95 FAT32 (LBA)
/dev/sdb2          84,983,850   169,550,009    84,566,160  83 Linux
/dev/sdb3    *    169,550,010   240,219,944    70,669,935   c W95 FAT32 (LBA)
/dev/sdb4         240,220,006   390,716,864   150,496,859   f W95 Extended (LBA)
/dev/sdb5         240,220,008   285,266,204    45,046,197   b W95 FAT32
/dev/sdb6         285,266,268   387,793,034   102,526,767   7 NTFS / exFAT / HPFS
/dev/sdb7         387,793,098   390,716,864     2,923,767  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 15.4 GB, 15352725504 bytes
61 heads, 61 sectors/track, 8058 cylinders, total 29985792 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               8,064    29,985,791    29,977,728   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda5        19F2-323B                              vfat       DRIVE-TWO
/dev/sdb1        2940-DBAB                              vfat       INTERNET
/dev/sdb2        2e65e39b-c9c9-4627-814a-077d6ae24fa1   ext4       
/dev/sdb3        1966-DD90                              vfat       EBAY P2P
/dev/sdb5        4565-77FD                              vfat       BACKUP DRIV
/dev/sdb6        42DC5149DC51387D                       ntfs       Shared Docs
/dev/sdb7        1bdb7a63-b579-4d6e-be10-304962df81f4   swap       
/dev/sdc1        418A-3271                              vfat       USB2

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb2        /                        ext4       (rw,commit=0)
/dev/sdc1        /media/sda2              vfat       (rw)
/dev/sr0         /media/CONFLICT DESERT STORM iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


================================ sdb1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINNT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows 2000 Professional" /fastdetect 
--------------------------------------------------------------------------------

=========================== sdb2/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(hd1,msdos2)'
search --no-floppy --fs-uuid --set 2e65e39b-c9c9-4627-814a-077d6ae24fa1
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos2)'
search --no-floppy --fs-uuid --set 2e65e39b-c9c9-4627-814a-077d6ae24fa1
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set 2e65e39b-c9c9-4627-814a-077d6ae24fa1
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=2e65e39b-c9c9-4627-814a-077d6ae24fa1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set 2e65e39b-c9c9-4627-814a-077d6ae24fa1
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=2e65e39b-c9c9-4627-814a-077d6ae24fa1 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set 2e65e39b-c9c9-4627-814a-077d6ae24fa1
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=2e65e39b-c9c9-4627-814a-077d6ae24fa1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set 2e65e39b-c9c9-4627-814a-077d6ae24fa1
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=2e65e39b-c9c9-4627-814a-077d6ae24fa1 ro single 
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
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set 2e65e39b-c9c9-4627-814a-077d6ae24fa1
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set 2e65e39b-c9c9-4627-814a-077d6ae24fa1
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows 2000 Professional (on /dev/sdb1)" {
    insmod part_msdos
    insmod fat
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 2940-dbab
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows 2000 Professional (on /dev/sdb3)" {
    insmod part_msdos
    insmod fat
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set 1966-dd90
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
--------------------------------------------------------------------------------

=============================== sdb2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  nodev,noexec,nosuid       0  0  
# / was on /dev/sdb2 during installation
UUID=2e65e39b-c9c9-4627-814a-077d6ae24fa1  /               ext4  defaults         0  1  
# swap was on /dev/sdb7 during installation
UUID=1bdb7a63-b579-4d6e-be10-304962df81f4  none            swap  sw                        0  0  
/dev/fd0                                   /media/floppy0  auto  rw,user,noauto,exec,utf8  0  0  
/dev/sdc1                                  /media/Drive Two  vfat  defaults                  0  0  
/dev/sdc1                                  /media/Drive Two  vfat  users                     0  0  
/dev/sdc1                                  /media/sda2     vfat  defaults                  0  0  
--------------------------------------------------------------------------------

=================== sdb2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  66.770905495 = 71.694713856   boot/grub/core.img                             1
  62.741387367 = 67.368051712   boot/grub/grub.cfg                             2
  41.783829689 = 44.865045504   boot/initrd.img-2.6.35-22-generic              2
  41.820332527 = 44.904240128   boot/initrd.img-2.6.35-28-generic              2
  66.906056404 = 71.839831040   boot/vmlinuz-2.6.35-22-generic                 1
  41.546895027 = 44.610638848   boot/vmlinuz-2.6.35-28-generic                 2
  41.820332527 = 44.904240128   initrd.img                                     2
  41.783829689 = 44.865045504   initrd.img.old                                 2
  41.546895027 = 44.610638848   vmlinuz                                        2
  66.906056404 = 71.839831040   vmlinuz.old                                    1

================================ sdb3/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(3)\WINNT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(3)\WINNT="Microsoft Windows 2000 Professional" /fastdetect 
--------------------------------------------------------------------------------

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb4

00000000  cb 3b d7 fa ab d1 93 b0  de 75 4d 63 56 6b b6 4e  |.;.......uMcVk.N|
00000010  8b 7b be d2 2d 0e ab 88  5d dd 95 0b 78 1d 03 28  |.{..-...]...x..(|
00000020  e1 f7 ec dd 28 14 af 6d  32 89 82 68 94 01 c9 2a  |....(..m2..h...*|
00000030  1e 25 f1 98 b3 17 37 7e  e8 e4 07 a1 99 ff 98 ee  |.%....7~........|
00000040  fc 53 94 1f 4b 83 09 68  20 7a f8 eb 32 2b 8a 13  |.S..K..h z..2+..|
00000050  f7 99 3b 9c ff f4 34 73  cd 95 de 3f e9 2e e7 91  |..;...4s...?....|
00000060  fc 9b e1 a0 2f 4d 1a b5  b8 db cd e6 a5 b4 36 19  |..../M........6.|
00000070  3d 57 3c 7c ed e9 67 d4  1c ed ae 2b 00 58 2d 53  |=W<|..g....+.X-S|
00000080  ed e7 04 ba 20 a6 fe c1  0d 7d 5b 8c ae 04 0d b3  |.... ....}[.....|
00000090  66 85 52 90 d6 28 62 87  24 f6 9c cc e5 a0 8e 51  |f.R..(b.$......Q|
000000a0  a5 2c 33 14 3e ba 57 8a  aa 3c a8 46 72 55 4f 4b  |.,3.>.W..<.FrUOK|
000000b0  90 e4 d2 b7 2c 81 ed 02  f7 66 1c 02 47 40 62 60  |....,....f..G@b`|
000000c0  f5 5c 4e 14 b2 a9 64 87  bc 00 06 97 98 66 0d 7e  |.\N...d......f.~|
000000d0  79 55 57 82 86 f1 ff ee  5c bf 4f 25 e6 6e 3b 9c  |yUW.....\.O%.n;.|
000000e0  67 b0 df a7 ee ed bb 44  cb 3d 85 73 c9 b3 60 5e  |g......D.=.s..`^|
000000f0  d7 f9 1c 5e 9b 3d 0b c0  b9 38 51 5f 19 94 b3 7b  |...^.=...8Q_...{|
00000100  16 50 b1 01 ad 47 7b 95  b5 10 2f d5 39 60 d2 63  |.P...G{.../.9`.c|
00000110  2e 58 de 1d 0d cc 17 e0  99 71 74 cc 5c 87 e7 bd  |.X.......qt.\...|
00000120  99 96 48 7b 8e 85 c9 8c  a7 fe ba 03 d0 59 fc 23  |..H{.........Y.#|
00000130  d9 0c 22 33 7e ad 6f 34  3d 2d 31 68 df d9 ea 0f  |.."3~.o4=-1h....|
00000140  b1 84 10 8f 51 72 f0 7d  4c 09 a9 bd 82 ce 62 e9  |....Qr.}L.....b.|
00000150  3f 44 fe a4 a3 5f 36 b3  c3 e5 8d a3 4d 7e bb 01  |?D..._6.....M~..|
00000160  5f 6b 27 4a f0 29 57 4c  97 bb 4b b6 c5 be c5 e7  |_k'J.)WL..K.....|
00000170  ee 18 2c 2a 46 67 28 89  db 3a fd 7f 93 ac 2b 89  |..,*Fg(..:....+.|
00000180  ef 54 ea 83 97 22 8c f1  34 14 4f fe 53 61 7d 7a  |.T..."..4.O.Sa}z|
00000190  be e7 31 64 38 0c 43 58  81 fc d6 61 29 73 5e 0e  |..1d8.CX...a)s^.|
000001a0  92 33 42 ae 2c 67 74 09  ce e6 99 98 6b 71 2d 47  |.3B.,gt.....kq-G|
000001b0  d9 9d 5e 59 c7 7b ba 39  44 b7 e6 f6 dd 8c 00 01  |..^Y.{.9D.......|
000001c0  c1 ff 0b fe ff ff 02 00  00 00 b5 59 af 02 00 fe  |...........Y....|
000001d0  ff ff 05 fe ff ff b7 59  af 02 6e 6f 1c 06 00 00  |.......Y..no....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

---

### Post by compmodder26 on 2011-06-16
> --------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0 
# / was on /dev/sdb2 during installation
UUID=2e65e39b-c9c9-4627-814a-077d6ae24fa1 / ext4 defaults 0 1 
# swap was on /dev/sdb7 during installation
UUID=1bdb7a63-b579-4d6e-be10-304962df81f4 none swap sw 0 0 
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0 
/dev/sdc1 /media/Drive Two vfat defaults 0 0 
/dev/sdc1 /media/Drive Two vfat users 0 0 
/dev/sdc1 /media/sda2 vfat defaults 0 0 
--------------------------------------------------------------------------------

Your fstab file is messed up.

1.  You cannot have the mount point as "/media/Drive Two".  The space between Drive and Two is throwing it off
2.  You're trying to mount /dev/sdc1 three times.  2 times to the same location with different mount options, and 1 time to /media/sda2

To fix number 1, I would recommend changing the mount point to a folder without a space in the name.  If you really want that space then try using the following:

```
/dev/sdc1 /media/Drive\ Two vfat defaults 0 0
```

To fix number 2, simply get rid of all but two of the mount lines for /dev/sdc1

---

### Post by oldfred on 2011-06-16
+1 on compmodder26 suggestions.

After using Linux for a while, I stopped using spaces. Even my shared folders with windows do not have to have spaces.

I do use others ways to highlight like CamelCase, Under_score, with-dash, or justonename. 

mkdir drive_two
or 
mkdir DriveTwo

Edit fstab:
gksudo gedit /etc/fstab

/dev/sdc1 /media/drive_two vfat defaults 0 0 

Better to use UUID:
UUID=19F2-323B /media/drive_two vfat defaults 0 0 

After all edits run this to make sure there are no errors. If is just returns then it is ok.

sudo mount -a

---

