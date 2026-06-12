---
title: "Another Grub Problem"
date: 2010-04-17
forum: New to Ubuntu
---

### Post by lanetherif on 2010-04-17
Few days ago, since I missed my Europa Universalis game, I have installed Windows 7. Today, I tried to reinstall Grub  and yet I guess I couldn`t. :) When I reboot, I am face to face with grub command line. 
This the info gathered by boot info script:
> ============================ Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda1 and 
                       looks at sector 7262015 of the same hard drive for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda4 and 
                       looks at sector 7133247 of the same hard drive for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x641354fd

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    51,199,154    51,199,092  83 Linux
/dev/sda2          71,473,185   440,213,129   368,739,945  83 Linux
/dev/sda3    *    440,213,504   512,118,783    71,905,280   7 HPFS/NTFS
/dev/sda4         512,120,070   976,768,064   464,647,995  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        d086dabf-935e-40a2-969d-e6518a74285d   ext4       Sistem                        
/dev/sda2        ccd25abd-ca50-4cdc-932e-6d95c8aa9376   ext4       Depo                          
/dev/sda3        0280EFD780EFCF6B                       ntfs                                     
/dev/sda4        dd990450-e201-4cfa-a195-f833d165f031   ext4       Hepsi                         

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda1        /media/Sistem            ext4       (rw,nosuid,nodev,uhelper=devkit)
I am not sure but it looks like I have two grubs installed. :)

 Any idea will be appriciated.

---

### Post by lanetherif on 2010-04-17
So? Any ideas just for where to start?

---

### Post by louieb on 2010-04-17
Did you post all the output of the script? Several sections are missing - including the grub configuration file -  wonder why. 

Was this a fresh install of Lucid or an upgrade? - Lucid uses GRUB2 - looks like you followed the instructions for fixing GRUB legacy.  

Here 1s some information about GRUB2 [Grub 2 Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1195275")

BTW: wrap the scripts output in code tags - the # on the toolbar.

---

### Post by lanetherif on 2010-04-18
> **louieb said:**
> Did you post all the output of the script? Several sections are missing - including the grub configuration file -  wonder why. 

Was this a fresh install of Lucid or an upgrade? - Lucid uses GRUB2 - looks like you followed the instructions for fixing GRUB legacy.  

Here 1s some information about GRUB2 [Grub 2 Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1195275")

BTW: wrap the scripts output in code tags - the # on the toolbar.

Sorry... Here is the complete one:
```
       Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda1 and 
                       looks at sector 7131455 of the same hard drive for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda4 and 
                       looks at sector 7133247 of the same hard drive for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x641354fd

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    51,199,154    51,199,092  83 Linux
/dev/sda2          71,473,185   440,213,129   368,739,945  83 Linux
/dev/sda3         440,213,504   512,118,783    71,905,280   7 HPFS/NTFS
/dev/sda4         512,120,070   976,768,064   464,647,995  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        d086dabf-935e-40a2-969d-e6518a74285d   ext4       Sistem                        
/dev/sda2        ccd25abd-ca50-4cdc-932e-6d95c8aa9376   ext4       Depo                          
/dev/sda3        0280EFD780EFCF6B                       ntfs                                     
/dev/sda4        dd990450-e201-4cfa-a195-f833d165f031   ext4       Hepsi                         

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


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
search --no-floppy --fs-uuid --set d086dabf-935e-40a2-969d-e6518a74285d
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
search --no-floppy --fs-uuid --set d086dabf-935e-40a2-969d-e6518a74285d
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
menuentry "Ubuntu, with Linux 2.6.32-20-generic" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set d086dabf-935e-40a2-969d-e6518a74285d
    linux    /boot/vmlinuz-2.6.32-20-generic root=UUID=d086dabf-935e-40a2-969d-e6518a74285d ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-20-generic
}
menuentry "Ubuntu, with Linux 2.6.32-20-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set d086dabf-935e-40a2-969d-e6518a74285d
    echo    Loading Linux 2.6.32-20-generic ...
    linux    /boot/vmlinuz-2.6.32-20-generic root=UUID=d086dabf-935e-40a2-969d-e6518a74285d ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.32-20-generic
}
menuentry "Ubuntu, with Linux 2.6.32-19-generic" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set d086dabf-935e-40a2-969d-e6518a74285d
    linux    /boot/vmlinuz-2.6.32-19-generic root=UUID=d086dabf-935e-40a2-969d-e6518a74285d ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-19-generic
}
menuentry "Ubuntu, with Linux 2.6.32-19-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set d086dabf-935e-40a2-969d-e6518a74285d
    echo    Loading Linux 2.6.32-19-generic ...
    linux    /boot/vmlinuz-2.6.32-19-generic root=UUID=d086dabf-935e-40a2-969d-e6518a74285d ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.32-19-generic
}
menuentry "Ubuntu, with Linux 2.6.32-18-generic" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set d086dabf-935e-40a2-969d-e6518a74285d
    linux    /boot/vmlinuz-2.6.32-18-generic root=UUID=d086dabf-935e-40a2-969d-e6518a74285d ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-18-generic
}
menuentry "Ubuntu, with Linux 2.6.32-18-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set d086dabf-935e-40a2-969d-e6518a74285d
    echo    Loading Linux 2.6.32-18-generic ...
    linux    /boot/vmlinuz-2.6.32-18-generic root=UUID=d086dabf-935e-40a2-969d-e6518a74285d ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.32-18-generic
}
menuentry "Ubuntu, with Linux 2.6.32-17-generic" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set d086dabf-935e-40a2-969d-e6518a74285d
    linux    /boot/vmlinuz-2.6.32-17-generic root=UUID=d086dabf-935e-40a2-969d-e6518a74285d ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-17-generic
}
menuentry "Ubuntu, with Linux 2.6.32-17-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set d086dabf-935e-40a2-969d-e6518a74285d
    echo    Loading Linux 2.6.32-17-generic ...
    linux    /boot/vmlinuz-2.6.32-17-generic root=UUID=d086dabf-935e-40a2-969d-e6518a74285d ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.32-17-generic
}
menuentry "Ubuntu, with Linux 2.6.32-16-generic" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set d086dabf-935e-40a2-969d-e6518a74285d
    linux    /boot/vmlinuz-2.6.32-16-generic root=UUID=d086dabf-935e-40a2-969d-e6518a74285d ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-16-generic
}
menuentry "Ubuntu, with Linux 2.6.32-16-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set d086dabf-935e-40a2-969d-e6518a74285d
    echo    Loading Linux 2.6.32-16-generic ...
    linux    /boot/vmlinuz-2.6.32-16-generic root=UUID=d086dabf-935e-40a2-969d-e6518a74285d ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.32-16-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set d086dabf-935e-40a2-969d-e6518a74285d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set d086dabf-935e-40a2-969d-e6518a74285d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=d086dabf-935e-40a2-969d-e6518a74285d /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda4 during installation
