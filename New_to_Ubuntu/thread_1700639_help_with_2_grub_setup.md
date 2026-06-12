---
title: "help with 2 grub setup"
date: 2011-03-05
forum: New to Ubuntu
---

### Post by jamby on 2011-03-05
Hi

  Second post.  The computer is a desktop with 2 sata hard drives.
  I am trying to get the grub2 in my ubuntu install linked by chainloader from my centos 5 install with its grub  loaded in the mrb.  Ubuntu was installed on sdb5 and grub2 was suppose to be loaded there at the root directory.
  I can't figure out nor stumble over the correct configuration for the centos grub at the mrb to chainload grub2 at sbd5. 

Below are the grubs for both OS's.  The second one is what I thought should be the correct stanza for the chainloader.

```

Ubuntu
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
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set 9840824f-7d88-4114-ad52-db2166fe538a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set 9840824f-7d88-4114-ad52-db2166fe538a
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod part_msdos
        insmod ext2
        set root='(hd1,msdos5)'
        search --no-floppy --fs-uuid --set 9840824f-7d88-4114-ad52-db2166fe538a
        linux   /boot/vmlinuz-2.6.35-22-generic root=UUID=9840824f-7d88-4114-ad52-db2166fe538a ro   quiet splash
        initrd  /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod part_msdos
        insmod ext2
        set root='(hd1,msdos5)'
        search --no-floppy --fs-uuid --set 9840824f-7d88-4114-ad52-db2166fe538a
        echo    'Loading Linux 2.6.35-22-generic ...'
        linux   /boot/vmlinuz-2.6.35-22-generic root=UUID=9840824f-7d88-4114-ad52-db2166fe538a ro single 
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
        insmod part_msdos
        insmod ext2
        set root='(hd1,msdos5)'
        search --no-floppy --fs-uuid --set 9840824f-7d88-4114-ad52-db2166fe538a
        linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
        insmod part_msdos
        insmod ext2
        set root='(hd1,msdos5)'
        search --no-floppy --fs-uuid --set 9840824f-7d88-4114-ad52-db2166fe538a
        linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "CentOS release 5 (Final) (on /dev/sdb1)" {
        insmod part_msdos
        insmod ext2
        set root='(hd1,msdos1)'
        search --no-floppy --fs-uuid --set 7b7f15a0-1b1f-45a8-8bc4-5353c9bb4586
        linux /boot/vmlinuz-2.6.18-53.el5xen root=/dev/sdb1
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

``````

#          initrd /initrd-version.img
#boot=/dev/sda
default=0
timeout=5
splashimage=(hd0,0)/grub/splash.xpm.gz
hiddenmenu
title CentOS (2.6.18-194.32.1.el5)
        root (hd0,0)
        kernel /vmlinuz-2.6.18-194.32.1.el5 ro root=/dev/VolGroup00/LogVol00 rhgb quiet crashkernel=128M@16M
        initrd /initrd-2.6.18-194.32.1.el5.img
title CentOS (2.6.18-164.el5)
        root (hd0,0)
        kernel /vmlinuz-2.6.18-164.el5 ro root=/dev/VolGroup00/LogVol00 rhgb quiet crashkernel=128M@16M
        initrd /initrd-2.6.18-164.el5.img
title Ubuntu (10.10)
        root (hd1,4)
        chainloader +1

```Any help appreciated.

---

### Post by oldfred on 2011-03-05
Post full boot script so we can see everything. Grub2 does not like to be in the PBR, but should work. But if you have two drives why not one in each MBR. I chainload different grub2 from different drives.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by jamby on 2011-03-05
Thanks oldfred,

    As always things never run smoothly.  Tried the script in CentOS, no - errors about missing files. So booted Ubuntu install disk.  Couldn't access installation possibly because of thumb drive in system at boot. (thumb drive was where the script was).  Rebooted, minus thumb drive, was able to access installed system, loaded thumb drive.  Copied script to my home and ran.  Wheew. 


