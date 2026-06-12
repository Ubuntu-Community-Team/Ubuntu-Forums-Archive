---
title: "Re-establishing the boot partition"
date: 2010-04-16
forum: New to Ubuntu
---

### Post by KirbySmith on 2010-04-16
After installing 9.10 onto IDE0 from a live CD, I discovered that grub2 was installed into the MBR of a separate data disk, call it SATA1, which had somehow moved to the top of the BIOS boot order.  After reordering the boot order in the BIOS, the installation would not boot because grub could not find the disk it wanted.

Working from the live cd and running "sudo fdisk -l", fdisk treated SATA1 as sda, SATA2 as sdb, and the actual ubuntu disk as sdc.  An asterisk after sda1 in fdisk showed that it was the boot disk.

Initial attempts to correct this using the cornucopia of grub 2 instructions on this forum were unsuccessful.  After the process leading to grub-install, aimed at sdc1, rebooting resulted in:[INDENT]> Alert! /dev/sdd1 does not exist.[/INDENT]sdd1 was never part of the conversation.

Doing the grub-install process all over again from the live cd with all drives removed except the one with the ubuntu installation led to it booting ok (I'm writing from it), but running "sudo fdisk -l" in a terminal window reveals that new sda1 does not have a boot asterisk.  I'm afraid that when I return the data disks to operation, the SATA1 grub installation will take over.

My questions.

How do I force the linux installation hard drive to be recognized as a boot drive in fdisk?

How do I remove (using the live cd, say) the grub installation from SATA1?

Thank you very much in advance

kirby

---

### Post by oldfred on 2010-04-16
The asterisk is the boot flag or windows active partition. Ubuntu/grub does not use the boot flag, windows has to have a boot flag, but some BIOS will not let you boot unless you have a boot flag on a primary partition. You can set boot flag with gparted (right click on partition and manage flags), Disk utility or command line with sfdisk, parttool or maybe others.

BIOS starts the boot and transfers to the primary master hard drive. With sata BIOS you can just select which drive to boot from and that drive's MBR (master boot record) will then take over booting. The MBR is tiny and transfers control to the grub files or windows PBR (partition boot record).

Having grub in any drive or all drives is not a problem. Generally you do not install grub to a partition (PBR) as that will overwrite the windows boot loader. You may install grub to the Ubuntu partition if you have multiple installs and want to use another grub to boot and then chainboot into the PBR.

With multiple drives you can better understand what is where with this tool we use to solve boot issues. I run it before and after any system updates to make sure I know where everything is at.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by KirbySmith on 2010-04-16
Oooo.  Thanks.  As soon as I can try it with the other drives (presently disconnected) I'll report the results.

kirby

---

### Post by KirbySmith on 2010-04-16
OK, oldfred, what I've done so far is hot start the two SATA drives and use Palimpsest Disk Utility to set the boot flag on the Linux drive and remove it from the SATA drive.  (I didn't appreciate what this utility could do until I started looking for gparted.)  The following is the output from Boot Info Script,   I think the first few lines clarify the situation.  I have yet to reboot.

Anticipating a smooth boot, thanks again

kirby

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks for 
    (UUID=122812e5-78f1-4861-b71f-b29fabc0a918)/boot/grub.
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0009ba9e

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   300,511,889   300,511,827  83 Linux
/dev/sda2         300,511,890   312,576,704    12,064,815   5 Extended
/dev/sda5         300,511,953   312,576,704    12,064,752  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd6c527e3

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   311,291,504   311,291,442   7 HPFS/NTFS
/dev/sdb2         311,291,505   625,137,344   313,845,840   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd6a93e20

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   311,291,504   311,291,442   7 HPFS/NTFS
/dev/sdc2         311,291,505   625,137,344   313,845,840   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        122812e5-78f1-4861-b71f-b29fabc0a918   ext4                                     
/dev/sda5        eb2fb67c-66cb-45c4-846b-058a883269be   swap                                     
/dev/sdb1        AA0066FB0066CE3F                       ntfs       BKP_O                         
/dev/sdb2        7878098E78094C76                       ntfs       BKP_P                         
/dev/sdc1        D840BF7040BF544A                       ntfs       Anime A-M                     
/dev/sdc2        32C4453AC4450219                       ntfs       Anime N-Z                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root=(hd0,1)
search --no-floppy --fs-uuid --set 122812e5-78f1-4861-b71f-b29fabc0a918
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
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 122812e5-78f1-4861-b71f-b29fabc0a918
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=122812e5-78f1-4861-b71f-b29fabc0a918 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 122812e5-78f1-4861-b71f-b29fabc0a918
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=122812e5-78f1-4861-b71f-b29fabc0a918 ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 122812e5-78f1-4861-b71f-b29fabc0a918
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=122812e5-78f1-4861-b71f-b29fabc0a918 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 122812e5-78f1-4861-b71f-b29fabc0a918
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=122812e5-78f1-4861-b71f-b29fabc0a918 ro single 
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
# / was on /dev/sdc1 during installation
UUID=122812e5-78f1-4861-b71f-b29fabc0a918 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=eb2fb67c-66cb-45c4-846b-058a883269be none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .3GB: boot/grub/core.img
    .3GB: boot/grub/grub.cfg
    .5GB: boot/initrd.img-2.6.31-14-generic
    .8GB: boot/initrd.img-2.6.31-20-generic
    .5GB: boot/vmlinuz-2.6.31-14-generic
    .6GB: boot/vmlinuz-2.6.31-20-generic
    .8GB: initrd.img
    .5GB: initrd.img.old
    .6GB: vmlinuz
    .5GB: vmlinuz.old
```

---

### Post by KirbySmith on 2010-04-17
boots fine now

thanks

---

