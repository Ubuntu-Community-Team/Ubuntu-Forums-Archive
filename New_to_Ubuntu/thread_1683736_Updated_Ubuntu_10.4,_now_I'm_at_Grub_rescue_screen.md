---
title: "Updated Ubuntu 10.4, now I'm at Grub rescue screen"
date: 2011-02-08
forum: New to Ubuntu
---

### Post by ClaudeFleming on 2011-02-08
I have successfully installed Ubuntu seven million times. This time, I went to Wal-Mart and bought a 500 GB external usb hard drive and after several attempts to install Ubuntu 10.4, got it to work. Well, a day later (tonight, to be precise) I received a notification that many different programs had been updated since 10.04 was released. So I installed them, and expected them to work. But they didn't. As soon as I booted from my usb device, I was sent to the grub rescue screen, with an "error: no such device" popping up on the computer. I can boot the live cd and look at my ubuntu upgraded hard drive, but I don't know what to do. What should I look for? Why does Ubuntu have to crash after every upgrade? All I want to do is learn how to use the Linux command prompt and have an alternative OS on my old laptop.

I guess the kernel got updated or deleted or something or was moved. Any help would be great.

Thanks and sorry for the mini-rant, but this is ridiculous: Ubuntu is advertised to be easy!

Claude

---

