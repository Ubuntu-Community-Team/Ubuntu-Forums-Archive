---
title: "Unable to boot Ubuntu loaded in dual operating system with WinXP"
date: 2010-07-30
forum: New to Ubuntu
---

### Post by electeng33 on 2010-07-30
I want to have a dual operating system Ubuntu/WindowsXP-Windows98.   WindowsXP and 98 were already loaded before a loaded Ubuntu and both work satisfactorily.   I have one 80Gb hard drive for Windows and a second 180Gb hard drive for exclusive use of Ubuntu.

I have been out of touch for some time owing to a WindowsXP crash which required wiping the hard drive, and reloading, etc.. During this time I installed a second hard drive 180Gb which I intend for Ubuntu. Previously I had Windows XP and Ubuntu loaded on the same 80Gb hard disc.

The WindowsXP/98 reload went satisfactorily, and are now up and running.

I  loaded Ubuntu on the second hard drive. After loading I shut down and tested that I could boot Ubuntu from the hard drive. Ubuntu loaded just as it should do.

Then I shut down again, re-started and selected WindowsXP to check that Windows XP was still working. I got a message that Windows needed to alter system files - it flashed up and then disappeared. WindowsXP duly booted.

I wondered what Windows had done to which system files, so shut down again, re-started and selected Ubuntu. It failed to boot just as it did some time ago when I first raised this problem, only I incorrectly thought at that time it was due to my loading Microsoft Office. 

On starting up WindowsXP a second time I did not get a message about system files, so I cannot look at it again - but I can remember there was no information about which files were altered. 

I am hoping that now someone may be able to assist me, as I am sure there must be others who have encountered this problem.

I will be most grateful for any suggestions anyone out there can make.