UUID=dd990450-e201-4cfa-a195-f833d165f031 /home          ext4    defaults        0       2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .6GB: boot/grub/core.img
   5.9GB: boot/grub/grub.cfg
   3.6GB: boot/grub/stage2
   4.8GB: boot/initrd.img-2.6.32-16-generic
    .0GB: boot/initrd.img-2.6.32-17-generic
   5.1GB: boot/initrd.img-2.6.32-18-generic
   8.0GB: boot/initrd.img-2.6.32-19-generic
   7.2GB: boot/initrd.img-2.6.32-20-generic
   4.8GB: boot/vmlinuz-2.6.32-16-generic
   4.8GB: boot/vmlinuz-2.6.32-17-generic
   4.9GB: boot/vmlinuz-2.6.32-18-generic
   4.9GB: boot/vmlinuz-2.6.32-19-generic
   7.1GB: boot/vmlinuz-2.6.32-20-generic
   7.2GB: initrd.img
   8.0GB: initrd.img.old
   7.1GB: vmlinuz
   4.9GB: vmlinuz.old
```I might have tried both Grub and Grub2 installation, to be fair. I didn`t install Ubuntu by the way, I installed Windows 7 then I tried to make Ubuntu visible again. 

At the moment, when I reboot the machine, neither Windows nor Ubuntu show up. There is only grub command prompt,

I am stuck.

---

### Post by lanetherif on 2010-04-18
Well... I am no longer stuck, I have followed the instructions (which I guess followed earlier, with no result) and am able to login to my Ubuntu, however Grub2 screen was missing, so no Windows7... 