### Post by Quackers on 2011-02-08
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by ClaudeFleming on 2011-02-08
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   145,846,508   145,846,446   7 HPFS/NTFS
/dev/sda2         145,848,318   194,850,815    49,002,498   5 Extended
Empty Partition


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107861504 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773167 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   970,817,535   970,815,488  83 Linux
/dev/sdb2         970,819,582   976,773,119     5,953,538   5 Extended
/dev/sdb5         970,819,584   976,773,119     5,953,536  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        7464C8BE64C883F8                       ntfs       SQ004126P01                   
/dev/sda2: PTTYPE="dos" 
/dev/sda: PTTYPE="dos" 
/dev/sdb1        078c4a39-1343-468d-8178-43138bcfd852   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        28ad6df1-a9cb-47d5-a5bd-ebefd166acde   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect 

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
search --no-floppy --fs-uuid --set 078c4a39-1343-468d-8178-43138bcfd852
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
search --no-floppy --fs-uuid --set 078c4a39-1343-468d-8178-43138bcfd852
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
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 078c4a39-1343-468d-8178-43138bcfd852
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=078c4a39-1343-468d-8178-43138bcfd852 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 078c4a39-1343-468d-8178-43138bcfd852
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=078c4a39-1343-468d-8178-43138bcfd852 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 078c4a39-1343-468d-8178-43138bcfd852
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=078c4a39-1343-468d-8178-43138bcfd852 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 078c4a39-1343-468d-8178-43138bcfd852
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=078c4a39-1343-468d-8178-43138bcfd852 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 078c4a39-1343-468d-8178-43138bcfd852
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 078c4a39-1343-468d-8178-43138bcfd852
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows XP Media Center Edition (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 7464c8be64c883f8
    drivemap -s (hd0) ${root}
    chainloader +1
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
UUID=078c4a39-1343-468d-8178-43138bcfd852 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=28ad6df1-a9cb-47d5-a5bd-ebefd166acde none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


   8.7GB: boot/grub/core.img
 388.8GB: boot/grub/grub.cfg
   8.8GB: boot/initrd.img-2.6.32-24-generic
   8.8GB: boot/initrd.img-2.6.32-28-generic
   8.7GB: boot/vmlinuz-2.6.32-24-generic
   8.7GB: boot/vmlinuz-2.6.32-28-generic
   8.8GB: initrd.img
   8.8GB: initrd.img.old
   8.7GB: vmlinuz
   8.7GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  10 8b 45 08 c1 e2 05 33  10 81 e2 e0 00 00 00 31  |..E....3.......1|
00000010  10 39 4d ec 74 10 8b 7d  e4 83 c7 10 8d 75 9c a5  |.9M.t..}.....u..|
00000020  a5 a5 a5 8b 75 f4 85 f6  0f 85 3a fc 5c 00 39 4d  |....u.....:.\.9M|
00000030  e0 0f 85 40 fc 5c 00 8b  43 1c 8b 08 50 ff 51 6c  |...@.\..C...P.Ql|
00000040  85 c0 0f 84 56 3a ff ff  8b 45 08 8b 00 8b 4b 1c  |....V:...E....K.|
00000050  6a 13 ff 75 e4 c1 e8 05  83 e0 07 50 53 e8 52 a8  |j..u.......PS.R.|
00000060  00 00 e9 37 3a ff ff 83  7d 18 00 75 18 8b 4d 08  |...7:...}..u..M.|
00000070  e8 e7 c2 fe ff 8b 00 c1  e0 0b c1 f8 16 3b c7 0f  |.............;..|
00000080  84 c9 fc ff ff 8b ce e8  d0 c2 fe ff 8b 00 c1 e0  |................|
00000090  0b c1 f8 16 3b c7 0f 84  f4 08 00 00 8b 46 0c 89  |....;........F..|
000000a0  43 0c 89 5e 0c 83 7d 14  00 0f 84 82 df 08 00 5f  |C..^..}........_|
000000b0  5e 5b c9 c2 14 00 8b 75  0c 33 ff 57 57 57 ff 76  |^[.....u.3.WWW.v|
000000c0  10 8d 45 ac 50 8b cb e8  36 00 00 00 39 7d e0 75  |..E.P...6...9}.u|
000000d0  15 8b 46 14 83 f8 fe 0f  84 31 fb 5c 00 83 f8 ff  |..F......1.\....|
000000e0  0f 84 28 fb 5c 00 ff 75  fc 8d 45 ac 50 ff 15 e8  |..(.\..u..E.P...|
000000f0  1e 60 32 8b f0 f7 de 1b  f6 46 89 75 f4 e9 c7 fe  |.`2......F.u....|
00000100  ff ff 55 8b ec 81 ec 6c  01 00 00 8b 55 14 53 56  |..U....l....U.SV|
00000110  57 33 ff 47 0f b6 c2 23  c7 89 45 c8 8b c2 c1 e8  |W3.G...#..E.....|
00000120  02 23 c7 89 85 10 ff ff  ff 8b c2 c1 e8 03 23 c7  |.#............#.|
00000130  89 85 b8 fe ff ff 8b c2  c1 e8 04 23 c7 8b d9 89  |...........#....|
00000140  85 f8 fe ff ff 8b ca d1  e9 8b c2 23 cf c1 e8 05  |...........#....|
00000150  33 f6 a8 01 89 4d bc 0f  85 a2 13 06 00 3b ce 89  |3....M.......;..|
00000160  b5 f4 fe ff ff 0f 85 94  13 06 00 8b bb a8 00 00  |................|
00000170  00 83 4d 94 ff c1 ea 07  c1 ef 1b 83 e2 01 83 e7  |..M.............|
00000180  01 8b cb 89 55 a8 89 bd  bc fe ff ff 89 75 cc 89  |....U........u..|
00000190  75 d0 89 75 e4 89 75 e0  89 75 fc 89 75 f8 89 75  |u..u..u..u..u..u|
000001a0  98 e8 b7 02 00 00 85 c0  0f 85 c4 f1 00 00 f6 43  |...............C|
000001b0  7b 01 89 b5 08 ff ff ff  0f 85 b4 f1 00 00 00 00  |{...............|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

Thanks for the help!

---

### Post by Clever_Username on 2011-02-08
You might try updating grub. 
[PHP]sudo update-grub[/PHP]

---

### Post by ClaudeFleming on 2011-02-09
If I updated grub, how would I update it in the external hard drive while running the Live CD.

---

### Post by ClaudeFleming on 2011-02-09
I tried reinstalling it. Now here are my results:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   145,846,508   145,846,446   7 HPFS/NTFS
/dev/sda2         145,848,318   194,850,815    49,002,498   5 Extended
Empty Partition


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107861504 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773167 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   970,817,535   970,815,488  83 Linux
/dev/sdb2         970,819,582   976,773,119     5,953,538   5 Extended
/dev/sdb5         970,819,584   976,773,119     5,953,536  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 8029 MB, 8029470208 bytes
255 heads, 63 sectors/track, 976 cylinders, total 15682559 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             44    15,679,439    15,679,396   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        7464C8BE64C883F8                       ntfs       SQ004126P01                   
/dev/sda2: PTTYPE="dos" 
/dev/sda: PTTYPE="dos" 
/dev/sdb1        614272ff-e5ba-48f2-be94-38da14c0fdfb   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        bf4ed586-b399-4afd-883a-b15f8b74f85a   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        FAA6-C7E2                              vfat                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/FAA6-C7E2         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdb1        /media/614272ff-e5ba-48f2-be94-38da14c0fdfb ext4       (rw,nosuid,nodev,uhelper=udisks)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect 

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
search --no-floppy --fs-uuid --set 614272ff-e5ba-48f2-be94-38da14c0fdfb
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
search --no-floppy --fs-uuid --set 614272ff-e5ba-48f2-be94-38da14c0fdfb
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 614272ff-e5ba-48f2-be94-38da14c0fdfb
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=614272ff-e5ba-48f2-be94-38da14c0fdfb ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 614272ff-e5ba-48f2-be94-38da14c0fdfb
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=614272ff-e5ba-48f2-be94-38da14c0fdfb ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 614272ff-e5ba-48f2-be94-38da14c0fdfb
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 614272ff-e5ba-48f2-be94-38da14c0fdfb
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows XP Media Center Edition (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 7464c8be64c883f8
    drivemap -s (hd0) ${root}
    chainloader +1
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
UUID=614272ff-e5ba-48f2-be94-38da14c0fdfb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=bf4ed586-b399-4afd-883a-b15f8b74f85a none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


 322.2GB: boot/grub/core.img
 270.8GB: boot/grub/grub.cfg
 322.2GB: boot/initrd.img-2.6.32-24-generic
 322.2GB: boot/vmlinuz-2.6.32-24-generic
 322.2GB: initrd.img
 322.2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  10 8b 45 08 c1 e2 05 33  10 81 e2 e0 00 00 00 31  |..E....3.......1|
00000010  10 39 4d ec 74 10 8b 7d  e4 83 c7 10 8d 75 9c a5  |.9M.t..}.....u..|
00000020  a5 a5 a5 8b 75 f4 85 f6  0f 85 3a fc 5c 00 39 4d  |....u.....:.\.9M|
00000030  e0 0f 85 40 fc 5c 00 8b  43 1c 8b 08 50 ff 51 6c  |...@.\..C...P.Ql|
00000040  85 c0 0f 84 56 3a ff ff  8b 45 08 8b 00 8b 4b 1c  |....V:...E....K.|
00000050  6a 13 ff 75 e4 c1 e8 05  83 e0 07 50 53 e8 52 a8  |j..u.......PS.R.|
00000060  00 00 e9 37 3a ff ff 83  7d 18 00 75 18 8b 4d 08  |...7:...}..u..M.|
00000070  e8 e7 c2 fe ff 8b 00 c1  e0 0b c1 f8 16 3b c7 0f  |.............;..|
00000080  84 c9 fc ff ff 8b ce e8  d0 c2 fe ff 8b 00 c1 e0  |................|
00000090  0b c1 f8 16 3b c7 0f 84  f4 08 00 00 8b 46 0c 89  |....;........F..|
000000a0  43 0c 89 5e 0c 83 7d 14  00 0f 84 82 df 08 00 5f  |C..^..}........_|
000000b0  5e 5b c9 c2 14 00 8b 75  0c 33 ff 57 57 57 ff 76  |^[.....u.3.WWW.v|
000000c0  10 8d 45 ac 50 8b cb e8  36 00 00 00 39 7d e0 75  |..E.P...6...9}.u|
000000d0  15 8b 46 14 83 f8 fe 0f  84 31 fb 5c 00 83 f8 ff  |..F......1.\....|
000000e0  0f 84 28 fb 5c 00 ff 75  fc 8d 45 ac 50 ff 15 e8  |..(.\..u..E.P...|
000000f0  1e 60 32 8b f0 f7 de 1b  f6 46 89 75 f4 e9 c7 fe  |.`2......F.u....|
00000100  ff ff 55 8b ec 81 ec 6c  01 00 00 8b 55 14 53 56  |..U....l....U.SV|
00000110  57 33 ff 47 0f b6 c2 23  c7 89 45 c8 8b c2 c1 e8  |W3.G...#..E.....|
00000120  02 23 c7 89 85 10 ff ff  ff 8b c2 c1 e8 03 23 c7  |.#............#.|
00000130  89 85 b8 fe ff ff 8b c2  c1 e8 04 23 c7 8b d9 89  |...........#....|
00000140  85 f8 fe ff ff 8b ca d1  e9 8b c2 23 cf c1 e8 05  |...........#....|
00000150  33 f6 a8 01 89 4d bc 0f  85 a2 13 06 00 3b ce 89  |3....M.......;..|
00000160  b5 f4 fe ff ff 0f 85 94  13 06 00 8b bb a8 00 00  |................|
00000170  00 83 4d 94 ff c1 ea 07  c1 ef 1b 83 e2 01 83 e7  |..M.............|
00000180  01 8b cb 89 55 a8 89 bd  bc fe ff ff 89 75 cc 89  |....U........u..|
00000190  75 d0 89 75 e4 89 75 e0  89 75 fc 89 75 f8 89 75  |u..u..u..u..u..u|
000001a0  98 e8 b7 02 00 00 85 c0  0f 85 c4 f1 00 00 f6 43  |...............C|
000001b0  7b 01 89 b5 08 ff ff ff  0f 85 b4 f1 00 00 00 00  |{...............|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```
I also installed  Ubuntu in C:\ drive and deleted a lot of it in Gparted, so I'm hosed. Could you help me get my windows boot back. Now I cannot boot from C:\ drive or external usb drive. What are the grub rescue commands that I need?

I'm desperate!

Thanks,

Claude

---