At 'wilee-nilee' 's suggestion I have run 'bootscript' which I will try to attach to this thread for any readers who might like to see it, if it doesnt open in a readable format
(I have never used it before nor have any experience of using the formatting codes (when viewed through live Ubuntu CD the 'results.txt' file looked good and the formatting was ok) please reply to advise me - and let me know  what relevant infomation you may need:-

[URL="file:///media/CORSAIR/RESULTS.txt"]file:///media/CORSAIR/RESULTS.```
txt
```[/URL]

(I have had this problem for several months, but previously thought, incorrectly, that it was due to loading MS Office whjich I did after loading and testing Ubuntu the first time.   I asked for assistance in a thread entitled: Unable to boot after loading MD Office.   I thank all who responded to my query and gtried to nhelp.   I was advised by wilee-nilee  to start this new thread as the apparent circumstances are now different - and the original title is therefore now misleading)

---

### Post by oldfred on 2010-07-30
You need to open result.txt, and copy the entire thing and paste as part of your message. Highlight and click on code tags (#) as you did with just txt in your first post.

---

### Post by electeng33 on 2010-07-30
Thanks 'Oldfred'  for our advice, the complete text is as follows:-
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=e8543f56-9f90-4f3e-96bf-a5bac8701261)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 98
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /IO.SYS /MSDOS.SYS 
                       /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb9 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb11: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcba8cba8

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     4,192,964     4,192,902   b W95 FAT32
/dev/sda2           4,192,965   156,296,384   152,103,420   f W95 Ext d (LBA)
/dev/sda5           4,193,028    47,713,049    43,520,022   b W95 FAT32
/dev/sda6          47,713,113    68,195,924    20,482,812   b W95 FAT32
/dev/sda7          68,195,988    84,582,224    16,386,237   b W95 FAT32
/dev/sda8          84,582,288   108,149,579    23,567,292   b W95 FAT32
/dev/sda9         108,149,643   131,716,934    23,567,292   b W95 FAT32
/dev/sda10        131,716,998   156,296,384    24,579,387   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00031a86

Partition  Boot         Start           End          Size  Id System

/dev/sdb1              16,065   312,576,704   312,560,640   f W95 Ext d (LBA)
/dev/sdb5              16,128    61,464,689    61,448,562   7 HPFS/NTFS
/dev/sdb6          61,464,753   122,913,314    61,448,562   7 HPFS/NTFS
/dev/sdb7         122,913,378   184,361,939    61,448,562   7 HPFS/NTFS
/dev/sdb8         184,362,003   215,624,429    31,262,427   7 HPFS/NTFS
/dev/sdb9         245,810,628   279,723,779    33,913,152   7 HPFS/NTFS
/dev/sdb10        279,723,843   311,098,724    31,374,882  83 Linux
/dev/sdb11        311,098,788   312,576,704     1,477,917  82 Linux swap / Solaris
/dev/sdb2                  63        16,064        16,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda10       3A35-1AEB                              vfat                                     
/dev/sda1        0735-1D01                              vfat                                     
/dev/sda5        3D6B-1D06                              vfat                                     
/dev/sda6        1966-1ADE                              vfat                                     
/dev/sda7        3639-1AE1                              vfat                                     
/dev/sda8        305A-1AE4                              vfat                                     
/dev/sda9        1D36-1AE8                              vfat                                     
/dev/sdb10       e8543f56-9f90-4f3e-96bf-a5bac8701261   ext4                                     
/dev/sdb11       8a4cba99-a978-4253-b3ed-20102a4aaec7   swap                                     
/dev/sdb2        821810C21810B6DF                       ntfs                                     
/dev/sdb5        EA0CE5720CE539E9                       ntfs                                     
/dev/sdb6        5A640BD3640BB0B5                       ntfs                                     
/dev/sdb7        3E940FBF940F78A3                       ntfs                                     
/dev/sdb8        9230137730136211                       ntfs                                     
/dev/sdb9        EC1817A418176CB8                       ntfs                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda1        /media/0735-1D01         vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda10       /media/3A35-1AEB         vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda5        /media/3D6B-1D06         vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda6        /media/1966-1ADE         vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda7        /media/3639-1AE1         vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda8        /media/305A-1AE4         vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda9        /media/1D36-1AE8         vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdb10       /media/e8543f56-9f90-4f3e-96bf-a5bac8701261 ext4       (rw,nosuid,nodev,uhelper=devkit)
/dev/sdb5        /media/EA0CE5720CE539E9  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb6        /media/5A640BD3640BB0B5  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb7        /media/3E940FBF940F78A3  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb8        /media/9230137730136211  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb9        /media/EC1817A418176CB8  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb2        /media/821810C21810B6DF  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=512)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\ = "Microsoft Windows" 

========================== sdb10/boot/grub/grub.cfg: ==========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,10)
search --no-floppy --fs-uuid --set e8543f56-9f90-4f3e-96bf-a5bac8701261
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,10)
    search --no-floppy --fs-uuid --set e8543f56-9f90-4f3e-96bf-a5bac8701261
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=e8543f56-9f90-4f3e-96bf-a5bac8701261 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,10)
    search --no-floppy --fs-uuid --set e8543f56-9f90-4f3e-96bf-a5bac8701261
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=e8543f56-9f90-4f3e-96bf-a5bac8701261 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod fat
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 0735-1d01
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb10/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb10 during installation
UUID=e8543f56-9f90-4f3e-96bf-a5bac8701261 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb11 during installation
UUID=8a4cba99-a978-4253-b3ed-20102a4aaec7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb10: Location of files loaded by Grub: ===================


 145.8GB: boot/grub/core.img
 145.8GB: boot/grub/grub.cfg
 144.0GB: boot/initrd.img-2.6.31-14-generic
 145.2GB: boot/vmlinuz-2.6.31-14-generic
 144.0GB: initrd.img
 145.2GB: vmlinuz
```

That seems to have worked - I am afraid it does not mean very much to me, but I hope that it will mean more to you out there and that you may be able to suggest a remedy.

Thanks for your interest.
[]("file:///media/CORSAIR/RESULTS.txt")

---

### Post by electeng33 on 2010-07-30
Thanks again 'Oldfred', but I spoke too soon.

my message 3 seems to have left out a huge chunk of the results.txt file, I have sent it again as it now seems to be ok:-


[URL="file:///media/CORSAIR/RESULTS.txt"]```
  Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=e8543f56-9f90-4f3e-96bf-a5bac8701261)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 98
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /IO.SYS /MSDOS.SYS 
                       /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb9 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb11: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcba8cba8

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     4,192,964     4,192,902   b W95 FAT32
/dev/sda2           4,192,965   156,296,384   152,103,420   f W95 Ext d (LBA)
/dev/sda5           4,193,028    47,713,049    43,520,022   b W95 FAT32
/dev/sda6          47,713,113    68,195,924    20,482,812   b W95 FAT32
/dev/sda7          68,195,988    84,582,224    16,386,237   b W95 FAT32
/dev/sda8          84,582,288   108,149,579    23,567,292   b W95 FAT32
/dev/sda9         108,149,643   131,716,934    23,567,292   b W95 FAT32
/dev/sda10        131,716,998   156,296,384    24,579,387   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00031a86

Partition  Boot         Start           End          Size  Id System

/dev/sdb1              16,065   312,576,704   312,560,640   f W95 Ext d (LBA)
/dev/sdb5              16,128    61,464,689    61,448,562   7 HPFS/NTFS
/dev/sdb6          61,464,753   122,913,314    61,448,562   7 HPFS/NTFS
/dev/sdb7         122,913,378   184,361,939    61,448,562   7 HPFS/NTFS
/dev/sdb8         184,362,003   215,624,429    31,262,427   7 HPFS/NTFS
/dev/sdb9         245,810,628   279,723,779    33,913,152   7 HPFS/NTFS
/dev/sdb10        279,723,843   311,098,724    31,374,882  83 Linux
/dev/sdb11        311,098,788   312,576,704     1,477,917  82 Linux swap / Solaris
/dev/sdb2                  63        16,064        16,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda10       3A35-1AEB                              vfat                                     
/dev/sda1        0735-1D01                              vfat                                     
/dev/sda5        3D6B-1D06                              vfat                                     
/dev/sda6        1966-1ADE                              vfat                                     
/dev/sda7        3639-1AE1                              vfat                                     
/dev/sda8        305A-1AE4                              vfat                                     
/dev/sda9        1D36-1AE8                              vfat                                     
/dev/sdb10       e8543f56-9f90-4f3e-96bf-a5bac8701261   ext4                                     
/dev/sdb11       8a4cba99-a978-4253-b3ed-20102a4aaec7   swap                                     
/dev/sdb2        821810C21810B6DF                       ntfs                                     
/dev/sdb5        EA0CE5720CE539E9                       ntfs                                     
/dev/sdb6        5A640BD3640BB0B5                       ntfs                                     
/dev/sdb7        3E940FBF940F78A3                       ntfs                                     
/dev/sdb8        9230137730136211                       ntfs                                     
/dev/sdb9        EC1817A418176CB8                       ntfs                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda1        /media/0735-1D01         vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda10       /media/3A35-1AEB         vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda5        /media/3D6B-1D06         vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda6        /media/1966-1ADE         vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda7        /media/3639-1AE1         vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda8        /media/305A-1AE4         vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda9        /media/1D36-1AE8         vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdb10       /media/e8543f56-9f90-4f3e-96bf-a5bac8701261 ext4       (rw,nosuid,nodev,uhelper=devkit)
/dev/sdb5        /media/EA0CE5720CE539E9  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb6        /media/5A640BD3640BB0B5  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb7        /media/3E940FBF940F78A3  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb8        /media/9230137730136211  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb9        /media/EC1817A418176CB8  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb2        /media/821810C21810B6DF  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=512)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\ = "Microsoft Windows" 

========================== sdb10/boot/grub/grub.cfg: ==========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,10)
search --no-floppy --fs-uuid --set e8543f56-9f90-4f3e-96bf-a5bac8701261
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,10)
    search --no-floppy --fs-uuid --set e8543f56-9f90-4f3e-96bf-a5bac8701261
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=e8543f56-9f90-4f3e-96bf-a5bac8701261 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,10)
    search --no-floppy --fs-uuid --set e8543f56-9f90-4f3e-96bf-a5bac8701261
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=e8543f56-9f90-4f3e-96bf-a5bac8701261 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod fat
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 0735-1d01
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb10/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb10 during installation
UUID=e8543f56-9f90-4f3e-96bf-a5bac8701261 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb11 during installation
UUID=8a4cba99-a978-4253-b3ed-20102a4aaec7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb10: Location of files loaded by Grub: ===================


 145.8GB: boot/grub/core.img
 145.8GB: boot/grub/grub.cfg
 144.0GB: boot/initrd.img-2.6.31-14-generic
 145.2GB: boot/vmlinuz-2.6.31-14-generic
 144.0GB: initrd.img
 145.2GB: vmlinuz
```[/URL]


Regards,

electeng33

---

### Post by electeng33 on 2010-07-30
Sorry 'Oldfred' and any others reading messages 3 and 4.

Although I have copied the whole of the reading.txt file into my messages, after I pressed the  Submit Reply button and then look at the thread to read what has gone out to all viewing the thread the text seems to have been truncated.

HELP !!! Can you advise me how to send the complete text as requested.

Many thanks.

Electeng33

---

### Post by oldfred on 2010-07-30
It looks complete to me. Sometimes there are error messages at the end but I have not learned how to use them.

I do not see anything out of place. Windows did combine your boot into the sda1 partition. It would have been better to have used another primary to install XP, but as long as it works it is ok. You cannot uninstall win98 without reinstalling XP though.

I would suggest to install Ubuntu to sdb and change BIOS or if PATA, drive order so Ubuntu boots. Not sure if with PATA that  may confuse windows but updates to grub if drive order changes will normally make windows still think it is first.

sudo update-grub

If booted into Ubuntu you do not have to use a liveCD to install grub to sdb.

reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
If that returns any errors run:
sudo grub-install --recheck /dev/sdb
Then:
sudo update-grub
to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
spacebar to choose drive, enter to accept, do not choose partitions

If you can choose drives to boot then it is easy to test if sdb is working. Once you know you can boot from sdb, I would then also reinstall a windows boot loader to sda.

Restore basic windows boot loader - universe enabled from Ubuntu or liveCD
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

While the problem of windows software writing into the MBR is mostly related to win7 there are a few apps like Norton that you can still run in XP that may do that also and corrupt a grub MBR.

---

### Post by viking350 on 2010-07-30
you might be asking for to many partition's :p

---

### Post by oldfred on 2010-07-30
As long as you can create and see the partitions, it should be ok. 

I now see this also in your boot.ini
multi(0)disk(0)rdisk(0)[COLOR=Red]partition(2)
[/COLOR]
It says your windows XP was in sda2 which is now the extended partition.

Your message 4 seems to be in a box and does not want to scroll. The first time I looked it was all underlined???

---

### Post by electeng33 on 2010-08-10
Thanks 'oldfred' for your suggestions.

Before  contacting the forum I tried to sort the problem by opening using the recovery mode (which did open).  I chose the menu option to repair faults, and found that it appeared to install an upgrade (details later in this reply).

I first booted with the originally downloaded Ubuntu version
On running sudo fdisk -l I got a display of the disk partitions from which                           the linux boot appeared to be /dev/sdb1 - but 'system' was labelled asd W95 Ext'd (LBA)

Ran sudo grub-install /dev/sdb - received response:-
     Installation finished.  No error reported.
     This is the contents of the device map /boot/grub/device.map
     Check if this is correct or not.   If any of the lines is incorrect, fix it and re-run
     the script 'grub-install'
            (I dont how to check whether this is correct or not, so I carried on going 
              through your instructions)

Ran sudo update-grub - response:-
     Found linux image  /bootumlinuz - 2.6.31-32 generic
               initrd image /boot/unitrd.img - 2.6.31-32 generic
               linux image /boot/umlinuz - 2.6.31-124 generic
               initrd image /boot/initrd.img - 2.6.31-14 generic
               memtest86+ image /memtest86+.bin
               Windows XP Professional in dev/sda1
     done

Ran sudo dpkg-reconfigure grub-pc - response:-
    message   /usr/sbin/dpkg - reconfigure: grub-pc is broken or not fully installed

    (there was then a 'dos' prompt  -  is there a way to shut down without switching off 
     the pc, or is it acceptable practice to do that)

Ubunto still would not boot up

I then used the linux 2.6.31-22 generic upgrade in recovery mode,  after a string of
    lines during boot I got 'Done'

    underneath them was the following:-
          Gave up waiting for boot device.   Common problems:
              - Boot args (cat /proc/cmdline)
                    - check root delay = (did the system wait long enough?)
                    - check root = (did the system wait for the right device?)
              - Missing modjules (cat /proc/modules: ls/dev)
     
          ALERT! /dev/disk/by-uuid/e8543F56-9F90-4f3E -96bf-a5bac8701261 does not
              exist.
              Dropping to a shell!
          BusyBox v1.13.3 (Ubuntu 1:1.13.3-1 ubuntu 7) built in shell (ash)
          Enter 'help' for a list of built-in commands.

(initramfs)_

Not surprisingly Ubuntu still did not boot after I had carried out this. 

I have given the results in full in the hope that the key to the problem will be revealed to those who know how to interpret the messages.

On the other hand, they may point the way to further investigation in which I will be grateful to be guided so that I can join the ranks of those enjoying trouble free Ubuntu.
Any help will be greatly appreciated.

---

### Post by oldfred on 2010-08-10
You have made a lot of changes and updates, Please rerun the boot_info script and post the full results.txt.

If it shows a device map it should just show sda & sdb. If it only shows sda it is wrong, but we can easily fix.

Can you easily change boot drive with BIOS so grub installed to sdb (160GB) can be the one booting?

---

### Post by electeng33 on 2010-08-10
Further to message 9, on the point about Windows XP being in the extended partition of the first hard drive.   This is because in the beginning I loaded Windows 98.   When I came to load Windows XP I wanted it to be on a separate partition, and installed it as a dual operating system.   

At the time, Windows 98 was quite important to me, but now that I have been using Windows XP for a while I can do without Windows98 if necessary.

Both boot up satisfactorily, but since loading Ubuntu I have found that when I seek to shut down from Windows 98 I am returned to the Grub menu and then either have to load WindowsXP in order to shut down, or else switch off the power to the pc.   

This does not worry me unduly, but I have added the comment incase it has any significance to my problem in booting Ubuntu.

Again, any observations will be gratefully received.

---

### Post by oldfred on 2010-08-10
I am surprised you get a reboot after shutting down win98. You can add a halt command to the grub menu ( I have both halt & reboot for when I boot wrong drive). But the correct thing is why is win98 shutting down with reboot and not full shutdown if that is what you want.

This would be the correct way to install a second windows. See the link to understand windows, boot sectors (PBR) and multiple installs of windows. It has lots of detail but just reviewing the pictures is worthwhile. Window combines boot into one active (boot flag) primary partition and will not directly boot from a logical partition.

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

### Post by electeng33 on 2010-08-10
Thanks 'oldfred' for your message.   I will re-run the boot-info and post to you as suggested.

In the meantime I have looked into BIOS of my machine which is a Dell Dimension 2350.   I found there is a Hard Disk Boot Priority option, and the order can quite easily be changed.  At present it is set:-

1. Pri.M ExcelStor TRechnology J8080
2. Pri.AS  WDC WD1600AVBB - 63SYA0
3. Bootable Add-in Cards.

Would I be able to change the second entry to make it the first priority without screwing up the configuration which has been applied during the installation processes. or will re-installation be required.

Thanks for the links you provided to items giving information about Windows, I will certainly read them.   Anything that helps to see through the fog is very useful.

---

### Post by oldfred on 2010-08-10
When you have more than one drive I like to have each install on a different drive and that installs boot loader in the MBR of that drive. Then each drive can be booted thru BIOS if there is a problem with the other drive. 
I have 3 drives & four installs so only 3 of my installs are in the MBR of those drives. I also have 2 USB's that boot grub2 just for emergencies. 

We can then install grub2 to sdb and you then change boot order to boot sdb. We can install a windows boot loader to sda which you will not normally use as grub will let you boot windows but just in case it is there.

---

### Post by electeng33 on 2010-08-11
Reference Message 10:

Here is the boot info script results file:-

```
   Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=e8543f56-9f90-4f3e-96bf-a5bac8701261)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 98
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /IO.SYS /MSDOS.SYS 
                       /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb9 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb11: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcba8cba8

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     4,192,964     4,192,902   b W95 FAT32
/dev/sda2           4,192,965   156,296,384   152,103,420   f W95 Ext d (LBA)
/dev/sda5           4,193,028    47,713,049    43,520,022   b W95 FAT32
/dev/sda6          47,713,113    68,195,924    20,482,812   b W95 FAT32
/dev/sda7          68,195,988    84,582,224    16,386,237   b W95 FAT32
/dev/sda8          84,582,288   108,149,579    23,567,292   b W95 FAT32
/dev/sda9         108,149,643   131,716,934    23,567,292   b W95 FAT32
/dev/sda10        131,716,998   156,296,384    24,579,387   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00031a86

Partition  Boot         Start           End          Size  Id System

/dev/sdb1              16,065   312,576,704   312,560,640   f W95 Ext d (LBA)
/dev/sdb5              16,128    61,464,689    61,448,562   7 HPFS/NTFS
/dev/sdb6          61,464,753   122,913,314    61,448,562   7 HPFS/NTFS
/dev/sdb7         122,913,378   184,361,939    61,448,562   7 HPFS/NTFS
/dev/sdb8         184,362,003   215,624,429    31,262,427   7 HPFS/NTFS
/dev/sdb9         245,810,628   279,723,779    33,913,152   7 HPFS/NTFS
/dev/sdb10        279,723,843   311,098,724    31,374,882  83 Linux
/dev/sdb11        311,098,788   312,576,704     1,477,917  82 Linux swap / Solaris
/dev/sdb2                  63        16,064        16,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda10       3A35-1AEB                              vfat                                     
/dev/sda1        0735-1D01                              vfat                                     
/dev/sda5        3D6B-1D06                              vfat                                     
/dev/sda6        1966-1ADE                              vfat                                     
/dev/sda7        3639-1AE1                              vfat                                     
/dev/sda8        305A-1AE4                              vfat                                     
/dev/sda9        1D36-1AE8                              vfat                                     
/dev/sdb10       e8543f56-9f90-4f3e-96bf-a5bac8701261   ext4                                     
/dev/sdb11       8a4cba99-a978-4253-b3ed-20102a4aaec7   swap                                     
/dev/sdb2        821810C21810B6DF                       ntfs                                     
/dev/sdb5        EA0CE5720CE539E9                       ntfs                                     
/dev/sdb6        5A640BD3640BB0B5                       ntfs                                     
/dev/sdb7        3E940FBF940F78A3                       ntfs                                     
/dev/sdb8        9230137730136211                       ntfs                                     
/dev/sdb9        EC1817A418176CB8                       ntfs                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda1        /media/0735-1D01         vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda10       /media/3A35-1AEB         vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda5        /media/3D6B-1D06         vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda6        /media/1966-1ADE         vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda7        /media/3639-1AE1         vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda8        /media/305A-1AE4         vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda9        /media/1D36-1AE8         vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdb10       /media/e8543f56-9f90-4f3e-96bf-a5bac8701261 ext4       (rw,nosuid,nodev,uhelper=devkit)
/dev/sdb5        /media/EA0CE5720CE539E9  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb6        /media/5A640BD3640BB0B5  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb7        /media/3E940FBF940F78A3  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb8        /media/9230137730136211  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb9        /media/EC1817A418176CB8  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb2        /media/821810C21810B6DF  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=512)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
C:\ = "Microsoft Windows"

========================== sdb10/boot/grub/grub.cfg: ==========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,10)
search --no-floppy --fs-uuid --set e8543f56-9f90-4f3e-96bf-a5bac8701261
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,10)
    search --no-floppy --fs-uuid --set e8543f56-9f90-4f3e-96bf-a5bac8701261
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=e8543f56-9f90-4f3e-96bf-a5bac8701261 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,10)
    search --no-floppy --fs-uuid --set e8543f56-9f90-4f3e-96bf-a5bac8701261
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=e8543f56-9f90-4f3e-96bf-a5bac8701261 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod fat
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 0735-1d01
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb10/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb10 during installation
UUID=e8543f56-9f90-4f3e-96bf-a5bac8701261 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb11 during installation
UUID=8a4cba99-a978-4253-b3ed-20102a4aaec7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb10: Location of files loaded by Grub: ===================


 145.8GB: boot/grub/core.img
 145.8GB: boot/grub/grub.cfg
 144.0GB: boot/initrd.img-2.6.31-14-generic
 145.2GB: boot/vmlinuz-2.6.31-14-generic
 144.0GB: initrd.img
 145.2GB: vmlinuz
 
```

I see that the Ubuntu boot loader is installed in sda1, and not in sdb as I had thought it would be.   The Ubuntu CD that I used did not give me any choice - just the option to use the whole of the second hard drive for Ubuntu - I could have chosen the custom installation, but did not think I would be able to handle that.   Please let me know what else of significance the above reveals


Reference Message 14:

This looks promising.   I will be very grateful if you can guide me through the processes, as you will appreciate my knowledge is centred round Windows at the moment, and with Windows the user presses different buttons etc without knowing what is going on.   Ubuntu seems to offer much more versatility and control.  As I have obtained some books on Ubuntu I am able to follow the steps you have indicated so far - but finding them in the first place in books is a much more difficult matter!!

---

### Post by oldfred on 2010-08-11
Post #6 has my instructions on booting into Ubuntu and from there installing grub2 to sdb. You should then test that it boots ok from sdb by changing boot order in BIOS or if one time boot key (f12 on my system) choose sdb. If it works then you can in BIOS change which drive is first so sdb is the boot drive.

If booting Ubuntu from sdb works then we can add a windows boot loader to sda. The lilo boot loader in the MBR works just like windows in searching the partition table for the boot flag (active partition) and jumping to additional boot code in the partition boot sector. We just do not install the rest of lilo but use the existing windows boot code in the windows partition to boot windows.

Once grub turns over booting to windows there should not be any grub/ubuntu info left. So is the issue with booting XP just from win98? Or is it a total reboot thru grub2?

---

### Post by electeng33 on 2010-08-12
Thanks 'oldfred' for your message no. 16, in which you referred to guidance given in your message no. 6.

I actually ran through those steps, and gave the results in my message no. 9.

After your line - 're-install from working (not live CD) system...' you indicate the code 'sudo fdisk -l'

Although to me the read out did not show what is installed on the drives, I thought it showed that gtrub was not on /sbd.

Your sudo instructions seem to refer to the case when grub is already on /sdb, however in case on the 5th line 'Then' refers to both cases (grub on /sda or grub on /sdb) I ran through the remaining lines of your sudo instructions.

The final screen response was -'reconfigure:  grub-pc is broken or not fully installed.   This I took as confirmation that there was no gtrub on/sdb.

From this I believe maybe what I now need to know is how to get grub on to /sdb, from /sda, which does not appear to be mentioned in your message 6.

I am afraid it is not clear to me how to do this, even though I expect it is obvious to you.

Once again, thanks for your time spent on this problem.   If anything in this message is unclear when you read it, please let me know and I will re-phrase.

---

### Post by oldfred on 2010-08-12
The dpkg reconfigure has to be run from the system you want to maintain, so I would run it after rebooting into your system and then rechoose sdb with spacebar and if sda is choosen use spacebar to unchoose it.

The reference to sda or sdb is if you want it in either or both. I thought in your case you wanted it into sdb. Many times I post more generic instructions so others can also use them if they run across this thread.

From your working install this command alone should reinstall grub to sdb. 

sudo grub-install /dev/sdb

If you did the steps in post #6 your results from post #15 should have shown grub2 installed in sdb, or did you not rerun the boot info script and post results2?

Have you tried booting sdb?

---

### Post by electeng33 on 2010-08-12
Thanks for message no. 18

I believe I have gone through your instructions, but unfortunately again without success.   I fear that I may be mis-interpreting them somewhere so I will go through your reply one paragraph at a time.


_First paragraph:_
When you  refer to dpkg reconfigure, do you mean that I need to switch off the computer (not shut down, because I dont know of a way of doing that when in recovery mode).   I have actually also done that, but it has made no difference.

I again get the message:-
/usr/sbin/dpkg-reconfigure: grub-pc is broken or not fully installed

After having run sudo update-grub which in your message 6 follows sudo grub-install /dev/sdb I can still only boot the recovery mode  of the system - and I cannot see where to apply 're-choose /sdb by using the space bar', as no choice presents itself.


_Second paragraph._
I quite understand your reasoning, and 'yes' from what you have told me so far I do want grub to be in /sdb


_Two separate lines after second paragraph._
I have repeated the sudo grub-install /dev/sdb, but received the same screen messages I posted you in no 9.   It again advised checking the contents of the device map /boot/grub/device.map - I do not know how to do this or how significant it is.

_Following paragraph._   The results posted in message  no 15 were from re-running the boot info script just before sending them to you - but as you have said grub2 is not shown, which suggests something keeps going wrong before that point.

_Last line._   I do not appear to have a way to change the disk boot order 'just for this time'.   F12 on my machine is a short cut key to the boot drive order menu.    However I have changed the order to make disk 2  the boot disk,  Ubuntu still does not boot and Windows  is unaffected in that it still boots as before when selected.   


I hope you are able to make sense of all this.   The principle of making disk 2 the boot disc and installing grub on to it, seem to be a way that ought to work, so I am hoping that the solution is not far off.

---

### Post by oldfred on 2010-08-13
With the grub in sda are you able to boot? Or are you only using recovery mode?

The newest versions of grub do not even have device.map.
From your install in places, computer, file system drill down to /boot/grub on your install. See if this file is there and what are its contends.
 
/boot/grub/device.map
It should look like this:
(hd0)    /dev/sda
(hd1)    /dev/sdb

to update device map:
If it complains about a device map
sudo grub-mkdevicemap
sudo update-grub

From your install (not liveCD) are you not able to run:
sudo dpkg-reconfigure grub-pc

---

### Post by electeng33 on 2010-08-13
Thanks for post no.20, looking at each of your points in order:-

1. _First line_  I am only able to get recovery mode.

2. _Paragraph following first line._   Using live CD file browser Places -> File Systems I was able to find /boot/grub on /sdb and grub had only one file which was grubenv.

3. _Following paragraph_   Following your comments I looked in my Beginning Ubuntu  Linux book (p.98) which was written for Ubuntu 8.04, and found that it lists commands that can be used with recovery mode - it did not include grub-install.   I suppose there is no device.map file, because I was trying to use grub-install from recovery mode.

4. _Paragraph 'to update device map...'__:_   As the book did not include 'mkdevicemap' among the recovery mode commands, I did not try to do that

5._Final paragraph_    From recovery mode I ran dpkg-reconfigure grub-pc.   The results I gave, perhaps in too much detail, in message no.9.   I ran this in both Ubuntu Linux 2.6.31-14 generic and Ubuntu Linux 2.6.31-22 generic because I did not know what the recovery mode option of 'repair broken packages' had done to 2.6.31-14 or what 2.5.31-22 actually is.   The result from 2.6.31-14 was that grub-pc is broken or not fully installed, 2.5.31-22 gave an ALERT that a file was missing!!


One way I can think of which might get grub onto /sdb is to again install Ubuntu from my CD, then before WindowsXP has a chance to corrupt files, I could use grub-install to put it onto /sdb.   It is a bit messy, because I will then have to delete the unwanted Ubuntu files installed earlier, also it is something which I do not know how to do.

I expect you know a much better way of achieving the desired result, than that, so I await your comments with anticipation.   Once again thanking you for your interest and time.

---

### Post by oldfred on 2010-08-13
My Ubuntu book is 6.06, but I still use it for many things. My old ME professor said you should mark texts up with new data and/or paste in new/additional info as you find it. Grub2 is one of the major changes since 9.10. About the only thing similar to grub legacy is sudo update-grub. 

General info:
[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

From recovery mode do you only get command line and do you have network connection?

If so I would run these commands to update system and reinstall grub2 (grub-pc)

I am copying from a chroot command where sudo is not required. You will need sudo for most if not all these commands. You can copy but do not include any thing after a # which is just a comment.

#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

# uninstall both grub legacy & grub2 reinstall grub2 and to sdb
apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
grub-install /dev/sdb
grub-install --recheck /dev/sdb

sudo dpkg-reconfigure grub-pc

If all this does not work, then reinstall is probalby the better solution. If you use manual reinstall you can choose the same partitions.

---

### Post by electeng33 on 2010-08-17
Thanks 'oldfred' for your further words of wisdom.  Unfortunately when I run recovery mode I only get the command prompt, I have no way of accessing the internet.   That being the case, it appears the only alternative left is to re-install Ubuntu.

I did think I might have stumbled upon something when I saw a thread, which I then printed but the complete reference is off the top of the page, however I can see the number 224351 which I think is its reference number, and it is dated July 28, 2006.  It is entitled 'How to restore Grub from a live Ubuntu cd - but it did not work - when I entered sudo grub I got back the messager 'command not found', same when I tried grub2.

M\ny thanks for the list of commands you included in message # 22 and also for the links you included which I will download for detailed reading.

---

### Post by oldfred on 2010-08-17
Sometimes reinstall is the quickest solution. You can also chroot from liveCD into your install to update it.

If you reinstall be sure to use the advanced button to install grub to sdb.
[http://members.iinet.net/~herman546/p28/032_install-now.png](http://members.iinet.net/~herman546/p28/032_install-now.png)

Dual boot 2 drives, windows & Lucid 10.04
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by electeng33 on 2010-09-01
Back again !!
I have cleaned off Windows and Ubuntu from my hard drives and then reloaded.   The Ubuntu I installed manually and changing BIOS selection I made the 180Gb hard drive (Ubuntu) the primary hard drive.   I think I may have mis-interpreted one or two of the questions on the manual installation screens.

Now Ununtu will not boot, whilst the Ubuntu symbol against the black background is on screen an error message flashes on screen, but it disappears so quickly that I cannot read it (is there a way to persuade it to freeze until a release button of some kind is pressed).

I have found, however, that I can get Ubuntu  to boot from the hard drive by first running the live CD, opening an application and then pressing control_alt_delete and asking for the PC to be restarted - the Ubuntu installed on the hard drive then boots.   

When I change the BIOS selection back to make the Windows hard drive the primary drive, I can boot Windows.

The grub menu only contains Ubuntu selections, the Window menu only contains Windows XP and Windows 98.

I append the boot info record below:-

```

```Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #10 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 98
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /IO.SYS /MSDOS.SYS 
                       /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb11: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcba8cba8

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     4,192,964     4,192,902   b W95 FAT32
/dev/sda2           4,192,965   156,296,384   152,103,420   f W95 Ext d (LBA)
/dev/sda5           4,193,028    47,713,049    43,520,022   b W95 FAT32
/dev/sda6          47,713,113    68,195,924    20,482,812   b W95 FAT32
/dev/sda7          68,195,988    84,582,224    16,386,237   b W95 FAT32
/dev/sda8          84,582,288   108,149,579    23,567,292   b W95 FAT32
/dev/sda9         108,149,643   131,716,934    23,567,292   b W95 FAT32
/dev/sda10        131,716,998   156,296,384    24,579,387   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00031a86

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63        16,064        16,002   7 HPFS/NTFS
/dev/sdb2              16,065   312,576,704   312,560,640   f W95 Ext d (LBA)
/dev/sdb5              16,128    61,464,689    61,448,562   7 HPFS/NTFS
/dev/sdb6          61,464,753   122,913,314    61,448,562   7 HPFS/NTFS
/dev/sdb7         245,810,628   279,723,779    33,913,152   7 HPFS/NTFS
/dev/sdb8         279,723,843   311,098,724    31,374,882   7 HPFS/NTFS
/dev/sdb9         311,098,788   312,576,704     1,477,917  82 Linux swap / Solaris
/dev/sdb10        122,913,378   184,361,939    61,448,562  83 Linux
/dev/sdb11        184,362,003   245,810,564    61,448,562  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda10       3A35-1AEB                              vfat                                     
/dev/sda1        172B-13E1                              vfat                                     
/dev/sda5        1E57-1803                              vfat                                     
/dev/sda6        1966-1ADE                              vfat                                     
/dev/sda7        3639-1AE1                              vfat                                     
/dev/sda8        305A-1AE4                              vfat                                     
/dev/sda9        1D36-1AE8                              vfat                                     
/dev/sdb10       a13c1388-ca02-4361-91c6-c9fcc9fca51e   ext4                                     
/dev/sdb11       a619b12c-15eb-4fff-9ef2-3f1992fd6074   ext4                                     
/dev/sdb1        821810C21810B6DF                       ntfs                                     
/dev/sdb5        EA0CE5720CE539E9                       ntfs                                     
/dev/sdb6        5A640BD3640BB0B5                       ntfs                                     
/dev/sdb7        EC1817A418176CB8                       ntfs                                     
/dev/sdb8        01CB43D9F34CEC20                       ntfs                                     
/dev/sdb9        ce7f5776-5a9f-4441-925f-e2cd062af40e   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdb6        /media/5A640BD3640BB0B5  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(5)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(5)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\="Microsoft Windows"  

========================== sdb10/boot/grub/grub.cfg: ==========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,7)
search --no-floppy --fs-uuid --set a13c1388-ca02-4361-91c6-c9fcc9fca51e
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,7)
    search --no-floppy --fs-uuid --set a13c1388-ca02-4361-91c6-c9fcc9fca51e
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=a13c1388-ca02-4361-91c6-c9fcc9fca51e ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,7)
    search --no-floppy --fs-uuid --set a13c1388-ca02-4361-91c6-c9fcc9fca51e
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=a13c1388-ca02-4361-91c6-c9fcc9fca51e ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb10/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb7 during installation
UUID=a13c1388-ca02-4361-91c6-c9fcc9fca51e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb12 during installation
UUID=8a4cba99-a978-4253-b3ed-20102a4aaec7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb10: Location of files loaded by Grub: ===================


  63.5GB: boot/grub/core.img
  63.5GB: boot/grub/grub.cfg
  63.5GB: boot/initrd.img-2.6.31-14-generic
  63.5GB: boot/vmlinuz-2.6.31-14-generic
  63.5GB: initrd.img
  63.5GB: vmlinuz

