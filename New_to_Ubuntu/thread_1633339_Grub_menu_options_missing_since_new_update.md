---
title: "Grub menu options missing since new update"
date: 2010-11-29
forum: New to Ubuntu
---

### Post by winjeel on 2010-11-29
I did the regular updates this morning before leaving for work. I come home from work (to do more work), but Windows is now missing from the grub menu list. I use some specialised programs that will never be available for Linux or Wine and I desperately need to use them **now**. I am of course pretty peeved, because I promised to make some files available for some people tonight (it's night time already here in Japan). How can I have Windows put back as a menu option?

---

### Post by whitehorse2010 on 2010-11-29
Are you saying you can log into ubuntu? If so type this on the command line and see which drive shows 'windows'.

$ sudo fdisk -l

And lets know what you find.

---

### Post by winjeel on 2010-11-29
> **whitehorse2010 said:**
> Are you saying you can log into ubuntu? If so type this on the command line and see which drive shows 'windows'.

$ sudo fdisk -l

And lets know what you find.

Ubuntu is fine. In fact it lists about 10 Ubuntus (I have only one installed, though), plus Dell Utilities.

---

### Post by winjeel on 2010-11-29
I tried it but it gave me an error message with this: `'.

---

### Post by amjjawad on 2010-11-29
> **prabhakaran99 said:**
> Friends,


             Please give some idea, because i installed the ocs inventory-agent one option will appear Local or HTTP. my support office gave ip id for HTTP i typed the ip but i was incomplete  (Ex: 192.168.53 ) like this. I try to remove the package but i'll be skip the option (Local or http)  what can i do today i submit the report to my boss. please sent the answer.

With Regards 

Prabhakaran99

Please start a new thread :)

---

### Post by amjjawad on 2010-11-29
> **winjeel said:**
> I did the regular updates this morning before leaving for work. I come home from work (to do more work), but Windows is now missing from the grub menu list. I use some specialised programs that will never be available for Linux or Wine and I desperately need to use them **now**. I am of course pretty peeved, because I promised to make some files available for some people tonight (it's night time already here in Japan). How can I have Windows put back as a menu option?

If that's a regular Ubuntu-Installation and NOT wubi installation then try:

Applications > Accessories > Terminal
Type:

```
sudo update-grub

```
or just copy and paste the above code into the Terminal.

That's IMHO the first step. If it did not work, certainly there are other steps.

---

### Post by winjeel on 2010-11-29
I tried that, it said that if found Windows XP. I restarted and still no Windows in the Grub menu.

---

### Post by amjjawad on 2010-11-29
> **winjeel said:**
> I tried that, it said that if found Windows XP. I restarted and still no Windows in the Grub menu.

Is it [wubi]("https://wiki.ubuntu.com/WubiGuide") installation or regular installation?

---

### Post by winjeel on 2010-11-29
A regular installation

---

### Post by amjjawad on 2010-11-29
> **winjeel said:**
> A regular installation

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Please, post the result here and wrap up the text with CODE (#) tag.

---

### Post by winjeel on 2010-11-29
Here it is...

PS: I have Puppy Linux installed and Dell Utilities in their own partitions.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr /wubildr

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

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262   6 FAT16
/dev/sda2    *         80,325    91,775,876    91,695,552   7 HPFS/NTFS
/dev/sda3          91,777,022   117,209,087    25,432,066   5 Extended
/dev/sda5          91,777,024   116,039,679    24,262,656  83 Linux
/dev/sda6         116,041,728   117,209,087     1,167,360  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1              16,065 1,953,520,064 1,953,504,000   f W95 Ext d (LBA)
/dev/sdb5              16,128 1,953,520,064 1,953,503,937   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07D6-0705                              vfat       DellUtility                   
/dev/sda2        5A04F93304F912AD                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        27714869-468d-4f30-8ca5-4318c7a6f470   ext4                                     
/dev/sda6        56128b27-1d2d-46d1-94f3-0a9adcac4556   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1: PTTYPE="dos" 
/dev/sdb5        300C-12EA                              vfat       LOGITEC HD                    
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sdb5        /media/LOGITEC HD        vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\wubildr.mbr="Ubuntu"  

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
search --no-floppy --fs-uuid --set 27714869-468d-4f30-8ca5-4318c7a6f470
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
search --no-floppy --fs-uuid --set 27714869-468d-4f30-8ca5-4318c7a6f470
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
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 27714869-468d-4f30-8ca5-4318c7a6f470
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=27714869-468d-4f30-8ca5-4318c7a6f470 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 27714869-468d-4f30-8ca5-4318c7a6f470
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=27714869-468d-4f30-8ca5-4318c7a6f470 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 27714869-468d-4f30-8ca5-4318c7a6f470
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=27714869-468d-4f30-8ca5-4318c7a6f470 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 27714869-468d-4f30-8ca5-4318c7a6f470
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=27714869-468d-4f30-8ca5-4318c7a6f470 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 27714869-468d-4f30-8ca5-4318c7a6f470
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=27714869-468d-4f30-8ca5-4318c7a6f470 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 27714869-468d-4f30-8ca5-4318c7a6f470
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=27714869-468d-4f30-8ca5-4318c7a6f470 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 27714869-468d-4f30-8ca5-4318c7a6f470
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=27714869-468d-4f30-8ca5-4318c7a6f470 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 27714869-468d-4f30-8ca5-4318c7a6f470
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=27714869-468d-4f30-8ca5-4318c7a6f470 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 27714869-468d-4f30-8ca5-4318c7a6f470
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=27714869-468d-4f30-8ca5-4318c7a6f470 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 27714869-468d-4f30-8ca5-4318c7a6f470
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=27714869-468d-4f30-8ca5-4318c7a6f470 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 27714869-468d-4f30-8ca5-4318c7a6f470
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=27714869-468d-4f30-8ca5-4318c7a6f470 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 27714869-468d-4f30-8ca5-4318c7a6f470
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=27714869-468d-4f30-8ca5-4318c7a6f470 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 27714869-468d-4f30-8ca5-4318c7a6f470
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 27714869-468d-4f30-8ca5-4318c7a6f470
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Dell Utility Partition (on /dev/sda1)" {
    insmod fat
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 07d6-0705
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 5a04f93304f912ad
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
UUID=27714869-468d-4f30-8ca5-4318c7a6f470 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=56128b27-1d2d-46d1-94f3-0a9adcac4556 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  54.8GB: boot/grub/core.img
  57.3GB: boot/grub/grub.cfg
  53.7GB: boot/initrd.img-2.6.32-21-generic
  54.2GB: boot/initrd.img-2.6.32-22-generic
  55.0GB: boot/initrd.img-2.6.32-23-generic
  57.3GB: boot/initrd.img-2.6.32-24-generic
  55.6GB: boot/initrd.img-2.6.32-25-generic
  55.1GB: boot/initrd.img-2.6.32-26-generic
  53.7GB: boot/vmlinuz-2.6.32-21-generic
  54.1GB: boot/vmlinuz-2.6.32-22-generic
  54.8GB: boot/vmlinuz-2.6.32-23-generic
  57.3GB: boot/vmlinuz-2.6.32-24-generic
  54.9GB: boot/vmlinuz-2.6.32-25-generic
  55.1GB: boot/vmlinuz-2.6.32-26-generic
  55.1GB: initrd.img
  55.6GB: initrd.img.old
  55.1GB: vmlinuz
  54.9GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  f6 f7 f6 fa fb f6 f7 f8  f6 f6 f7 f5 f0 f8 f5 f2  |................|
00000010  f4 f1 f3 f3 f3 f1 f2 f2  f2 f2 ef e4 ed f1 ef ef  |................|
00000020  ec e9 e5 e9 e4 ea e5 e8  e5 e7 e3 e9 e7 e4 e3 e5  |................|
00000030  e4 e1 e5 df e4 e6 e8 e6  e6 e6 e0 e4 e7 e5 e3 e3  |................|
00000040  e2 db e2 e4 e5 e1 de dd  df e3 e0 db e0 de de dc  |................|
00000050  e2 e3 e1 e2 de e0 dc de  e3 e0 e5 e5 e1 e0 e4 e3  |................|
00000060  e4 e3 e5 e3 e2 dd db da  d9 d9 d9 da d8 d5 d6 d9  |................|
00000070  db d8 db d6 d8 db d9 d6  d8 d8 db d8 d8 db da d8  |................|
00000080  d9 d8 db db d7 d9 d6 d9  d9 d9 d5 d7 d3 d7 da da  |................|
00000090  d8 db d8 d8 d8 db db d9  d4 d8 d2 d5 d2 d2 d0 cf  |................|
000000a0  cf cd cb c2 a5 cb ce 9a  f5 f7 f4 ee ee ef ee ee  |................|
000000b0  ec ec eb ec ea e7 e7 e8  eb eb ee ef f0 ed f0 f0  |................|
000000c0  f0 f1 f1 f1 f3 f5 f4 f4  f4 f2 f1 f0 ef f0 f0 f2  |................|
000000d0  f4 f2 f3 f2 f3 f1 ee ee  f1 ef f2 f2 f2 f3 f1 f2  |................|
000000e0  f1 f1 f1 ef f3 f3 f5 f4  f2 f5 f4 f5 f6 f6 f7 f6  |................|
000000f0  f4 f4 f4 f5 f6 f8 fa f6  f5 f9 f5 f6 f9 f7 f8 f7  |................|
00000100  f5 f6 fa f4 f5 f4 f4 f5  f6 f8 f9 f7 f6 f4 f3 f3  |................|
00000110  f4 f3 f2 f0 f1 f2 f2 f5  f1 f2 f0 ef f0 f3 f1 f3  |................|
00000120  f2 ef ea ee ee ee ef e9  eb ea e8 eb ea ea ea ea  |................|
00000130  e9 e7 e9 e7 e7 e5 e7 e6  e5 e6 e7 e5 e4 e4 e4 e2  |................|
00000140  e5 e1 e0 e2 e4 e3 e4 e1  e3 e4 e3 de e2 e0 df e2  |................|
00000150  e4 e4 e3 e2 e2 e0 df df  e3 e1 df e2 e2 dd df e3  |................|
00000160  e3 e7 e6 e4 e1 d9 d6 d7  d9 db d5 d8 db d7 d7 db  |................|
00000170  d6 da d9 db de dc da d6  dc db d9 da da da da d9  |................|
00000180  dd d9 d8 da d6 d9 d8 d7  da d9 d7 d9 d7 d8 d7 d8  |................|
00000190  d8 d6 d6 d7 d8 d9 d8 d5  d7 d7 d4 d6 d4 d4 d7 d7  |................|
000001a0  cf cd c9 be a5 c9 cb 9f  ee ec ee ef eb ec ee ee  |................|
000001b0  ed ef f0 ec ed e9 eb ea  ea ea ee ef ef ef 00 fe  |................|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 38 72 01 00 fe  |...........8r...|
000001d0  ff ff 05 fe ff ff 02 38  72 01 00 d8 11 00 00 00  |.......8r.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by winjeel on 2010-11-29
Logitec HD is an external USB drive.

---

### Post by amjjawad on 2010-11-29
```
C:\wubildr.mbr="Ubuntu"
```This is not a regular installation, this is a wubi installation.

From the link I posted previously:

> **How do I manually uninstall Wubi?**

 Remove C:\ubuntu and C:\wubildr*  
In Windows XP you need to edit C:\boot.ini and delete the Ubuntu/Wubi line.

My point is: C:\wubildr.mbr="Ubuntu" means it's wubi installation.


I have no experience in wubi but what I know base on what I've read here in this forum that you need to use Windows XP's CD to re-install Windows Bootloader in the MBR.

Search the forum here or use google. You should get many helpful information. Sorry, I don't use wubi so I can't be very helpful.

---

### Post by winjeel on 2010-11-29
> **amjjawad said:**
> ```
C:\wubildr.mbr="Ubuntu"
```This is not a regular installation, this is a wubi installation.

From the link I posted previously:



I have no experience in wubi but what I know base on what I've read here in this forum that you need to use Windows XP's CD to re-install Windows Bootloader in the MBR.

Search the forum here or use google. You should get many helpful information. Sorry, I don't use wubi so I can't be very helpful.

Arrr... I have used wubi in the past with 10Gb file size, but that turned out to be too small, so then I permanently installed Linux. So, I have Grub, so when I select Windows it then goes to Wubi and I select Windows again.

---

### Post by winjeel on 2010-11-29
I **really** needed to get work done tonight. Is it possible to uninstall the Grub updates? Would uninstalling the updates have the Grub go back to its original configuration?

---

### Post by amjjawad on 2010-11-29
> **winjeel said:**
> I **really** needed to get work done tonight. Is it possible to uninstall the Grub updates? Would uninstalling the updates have the Grub go back to its original configuration?

If I were you and can't really wait, I would install Windows Bootloader in the MBR for tonight then worry about GRUB later.

_**Edit**_:
I don't know why "sudo update-grub" didn't work. It should work and fix the problem.

---

### Post by drs305 on 2010-11-29
If you are in a rush to restore Windows and are currently on the LiveCD this can probably restore Windows as quickly as anything:

Install the lilo bootloader and let it point to your Windows OS. Disregard the messages lilo produces since you aren't fully 'installing' it:

```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

We can sort out the rest after you get Windows working.

---

### Post by amjjawad on 2010-11-29
> **drs305 said:**
> If you are in a rush to restore Windows and are currently on the LiveCD this can probably restore Windows as quickly as anything:

Install the lilo bootloader and let it point to your Windows OS. Disregard the messages lilo produces since you aren't fully 'installing' it:

```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```We can sort out the rest after you get Windows working.

I was waiting for you to show up :D

Allow me to ask two questions if you don't mind:

1- Why "sudo update-grub" didn't work? I'm really surprised?!

2- Can he use Windows CD to restore MBR and give Windows loader the control instead of GRUB just for tonight?

---

### Post by drs305 on 2010-11-29
> **amjjawad said:**
> I was waiting for you to show up :D

Allow me to ask two questions if you don't mind:

1- Why "sudo update-grub" didn't work? I'm really surprised?!

2- Can he use Windows CD to restore MBR and give Windows loader the control instead of GRUB just for tonight?

1. I don't know for sure. Windows is already listed in grub.cfg . In cases like this, I often suspect another grub.cfg file is being used instead, but this is usually when there are multiple installs of Ubuntu on the drive. I will have to inspect the syntax of the Windows entry again to see if there is a syntax problem for why it's not displaying.

2. Yes, the OP can use the Windows CD to restore the MBR and would be the preferred method. The 'lilo' solution is just a very quick and easy way to return control back over to Windows if the user is already in Linux or if the user doesn't have a repair CD available. 

'lilo' will not fix problems if the Windows bootloader files are damaged or missing. All we use lilo for is to write to the MBR and have it transfer control to whatever is marked with the 'boot' flag.

---

### Post by amjjawad on 2010-11-29
> **drs305 said:**
> 1. I don't know for sure. Windows is already listed in grub.cfg . In cases like this, I often suspect another grub.cfg file is being used instead, but this is usually when there are multiple installs of Ubuntu on the drive. I will have to inspect the syntax of the Windows entry again to see if there is a syntax problem for why it's not displaying.

I tried to figure out what's wrong but couldn't. Then I remembered when I used "sudo update-grub" after I Installed 7 Linux Distributions on my PC and it founded all the other systems. In this case, I don't know why it failed but perhaps you're right. I see it's a bit messed up.


> 2. Yes, the OP can use the Windows CD to restore the MBR and would be the preferred method. 
That would be the easiest and the fastest method :)