Results.txt
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks at sector 191553 
    on boot drive #1 for the stage2 file. A stage2 file is at this location on 
    /dev/sda. Stage2 looks on partition #1 for /grub/grub.conf.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks at sector 15630399 
    on boot drive #1 for the stage2 file. A stage2 file is at this location on 
    /dev/sdb. Stage2 looks on partition #1 for /boot/grub/grub.conf.
 => Windows is installed in the MBR of /dev/sdg

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst /grub/grub.conf

sda2: _________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  CentOS release 5 (Final) Kernel 
                       on an
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

sdb2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdg1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /grub.cfg

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63       208,844       208,782  83 Linux
/dev/sda2             208,845   312,576,704   312,367,860  8e Linux LVM


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   146,287,889   146,287,827  83 Linux
/dev/sdb2         146,287,890   148,392,404     2,104,515  82 Linux swap / Solaris
/dev/sdb3         148,393,982   230,486,015    82,092,034   5 Extended
/dev/sdb5         148,393,984   230,486,015    82,092,032  83 Linux


Drive: sdg ___________________ _____________________________________________________

Disk /dev/sdg: 4051 MB, 4051697152 bytes
4 heads, 32 sectors/track, 61823 cylinders, total 7913471 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdg1    *             32     7,913,470     7,913,439   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        046838cc-7fdf-4e3f-af3e-117bb43ee907   ext3       /boot                         
/dev/sda2        tGT7Iy-3PZF-VPih-YuNN-uFuH-fYxi-q3iJ1H LVM2_member                               
/dev/sda: PTTYPE="dos" 
/dev/sdb1        7b7f15a0-1b1f-45a8-8bc4-5353c9bb4586   ext3       /                             
/dev/sdb2                                               swap                                     
/dev/sdb3: PTTYPE="dos" 
/dev/sdb5        9840824f-7d88-4114-ad52-db2166fe538a   ext3                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdg1        20AF-034D                              vfat       CRUZER                        
/dev/sdg: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb5        /media/9840824f-7d88-4114-ad52-db2166fe538a ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdg1        /media/CRUZER            vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


============================= sda1/grub/grub.conf: =============================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,0)
#          kernel /vmlinuz-version ro root=/dev/VolGroup00/LogVol00
#          initrd /initrd-version.img
#boot=/dev/sda
default=0
timeout=5
splashimage=(hd0,0)/grub/splash.xpm.gz
hiddenmenu
title CentOS (2.6.18-194.32.1.el5)
    root (hd0,0)
    kernel /vmlinuz-2.6.18-194.32.1.el5 ro root=/dev/VolGroup00/LogVol00 rhgb quiet crashkernel=128M@16M
    initrd /initrd-2.6.18-194.32.1.el5.img
title CentOS (2.6.18-164.el5)
    root (hd0,0)
    kernel /vmlinuz-2.6.18-164.el5 ro root=/dev/VolGroup00/LogVol00 rhgb quiet crashkernel=128M@16M
    initrd /initrd-2.6.18-164.el5.img
title Ubuntu (10.10)
    root (hd1,2)
    chainloader +1

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: grub/grub.conf
    .0GB: grub/menu.lst
    .0GB: grub/stage2
    .0GB: initrd-2.6.18-164.el5.img
    .0GB: initrd-2.6.18-164.el5kdump.img
    .0GB: initrd-2.6.18-194.32.1.el5.img
    .0GB: initrd-2.6.18-194.32.1.el5kdump.img
    .0GB: vmlinuz-2.6.18-164.el5
    .0GB: vmlinuz-2.6.18-194.32.1.el5

========================== sdb1/boot/grub/grub.conf: ==========================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd0,0)
#          kernel /boot/vmlinuz-version ro root=/dev/sda1
#          initrd /boot/initrd-version.img
#boot=/dev/sda
default=0
timeout=5
splashimage=(hd0,0)/boot/grub/splash.xpm.gz
hiddenmenu
title CentOS (2.6.18-53.el5xen)
    root (hd0,0)
    kernel /boot/xen.gz-2.6.18-53.el5 crashkernel=128M@16M
    module /boot/vmlinuz-2.6.18-53.el5xen ro root=LABEL=/ rhgb quiet
    module /boot/initrd-2.6.18-53.el5xen.img