========================== sdb11/boot/grub/grub.cfg: ==========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,11)
search --no-floppy --fs-uuid --set a619b12c-15eb-4fff-9ef2-3f1992fd6074
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,11)
    search --no-floppy --fs-uuid --set a619b12c-15eb-4fff-9ef2-3f1992fd6074
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=a619b12c-15eb-4fff-9ef2-3f1992fd6074 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,11)
    search --no-floppy --fs-uuid --set a619b12c-15eb-4fff-9ef2-3f1992fd6074
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=a619b12c-15eb-4fff-9ef2-3f1992fd6074 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod fat
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 172b-13e1
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sdb10)" {
    insmod ext2
    set root=(hd1,10)
    search --no-floppy --fs-uuid --set a13c1388-ca02-4361-91c6-c9fcc9fca51e
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=a13c1388-ca02-4361-91c6-c9fcc9fca51e ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sdb10)" {
    insmod ext2
    set root=(hd1,10)
    search --no-floppy --fs-uuid --set a13c1388-ca02-4361-91c6-c9fcc9fca51e
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=a13c1388-ca02-4361-91c6-c9fcc9fca51e ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb11/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb11 during installation
UUID=a619b12c-15eb-4fff-9ef2-3f1992fd6074 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb9 during installation
UUID=ce7f5776-5a9f-4441-925f-e2cd062af40e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb11: Location of files loaded by Grub: ===================


 100.0GB: boot/grub/core.img
 100.0GB: boot/grub/grub.cfg
  94.9GB: boot/initrd.img-2.6.31-14-generic
  94.9GB: boot/vmlinuz-2.6.31-14-generic
  94.9GB: initrd.img
  94.9GB: vmlinuz


