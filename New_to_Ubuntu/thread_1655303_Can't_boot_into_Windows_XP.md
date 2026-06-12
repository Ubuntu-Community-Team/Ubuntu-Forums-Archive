---
title: "Can't boot into Windows XP"
date: 2010-12-29
forum: New to Ubuntu
---

### Post by DayLite on 2010-12-29
This morning I tried to boot into windows, (Ubuntu is ok). When I select windows my only choice is the System Recovery Mode.

What happened?

[IMG]http://inlinethumb61.webshots.com/21180/2863958840056553245S600x600Q85.jpg[/IMG]

---

### Post by duanedesign on 2010-12-29
Mine does this on occasion. I have not figured out exactly the issue at hand but maybe I can tell you which wires I jiggle to get Windows to boot.

Usually I boot into the Windows Partition that is showing. Sometimes it is only the Recovery Partition (can't remember if XP has 2 partitions like Vista). Try and run the Startup Repair. I can then usually boot into Linux and run in a Terminal the command 'update-grub' to get both my Windows partitions to show up in Grub. Sometimes it then takes as much as 6 restarts and running the Startup Repair in Windows to get it to boot.

If I get any better info I will post it.

---

### Post by DayLite on 2010-12-29
> **duanedesign said:**
> Mine does this on occasion. I have not figured out exactly the issue at hand but maybe I can tell you which wires I jiggle to get Windows to boot.

Usually I boot into the Windows Partition that is showing. Sometimes it is only the Recovery Partition (can't remember if XP has 2 partitions like Vista). Try and run the Startup Repair. I can then usually boot into Linux and run in a Terminal the command 'update-grub' to get both my Windows partitions to show up in Grub. Sometimes it then takes as much as 6 restarts and running the Startup Repair in Windows to get it to boot.

If I get any better info I will post it.

The System Recovery will begin to go back to the factory default settings and I will loose everything! If I start to do it, how do I stop it before is turns everything back?

You are not clear to me as to what to do. Windows XP suppose to have a regular boot and a recovery choice.  I now have only one :confused:

I did put into the terminal "update grub" and I got this:
> joan@joan-desktop:~$ update grub
No command 'update' found, did you mean:
 Command 'uupdate' from package 'devscripts' (main)
 Command 'lupdate' from package 'libqt4-dev' (main)
 Command 'lupdate' from package 'qt3-dev-tools' (main)
update: command not found


---

### Post by wilee-nilee on 2010-12-29
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags paste all the text in between.

The command you can't run is.
sudo update-grub

---

### Post by DayLite on 2010-12-29
> **wilee-nilee said:**
> So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags paste all the text in between.

The command you can't run is.
sudo update-grub

This is all confusing to me:confused:. I boot into Ubuntu alright, I need to boot also into Windows XP. In the grub, there should be two choices for windows. Regular and recovery.

---

### Post by wilee-nilee on 2010-12-29
Okay you ran the update-grub command it has to have a sudo in front of it, to work.

The botscript just needs to be downloaded dragged to your desktop then copy and paste this command to a terminal.
```
sudo bash ~/Desktop/boot_info_script*.sh 
```

This will generate a text file on the desktop right click copy copy all the text come to the thread open a reply click on the # in te reply panel you will see code tags paste that text between

---

### Post by DayLite on 2010-12-29
> **wilee-nilee said:**
> Okay you ran the update-grub command it has to have a sudo in front of it, to work.

The botscript just needs to be downloaded dragged to your desktop then copy and paste this command to a terminal.
```
sudo bash ~/Desktop/boot_info_script*.sh 
```This will generate a text file on the desktop right click copy copy all the text come to the thread open a reply click on the # in te reply panel you will see code tags paste that text between

Why do I have to download your bootscript to my computer?

I can mount Presario from Ubuntu. I saw it has a boot ini.

---

### Post by wilee-nilee on 2010-12-29
thanks

---

### Post by DayLite on 2010-12-29
I looked at the grub in my laptop and noticed it was the same as in my desktop. The only difference is that when I choose the one on my laptop it boots into windows and on my desktop it boots into system recovery.

---

### Post by DayLite on 2010-12-29
```
          Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => No known boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
240 heads, 63 sectors/track, 32301 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63     8,542,799     8,542,737   b W95 FAT32
/dev/sda2    *      8,542,800   406,813,155   398,270,356   7 HPFS/NTFS
/dev/sda3         406,814,718   488,396,799    81,582,082   5 Extended
/dev/sda5         406,814,720   485,795,839    78,981,120  83 Linux
/dev/sda6         485,797,888   488,396,799     2,598,912  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63 1,445,865,854 1,445,865,792   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        33D4-2777                              vfat       PRESARIO_RP                   
/dev/sda2        22BC8ED0BC8E9E43                       ntfs       PRESARIO                      
/dev/sda3: PTTYPE="dos" 
/dev/sda5        060f1b08-b13c-4fca-aec7-3d0856e3edf6   ext4                                     
/dev/sda6        a131b501-a7c1-4f1c-93ec-f0aa4dfc0f22   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        55D123D9E79ABF54                       ntfs       OneTouch4 Plus                
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/OneTouch4 Plus    fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2        /media/PRESARIO          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1        /media/PRESARIO_RP       vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=0 
default=C:\CMDCONS\BOOTSECT.DAT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 

================================ sda2/boot.ini: ================================

[boot loader] 
timeout=3 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 060f1b08-b13c-4fca-aec7-3d0856e3edf6
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 060f1b08-b13c-4fca-aec7-3d0856e3edf6
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
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 060f1b08-b13c-4fca-aec7-3d0856e3edf6
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=060f1b08-b13c-4fca-aec7-3d0856e3edf6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 060f1b08-b13c-4fca-aec7-3d0856e3edf6
    echo    'Loading Linux 2.6.32-27-generic ...'
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=060f1b08-b13c-4fca-aec7-3d0856e3edf6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 060f1b08-b13c-4fca-aec7-3d0856e3edf6
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=060f1b08-b13c-4fca-aec7-3d0856e3edf6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 060f1b08-b13c-4fca-aec7-3d0856e3edf6
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=060f1b08-b13c-4fca-aec7-3d0856e3edf6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 060f1b08-b13c-4fca-aec7-3d0856e3edf6
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=060f1b08-b13c-4fca-aec7-3d0856e3edf6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 060f1b08-b13c-4fca-aec7-3d0856e3edf6
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=060f1b08-b13c-4fca-aec7-3d0856e3edf6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 060f1b08-b13c-4fca-aec7-3d0856e3edf6
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=060f1b08-b13c-4fca-aec7-3d0856e3edf6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 060f1b08-b13c-4fca-aec7-3d0856e3edf6
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=060f1b08-b13c-4fca-aec7-3d0856e3edf6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 060f1b08-b13c-4fca-aec7-3d0856e3edf6
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=060f1b08-b13c-4fca-aec7-3d0856e3edf6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 060f1b08-b13c-4fca-aec7-3d0856e3edf6
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=060f1b08-b13c-4fca-aec7-3d0856e3edf6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 060f1b08-b13c-4fca-aec7-3d0856e3edf6
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=060f1b08-b13c-4fca-aec7-3d0856e3edf6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 060f1b08-b13c-4fca-aec7-3d0856e3edf6
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=060f1b08-b13c-4fca-aec7-3d0856e3edf6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 060f1b08-b13c-4fca-aec7-3d0856e3edf6
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 060f1b08-b13c-4fca-aec7-3d0856e3edf6
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
    insmod fat
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 33d4-2777
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 22bc8ed0bc8e9e43
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=060f1b08-b13c-4fca-aec7-3d0856e3edf6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=a131b501-a7c1-4f1c-93ec-f0aa4dfc0f22 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 211.1GB: boot/grub/core.img
 226.1GB: boot/grub/grub.cfg
 224.8GB: boot/initrd.img-2.6.32-21-generic
 224.8GB: boot/initrd.img-2.6.32-23-generic
 228.9GB: boot/initrd.img-2.6.32-24-generic
 231.4GB: boot/initrd.img-2.6.32-25-generic
 232.0GB: boot/initrd.img-2.6.32-26-generic
 234.1GB: boot/initrd.img-2.6.32-27-generic
 210.6GB: boot/vmlinuz-2.6.32-21-generic
 214.7GB: boot/vmlinuz-2.6.32-23-generic
 216.9GB: boot/vmlinuz-2.6.32-24-generic
 229.8GB: boot/vmlinuz-2.6.32-25-generic
 228.9GB: boot/vmlinuz-2.6.32-26-generic
 231.1GB: boot/vmlinuz-2.6.32-27-generic
 234.1GB: initrd.img
 232.0GB: initrd.img.old
 231.1GB: vmlinuz
 228.9GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdb

00000000  e8 12 01 b9 f0 01 be 10  7c bf 10 06 57 f3 a4 c3  |........|...W...|
00000010  8b 4e 14 83 f9 0e 75 08  8d 5e 07 43 02 07 e2 fb  |.N....u..^.C....|
00000020  8c 56 0c 8c 56 0e 75 69  8a 56 10 84 d2 79 62 e8  |.V..V.ui.V...yb.|
00000030  f6 00 bb aa 55 cd 13 72  6f 3b 5e 5c 75 6a d1 e9  |....U..ro;^\uj..|
00000040  73 66 b4 42 c6 46 02 01  eb 66 89 b6 f6 fe 8a 44  |sf.B.F...f.....D|
00000050  04 84 c0 74 0f 3c 05 74  0b 3c 0f 74 07 8a 14 80  |...t.<.t.<.t....|
00000060  e2 80 75 cb 83 c6 10 06  c4 5c 08 89 5e 08 8c 46  |..u......\..^..F|
00000070  0a 07 fe 8e f9 fe 75 d2  b0 31 c6 46 d5 50 88 46  |......u..1.F.P.F|
00000080  d2 be 68 07 ac 84 c0 74  08 b4 0e b3 07 cd 10 eb  |..h....t........|
00000090  f3 e8 81 00 88 46 11 be  ae 07 3c 05 75 c6 cd 16  |.....F....<.u...|
000000a0  33 d2 89 56 08 89 56 0a  e8 7d 00 72 1b b8 01 02  |3..V..V..}.r....|
000000b0  bf 05 00 8b dc 56 50 50  32 e4 cd 13 58 8b f5 cd  |.....VPP2...X...|
000000c0  13 58 5e 73 03 4f 75 eb  b0 32 72 b2 40 8a 66 11  |.X^s.Ou..2r.@.f.|
000000d0  9e 7b 04 c6 47 02 0e 72  35 75 0c 88 57 40 c4 4e  |.{..G..r5u..W@.N|
000000e0  08 89 4f 1c 8c 47 1e 79  06 8a 4e 12 88 4f 25 80  |..O..G.y..N..O%.|
000000f0  c7 02 81 7f fe 55 aa 75  85 81 7f fc cd 19 75 09  |.....U.u......u.|
00000100  c6 47 fc e9 c7 47 fd 92  88 e8 1c 00 ff e4 74 ce  |.G...G........t.|
00000110  88 57 24 eb c9 5d 33 c0  8e d8 8e c0 8e d0 bc 00  |.W$..]3.........|
00000120  7c 55 bd a2 07 fc fb c3  b4 08 52 06 cd 13 07 33  ||U........R....3|
00000130  db 8a de 8b 46 0a 33 d2  83 e1 3f f7 f1 91 97 8b  |....F.3...?.....|
00000140  46 08 f7 f7 42 87 ca 3b  da 72 17 43 f7 f3 8a f2  |F...B..;.r.C....|
00000150  86 c5 d1 e8 d1 e8 0a c8  d0 cc d0 cc 0a f4 84 e4  |................|
00000160  74 02 b4 41 5b 8a d3 c3  0d 0a 4d 42 52 20 45 72  |t..A[.....MBR Er|
00000170  72 6f 72 20 00 0d 0a 00  72 65 73 73 20 61 6e 79  |ror ....ress any|
00000180  20 6b 65 79 20 74 6f 20  62 6f 6f 74 20 66 72 6f  | key to boot fro|
00000190  6d 20 66 6c 6f 70 70 79  2e 2e 2e 00 00 00 00 00  |m floppy........|
000001a0  00 00 10 00 01 00 00 7c  00 00 00 00 00 00 00 00  |.......|........|
000001b0  00 00 00 00 00 00 00 00  ec 81 4e 26 00 00 80 01  |..........N&....|
000001c0  01 00 07 fe ff ff 3f 00  00 00 40 29 2e 56 00 00  |......?...@).V..|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sda3

00000000  5c 03 38 9f 30 30 7f fd  92 55 ca 67 a8 06 60 03  |\.8.00...U.g..`.|
00000010  ab 1e 1d 83 b0 0d 25 1b  7c 08 d5 e8 01 6d 11 39  |......%.|....m.9|
00000020  b1 a4 58 1b 7f fe ed 29  39 42 ba 47 10 63 a2 28  |..X....)9B.G.c.(|
00000030  0b 6d 65 7e 0d 7f ff 11  81 8b ff ef b0 1d 23 47  |.me~..........#G|
00000040  db 98 73 9c 23 11 61 4f  3d fc 19 3f fe 27 b8 a1  |..s.#.aO=..?.'..|
00000050  c0 70 eb 16 00 3b 96 b0  01 cc 00 00 01 06 2b 42  |.p...;........+B|
00000060  1f b1 47 8e 8c 38 8f 18  07 40 36 b7 b6 10 4e 85  |..G..8...@6...N.|
00000070  10 07 40 32 bb 49 7e 03  e8 d3 ed c4 11 04 1f 09  |..@2.I~.........|
00000080  50 06 d6 87 f8 50 54 b6  92 70 11 8f 01 70 ea f3  |P....PT..p...p..|
00000090  00 64 15 1a 38 2a 12 c0  ca 00 30 0c c7 99 6c 63  |.d..8*....0...lc|
000000a0  90 23 80 5b 00 6f 1d 94  b1 41 74 44 42 08 49 5c  |.#.[.o...AtDB.I\|
000000b0  94 5a 46 7e e7 8c 49 cb  23 71 01 74 3d 9f ab 70  |.ZF~..I.#q.t=..p|
000000c0  32 4a c3 0b 25 27 ad 24  b1 a3 72 32 0b dd d1 c0  |2J..%'.$..r2....|
000000d0  7a 86 80 a8 d0 42 00 84  6c 83 ce 00 b7 93 56 53  |z....B..l.....VS|
000000e0  82 30 02 ab 30 69 74 b2  8a 41 31 29 fb 96 03 91  |.0..0it..A1)....|
000000f0  8e 02 8e ec 9e c8 26 27  bf c9 35 63 85 c0 1f 35  |......&'..5c...5|
00000100  11 50 81 9b 84 28 8f be  13 0e e1 66 f6 9c e1 9c  |.P...(.....f....|
00000110  2d 1b 1c 28 29 f3 3c 53  3a ff 11 c7 31 c2 a8 e3  |-..().<S:...1...|
00000120  ee ff 85 07 72 08 ea 60  85 93 9e 4b 37 70 b5 49  |....r..`...K7p.I|
00000130  37 eb a0 a0 80 90 9c c2  d0 cb 73 b8 f8 33 74 86  |7.........s..3t.|
00000140  b8 ce 03 c6 0c c8 75 76  0d f9 c7 6e ca 86 2c ec  |......uv...n..,.|
00000150  a5 f3 cd 8b 26 a4 33 06  04 24 d6 db ba c7 90 2c  |....&.3..$.....,|
00000160  c7 a2 23 50 31 20 18 80  3d 26 80 e8 03 40 28 82  |..#P1 ..=&...@(.|
00000170  69 08 0a 00 ef 84 20 07  60 06 c4 d0 de 42 04 20  |i..... .`....B. |
00000180  07 51 30 b0 c0 1b 82 17  fc 8c e5 13 57 dd 6e b8  |.Q0.........W.n.|
00000190  04 25 86 60 0b c8 60 54  0c 0c 39 b7 40 05 84 c0  |.%.`..`T..9.@...|
000001a0  1d 00 dc 0f a7 b9 34 0a  00 e8 ac 5a 53 f8 13 5a  |......4....ZS..Z|
000001b0  a0 d0 28 02 60 03 f2 1a  4b e4 d2 92 9c ac 00 ef  |..(.`...K.......|
000001c0  ff ff 83 ef ff ff 02 00  00 00 00 28 b5 04 00 ef  |...........(....|
000001d0  ff ff 05 ef ff ff 02 28  b5 04 00 b0 27 00 00 00  |.......(....'...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

---

### Post by wilee-nilee on 2010-12-29
So you may need a chkdsk /r run on sda2 it is showing as the partition to boot in the script and has the bootflag, it just might not be loading if it is a little broken, hard to say.

Do you have a install disc?

So you have run from Ubuntu

sudo update-grub 

correct?

Have you just used the arrow key to see if sda2 is below the sda1 on the grub menu list you have a lot of kernels, scroll to the bottom of grub.

---

### Post by DayLite on 2010-12-29
> **wilee-nilee said:**
> So you may need a chkdsk /r run on sda2 it is showing as the partition to boot in the script and has the bootflag, it just might not be loading if it is a little broken, hard to say.

Do you have a install disc?

What install disc? Windows or Ubuntu?

---

### Post by wilee-nilee on 2010-12-29
> **DayLite said:**
> What install disc? Windows or Ubuntu?

I edited my last post so take another look.

A chkdsk would be from a XP disc.

I think you haven't just scrolled to the bottom of the grub menu to be honest sda2 shows in the script, or you haven't run the 
sudo update-grub 
it is hard to say here.

---

### Post by DayLite on 2010-12-29
> **wilee-nilee said:**
> 
I think you haven't just scrolled to the bottom of the grub menu to be honest sda2 shows in the script, or you haven't run the 
sudo update-grub 
it is hard to say here.

**Problem solved** :lolflag:

I didn't realize the addition to more grub so that I needed to scroll. Overlooked the tiny whit arrow point to 'down'. I found it ! Now when I want to boot to windows I can.

Thank you very much for observing this from the photo.

---

### Post by wilee-nilee on 2010-12-29
> **DayLite said:**
> **Problem solved** :lolflag:

I didn't realize the addition to more grub so that I needed to scroll. Overlooked the tiny whit arrow point to 'down'. I found it ! Now when I want to boot to windows I can.

Thank you very much for observing this from the photo.

Hey it is a easy thing to miss.:)

---

### Post by DayLite on 2010-12-29
> **wilee-nilee said:**
> Hey it is a easy thing to miss.:)

Thank you, again for being there for me. You are very appreciated.:biggrin:

---

