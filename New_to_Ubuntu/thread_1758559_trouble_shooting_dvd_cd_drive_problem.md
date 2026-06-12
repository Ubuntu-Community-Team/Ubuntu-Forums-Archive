---
title: "trouble shooting dvd cd drive problem"
date: 2011-05-14
forum: New to Ubuntu
---

### Post by abma321 on 2011-05-14
I installed Ubuntu 10.10 on HP dv41114nr. The previous hard disk crashed. Got a new hard disk and installed ubuntu. Currently not able to read cd or dvd discs from the attached cd drive. 
Trying to access cd files from
 >>Places>>Computer>>CD/DVD Drive.
The below error pops up - 
could not display the "computer:///cd%5CDVD%20Drive.drive" location is not a folder 

How can this issue be solved / how to troubleshoot this futher?

Thanks.

-----------------------------------------------

some more info - 

$ dmesg | grep CD
[    5.254840] ata2.00: ATAPI: TSSTcorp CDDVDW TS-L633L, 0400, max UDMA/100
[    5.302925] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L633L  0400 PQ: 0 ANSI: 5
[    5.310906] Uniform CD-ROM driver Revision: 3.20
[    5.311069] sr 1:0:0:0: Attached scsi CD-ROM sr0
[ 2483.116671] ata2.00: ATAPI: TSSTcorp CDDVDW TS-L633L, 0400, max UDMA/100
[ 2483.359686] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L633L  0400 PQ: 0 ANSI: 5
[ 2483.551434] sr 1:0:0:0: Attached scsi CD-ROM sr0
$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=ae1a3882-04fb-491a-908d-a5aeb6323c4a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=8caaf023-aaeb-412f-a8b1-2d66ec77b706 none            swap    sw              0       0

$ mount|grep ^'/dev'
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            461229088   4032872 433767148   1% /
none                   1523592       292   1523300   1% /dev
none                   1529312      1460   1527852   1% /dev/shm
none                   1529312       104   1529208   1% /var/run
none                   1529312         0   1529312   0% /var/lock
none                 461229088   4032872 433767148   1% /var/lib/ureadahead/debugfs
$

---

### Post by Hedgehog1 on 2011-05-14
First:

Is the new hard drive IDE or SATA?

Is the CD/DVD drive IDE or SATA?

Be aware that if the old hard drive was IDE and was on the same cable as the CD/DVD, and the new drive hard drive is SATA, you need to change the CD/DVD drive from the 'slave' setting to the 'master' setting.

If none of this works/seems to be the issue, please do this:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the [noparse]```
 & 
```[/noparse] tags.

***The Hedge***

:KS

---

### Post by abma321 on 2011-05-14
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   937,164,799   937,162,752  83 Linux
/dev/sda2         937,166,846   976,771,071    39,604,226   5 Extended
/dev/sda5         937,166,848   976,771,071    39,604,224  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        ae1a3882-04fb-491a-908d-a5aeb6323c4a   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        8caaf023-aaeb-412f-a8b1-2d66ec77b706   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set ae1a3882-04fb-491a-908d-a5aeb6323c4a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set ae1a3882-04fb-491a-908d-a5aeb6323c4a
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set ae1a3882-04fb-491a-908d-a5aeb6323c4a
    linux    /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=ae1a3882-04fb-491a-908d-a5aeb6323c4a ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set ae1a3882-04fb-491a-908d-a5aeb6323c4a
    echo    'Loading Linux 2.6.35-28-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=ae1a3882-04fb-491a-908d-a5aeb6323c4a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set ae1a3882-04fb-491a-908d-a5aeb6323c4a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set ae1a3882-04fb-491a-908d-a5aeb6323c4a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 9ef6a6f9f6a6d0b7
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 7272a0d672a0a079
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=ae1a3882-04fb-491a-908d-a5aeb6323c4a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=8caaf023-aaeb-412f-a8b1-2d66ec77b706 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 227.7GB: boot/grub/core.img
 373.8GB: boot/grub/grub.cfg
   1.6GB: boot/initrd.img-2.6.35-28-generic-pae
 227.7GB: boot/vmlinuz-2.6.35-28-generic-pae
   1.6GB: initrd.img
 227.7GB: vmlinuz


```

---

### Post by Hedgehog1 on 2011-05-15
Your install looks very clean and organized. It is a welcome change!

The solution may be this simple:

```
sudo mkdir /media/cdrom0
```
This directory likely already exists, so an error message to that effect is harmless.

```
gksudo gedit /etc/fstab
```

And add this line to the end of the fstab file:

```
/dev/sr0   /media/cdrom0     auto user,noauto,exec      0  0
```

Save the file, exit the text editor, and reboot.

With any luck, you should start seeing CDs and DVDs appear on the desktop when inserted.

***The Hedge***

:KS

---

### Post by abma321 on 2011-05-15
Followed all the steps, still the issue is there. How to test if this is a hardware problem and not a driver / software issue? That should hopefully rule out any hardware problems.

---

### Post by abma321 on 2011-05-20
Since the DVD drive shows up this should be a driver issue. What will be the best way to determine the Drive is working without actually reading any CDs or DVDs ?

---