I suppose I could clean the hard drives again and then reinstall, trying to answer the manual installation questions differently, but I thought it likely reading the above you would be able to suggest a simple way to remedy the situation.    

It does seem that a solution is now close, because both Ubuntu and Windows can be made to work.    I will greatly appreciate any further advice you can offer.

---

### Post by oldfred on 2010-09-01
It looks like you installed another copy of Ubuntu into sdb11, but had a install in sdb10. The grub in the sdb MBR uses the install in sdb10 not the newest.

When you did the second install did you not use the advanced button and install grub to sdb? Was there some reason for the second install. It is good experience but I am not sure it is necessary.

Dual boot 2 drives, windows & Lucid 10.04
[http://members.iinet.net.au/~herman546/p24/022f.png](http://members.iinet.net.au/~herman546/p24/022f.png)
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

If you can boot run this and it should find windows and your second install.
sudo update-grub

Then if you boot the second install
sudo update-grub

Do you want to have the MBR with the install in sdb10 or sdb11.
If you want sdb11 boot into that install.

You can use this after booting either sdb10 or sdb11 to install its boot loader but you only can have one as the default. If you want to uninstall one then make sure you have the other in the MBR beefore you do any deletetion.
reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
If that returns any errors run:
sudo grub-install --recheck /dev/sdb
Then:
sudo update-grub
to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
spacebar to choose/unchoose drive, enter to accept, do not choose partitions

Once you get both booting come back and we can discuss what to do with the second install.

---

### Post by electeng33 on 2010-09-02
Thanks 'oldfred' for message #26.

For ease of identification I will go through the points in your message in some order

1. I did think I had removed all the Ubuntu from my second hard drive, and the significance of the entry 'Ubuntu 9.10 ' in both sdb10 and sdb11 had escaped me.

2. Yes, I did select the advance button to enable manual loading, although I did think I may have answered one or two questions incorrectly - there was one about making Ubuntu self contained or some such, to which I answered 'yes'.

3. I actually re-installed because your message #24 said 'sometimes re-0install is the quickest solution.   The alternative 'you cal also chroot from live CD' I could not understand, so rather than take up more  time by raising another query, I thought re-installation muight be the best option.


I have run through the code which you sent, and was very pleased to note that the 
boot menu now has an additional entry at the top which I believe to be for sdb10, because the entry near the bottom of tyhe list has in brackets 'sdb11'.   Above that now appears Windows XP.   I have tested that and can now load Windows from the Ubuntu menu list.

However Ubuntu will still not boot from the menu, I booted from the disk by going into both the live CD and then into Windows and in each case using 'ctrl-alt-delete' whereupon Ubuntu booted from the hard drive.

I paste below a copy of the terminal screen display in case that is of help in showing you what happening when I used the code you provided:-.

```

```roy@roy-desktop:~$ sudo update-grub
[sudo] password for roy: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
Found Ubuntu 9.10 (9.10) on /dev/sdb11
done
roy@roy-desktop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcba8cba8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         261     2096451    b  W95 FAT32
/dev/sda2             262        9729    76051710    f  W95 Ext'd (LBA)
/dev/sda5             262        2970    21760011    b  W95 FAT32
/dev/sda6            2971        4245    10241406    b  W95 FAT32
/dev/sda7            4246        5265     8193118+   b  W95 FAT32
/dev/sda8            5266        6732    11783646    b  W95 FAT32
/dev/sda9            6733        8199    11783646    b  W95 FAT32
/dev/sda10           8200        9729    12289693+   b  W95 FAT32

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00031a86

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1           1        8001    7  HPFS/NTFS
/dev/sdb2               2       19457   156280320    f  W95 Ext'd (LBA)
/dev/sdb5               2        3826    30724281    7  HPFS/NTFS
/dev/sdb6            3827        7651    30724281    7  HPFS/NTFS
/dev/sdb7           15302       17412    16956576    7  HPFS/NTFS
/dev/sdb8           17413       19365    15687441    7  HPFS/NTFS
/dev/sdb9           19366       19457      738958+  82  Linux swap / Solaris
/dev/sdb10           7652       11476    30724281   83  Linux
/dev/sdb11          11477       15301    30724281   83  Linux

Partition table entries are not in disk order
roy@roy-desktop:~$ 

It was my intention to copy the whole of the screen but I got to a dialogue screen telling me that there is a later version available, then it froze, when I went to close the screen it cancelled the terminal.   I re-ran to get the above, but did not want to use  the  install command again incase it further 'gummed up the works' by adding another copy of the boot loader.

In my reply #25 I mentioned that during boot up there was an error message.   I have now been able to read part of it (just a word or two at each attempt because it leaves the screen so quickly):-

'swap waiting for ... /etc/fstab.   One or more of mounts listed...cannot yet be mounted...UUID....'.   

If it is likely to be of help, I can with patience, get the complete message.   Please let me know if this will help.

A few seconds after that message the Ubuntu motif on the black screen disappears , leaving the entirely black screen, and then the machine waits - until I turn off.

I hope what I have given above will further narrow down the field, to help focus on the cause of the problem,     I will of course be happy to give any further details - I think it is probably a step forward in that I can now actually boot from the hard drive, even though I have to do it in a devious way.

I will be most grateful for your further comments.

---

### Post by oldfred on 2010-09-02
I missed it the first time and it was there:

From sudo blkid (in script)
/dev/sdb9 ce7f5776-5a9f-4441-925f-e2cd062af40e swap
Install on sdb10
# swap was on /dev/sdb12 during installation
UUID=8a4cba99-a978-4253-b3ed-20102a4aaec7 none swap sw 0 0
Install on sdb11
# swap was on /dev/sdb9 during installation
UUID=ce7f5776-5a9f-4441-925f-e2cd062af40e none swap sw 0 0

Your install in sdb10 used a swap from sdb12 and that UUID does not exist anymore. You can easily fix it by changing it to the UUID for sdb9. It also looks like you should be able to boot the install in sdb11.

If you can boot and get past the errror or from a liveCD (or other install)  drill down to /etc/fstab (path will be different if from liveCD.

gksudo gedit /etc/fstab

Replace UUID for swap with correct one 
ce7f5776-5a9f-4441-925f-e2cd062af40e

---

### Post by electeng33 on 2010-09-02
Many thanks for your last reply.   That really sounded good, and I followed the steps you suggested.   Unfortunately it has not worked though, now I do not get the error message dduring booting, but it still will not boot in Ubuntu.   I can no longer boot by the 'ctrl-alt-delete' subterfuge, so the boot info script I have pasted below was done with the live CD in the hope that it might show something else that has gone wrong..



```

```     Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #10 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 98
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /IO.SYS /MSDOS.SYS 
                       /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb11: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcba8cba8

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     4,192,964     4,192,902   b W95 FAT32
/dev/sda2           4,192,965   156,296,384   152,103,420   f W95 Ext d (LBA)
/dev/sda5           4,193,028    47,713,049    43,520,022   b W95 FAT32
/dev/sda6          47,713,113    68,195,924    20,482,812   b W95 FAT32
/dev/sda7          68,195,988    84,582,224    16,386,237   b W95 FAT32
/dev/sda8          84,582,288   108,149,579    23,567,292   b W95 FAT32
/dev/sda9         108,149,643   131,716,934    23,567,292   b W95 FAT32
/dev/sda10        131,716,998   156,296,384    24,579,387   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00031a86

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63        16,064        16,002   7 HPFS/NTFS
/dev/sdb2              16,065   312,576,704   312,560,640   f W95 Ext d (LBA)
/dev/sdb5              16,128    61,464,689    61,448,562   7 HPFS/NTFS
/dev/sdb6          61,464,753   122,913,314    61,448,562   7 HPFS/NTFS
/dev/sdb7         245,810,628   279,723,779    33,913,152   7 HPFS/NTFS
/dev/sdb8         279,723,843   311,098,724    31,374,882   7 HPFS/NTFS
/dev/sdb9         311,098,788   312,576,704     1,477,917  82 Linux swap / Solaris
/dev/sdb10        122,913,378   184,361,939    61,448,562  83 Linux
/dev/sdb11        184,362,003   245,810,564    61,448,562  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda10       3A35-1AEB                              vfat                                     
/dev/sda1        172B-13E1                              vfat                                     
/dev/sda5        1E57-1803                              vfat                                     
/dev/sda6        1966-1ADE                              vfat                                     
/dev/sda7        3639-1AE1                              vfat                                     
/dev/sda8        305A-1AE4                              vfat                                     
/dev/sda9        1D36-1AE8                              vfat                                     
/dev/sdb10       a13c1388-ca02-4361-91c6-c9fcc9fca51e   ext4                                     
/dev/sdb11       a619b12c-15eb-4fff-9ef2-3f1992fd6074   ext4                                     
/dev/sdb1        821810C21810B6DF                       ntfs                                     
/dev/sdb5        EA0CE5720CE539E9                       ntfs                                     
/dev/sdb6        5A640BD3640BB0B5                       ntfs                                     
/dev/sdb7        EC1817A418176CB8                       ntfs                                     
/dev/sdb8        01CB43D9F34CEC20                       ntfs                                     
/dev/sdb9        ce7f5776-5a9f-4441-925f-e2cd062af40e   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(5)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(5)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\="Microsoft Windows"  

========================== sdb10/boot/grub/grub.cfg: ==========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,10)
search --no-floppy --fs-uuid --set a13c1388-ca02-4361-91c6-c9fcc9fca51e
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,10)
    search --no-floppy --fs-uuid --set a13c1388-ca02-4361-91c6-c9fcc9fca51e
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=a13c1388-ca02-4361-91c6-c9fcc9fca51e ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,10)
    search --no-floppy --fs-uuid --set a13c1388-ca02-4361-91c6-c9fcc9fca51e
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=a13c1388-ca02-4361-91c6-c9fcc9fca51e ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod fat
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 172b-13e1
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sdb11)" {
    insmod ext2
    set root=(hd1,11)
    search --no-floppy --fs-uuid --set a619b12c-15eb-4fff-9ef2-3f1992fd6074
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=a619b12c-15eb-4fff-9ef2-3f1992fd6074 ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sdb11)" {
    insmod ext2
    set root=(hd1,11)
    search --no-floppy --fs-uuid --set a619b12c-15eb-4fff-9ef2-3f1992fd6074
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=a619b12c-15eb-4fff-9ef2-3f1992fd6074 ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb10/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb7 during installation
UUID=a13c1388-ca02-4361-91c6-c9fcc9fca51e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb12 during installation
UUID=ce7f5776-5a9f-4441-925f-e2cd062af40e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb10: Location of files loaded by Grub: ===================


  68.5GB: boot/grub/core.img
  63.5GB: boot/grub/grub.cfg
  63.5GB: boot/initrd.img-2.6.31-14-generic
  63.5GB: boot/vmlinuz-2.6.31-14-generic
  63.5GB: initrd.img
  63.5GB: vmlinuz

