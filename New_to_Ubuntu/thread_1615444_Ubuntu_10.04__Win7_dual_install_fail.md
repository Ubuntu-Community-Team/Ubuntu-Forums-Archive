---
title: "Ubuntu 10.04 / Win7 dual install fail"
date: 2010-11-07
forum: New to Ubuntu
---

### Post by drusmanbashir on 2010-11-07
Hi everyone i have searched forums for hours, but did not find useful help. i installed ubuntu yesterday, in addition to my previous Win7 install. now the problem is that Grub does allow me to choose whichever OS i want, but windows 7 shows an error message during boot up giving me the option to run windows cd --> repair. i tried the repair window7-64 option but that did not work. here is my boot script. i am a total noob so plz guide me step-by-step.

# 

               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   122,882,047   122,675,200   7 HPFS/NTFS
/dev/sda3         122,884,094   242,632,703   119,748,610   5 Extended
/dev/sda5         122,884,096   138,506,239    15,622,144  82 Linux swap / Solaris
/dev/sda6         138,508,288   158,038,015    19,529,728  83 Linux
/dev/sda7         158,040,064   242,632,703    84,592,640  83 Linux
/dev/sda4         242,634,752   488,394,751   245,760,000   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1999 MB, 1999568384 bytes
32 heads, 63 sectors/track, 1937 cylinders, total 3905407 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63     3,904,991     3,904,929   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        24FC3649FC361610                       ntfs       System Reserved               
/dev/sda2        988656C98656A810                       ntfs       RADIOLOGY                     
/dev/sda3: PTTYPE="dos" 
/dev/sda4        585A87115A86EAD8                       ntfs                                     
/dev/sda5        f90a1bc4-980b-4983-8b7a-77b86748e7d8   swap                                     
/dev/sda6        da3bbe07-df64-4ad6-a927-004b5be5bf5e   ext4                                     
/dev/sda7        49aa2997-2cdd-465a-a7e6-74af18511aec   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        9039-D331                              vfat       KINGSTON                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)
/dev/sda7        /home                    ext4       (rw)
/dev/sdb1        /media/KINGSTON          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set da3bbe07-df64-4ad6-a927-004b5be5bf5e
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set da3bbe07-df64-4ad6-a927-004b5be5bf5e
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
menuentry 'Ubuntu, with Linux 2.6.32-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set da3bbe07-df64-4ad6-a927-004b5be5bf5e
    linux    /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=da3bbe07-df64-4ad6-a927-004b5be5bf5e ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set da3bbe07-df64-4ad6-a927-004b5be5bf5e
    echo    'Loading Linux 2.6.32-25-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=da3bbe07-df64-4ad6-a927-004b5be5bf5e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set da3bbe07-df64-4ad6-a927-004b5be5bf5e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set da3bbe07-df64-4ad6-a927-004b5be5bf5e
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 24fc3649fc361610
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

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
UUID=da3bbe07-df64-4ad6-a927-004b5be5bf5e /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=49aa2997-2cdd-465a-a7e6-74af18511aec /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=f90a1bc4-980b-4983-8b7a-77b86748e7d8 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


  73.2GB: boot/grub/core.img
  78.2GB: boot/grub/grub.cfg
  73.3GB: boot/initrd.img-2.6.32-25-generic-pae
  73.2GB: boot/vmlinuz-2.6.32-25-generic-pae
  73.3GB: initrd.img
  73.2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  00 00 00 10 00 00 00 00  0a 00 53 00 79 00 73 00  |..........S.y.s.|
00000010  74 00 65 00 6d 00 2e 00  57 00 65 00 62 00 41 00  |t.e.m...W.e.b.A.|
00000020  48 03 00 00 00 00 01 00  70 00 5a 00 00 00 00 00  |H.......p.Z.....|
00000030  0d 03 00 00 00 00 01 00  a6 33 c6 fd 31 04 ca 01  |.........3..1...|
00000040  a6 33 c6 fd 31 04 ca 01  d0 80 ca 0f ed 3c cb 01  |.3..1........<..|
00000050  a6 33 c6 fd 31 04 ca 01  00 00 00 00 00 00 00 00  |.3..1...........|
00000060  00 00 00 00 00 00 00 00  00 00 00 10 00 00 00 00  |................|
00000070  0c 02 53 00 59 00 53 00  54 00 45 00 4d 00 7e 00  |..S.Y.S.T.E.M.~.|
00000080  31 00 2e 00 44 00 41 00  54 00 00 00 00 00 00 00  |1...D.A.T.......|
00000090  4c 03 00 00 00 00 01 00  70 00 5a 00 00 00 00 00  |L.......p.Z.....|
000000a0  0d 03 00 00 00 00 01 00  a6 33 c6 fd 31 04 ca 01  |.........3..1...|
000000b0  00 95 c8 fd 31 04 ca 01  d0 80 ca 0f ed 3c cb 01  |....1........<..|
000000c0  00 95 c8 fd 31 04 ca 01  00 00 00 00 00 00 00 00  |....1...........|
000000d0  00 00 00 00 00 00 00 00  00 00 00 10 00 00 00 00  |................|
000000e0  0c 02 53 00 59 00 53 00  54 00 45 00 4d 00 7e 00  |..S.Y.S.T.E.M.~.|
000000f0  31 00 2e 00 45 00 4e 00  54 00 00 00 00 00 00 00  |1...E.N.T.......|
00000100  4a 03 00 00 00 00 01 00  70 00 5a 00 00 00 00 00  |J.......p.Z.....|
00000110  0d 03 00 00 00 00 01 00  a6 33 c6 fd 31 04 ca 01  |.........3..1...|
00000120  a6 33 c6 fd 31 04 ca 01  d0 80 ca 0f ed 3c cb 01  |.3..1........<..|
00000130  a6 33 c6 fd 31 04 ca 01  00 00 00 00 00 00 00 00  |.3..1...........|
00000140  00 00 00 00 00 00 00 00  00 00 00 10 00 00 00 00  |................|
00000150  0c 02 53 00 59 00 53 00  54 00 45 00 4d 00 7e 00  |..S.Y.S.T.E.M.~.|
00000160  31 00 2e 00 4f 00 52 00  41 00 00 00 00 00 00 00  |1...O.R.A.......|
00000170  4e 03 00 00 00 00 01 00  70 00 5a 00 00 00 00 00  |N.......p.Z.....|
00000180  0d 03 00 00 00 00 01 00  00 9d a2 81 44 04 ca 01  |............D...|
00000190  00 9d a2 81 44 04 ca 01  d0 80 ca 0f ed 3c cb 01  |....D........<..|
000001a0  00 9d a2 81 44 04 ca 01  00 00 00 00 00 00 00 00  |....D...........|
000001b0  00 00 00 00 00 00 00 00  00 00 00 10 00 00 00 ef  |................|
000001c0  ff ff 82 ef ff ff 02 00  00 00 00 60 ee 00 00 ef  |...........`....|
000001d0  ff ff 05 ef ff ff 02 60  ee 00 00 08 2a 01 00 00  |.......`....*...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

