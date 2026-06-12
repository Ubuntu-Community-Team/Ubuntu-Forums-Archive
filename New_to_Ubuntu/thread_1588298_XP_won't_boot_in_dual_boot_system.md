---
title: "XP won't boot in dual boot system"
date: 2010-10-04
forum: New to Ubuntu
---

### Post by dondiego2 on 2010-10-04
I have 2 hds.  One with 10.04 Ubuntu and one with Window XP Professional and I was dual booting.  I have been living without Windows for a while but now I need it for some school work.  XP will not boot from grub, it just goes to a flashing icon.  Ubuntu boots fine.  I think this happened during a grub update or updating to 10.04, I'm not sure.  Is there any way to fix this from the terminal?

---

### Post by oldfred on 2010-10-04
Post results.txt from this so we can see your details.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by dondiego2 on 2010-10-04
Never mind.  I just rebooted Windows from my Windows disk and it works now.  Thanks for replying though.  Now I just have to find all my files in Windows.  They show up when I click on the drive in Ubuntu.  I'm going to reboot into Windows and see if I can figure it out.  It reinstalled Windows XP but it doesn't show my old files even though they are still there.

---

### Post by pavanmatham on 2010-12-04
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for (,msdos7)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    39,072,253    39,072,191   7 HPFS/NTFS
/dev/sda2          39,073,790   156,288,887   117,215,098   f W95 Ext d (LBA)
/dev/sda5          78,144,507   117,221,327    39,076,821   7 HPFS/NTFS
/dev/sda6         117,221,391   156,288,887    39,067,497   7 HPFS/NTFS
/dev/sda7          39,073,792    76,421,119    37,347,328  83 Linux
/dev/sda8          76,423,168    78,139,391     1,716,224  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        20C8A5C2C8A59696                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        286C6FA96C6F708C                       ntfs                                     
/dev/sda6        FCE87A2DE879E5F4                       ntfs                                     
/dev/sda7        791546ec-12c0-48f0-884c-f8af107de518   ext4       ubuntu C                      
/dev/sda8        6bf9dcb6-9ffb-4602-a19e-31b160a620b1   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro,commit=600)
/dev/sda1        /media/20C8A5C2C8A59696  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 791546ec-12c0-48f0-884c-f8af107de518
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 791546ec-12c0-48f0-884c-f8af107de518
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
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 791546ec-12c0-48f0-884c-f8af107de518
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=791546ec-12c0-48f0-884c-f8af107de518 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 791546ec-12c0-48f0-884c-f8af107de518
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=791546ec-12c0-48f0-884c-f8af107de518 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 791546ec-12c0-48f0-884c-f8af107de518
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=791546ec-12c0-48f0-884c-f8af107de518 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 791546ec-12c0-48f0-884c-f8af107de518
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=791546ec-12c0-48f0-884c-f8af107de518 ro single 
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
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 791546ec-12c0-48f0-884c-f8af107de518
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 791546ec-12c0-48f0-884c-f8af107de518
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 20c8a5c2c8a59696
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

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=791546ec-12c0-48f0-884c-f8af107de518 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=6bf9dcb6-9ffb-4602-a19e-31b160a620b1 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


  35.1GB: boot/grub/core.img
  30.9GB: boot/grub/grub.cfg
  21.3GB: boot/initrd.img-2.6.35-22-generic
  21.5GB: boot/initrd.img-2.6.35-23-generic
  35.1GB: boot/vmlinuz-2.6.35-22-generic
  35.2GB: boot/vmlinuz-2.6.35-23-generic
  21.5GB: initrd.img
  21.3GB: initrd.img.old
  35.2GB: vmlinuz
  35.1GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000040  00 00 00 00 00 00 00 00  00 00 00 e0 ff ff ff ff  |................|
00000050  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
00000130  ff ff ff ff ff ff ff ff  ff c1 ff ff ff ff ff ff  |................|
00000140  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 01  |................|
000001c0  c1 ff 07 93 ff ff fd 2b  54 02 d5 43 54 02 00 fe  |.......+T..CT...|
000001d0  ff ff 05 fe ff ff d2 6f  a8 04 a8 1f 54 02 00 00  |.......o....T...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```
I too have the same problem. 
Can this solve?
Regards,

pavan

---

### Post by oldfred on 2010-12-04
pavanmatham, It is generally better to start your own thread if the solution in the thread does not work for you. Boot problems almost always are unique as everyone's configuration is different.

You have both a full install and wubi. Does Ubuntu boot ok? XP looks like it has its boot files and the boot stanza in the grub menu looks correct. What does not work exactly.

Also have you tried running chkdsk from a windows CD.
XP CHKDSK
chkdsk drive /p /r
The chkdsk command checks the specified drive and repairs or recovers the drive if the drive requires it. The command also marks any bad sectors and it recovers readable information. Run chkdsk several times, until no more errors are detected.
chkdsk c: /r
You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect.

---