========================== sdb11/boot/grub/grub.cfg: ==========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,11)
search --no-floppy --fs-uuid --set a619b12c-15eb-4fff-9ef2-3f1992fd6074
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,11)
    search --no-floppy --fs-uuid --set a619b12c-15eb-4fff-9ef2-3f1992fd6074
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=a619b12c-15eb-4fff-9ef2-3f1992fd6074 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,11)
    search --no-floppy --fs-uuid --set a619b12c-15eb-4fff-9ef2-3f1992fd6074
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=a619b12c-15eb-4fff-9ef2-3f1992fd6074 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod fat
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 172b-13e1
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sdb10)" {
    insmod ext2
    set root=(hd1,10)
    search --no-floppy --fs-uuid --set a13c1388-ca02-4361-91c6-c9fcc9fca51e
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=a13c1388-ca02-4361-91c6-c9fcc9fca51e ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sdb10)" {
    insmod ext2
    set root=(hd1,10)
    search --no-floppy --fs-uuid --set a13c1388-ca02-4361-91c6-c9fcc9fca51e
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=a13c1388-ca02-4361-91c6-c9fcc9fca51e ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb11/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb11 during installation
UUID=a619b12c-15eb-4fff-9ef2-3f1992fd6074 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb9 during installation
UUID=ce7f5776-5a9f-4441-925f-e2cd062af40e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb11: Location of files loaded by Grub: ===================


 100.0GB: boot/grub/core.img
 100.0GB: boot/grub/grub.cfg
  94.9GB: boot/initrd.img-2.6.31-14-generic
  94.9GB: boot/vmlinuz-2.6.31-14-generic
  94.9GB: initrd.img
  94.9GB: vmlinuz

