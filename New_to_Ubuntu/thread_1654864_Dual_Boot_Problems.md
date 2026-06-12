---
title: "Dual Boot Problems"
date: 2010-12-29
forum: New to Ubuntu
---

### Post by joetheplumber67 on 2010-12-29
Hey everyone,

I just installed ubuntu on my Sony Vaio alongside WIndows 7 (dual boot). However, whenever I restart my computer, it goes directly to Windows instead of giving me the choice of Ubuntu or Windows. How do I fix this so I can choose either one?

Thanks!

---

### Post by wilee-nilee on 2010-12-29
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out, in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags paste all the text in between.

This will give us a what is where look at the computer.

---

### Post by joetheplumber67 on 2010-12-29
Ok, so I went to the website and it said to use the USB to boot into Ubuntu. When I did that, it gave me the option to choose which OS i wanted. I haven't tried the program yet, but I was wondering if I need to use my flash drive?

---

### Post by wilee-nilee on 2010-12-29
> **joetheplumber67 said:**
> Ok, so I went to the website and it said to use the USB to boot into Ubuntu. When I did that, it gave me the option to choose which OS i wanted. I haven't tried the program yet, but I was wondering if I need to use my flash drive?

So when you used the thumb you installed with to boot you got the grub menu showing Ubuntu and Windows?

If yes boot into the install and run the script that will just generate another text file to be posted in code tags.

Edit: If your question about the USB is will you need to always use it to boot in, no.

---

### Post by joetheplumber67 on 2010-12-29
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 8015 MB, 8015282176 bytes
32 heads, 63 sectors/track, 7765 cylinders, total 15654848 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    15,654,239    15,654,177   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048    21,250,047    21,248,000  27 Hidden HPFS/NTFS
/dev/sdb2    *     21,250,048    21,454,847       204,800   7 HPFS/NTFS
/dev/sdb3          21,454,848   520,282,799   498,827,952   7 HPFS/NTFS
/dev/sdb4         520,284,158   625,141,759   104,857,602   5 Extended
/dev/sdb5         520,284,160   620,763,135   100,478,976  83 Linux
/dev/sdb6         620,765,184   625,141,759     4,376,576  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        55E5-5B32                              vfat       PENDRIVE                      
/dev/sda: PTTYPE="dos" 
/dev/sdb1        6EE65CBAE65C83ED                       ntfs       Recovery                      
/dev/sdb2        7C8AD3858AD33A7A                       ntfs       System Reserved               
/dev/sdb3        AE8AD4B38AD47973                       ntfs                                     
/dev/sdb4: PTTYPE="dos" 
/dev/sdb5        6d926911-fd3f-4be5-8a02-9cc66ef4139c   ext4                                     
/dev/sdb6        c351500c-02fd-4d53-a87e-18e3679ece16   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro)
/dev/sda1        /media/PENDRIVE          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 6d926911-fd3f-4be5-8a02-9cc66ef4139c
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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 6d926911-fd3f-4be5-8a02-9cc66ef4139c
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
menuentry 'Ubuntu, with Linux 2.6.32-27-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 6d926911-fd3f-4be5-8a02-9cc66ef4139c
    linux    /boot/vmlinuz-2.6.32-27-generic-pae root=UUID=6d926911-fd3f-4be5-8a02-9cc66ef4139c ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-27-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 6d926911-fd3f-4be5-8a02-9cc66ef4139c
    echo    'Loading Linux 2.6.32-27-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-27-generic-pae root=UUID=6d926911-fd3f-4be5-8a02-9cc66ef4139c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 6d926911-fd3f-4be5-8a02-9cc66ef4139c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 6d926911-fd3f-4be5-8a02-9cc66ef4139c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6ee65cbae65c83ed
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdb2)" {
    insmod ntfs
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 7c8ad3858ad33a7a
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

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
UUID=6d926911-fd3f-4be5-8a02-9cc66ef4139c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=c351500c-02fd-4d53-a87e-18e3679ece16 none            swap    sw              0       0

