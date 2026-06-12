---
title: "proplem in entering ubuntu"
date: 2010-10-05
forum: New to Ubuntu
---

### Post by Andrew9000 on 2010-10-05
after the last update when i enter ubuntu the computer restart
 
any ideas ??????

---

### Post by Rubi1200 on 2010-10-05
The information you have provided is insufficient for us to answer your problem.

Please post the computer specifications, Ubuntu version, and how you installed (hard drive or via Wubi).

Thanks.

Oh, and welcome to the forums!

---

### Post by Andrew9000 on 2010-10-05
thanks alot for reply :)

my computer specifications:
pentium(R) 4 CPU 3.00GHZ
3.00GHZ, 0.99 GB of RAM
 
Ubuntu version:
ubuntu 10.04
 
installed it by wubi

---

### Post by Andrew9000 on 2010-10-05
i download boot info script
the _RESULTS.txt_ is:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr /wubildr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk 
                       /boot/grub/core.img

sda8/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda9: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sda9 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    19,535,039    19,534,977   c W95 FAT32 (LBA)
/dev/sda2          19,535,040   234,435,438   214,900,399   f W95 Ext d (LBA)
/dev/sda5          19,535,103    39,070,079    19,534,977   b W95 FAT32
/dev/sda6          39,070,143    87,907,679    48,837,537   b W95 FAT32
/dev/sda7          87,907,743   136,745,279    48,837,537   b W95 FAT32
/dev/sda8         136,745,343   185,582,879    48,837,537   b W95 FAT32
/dev/sda9         185,582,943   234,435,438    48,852,496   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       94feec36-3311-4ad9-9f62-95bfea677dc5   ext4                                     
/dev/sda1        2C4D-6E46                              vfat                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        98CD-B175                              vfat       SONGS                         
/dev/sda6        0000-0EBF                              vfat       CHRISTIANS                    
/dev/sda7        98E9-BB06                              vfat       GAMES                         
/dev/sda8        0000-0EC1                              vfat       ORIGINAL                      
/dev/sda9        7CF1-D9E7                              vfat       MOVIES                        
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda7        /media/GAMES             vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\wubildr.mbr = "Ubuntu" 

=================== sda8: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

======================== sda8/Wubi/boot/grub/grub.cfg: ========================

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
insmod fat
set root='(hd0,8)'
search --no-floppy --fs-uuid --set 0000-0ec1
loopback loop0 /ubuntu/disks/usr.disk
set root=(loop0)
if loadfont /share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod fat
set root='(hd0,8)'
search --no-floppy --fs-uuid --set 0000-0ec1
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-25-generic" {
    insmod fat
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 0000-0ec1
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sda8 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, Linux 2.6.32-25-generic (recovery mode)" {
    insmod fat
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 0000-0ec1
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sda8 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic" {
    insmod fat
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 0000-0ec1
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda8 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic (recovery mode)" {
    insmod fat
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 0000-0ec1
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda8 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, Linux 2.6.32-21-generic" {
    insmod fat
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 0000-0ec1
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda8 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, Linux 2.6.32-21-generic (recovery mode)" {
    insmod fat
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 0000-0ec1
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda8 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod fat
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2c4d-6e46
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda8/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/usr.disk /usr            ext4    loop            0       2
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

================= sda8/Wubi: Location of files loaded by Grub: =================


    .1GB: boot/grub/core.img
    .7GB: boot/grub/grub.cfg
    .6GB: boot/initrd.img-2.6.32-21-generic
    .6GB: boot/initrd.img-2.6.32-24-generic
    .0GB: boot/initrd.img-2.6.32-25-generic
    .4GB: boot/vmlinuz-2.6.32-21-generic
    .5GB: boot/vmlinuz-2.6.32-24-generic
    .4GB: boot/vmlinuz-2.6.32-25-generic
    .0GB: initrd.img
    .6GB: initrd.img.old
    .4GB: vmlinuz
    .5GB: vmlinuz.old
```

---

### Post by mastablasta on 2010-10-05
Ok so you used Wubi to install it. Wubi still has some issues. It is running some sort of virtualisation withing windows. more here: [http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)
 
i suggest you do a propper dual boot instal. check the manual on how to do it.

---

### Post by Rubi1200 on 2010-10-05
Installing Wubi can be problematic, especially since there have been recent GRUB related issues.

See here for more information:
> **[COLOR=DarkRed][SIZE=3]Important Note to Wubi (Windows Ubuntu) Users: Grub Update results in "No Such Disk":[/SIZE][/COLOR] **
A late July 2010 Grub 2 update is causing a "**[COLOR=DarkRed]no such disk[/COLOR]**"  error for some users of WUBI, resulting in an unbootable system. If the  system doesn't display the original Windows menu, the most likely cause  of the failure is that Grub 2 was installed in the MBR and/or on the  Windows partition. To correct this, restore the Windows bootloader using  this link:
[How to restore the Ubuntu/XP/Vista/7 bootloader]("http://ubuntuforums.org/showthread.php?t=1014708")

Whether the failure is due to improper user selections or Grub 2's  failure to recognize a Wubi install, it has been reported in the  following bug and users can review it for status updates and recovery  options when they become available:
[https://bugs.launchpad.net/wubi/+bug/610898](https://bugs.launchpad.net/wubi/+bug/610898)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

If you can still boot into Windows, then consider moving the Ubuntu install to the drive:
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

If you are also having problems booting Windows, I suggest first reinstall the Windows bootloader and then take the necessary steps to make Ubuntu a more permanent install.

Restore Windows bootloader:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by Andrew9000 on 2010-10-05
i don't know how to do a proper a dual boot i tried many things and failed :(

---

### Post by krishnandu.sarkar on 2010-10-05
Well...google it out...there are lots of step by step tutorial.

---

### Post by Rubi1200 on 2010-10-05
Or we can help a little bit:
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

---

### Post by Andrew9000 on 2010-10-05
this the result of sudo fdisk -l   it's not the same in the examples 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2c9b2c9b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9767488+   c  W95 FAT32 (LBA)
/dev/sda2            1217       14593   107450199+   f  W95 Ext'd (LBA)
/dev/sda5            1217        2432     9767488+   b  W95 FAT32
/dev/sda6            2433        5472    24418768+   b  W95 FAT32
/dev/sda7            5473        8512    24418768+   b  W95 FAT32
/dev/sda8            8513       11552    24418768+   b  W95 FAT32
/dev/sda9           11553       14593    24426248    b  W95 FAT32

---

### Post by bcbc on 2010-10-05
There is a problem with grub2 and lupin (used for wubi) that has got the wubildr out of sync with the latest version of grub.

So, basically, wubildr can't handle the commands in the grub.cfg menu and the computer reboots.

To fix from live CD:
```
sudo mkdir /media/win
sudo mount /dev/sda8 /media/win
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt

```
Edit grub.cfg and delete everything above the first menuentry. Everything above
> ### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-25-generic" { 
```
gksudo gedit /mnt/boot/grub/grub.cfg
```

save and reboot. Don't update grub-pc afterwards, run "sudo update-grub", or install/uninstall any kernels, or the problem will reoccur.

I'm not aware of a fix. So you can install a direct version of ubuntu. Or you can migrate your wubi install to a direct install. This will prevent the problem reoccurring and keep all your data/settings in tact.
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