Once again, thanks for your help.

---

### Post by oldfred on 2010-09-02
Do you get a menu? 

Can you boot in the other install in sdb11 (at bottom of menu) and/or boot the recovery mode?

---

### Post by electeng33 on 2010-09-03
Thanks 'oldfred' for reply no.30.

No, I can not boot from either sdb10 or sdb11, but I can boot into recovery mode and get to the root shell prompt.

I could also restore the UUID which I replaced as suggested in reply no.28, in the hope that I can then boot from sdb11 by the 'ctrl-alt-delete' subterfuge, if that will help in eradicating the source of the problem.   I expect you will regard that as a retrograde step, and I am not really keen to step backwards except as a means to an end.

One consolation for me is that at each turn I am learning more about Ubuntu, and I do appreciate your patience.

---

### Post by oldfred on 2010-09-03
If you can get to a command line with either sda10 and/or sda11 lets try a lot of updates and reinstall grub2 to the MBR sometimes with updatess a reinstall solves things. Sometimes not.

Edit - you will need sudo in front of these commands - copied from a liveCD update that I had saved. sudo -i I think gives you sudo for multi commands.

sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
grub-install /dev/sda
grub-install --recheck /dev/sda

sudo dpkg-reconfigure grub-pc
Choose sda with space bar, if not the default

---

### Post by electeng33 on 2010-09-03
Many thanks  'oldfred'  for reply no.32.   I have run through all instructions as far as I could, the final result is that I cannot now get the boot menu.   I have used the liveCD to send this and to get the boot info script that I include below in case it will be useful.

On switch on I get a screen message:-

             GNU GRUB version 1.97 beta 4

[Manual BASH=like line editing is supported.   For the first word TAB lists possible command completions.   Anywhere else TAB lists possible device/file completions]

sh:grub>   (prompt awaiting instructions).

I expect that will mean something to you.  

apt-get -finstall would not run
mv /boot/grub l/book/grub_backup received the response - no such file ;/boot/grub'

Both apt-get upgrade and apt-get dist-upgrade switched to a completely black screen when they finished, requiring me to switch off the PC and then reboot into recovery mode.   I then continued at the point that had been reached before that happened.   Of course, I dont know whether that has had any undesirable effect on the rest of the processes.
 

```

```  Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=a13c1388-ca02-4361-91c6-c9fcc9fca51e)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #10 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 98
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /IO.SYS /MSDOS.SYS 
                       /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab /boot/grub/core.img

sdb11: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcba8cba8

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     4,192,964     4,192,902   b W95 FAT32
/dev/sda2           4,192,965   156,296,384   152,103,420   f W95 Ext d (LBA)
/dev/sda5           4,193,028    47,713,049    43,520,022   b W95 FAT32
/dev/sda6          47,713,113    68,195,924    20,482,812   b W95 FAT32
/dev/sda7          68,195,988    84,582,224    16,386,237   b W95 FAT32
/dev/sda8          84,582,288   108,149,579    23,567,292   b W95 FAT32
/dev/sda9         108,149,643   131,716,934    23,567,292   b W95 FAT32
/dev/sda10        131,716,998   156,296,384    24,579,387   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00031a86

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63        16,064        16,002   7 HPFS/NTFS
/dev/sdb2              16,065   312,576,704   312,560,640   f W95 Ext d (LBA)
/dev/sdb5              16,128    61,464,689    61,448,562   7 HPFS/NTFS
/dev/sdb6          61,464,753   122,913,314    61,448,562   7 HPFS/NTFS
/dev/sdb7         245,810,628   279,723,779    33,913,152   7 HPFS/NTFS
/dev/sdb8         279,723,843   311,098,724    31,374,882   7 HPFS/NTFS
/dev/sdb9         311,098,788   312,576,704     1,477,917  82 Linux swap / Solaris
/dev/sdb10        122,913,378   184,361,939    61,448,562  83 Linux
/dev/sdb11        184,362,003   245,810,564    61,448,562  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda10       3A35-1AEB                              vfat                                     
/dev/sda1        172B-13E1                              vfat                                     
/dev/sda5        1E57-1803                              vfat                                     
/dev/sda6        1966-1ADE                              vfat                                     
/dev/sda7        3639-1AE1                              vfat                                     
/dev/sda8        305A-1AE4                              vfat                                     
/dev/sda9        1D36-1AE8                              vfat                                     
/dev/sdb10       a13c1388-ca02-4361-91c6-c9fcc9fca51e   ext4                                     
/dev/sdb11       a619b12c-15eb-4fff-9ef2-3f1992fd6074   ext4                                     
/dev/sdb1        821810C21810B6DF                       ntfs                                     
/dev/sdb5        EA0CE5720CE539E9                       ntfs                                     
/dev/sdb6        5A640BD3640BB0B5                       ntfs                                     
/dev/sdb7        EC1817A418176CB8                       ntfs                                     
/dev/sdb8        01CB43D9F34CEC20                       ntfs                                     
/dev/sdb9        ce7f5776-5a9f-4441-925f-e2cd062af40e   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(5)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(5)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\="Microsoft Windows"  

=============================== sdb10/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb7 during installation
UUID=a13c1388-ca02-4361-91c6-c9fcc9fca51e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb12 during installation
UUID=ce7f5776-5a9f-4441-925f-e2cd062af40e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb10: Location of files loaded by Grub: ===================


  63.6GB: boot/grub/core.img
  63.5GB: boot/initrd.img-2.6.31-14-generic
  63.5GB: boot/vmlinuz-2.6.31-14-generic
  63.5GB: initrd.img
  63.5GB: vmlinuz