#

---

### Post by Jeff.Smith on 2010-11-07
Did you use wubi to install ubuntu or did you partition your hard drive?

---

### Post by sikander3786 on 2010-11-07
Some Windows boot files that should have been on sda1 are missing. You tried the startup repair from Windows 7 recovery disc, but you need to try it 3 times. Start again and retry 3 times to see if you are able to boot into Windows this time.

Every thing else seems fine to me except the boot files on sda4. Seems like a Wubi install is as well present there?

---

### Post by garvinrick4 on 2010-11-07
```
You have had a wubi install on your system and the wubildr is still in your in Windows install.
 You do have a boot partition is sda1 so that has to be mounted when reinstalling grub.
Do this for me. Boot into a Ubuntu Cd and choose try Ubuntu and open a terminal and copy and paste:
[CODE]sudo apt-get install lilo
``````
sudo lilo -M /dev/sda mbr
```will give errors ignore we only want mbr.
Now reboot into harddrive should boot into windows.
Now put Cd back in and choose Try Ubuntu and open a terminal.
```
sudo mkdir /media/boot
``````
sudo mkdir /media/root
``````
sudo mount /dev/sda1 /media/boot
``````
sudo mount /dev/sda6 /media/root
``````
sudo grub-install --recheck --root-directory=/media/root /dev/sda
``````
sudo umount /media/boot
``````
sudo umount /media/root
```umount is not a typo
reboot into harddrive and choose Ubuntu
run this when it boots.
```
sudo update-grub
```should be set now.[/CODE]

---

### Post by garvinrick4 on 2010-11-07
When you get done can you post this outcome just something I want to see.
```
sudo parted -l
```
lower case L

---

### Post by drusmanbashir on 2010-11-07
Hey thanks everyone for their help.
it took me the better part of the day, but i reinstalled windows 7,
 used forums to recover grub2 MBR and now both OS's are working

A small glitch though, the windows loader now shows the option of loading into two (including the corrupt) installations of windows7 . any pointers to how to get rid of the corrupt install?

---

### Post by thunk77 on 2010-11-07
This is a windows bootloader problem so you'll need to find a bootloader editor for Win7. I think there are some free apps on the net. I remember Vista Boot Pro, not sure if it works on 7 though..

---

### Post by garvinrick4 on 2010-11-07
> **drusmanbashir said:**
> Hey thanks everyone for their help.
it took me the better part of the day, but i reinstalled windows 7,
 used forums to recover grub2 MBR and now both OS's are working

A small glitch though, the windows loader now shows the option of loading into two (including the corrupt) installations of windows7 . any pointers to how to get rid of the corrupt install?
You are wasting a lot of disk space which partition is not being used.

---

### Post by Quackers on 2010-11-07
You would have needed to re-install Windows anyway. According to your boot script you only had 2 Windows boot files - No Windows operating system!

---

### Post by garvinrick4 on 2010-11-07
What does this say
```
sudo parted -l
``` (lower case L)

---

### Post by jtarin on 2010-11-07
> **garvinrick4 said:**
> What does this say
```
sudo parted -l
``` (lower case L)I can read that without my glasses....it says "sudo parted -l". :P

---

### Post by drusmanbashir on 2010-11-07
i ran parted

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  106MB   105MB   primary   ntfs            boot
 2      106MB   21.1GB  21.0GB  primary   ntfs
 3      62.9GB  124GB   61.3GB  extended
 5      62.9GB  70.9GB  7999MB  logical   linux-swap(v1)
 6      70.9GB  80.9GB  9999MB  logical   ext4
 7      80.9GB  124GB   43.3GB  logical   ext4
 4      124GB   250GB   126GB   primary   ntfs


Gav, please elaborate when you say 'you are wasting lotof disk space'
i know that there is 32G or so of unpartitioned space lying around which i may remap when i run out of the 126 odd GB storage partition
for the new install of win 7 i reduced the partition size to 20G

---