=================== sdb5: Location of files loaded by Grub: ===================


 279.4GB: boot/grub/core.img
 270.8GB: boot/grub/grub.cfg
 279.4GB: boot/initrd.img-2.6.32-27-generic-pae
 279.4GB: boot/vmlinuz-2.6.32-27-generic-pae
 279.4GB: initrd.img
 279.4GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb4

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 30 fd 05 00 fe  |...........0....|
000001d0  ff ff 05 fe ff ff 02 30  fd 05 00 d0 42 00 00 00  |.......0....B...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```Hope I did that right.

---

### Post by LetsMugSanta on 2010-12-29
There is also a video tutorial of this done by NixiePixel on Youtube. Search for Nixiepixel reinstalling grub on youtube and you should be able to find it if the other solution  didnt work for you

---

### Post by wilee-nilee on 2010-12-29
Just follow this link because the thumb is reading as sda, grub was put in its MBR rather then the HD reading as sdb in the script.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by joetheplumber67 on 2010-12-29
```

Disk /dev/sda: 8015 MB, 8015282176 bytes
32 heads, 63 sectors/track, 7765 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4b7702fc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7765     7827088+   b  W95 FAT32

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8121122b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1323    10624000   27  Unknown
/dev/sdb2   *        1323        1336      102400    7  HPFS/NTFS
/dev/sdb3            1336       32387   249413976    7  HPFS/NTFS
/dev/sdb4           32387       38914    52428801    5  Extended
/dev/sdb5           32387       38641    50239488   83  Linux
/dev/sdb6           38641       38914     2188288   82  Linux swap / Solaris

```It says to use ```
sudo mount /dev/sdXY /mnt
```Which X and Y should I use?

---

### Post by Quackers on 2010-12-29
```
sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
```

---

### Post by joetheplumber67 on 2010-12-29
So I updated GRUB, but now when I boot without my flash drive, it just says:

Error: file note found.
grub rescue>

It doesn't go to Windows automatically.

---

### Post by Quackers on 2010-12-29
If you've installed grub to the mbr, Windows shouldn't boot at this stage, Ubuntu should.
Please re-run the boot script and post the new output.

---

### Post by garvinrick4 on 2010-12-29
There is a boot partition in sdb that needs to be mounted also.
Copy and paste these in terminal live cd. (Ubuntu install cd using try ubuntu)
```

[CODE]sudo mkdir /media/boot
``````
sudo mkdir /media/root
``````
sudo mount /dev/sdb2 /media/boot
``````
sudo mount /dev/sdb5 /media/root
``````
sudo grub-install --recheck --root-directory=/media/root /dev/sdb
``````
sudo umount /media/boot
``````
sudo umount /media/root
```[/code] Boot into Ubuntu and
```
sudo update-grub
``` Same thing as previous except mounting in /media instead of /mnt so I can mount /boot partition easily.

---

### Post by joetheplumber67 on 2010-12-30
```

               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /mnt/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 8015 MB, 8015282176 bytes
32 heads, 63 sectors/track, 7765 cylinders, total 15654848 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    15,654,239    15,654,177   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048    21,250,047    21,248,000  27 Hidden HPFS/NTFS
/dev/sdb2    *     21,250,048    21,454,847       204,800   7 HPFS/NTFS
/dev/sdb3          21,454,848   520,282,799   498,827,952   7 HPFS/NTFS
/dev/sdb4         520,284,158   625,141,759   104,857,602   5 Extended
/dev/sdb5         520,284,160   620,763,135   100,478,976  83 Linux
/dev/sdb6         620,765,184   625,141,759     4,376,576  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        55E5-5B32                              vfat       PENDRIVE                      
/dev/sda: PTTYPE="dos" 
/dev/sdb1        6EE65CBAE65C83ED                       ntfs       Recovery                      
/dev/sdb2        7C8AD3858AD33A7A                       ntfs       System Reserved               
/dev/sdb3        AE8AD4B38AD47973                       ntfs                                     
/dev/sdb4: PTTYPE="dos" 
/dev/sdb5        6d926911-fd3f-4be5-8a02-9cc66ef4139c   ext4                                     
/dev/sdb6        c351500c-02fd-4d53-a87e-18e3679ece16   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro)
/dev/sda1        /media/PENDRIVE          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sdb5/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set 6d926911-fd3f-4be5-8a02-9cc66ef4139c
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
search --no-floppy --fs-uuid --set 6d926911-fd3f-4be5-8a02-9cc66ef4139c
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
menuentry 'Ubuntu, with Linux 2.6.32-27-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 6d926911-fd3f-4be5-8a02-9cc66ef4139c
    linux    /boot/vmlinuz-2.6.32-27-generic-pae root=UUID=6d926911-fd3f-4be5-8a02-9cc66ef4139c ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-27-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 6d926911-fd3f-4be5-8a02-9cc66ef4139c
    echo    'Loading Linux 2.6.32-27-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-27-generic-pae root=UUID=6d926911-fd3f-4be5-8a02-9cc66ef4139c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 6d926911-fd3f-4be5-8a02-9cc66ef4139c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 6d926911-fd3f-4be5-8a02-9cc66ef4139c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 6ee65cbae65c83ed
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 7c8ad3858ad33a7a
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

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
UUID=6d926911-fd3f-4be5-8a02-9cc66ef4139c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=c351500c-02fd-4d53-a87e-18e3679ece16 none            swap    sw              0       0