========================== sdb11/boot/grub/grub.cfg: ==========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,11)
search --no-floppy --fs-uuid --set a619b12c-15eb-4fff-9ef2-3f1992fd6074
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,11)
    search --no-floppy --fs-uuid --set a619b12c-15eb-4fff-9ef2-3f1992fd6074
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=a619b12c-15eb-4fff-9ef2-3f1992fd6074 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,11)
    search --no-floppy --fs-uuid --set a619b12c-15eb-4fff-9ef2-3f1992fd6074
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=a619b12c-15eb-4fff-9ef2-3f1992fd6074 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod fat
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 172b-13e1
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sdb10)" {
    insmod ext2
    set root=(hd1,10)
    search --no-floppy --fs-uuid --set a13c1388-ca02-4361-91c6-c9fcc9fca51e
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=a13c1388-ca02-4361-91c6-c9fcc9fca51e ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sdb10)" {
    insmod ext2
    set root=(hd1,10)
    search --no-floppy --fs-uuid --set a13c1388-ca02-4361-91c6-c9fcc9fca51e
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=a13c1388-ca02-4361-91c6-c9fcc9fca51e ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb11/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb11 during installation
UUID=a619b12c-15eb-4fff-9ef2-3f1992fd6074 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb9 during installation
UUID=ce7f5776-5a9f-4441-925f-e2cd062af40e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb11: Location of files loaded by Grub: ===================


 100.0GB: boot/grub/core.img
 100.0GB: boot/grub/grub.cfg
  94.9GB: boot/initrd.img-2.6.31-14-generic
  94.9GB: boot/vmlinuz-2.6.31-14-generic
  94.9GB: initrd.img
  94.9GB: vmlinuz

---

### Post by oldfred on 2010-09-03
If you cannot get the updates to run, it says there are major issues with the installs. We can keep trying to fix and I am willing to help if you want. but a new install may be in order. 

They have made improvements in grub2 but I found minor issues with initial boot of 10.04 where I had to add parameters to get video to work.

If you want a new install. Use gparted to delete sda10, sda11. You may want to make sda9 swap a little larger, I suggest a minimum of 2GB or the same size as RAM. You can create sda10 as 20GB and whatever is left as sda11.
Then use manual install and select sda10 as root and sda11 as /home and ext3 or ext4 for format. Since /home has no data you format it also although in the future you will not. On last partition screen use the advanced button to choose where to install grub.

---

### Post by electeng33 on 2010-09-04
Thanks for reply no.34.   I am not surprised at your suggestion to re-install, after having had to shut down twice whilst trying to follow the process you outlined in your last reply.  I do think re-installation sounds a better proposition than trying to fix the current installation, and from the position I am in at the moment it should be quite a simple procedure =- once I get a few things straight.

You mentioned 10.04, but I would rather stick with 9.10 as I am getting used to working with it, I have bought a 9.10 CD and have some books that I have found to be quite close to it on many points.   My experience with Windows has been that every new edition is quite different from the previous one, requiring a degree of re-learning.

Another consideration is that from some comments I have seen it appears that 10.04 may still have a few bugs - e.g. your comment about difficulty with video.

I thought a day or two ago that we were so close to getting 9.10 and WinXP to work together in harmony - with only the 'ctrl-alt-delete' subterfuge in the way.   This showed that it was only a booting problem.   However I would value your advice on this.

I should certainly take the opportunity to re-size and re-partition.   In paragra[h 3 of hyour reply you seem to be suggesting grub, sad10 and sda11 only,  but there are a bewildering array of othetr mount options available i.e. home, tmp, usr, var, svr, opt, usr/locaL  My thought orioginally was to have several partitions for documents, applications, etc., as I do with Windows.   Later reading has made me wonder whether this is possible with Ubuntu - or whether I should create folders within sdb11 for that purpose.   It would be helpful if you could also advise me on this.   

Could you also let me know whether it will also be necessary to remove anything from sda (WinXP disk),   At the moment windows will not run either, even when I select the windows hard disk as the primary boot drive.

Many thanks for expressing your willingness to continue to help me, it is greatly appreciated.

---

### Post by oldfred on 2010-09-04
You have grub in the MBR of both sda & sdb. You can reinstall a windows boot loader to sda. Then from BIOS you can boot windows. 

Restore basic windows style boot loader - universe enabled from Ubuntu or liveCD
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

All the other system folders (usr, tmp etc) do not need partitions. If you have a server the answer may be different but standard desktop only needs / (root) & swap. I recommend either separate /home or separate data partition. If sharing with windows a NTFS shared partition is a good idea. Because I am now mostly in Ubuntu I have both a NTFS shared for some data with windows and a /data partition since I have several versions of Ubuntu (like you do in sda10 & sda11:))