=============================== sdb1/etc/fstab: ===============================

LABEL=/                 /                       ext3    defaults        1 1
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
LABEL=SWAP-sda2         swap                    swap    defaults        0 0

=================== sdb1: Location of files loaded by Grub: ===================


   7.9GB: boot/grub/grub.conf
   7.9GB: boot/grub/menu.lst
   8.0GB: boot/grub/stage2
   7.9GB: boot/initrd-2.6.18-53.el5xen.img
   7.9GB: boot/vmlinuz-2.6.18-53.el5xen

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set 9840824f-7d88-4114-ad52-db2166fe538a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set 9840824f-7d88-4114-ad52-db2166fe538a
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 9840824f-7d88-4114-ad52-db2166fe538a
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=9840824f-7d88-4114-ad52-db2166fe538a ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 9840824f-7d88-4114-ad52-db2166fe538a
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=9840824f-7d88-4114-ad52-db2166fe538a ro single 
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
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 9840824f-7d88-4114-ad52-db2166fe538a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 9840824f-7d88-4114-ad52-db2166fe538a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "CentOS release 5 (Final) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 7b7f15a0-1b1f-45a8-8bc4-5353c9bb4586
    linux /boot/vmlinuz-2.6.18-53.el5xen root=/dev/sdb1
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
UUID=9840824f-7d88-4114-ad52-db2166fe538a /               ext3    errors=remount-ro 0       1
/dev/sdb2       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 108.8GB: boot/grub/core.img
 108.8GB: boot/grub/grub.cfg
 108.7GB: boot/initrd.img-2.6.35-22-generic
 108.8GB: boot/vmlinuz-2.6.35-22-generic
 108.7GB: initrd.img
 108.8GB: vmlinuz

================================ sdg1/grub.cfg: ================================

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
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set 9840824f-7d88-4114-ad52-db2166fe538a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set 9840824f-7d88-4114-ad52-db2166fe538a
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 9840824f-7d88-4114-ad52-db2166fe538a
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=9840824f-7d88-4114-ad52-db2166fe538a ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 9840824f-7d88-4114-ad52-db2166fe538a
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=9840824f-7d88-4114-ad52-db2166fe538a ro single 
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
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 9840824f-7d88-4114-ad52-db2166fe538a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 9840824f-7d88-4114-ad52-db2166fe538a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "CentOS release 5 (Final) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 7b7f15a0-1b1f-45a8-8bc4-5353c9bb4586
    linux /boot/vmlinuz-2.6.18-53.el5xen root=/dev/sdb1
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

=================== sdg1: Location of files loaded by Grub: ===================


    ??GB: grub.cfg
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 



```

---

### Post by oldfred on 2011-03-05
Grub2 is not installed to the partition boot sector. Grub2 also says it is unreliable if installed to a PBR. Since you have two drives just install Ubuntu's grub2 to sdb. You then can set BIOS to boot Ubuntu and choose centos or add a chainboot command from centos to boot Ubuntu.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sdb5 and want grub2 in drive sdb's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sdb5
sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sdb
# After rebooting into working system
sudo update-grub

This was my old grub boot stanza to boot sdb. My system always sees the boot drive as hd0. When I boot sdc it is hd0.

title       Ubuntu 9.04 Jaunty 32 bit @ sdb
root        (hd1)
chainloader +1

---

### Post by jamby on 2011-03-05
Thanks oldfred

  I am going to start from scratch with new installs of both then if need be I'll start a new thread.

---

### Post by oldfred on 2011-03-05
Just cleanly install each to its own drive, so each drive could boot and run without the other. With Ubuntu it is best to use manual install so then you get the choice on where to install grub2's boot loader. Most other distributions offer the choice regardless of how they install.

Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