> 
The 'lilo' solution is just a very quick and easy way to return control  back over to Windows if the user is already in Linux or if the user  doesn't have a repair CD available.

**'lilo' will not fix problems if the Windows bootloader files are damaged or missing. **All we use lilo for is to write to the MBR and have it transfer control to whatever is marked with the 'boot' flag.

This is very useful information. Thanks as always, drs305 :) I'm learning so much from you ;)

---

### Post by winjeel on 2010-11-29
Thanks for the help, so far. So what is the most recommended course of action? I don't want a messy (or messier) set up on my computer. As you know I have Grub, and then Wubi to get through for when I go to Windows; that in itself is a legacy from when I gave Ubuntu a trial before committing to it. For what it's worth, I'm still running 10.04, and haven't had the time to update to 10.10 yet. Does that open any windows of opportunity? (No pun intended).

---

### Post by drs305 on 2010-11-29
> **winjeel said:**
> Thanks for the help, so far. So what is the most recommended course of action? I don't want a messy (or messier) set up on my computer. As you know I have Grub, and then Wubi to get through for when I go to Windows; that in itself is a legacy from when I gave Ubuntu a trial before committing to it. For what it's worth, I'm still running 10.04, and haven't had the time to update to 10.10 yet. Does that open any windows of opportunity? (No pun intended).