Here I am sending new results of boot info script: ```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda1 and 
                       looks at sector 7131455 of the same hard drive for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda4 and 
                       looks at sector 7133247 of the same hard drive for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    51,199,154    51,199,092  83 Linux
/dev/sda2          71,473,185   440,213,129   368,739,945  83 Linux
/dev/sda3         440,213,504   512,118,783    71,905,280   7 HPFS/NTFS
/dev/sda4         512,120,070   976,768,064   464,647,995  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        d086dabf-935e-40a2-969d-e6518a74285d   ext4       Sistem                        
/dev/sda2        ccd25abd-ca50-4cdc-932e-6d95c8aa9376   ext4       Depo                          
/dev/sda3        0280EFD780EFCF6B                       ntfs                                     
/dev/sda4        dd990450-e201-4cfa-a195-f833d165f031   ext4       Hepsi                         
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sda4        /home                    ext4       (rw)


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
search --no-floppy --fs-uuid --set d086dabf-935e-40a2-969d-e6518a74285d
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
search --no-floppy --fs-uuid --set d086dabf-935e-40a2-969d-e6518a74285d
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
menuentry "Ubuntu, with Linux 2.6.32-20-generic" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set d086dabf-935e-40a2-969d-e6518a74285d
    linux    /boot/vmlinuz-2.6.32-20-generic root=UUID=d086dabf-935e-40a2-969d-e6518a74285d ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-20-generic
}
menuentry "Ubuntu, with Linux 2.6.32-20-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set d086dabf-935e-40a2-969d-e6518a74285d
    echo    Loading Linux 2.6.32-20-generic ...
    linux    /boot/vmlinuz-2.6.32-20-generic root=UUID=d086dabf-935e-40a2-969d-e6518a74285d ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.32-20-generic
}
menuentry "Ubuntu, with Linux 2.6.32-19-generic" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set d086dabf-935e-40a2-969d-e6518a74285d
    linux    /boot/vmlinuz-2.6.32-19-generic root=UUID=d086dabf-935e-40a2-969d-e6518a74285d ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-19-generic
}
menuentry "Ubuntu, with Linux 2.6.32-19-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set d086dabf-935e-40a2-969d-e6518a74285d
    echo    Loading Linux 2.6.32-19-generic ...
    linux    /boot/vmlinuz-2.6.32-19-generic root=UUID=d086dabf-935e-40a2-969d-e6518a74285d ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.32-19-generic
}
menuentry "Ubuntu, with Linux 2.6.32-18-generic" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set d086dabf-935e-40a2-969d-e6518a74285d
    linux    /boot/vmlinuz-2.6.32-18-generic root=UUID=d086dabf-935e-40a2-969d-e6518a74285d ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-18-generic
}
menuentry "Ubuntu, with Linux 2.6.32-18-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set d086dabf-935e-40a2-969d-e6518a74285d
    echo    Loading Linux 2.6.32-18-generic ...
    linux    /boot/vmlinuz-2.6.32-18-generic root=UUID=d086dabf-935e-40a2-969d-e6518a74285d ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.32-18-generic
}
menuentry "Ubuntu, with Linux 2.6.32-17-generic" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set d086dabf-935e-40a2-969d-e6518a74285d
    linux    /boot/vmlinuz-2.6.32-17-generic root=UUID=d086dabf-935e-40a2-969d-e6518a74285d ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-17-generic
}
menuentry "Ubuntu, with Linux 2.6.32-17-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set d086dabf-935e-40a2-969d-e6518a74285d
    echo    Loading Linux 2.6.32-17-generic ...
    linux    /boot/vmlinuz-2.6.32-17-generic root=UUID=d086dabf-935e-40a2-969d-e6518a74285d ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.32-17-generic
}
menuentry "Ubuntu, with Linux 2.6.32-16-generic" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set d086dabf-935e-40a2-969d-e6518a74285d
    linux    /boot/vmlinuz-2.6.32-16-generic root=UUID=d086dabf-935e-40a2-969d-e6518a74285d ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-16-generic
}
menuentry "Ubuntu, with Linux 2.6.32-16-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set d086dabf-935e-40a2-969d-e6518a74285d
    echo    Loading Linux 2.6.32-16-generic ...
    linux    /boot/vmlinuz-2.6.32-16-generic root=UUID=d086dabf-935e-40a2-969d-e6518a74285d ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.32-16-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set d086dabf-935e-40a2-969d-e6518a74285d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set d086dabf-935e-40a2-969d-e6518a74285d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=d086dabf-935e-40a2-969d-e6518a74285d /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda4 during installation
UUID=dd990450-e201-4cfa-a195-f833d165f031 /home          ext4    defaults        0       2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .6GB: boot/grub/core.img
   5.9GB: boot/grub/grub.cfg
   3.6GB: boot/grub/stage2
   4.8GB: boot/initrd.img-2.6.32-16-generic
    .0GB: boot/initrd.img-2.6.32-17-generic
   5.1GB: boot/initrd.img-2.6.32-18-generic
   8.0GB: boot/initrd.img-2.6.32-19-generic
   7.2GB: boot/initrd.img-2.6.32-20-generic
   4.8GB: boot/vmlinuz-2.6.32-16-generic
   4.8GB: boot/vmlinuz-2.6.32-17-generic
   4.9GB: boot/vmlinuz-2.6.32-18-generic
   4.9GB: boot/vmlinuz-2.6.32-19-generic
   7.1GB: boot/vmlinuz-2.6.32-20-generic
   7.2GB: initrd.img
   8.0GB: initrd.img.old
   7.1GB: vmlinuz
   4.9GB: vmlinuz.old
```

I am eager to listen for ways to bring back Windows 7 and to an answer whether I really have to grubs installed. :)

Thanks.

---

### Post by Nesaskewatch on 2010-04-18
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

That should fix you up.

---

### Post by ed-koala on 2010-04-18
Not seeing Grub2 is normal.  It's default is to be hidden.  You need to do a couple of edits to get Grub to be visible and to add Windows 7 to the Grub list (it won't see it by default).

This thread tells how to fix it - [http://ubuntuforums.org/showthread.php?t=1453700]("http://ubuntuforums.org/showthread.php?t=1453700")

---

### Post by lanetherif on 2010-04-18
> **ed-koala said:**
> Not seeing Grub2 is normal.  It's default is to be hidden.  You need to do a couple of edits to get Grub to be visible and to add Windows 7 to the Grub list (it won't see it by default).

This thread tells how to fix it - [http://ubuntuforums.org/showthread.php?t=1453700](http://ubuntuforums.org/showthread.php?t=1453700)


Thanks... It's now back to normal ie. I have both Ubuntu and Windows 7.

---