If you want to reinstall 9.10 that is ok. My standard starting install is:
Herman on advantages/disadvantages of separate system partitions
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)
Install with creating partitions screen shots
[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")

1. 10-20 GB Mountpoint / primary beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical (or size of RAM memory)

If you do not want a separate /home make root the 20GB which still is enough if you have all (most) of your data in other (data) partitions. I use 20GB system partitions, but even with many programs installed have only used about 6GB (wine in .home seems to be one of the big ones). I did have /home separate in Karmic but only had about 1GB of mostly hidden folders & files, but I was aggressive in moving anything that accumulates data into a data partition.

If you do reinstall Karmic make sure you install grub to sdb by using the advanced button.

Install Screens shown with advanced button
[http://members.iinet.net.au/~herman546/p24/022f.png]("http://members.iinet.net.au/%7Eherman546/p24/022f.png")
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)

Dual boot 2 drives, windows & Lucid 10.04 (colors are the major change from 9.10 to 10.04 install procedure, Maverick has major changes)
[http://members.iinet.net.au/~herman546/p24/022f.png]("http://members.iinet.net.au/%7Eherman546/p24/022f.png")
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")

---

### Post by electeng33 on 2010-09-07
Thanks 'oldfred' for reply no.35, and particularly for the trouble you went to in giving me the helpful links.

I used the code which you suggested and was able to restore the boot for WindowsXP, which I am able to use quite satisfactorily.

Then I re-partitioned the Ubuntu hard disk (sdb), I intended to put on an NTFS partition but when I got to that there was no option in gparted for that but there was for FAT32 so I used that instead - I suppose that means that I can only use that partition for Windows.

I re-installed from my Ubuntu CD following your advice, paying particular attention to the 'advanced' button.   I note from the boot info script that grub is in sdb1, and there is no indication of a 'UUID... error'.    

At the end of the install process, the 'restart' option duly booted Ubuntu with my name in the top left hand corner and all seemed to be well.   Unfortunately, though, after then shutting down, I am unable to  boot Ubuntu.   

With BIOS set to give priority to sdb I get the grub menu, from which I am able to boot Windows.   When I try to boot Ubuntu I see the black screen with the Ubuntu motif in the middle with the small rotating circle.   Then both disappear and nothing further happens.   I can boot the recovery mode, though.  

I have copied the boot script record, from which I am hoping that you will be able to spot what is wrong and that it can be corrected as easily as the lilo boot for Windows. 

```

``` Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 98
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /IO.SYS /MSDOS.SYS 
                       /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcba8cba8

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     4,192,964     4,192,902   b W95 FAT32
/dev/sda2           4,192,965   156,296,384   152,103,420   f W95 Ext d (LBA)
/dev/sda5           4,193,028    47,713,049    43,520,022   b W95 FAT32
/dev/sda6          47,713,113    68,195,924    20,482,812   b W95 FAT32
/dev/sda7          68,195,988    84,582,224    16,386,237   b W95 FAT32
/dev/sda8          84,582,288   108,149,579    23,567,292   b W95 FAT32
/dev/sda9         108,149,643   131,716,934    23,567,292   b W95 FAT32
/dev/sda10        131,716,998   156,296,384    24,579,387   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00031a86

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    39,070,079    39,070,017  83 Linux
/dev/sdb2          39,070,080   312,576,704   273,506,625   5 Extended
/dev/sdb5          39,070,143    42,973,874     3,903,732  82 Linux swap / Solaris
/dev/sdb6          42,973,938    82,043,954    39,070,017   b W95 FAT32
/dev/sdb7          82,044,018   312,576,704   230,532,687  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda10       3A35-1AEB                              vfat                                     
/dev/sda1        172B-13E1                              vfat                                     
/dev/sda5        1E57-1803                              vfat                                     
/dev/sda6        1966-1ADE                              vfat                                     
/dev/sda7        3639-1AE1                              vfat                                     
/dev/sda8        305A-1AE4                              vfat                                     
/dev/sda9        1D36-1AE8                              vfat                                     
/dev/sdb1        c48afc08-79ff-4f50-98f6-37c6a13870c7   ext4                                     
/dev/sdb5        4fab9620-61eb-45b9-bf02-077e7eedfd7b   swap                                     
/dev/sdb6        87D3-E684                              vfat                                     
/dev/sdb7        3041cc1f-f255-4779-be08-b8df5dae93a6   ext4                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(5)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(5)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\="Microsoft Windows"  

=========================== sdb1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,1)
search --no-floppy --fs-uuid --set c48afc08-79ff-4f50-98f6-37c6a13870c7
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set c48afc08-79ff-4f50-98f6-37c6a13870c7
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=c48afc08-79ff-4f50-98f6-37c6a13870c7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set c48afc08-79ff-4f50-98f6-37c6a13870c7
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=c48afc08-79ff-4f50-98f6-37c6a13870c7 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod fat
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 172b-13e1
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=c48afc08-79ff-4f50-98f6-37c6a13870c7 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb7 during installation
UUID=3041cc1f-f255-4779-be08-b8df5dae93a6 /home           ext4    defaults        0       2
# /windows was on /dev/sdb6 during installation
UUID=87D3-E684  /windows        vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sdb5 during installation
UUID=4fab9620-61eb-45b9-bf02-077e7eedfd7b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .7GB: boot/grub/core.img
    .7GB: boot/grub/grub.cfg
    .7GB: boot/initrd.img-2.6.31-14-generic
    .6GB: boot/vmlinuz-2.6.31-14-generic
    .7GB: initrd.img
    .6GB: vmlinuz

---

### Post by oldfred on 2010-09-07
Could you start putting scripts in code tags, I meant to suggest that several posts ago and forgot. Code tags put the script in a scroll box and preserve formating to make it easier to read and review. You can highlight code with the cursor and click on the # icon above your post in the right side of the edit panel where it has fonts, colors and many other options. But I am not sure you will need to post it again.

If you are past the grub menu, then you are booting and now have some other issue.

If you can boot recovery mode, can you run the updates from that? From the recovery mode can you type startx and get to a graphical screen rather than just the command line? If you can get into your system try running all the updates from system, administration, update manager.

---

### Post by electeng33 on 2010-09-09
Thanks 'oldfred' for reply no.38.   Sorry about the '#', I did know about it and have generally been using it, but looking back I see that on the last message I sent I had forgotten it.

I used 'startx' as you suggested and was most surprised to get the Ubuntu graphical screen and apparently all the Ubuntu facilities as well.   This time it had 'root' in the top right hand corner of the screen instead of the customary 'Ubuntu' when using the CD, and my first name on the rare occasions I have been able to boot Ubuntu from the hard drive

I got into Upgrade Manager which told me it could update 315 files.   I set it to work, then it advised me that some of the packages could not be retrieved from the server.   I opted to continue, the dpkg was automatically run to install the software.

A message then came up asking what to do about grub (without telling me whether there was anything wrong with grub) and giving various options - as I did not know what the options entailed, I opted to 'keep version currently installed'.

A black terminal type screen then appeared with various lines of code, getting down to  the following:-

"Errors were encountered while processing:    
            grub-pc
W: Failed to fetch http>//security.ubuntu. com/ubuntu'pool/main/s/sudo/sudo1.7.0=ubuntu 2.4   i386.deb
404 Not found [IP: 91.189.88.37 80]
E: sub-process /var/bin/dpkg returned an error code (1)
A package failed to install
Trying to recover
Setting up grub-pc(1.97~beta4-lubuntu4.1)

The pc then stuck at that point and I had to switch off the supply.

I ran Update Manager again and got a message saying there was now 1 file for which there was an upgrade - "sudo (provide limited super user privileges to specific users) (size 290kb).   I tried to upgrade that and ended up with the same details on the screen as appeared at the end of the first running of Upgrade Manager. 
viz. 'Setting up grub-pc...'

I got into Upgrade Manager for the third time and it indicated no files needed so I selected the 'check' button, and it then came up with 'Firefox' saying 10 files could be upgraded.   I asked it to continue and it stuck at the same point
'Setting up grub-pc...'

I am sending the above in some detail, as I think it probably gives significant information as to where the source of the trouble now lies.   I would greatly appreciate your further advice as to how best to proceed having reached this point.
 
Many thanks

---

### Post by oldfred on 2010-09-09
I said keep installed version of some config files years ago and had monster problems as the new version software did not really work with the config file I had. It is best to have backups, but usually they make a backup anyway and you should choose to upgrade. It is only for those who have customized setting that they want to keep.

Not sure about sudo error on downloads. Have you tried changing Software Sources in system, Administration? Where is says download from click on combo box and let it give you an optimal choice.

You can try uninstalling grub & grub-pc (grub2). But if it does not reinstall you will not be able to boot.

I copied this from my chroot notes where you do not need sudo. You will need sudo before every command. Or, I think you can do sudo -i and then you will not need sudo for each command.
# uninstall both grub legacy & grub2 reinstall grub2 and to sda
apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
grub-install /dev/sda
grub-install --recheck /dev/sda

sudo dpkg-reconfigure grub-pc

---

### Post by electeng33 on 2010-09-17
```

```Thanks 'Oldfred' for reply no.40, I note your advice about not retaining old files.   I found my way through Upgrade Manager, changed the software source and after installation the application indicated that there were no further upgrades needed.  I presume that at that stage I had a completely upgraded Ubuntu

    I then went through the commands you gave regarding removal of grub and re-installing, and unfortunately I am now back in the position as outlined in reply no.33, with a 'sh:grub >' prompt.   Thus I was not able to boot the PC with either Ubuntu or WindowsXP.   I restored Windows boot by using my live CD and running through the code which you gave me in reply no36, but I cannot get either Ubuntu or the recovery mode to boot.     

    Let me go in detail through the steps I took, by showing you the screen printing, because there were some uncertainties as I went through, and the actual screen printing may show up what went wrong.   My comments I have put in parentheses and in red to ease identification, which when looking at my draft reply I thought might be quite difficult to sort out.   I hope this is a help:-

 root@roy-desktop: ~# sudo -i apt-get purge grub grub-pc grub-common
Reading package lists...Done
Building dependency tree
Reading state information...Done
Package grub is not installed, so not removed
     **[COLOR=Red](Is that significant? - If is is how could it not have been installed, and could you suggest a remedy?)[/COLOR]**
The following packages were uautomatically installed and are no longer required:
linux-headers-2.6.31-14 linux-headers-2.6.31-14generic
Use 'opt-get autoremove' to remove them
   **[COLOR=Red] (Could I do that from the live CDS, or must I get Ubuntu to boot first?)[/COLOR]**
The following packages will be REMOVED
    grub-common* grub-pc*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded
After this operation, 4170kB disk space will be freed.
Do you want to continue [y/n]?  
    **[COLOR=Red](I, of course, replied yes)[/COLOR]**

(Immediately another screen came up)
Do you want to have all GRUB2 files removed from /boot/grub?
    [B][COLOR=Red](- warning given that it will be unbootable if another boot loader is not installed
    - opted for yes)

    (Another screen came up)
[/COLOR][/B]Removing grub-common
    **[COLOR=Red](Although the command included grub-pc, it is not mentioned here - is that     significant?)[/COLOR]**
Purging configuration files for grub-common...
Processing triggers for man-db...
Processing triggers for ureadahead...
unreadahead will be reprofiled on next reboot...
Processing triggers for install-info...

root@roy-desktop:~#   mv /boot/grub /boot/grub_backup
    [B][COLOR=Red](on pressing enter I immediately got the command line, no confirmation of     action or notification of error - is that what is expected from 'mv' type     commmands? - I then continued going through your list of commands)
[/COLOR][/B]
root@roy-desktop:~#   sudo mkdir /boot/grub
   **[COLOR=Red] (then the following new screen came up)[/COLOR]**
                [Configuring grub-pc]
the following Linux command line was extracted from /etc/default/grub or the 'kopt' parameter in GRUB Legacy's menu list.   Please verify that it is correct and modify it if necessary
   [B][COLOR=Red] (there was a horizontal strip across the screen , at the left hand end of which it said 'Linux command line _', but there was nothing following that wording.       Even if there had been, I do not know enough to be able to say whether it is correct or not)
    (I therefore OK'd it)

    (a second screen then appeared)[/COLOR][/B]
                [Configuring grub-pc]
The following string will be used as Linux parameters for the default menu entry but not for the recovery mode.
Linux default command line:  quiet splash
   [B][COLOR=Red] (I presume that is what is expected, anyway I had no option but to OK it)
            
    (third screen appeared)[/COLOR][/B]
                [Configuring grub-pc] 
The grub package is being upgraded.   This menu allows you to select which devices you'd like grub-install to be automatically run for, if any.
It is recommended that you do this in most situations, to prevent the installed grub from getting out of synch with other components such as grub.cfg or with newer Linux images it will have to load.
If you're unsure which drive is designated as nboot drive by your BIOS it is often a good ideda to install GRUB to all of them    
    /dev/sda
    /dev/sdb
  [B][COLOR=Red]  (I could find no way of highlighting both of the menu items at the same time, so opted for /sdb.  Later, as you will see, I went though this again and highlighted /sda)

    (OK'd screen and immediately got the terminal prompt and continued down     your list of commands)[/COLOR][/B]
root@roy-desktop:~#   grub-install /dev/sda
Installation finished   No error reported.
This is the contents of the device map /boot/grub/devices.map.
Check if this is correct or not.   If any of the lines is incorrect fix it and re-run the script 'grub-install'
(fd0)   /dev/fd0
(hd0)   /dev/sda
(hd1)   /dev/sdb
    **[COLOR=Red](I dont know whether this is correct or not, so if there were errors I was not     able to correct them)[/COLOR]**

root@roy-desktop:~#   grub-install --recheck /dev/sda
    **[COLOR=Red](I then received a repeat of the three lines of the device map as above)[/COLOR]**

root@roy-desktop:~#  sudo dpkg-reconfigure grub-pc
    [B][COLOR=Red](I got a repeat of the earlier screen saying command line was extracted from     /etc/default....   received 'quiet splash' again, then received the third screen     about installing grub-pc, I selected /sda this time, as indicated earlier)
    
    (tried 'grub-install --recheck' again, and received the same screen printing as     before).

    (then switched off pc, and re-started, and received the following screen print) [/COLOR][/B]   
                            GNU GRUB version 1.97~ beta4
[Minimal BASH-like line editing is supported.   For the first word TAB lists possible command completion.   Anywhere else TAB lists possible device/file completion.]

    [B][COLOR=Red](On using TAB, screen displayed a long list of code)

    (I switched BIOS priority to /sda and received the same message on switch on)
[/COLOR][/B]

    It will be no great difficulty to re-install Ubuntu as I did before, and I already have your guidance as to how to do that from replies 34/36, but I presume something has gone wrong with the re-installation and unless this is identified it seems probable that I will end up with the same result again.   I will greatly appreciate your further advice.

---