Here is what I would do.

1, Repair your Windows boot first. We could start by trying to get Grub2 to see Windows, but even when it did there is no guarantee it will boot it if there is something wrong with the Windows files. The Windows menuentry is already in the grub.cfg file, so there is definitely some problem with either the entry or with the Windows boot files. 

Additionally, by fixing the Windows bootloader, you will also be able to boot into Windows and remove any traces of the old wubi install. 

Either you will be able to remove Wubi via the Add/Remove program, or at least you can manually delete the C:\ubuntu folder and then edit the Windows boot.ini file and remove the reference to Windows.

You can try the "lilo" method I described earlier or go with the Windows repair disk.

2. Once you have Windows booting and Wubi removed, reinstall Grub2. With a properly working Windows installation, Grub 2 should work. Since you have had some problems, I would recommend completely purging Grub and then reinstalling it so that you have a clean, uncluttered Grub installation. 

You can do this by booting the LiveCD, chrooting into sda5, and purging/installing grub-common/grub-pc. Here is the link to do that:
[HOWTO: Purge and Reinstall Grub 2 from the Live CD]("http://ubuntuforums.org/showthread.php?t=1581099")

---

### Post by winjeel on 2010-11-29
Thanks. I'm pretty busy all day today, so I need to prioritise and get to it when I can.