=================== sdb5: Location of files loaded by Grub: ===================


 279.4GB: boot/grub/core.img
 270.9GB: boot/grub/grub.cfg
 279.4GB: boot/initrd.img-2.6.32-27-generic-pae
 279.4GB: boot/vmlinuz-2.6.32-27-generic-pae
 279.4GB: initrd.img
 279.4GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb4

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 30 fd 05 00 fe  |...........0....|
000001d0  ff ff 05 fe ff ff 02 30  fd 05 00 d0 42 00 00 00  |.......0....B...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by joetheplumber67 on 2010-12-30
> **garvinrick4 said:**
> There is a boot partition in sdb that needs to be mounted also.
Copy and paste these in terminal live cd. (Ubuntu install cd using try ubuntu)
```

[CODE]sudo mkdir /media/boot
``````
sudo mkdir /media/root
``````
sudo mount /dev/sdb2 /media/boot
``````
sudo mount /dev/sdb5 /media/root
``````
sudo grub-install --recheck --root-directory=/media/root /dev/sdb
``````
sudo umount /media/boot
``````
sudo umount /media/root
```[/code] Boot into Ubuntu and
```
sudo update-grub
``` Same thing as previous except mounting in /media instead of /mnt so I can mount /boot partition easily.

How can I get back to the "try ubuntu?" Whenever I boot with the liveusb, it goes to the screen asking I want to run Windows 7 or Ubuntu because I already installed Ubuntu to my laptop.

---

### Post by Quackers on 2010-12-30
The bios would need to be set to boot the usb flash drive as first boot device to accesss the live usb. However I think that sdb2 is a Windows boot partition, not Ubuntu.
When you get to the grub menu now and it gives the two boot options, have you tried booting each one? What is happening when you try them please?
Try without the flash drive plugged in.

---

### Post by joetheplumber67 on 2010-12-30
I went into the BIOS and tried to change it to boot external device first, but it still goes to the grub menu. I tried both Windows 7 and Ubuntu with the USB plugged in and they both work fine. However, when I boot without the flash drive, it just says:

Error: file not found.
grub rescue>

---

### Post by joetheplumber67 on 2010-12-30
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

This is the GRUB menu. I was wondering if there was anything I could change here to fix the problem because I saw some similar forums and they changed things in the GRUB menu

---