---

### Post by winjeel on 2010-11-30
A quick update.

I've tried to use the Windows CD, but that didn't work. I inserted the disk before restart and it took me to the problematic grub. During bios start up I pushed F12 to go to the Boot Menu, I chose to start from the CD/DVD drive and it took me straight back to the problematic grub menu.

I went into Ubuntu, used lilo and on restart it took me to the Wubi menu so I could go to Windows and get done what I needed to get done. I was surprised at how quick and easy that method worked. Thanks for that.

Next, it's too late in the evening, and I have an early start, so I'll get to fixing grub and removing wubi on another night.

Thanks so much for the help so far.

---

### Post by amjjawad on 2010-11-30
Glad you got Windows booting, at least to finish your work and keep your promises to your people :D

Once you're ready, you could do it anytime.

Good luck and wish you all the best!

---

### Post by winjeel on 2010-12-01
It didn't work. I booted from a USB Start up disk, as a "Live CD", and then did this in Terminal (replacing x with 'a', and y with '5'):

```
sudo mount /dev/sd**XY** /mnt
sudo grub-install --root-directory=/mnt /dev/sd**X**
```

I restarted and there was no Windows XP in the menu, and had 6 regular and 6 recovery mode Ubuntu's in the list. I then did:

```
sudo update-grub
```
And still no Windows in the menu list. I was, and is using Grub v1.98. What's next? :neutral:

---

### Post by winjeel on 2010-12-01
I had a wonder into the Boot/Grub/grub.cfg and in the list of all the Ubuntu's and Recoveries, I found this:

```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Dell Utility Partition (on /dev/sda1)" {
    insmod fat
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 07d6-0705
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 5a04f93304f912ad
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###
```

It seems present and accounted for, but it doesn't show in the start up menu. Are the details here as should be expected? Do you need to see the whole file?

---

### Post by winjeel on 2010-12-01
I found the problem...

I have this rediculously long list of 

Ubuntu Linux...(I don't remember the full title)
Ubuntu Linux Recovery (I don't remember the full title)
Ubuntu Linux...(I don't remember the full title)
Ubuntu Linux Recovery (I don't remember the full title)
Ubuntu Linux...(I don't remember the full title)
Ubuntu Linux Recovery (I don't remember the full title)
Ubuntu Linux...(I don't remember the full title)
Ubuntu Linux Recovery (I don't remember the full title)
Ubuntu Linux...(I don't remember the full title)
Ubuntu Linux Recovery (I don't remember the full title)
Ubuntu Linux...(I don't remember the full title)
Ubuntu Linux Recovery (I don't remember the full title)
Memory test
Memory test serial (something)
Dell Utilities Partition

And then next to the bordered box that the above is contained in is a tiny little arrow. If I move the selection highlight bar down, down, and down past the Dell Utilities Partition, then I get to Windows XP. GRRRRRRrrrrrrrr That was annoying. However, I'm pretty sure that when I came home, started my computer up, I had something in my hand and was concentrating on that, I pushed the down arrow as far down until it stopped moving (noticing out of the corner of my eye), and as a habit I normally push a couple more times to be sure (as Windows is always last in the list), then I pressed enter. I waited, then a weird screen came up, the Dell Utilities display, now XP. So, I'm pretty sure I didn't have it before, so perhaps the first sudo update did work, but I didn't notice. Now, it seems I have a whole bunch of extra Ubuntu's to choose from, all but two are probably not needed. Can these be removed?

btw, thanks for your patience :D

---

### Post by amjjawad on 2010-12-01
> **winjeel said:**
> I found the problem...

I have this rediculously long list of 

Ubuntu Linux...(I don't remember the full title)
Ubuntu Linux Recovery (I don't remember the full title)
Ubuntu Linux...(I don't remember the full title)
Ubuntu Linux Recovery (I don't remember the full title)
Ubuntu Linux...(I don't remember the full title)
Ubuntu Linux Recovery (I don't remember the full title)
Ubuntu Linux...(I don't remember the full title)
Ubuntu Linux Recovery (I don't remember the full title)
Ubuntu Linux...(I don't remember the full title)
Ubuntu Linux Recovery (I don't remember the full title)
Ubuntu Linux...(I don't remember the full title)
Ubuntu Linux Recovery (I don't remember the full title)
Memory test
Memory test serial (something)
Dell Utilities Partition

And then next to the bordered box that the above is contained in is a tiny little arrow. If I move the selection highlight bar down, down, and down past the Dell Utilities Partition, then I get to Windows XP. GRRRRRRrrrrrrrr That was annoying. However, I'm pretty sure that when I came home, started my computer up, I had something in my hand and was concentrating on that, I pushed the down arrow as far down until it stopped moving (noticing out of the corner of my eye), and as a habit I normally push a couple more times to be sure (as Windows is always last in the list), then I pressed enter. I waited, then a weird screen came up, the Dell Utilities display, now XP. So, I'm pretty sure I didn't have it before, so perhaps the first sudo update did work, but I didn't notice. Now, it seems I have a whole bunch of extra Ubuntu's to choose from, all but two are probably not needed. Can these be removed?

btw, thanks for your patience :D

Let me get this straight. Are you trying to tell us that Windows XP entry is there already and you DID NOT SEE IT?

Hahaha, well, it happens to me sometimes but I do my best to check everything before starting a thread. Never mind, it could happen to anyone.

If you want to remove the unwanted entries, check drs305's signature. There are many useful links you could use. 

It's recommended to leave two entries for Ubuntu:
> 
Ubuntu Linux...(I don't remember the full title)
Ubuntu Linux Recovery (I don't remember the full title)
Ubuntu Linux...(I don't remember the full title)
Ubuntu Linux Recovery (I don't remember the full title) 

In that case, you'll be able to see XP :D

---

### Post by drs305 on 2010-12-01
> **winjeel said:**
> Now, it seems I have a whole bunch of extra Ubuntu's to choose from, all but two are probably not needed. Can these be removed?

This is probably the guide that will help you remvoe the extra kernels:
[URL="http://ubuntuforums.org/showthread.php?t=1587462"]HOWTO: Remove Older Kernels via GUI
[/URL]

---

### Post by drs305 on 2010-12-01
> **drs305 said:**
> This is probably the guide that will help you remvoe the extra kernels:
[URL="http://ubuntuforums.org/showthread.php?t=1587462"]HOWTO: Remove Older Kernels via GUI
[/URL]


Please don't forget to mark the thread SOLVED via the 'Thread Tools' link near the top right of the first post when you don't have any more questions.

---

### Post by winjeel on 2010-12-01
Thanks so much for your help. I am pretty sure that there was a problem at first, then doing this the first time

```
sudo update-grub
```

probably did solve it, but I couldn't see it. Anyway, thanks for your time. :D

---