### Post by joetheplumber67 on 2010-12-30
[https://help.ubuntu.com/community/Grub2#Rescue Mode](https://help.ubuntu.com/community/Grub2#Rescue Mode)

I found this and I'm not sure if it will help.
I'm also new to Ubuntu, so I'm not sure what I'm supposed to do.

---

### Post by Quackers on 2010-12-30
From the grub prompt you could try entering this
set prefix=(hd1,5)/boot/grub

set root=(hd1,5)

as the first 2 lines, then follow the guide.
If that doesn't work we can try purging and re-installing grub

---

### Post by Quackers on 2010-12-30
Please disregard previous post. I believe the correct entries would be

set root=(hd1,5)
linux /vmlinuz root=/dev/sdb5 ro
initrd /initrd.img
boot

I'm sorry about that. I was looking at the wrong section.

---

### Post by joetheplumber67 on 2010-12-30
I tried typing those in after the "grub rescue>" prompt and nothing happened. It said that linux, initrd, and boot were unknown commands.

---

### Post by joetheplumber67 on 2010-12-30
Does anyone have any ideas on what to do?

---

### Post by garvinrick4 on 2010-12-31
#grub is a piece of software that is put into your mbr (for you sdb) that looks into a partition for boot files.
#you want put grub2 in sdb and look for files in sdb5 and you have a /boot partition in sdb2 in your setup.
#If you can boot into ubuntu you can fix it there.
#If you cannot boot into ubuntu you must use a live cd or live usb to fix.
#Can you do any of those 2 things. Ubuntu on HDD or Live cd or usb?
#If you have a Live CD or USB use the code I have given you.
This should not be a major problem. Boot into Live using Try Ubuntu and copy and paste
the commands one at a time into a terminal.
# If you can to do it in Ubuntu install instead of Live Cd or Usb that is a different set of code.

---

### Post by garvinrick4 on 2010-12-31
sda is pendrive does not show operating system.

---

### Post by joetheplumber67 on 2010-12-31
I have my BIOS set up so that the external drive comes first, but I also installed Ubuntu on a separate partition than Windows. Also, I though sda had Windows and sdb had Ubuntu.

Without the LiveUSB, I can't do anything thing because it just say "error: file not found. grub rescue>" However, with the USB in, the grub menu shows up and I can choose either OS.

If I put Grub 2 in sda, how can I get it out and put it in sdb?

---

### Post by Quackers on 2010-12-31
I have just looked again at your boot script output, and I have noticed something I missed previously, namely
```
=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for [COLOR="Red"]/mnt/boot/grub.[/COLOR]

```
[COLOR="Black"]
The bit in red should be "/boot/grub". (no /mnt )

This can be cause, I think, by a missing space in the first command.

Please try running these commands again, by copy/paste preferrably.

```
sudo mount /dev/sdb5 /mnt 
sudo grub-install --root-directory=/mnt /dev/sdb
```

[/COLOR]

---

### Post by joetheplumber67 on 2010-12-31
Ok, I installed it and it said it installed properly without errors.

---

### Post by Quackers on 2010-12-31
Try rebooting then, but take out the flash drive when it powers down.
See if it boots now. 
There is still the full chroot method we haven't tried :-)

---

### Post by joetheplumber67 on 2010-12-31
It still says the same thing when i boot without the flash drive

---

### Post by joetheplumber67 on 2010-12-31
It still says the same thing when i boot without the flash drive

---

### Post by joetheplumber67 on 2010-12-31
It still says the same thing when i boot without the flash drive

---

### Post by joetheplumber67 on 2010-12-31
It still says the same thing when i boot without the flash drive

---

### Post by Quackers on 2010-12-31
Ok, just for clarification can you please say again the following.
Your hard drive configuration. 
The boot script states that you have an 8GB flash drive, which is picked up as sda
Your internal hard drive (presumably internal) is 320GB and is picked up as sdb

Your bios settings
Which is the first boot device in your bios
which is the second boot device in your bios

You previously mentioned an external drive - is this the 8GB flash stick or another?
Thanks

---

### Post by joetheplumber67 on 2010-12-31
I figured out my problem through the Grub rescue megathread, but thanks for all the time and help!

---

### Post by Quackers on 2010-12-31
Wouldn't you like to help others in your position and tell them what you did to fix it?

---

### Post by joetheplumber67 on 2010-12-31
Yes, I probably should. All the credit goes to drs305 for helping me out.

When I booted without my LiveUSB, it just said:

```
error: file not found.
grub rescue>
```

first type ```
ls
``` (without quotes) and check (hd0,x) or (hd1,x) with x being the partion on which ubuntu is installed.

next, type ```
ls (hd0,x)/boot
``` and check for "vmlinuz" and "initrd.img"

if you do, type ```
ls (hd0,5)/boot/grub
``` and look for a lot of ".mod" files

type ```
configfile (hd0,5)/boot/grub/grub.cfg
``` and see if it boots to ubuntu. if it says "unknown command", type all of the following:

```

set prefix=(hd0,5)/boot/grub
  
set root=(hd0,5)
  
insmod (hd0,5)/boot/grub/linux.mod

linux /vmlinuz root=/dev/sda5 ro
  
initrd /initrd.img
  
boot

```

if it works, it should boot straight to ubuntu and you should be set.

However, if you want to use dual boot, open a terminal and type:
```
sudo grub-install /dev/sdx
```

If it says installation complete with no errors type:

```
sudo update-grub
```

It should list all of your kernels (Windows and Ubuntu)

Try rebooting and it should go to the grub menu! :)

---

