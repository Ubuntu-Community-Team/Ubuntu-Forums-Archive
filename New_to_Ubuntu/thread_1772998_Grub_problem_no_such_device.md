---
title: "Grub problem: no such device"
date: 2011-06-01
forum: New to Ubuntu
---

### Post by fractalman on 2011-06-01
Ok i have 11:04 on my pc and i have 10:10 on a usb external harddrive.  i recently had to reinstall 11:04 and as a result i can no longer load 10:10, the usb was plugged in during installation  and 10:10 showed up on the partition manager.  10:10 shows up in the grub menu on booting ,when i try to boot 10:10 i get an error message saying that no such device is present and to install the headers

How do i reconfigure the boot/grub to load 10:10?

---

### Post by coffeecat on 2011-06-01
Can you boot into the freshly re-installed 11.04 with the 10.10 usb drive attached? If so, do so (with the usb drive attached) and open a terminal and run:

```
sudo update-grub
```Then reboot and see if you can boot into 10.10. If not, boot into 11.04 again (and again with the usb drive attached), and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Follow the instructions there to download and run the boot info script and post the contents of the RESULTS.txt file. Please remember to enclose these between [noparse]```
 and 
```[/noparse] tags. You can use the [IMG]http://ubuntuforums.org/images/editor/code.gif[/IMG] icon in the message toolbar for this.

---

### Post by fractalman on 2011-06-01
ok i tried "sudo update-grub" but it still wouldn't boot 10:10, i'm still getting the message - no such device- please install kernel

so i tried the boot script, the results are as follows, i got this warning at the start

"gawk" could not be found, using "busybox awk" instead.
This may lead to unreliable results.


and the textfile reads like this, it's rather long

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos7)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  BackTrack 5 - Code Name 
                       Revolution 32 bit
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda7: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb7: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048    97,656,831    97,654,784  83 Linux
/dev/sda2          97,658,878   156,299,263    58,640,386   5 Extended
/dev/sda5         114,259,968   148,436,991    34,177,024  83 Linux
/dev/sda6         148,439,040   156,299,263     7,860,224  82 Linux swap / Solaris
/dev/sda7          97,658,880   114,257,919    16,599,040  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048    97,658,297    97,656,250   b W95 FAT32
/dev/sdb2         335,112,190   976,771,071   641,658,882   5 Extended
/dev/sdb5         340,348,928   961,415,167   621,066,240  83 Linux
/dev/sdb6         961,417,216   976,771,071    15,353,856  82 Linux swap / Solaris
/dev/sdb7         335,112,192   340,336,639     5,224,448  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/cryptswap1 5f0907ef-5a66-48aa-89d2-67dc0f18d4ec   swap       
/dev/mapper/cryptswap2 7ef34967-5953-448b-94be-d686203077e4   swap       
/dev/mapper/cryptswap3 de50d45e-7d9a-466c-b511-e0a4060d4d7f   swap       
/dev/mapper/cryptswap4 49ab9e7d-9469-4231-81a1-2db52c37f108   swap       
/dev/sda1        6a1746dd-33b7-464b-b2eb-a5beb2b4a0b7   ext4       
/dev/sda5        6a250a37-edee-4bbe-a163-b30a517fcfb5   ext4       
/dev/sdb1        DB57-6EAB                              vfat       
/dev/sdb5        dfc2e79b-c312-4672-9ea5-e5261c5d46d0   ext4       

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
cryptswap1
cryptswap2
cryptswap3
cryptswap4

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/DB57-6EAB         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sdb5        /media/dfc2e79b-c312-4672-9ea5-e5261c5d46d0 ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sda1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 6a1746dd-33b7-464b-b2eb-a5beb2b4a0b7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 6a1746dd-33b7-464b-b2eb-a5beb2b4a0b7
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-9-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 6a1746dd-33b7-464b-b2eb-a5beb2b4a0b7
    linux    /boot/vmlinuz-2.6.38-9-generic root=UUID=6a1746dd-33b7-464b-b2eb-a5beb2b4a0b7 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-9-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-9-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 6a1746dd-33b7-464b-b2eb-a5beb2b4a0b7
    echo    'Loading Linux 2.6.38-9-generic ...'
    linux    /boot/vmlinuz-2.6.38-9-generic root=UUID=6a1746dd-33b7-464b-b2eb-a5beb2b4a0b7 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-9-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 6a1746dd-33b7-464b-b2eb-a5beb2b4a0b7
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=6a1746dd-33b7-464b-b2eb-a5beb2b4a0b7 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 6a1746dd-33b7-464b-b2eb-a5beb2b4a0b7
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=6a1746dd-33b7-464b-b2eb-a5beb2b4a0b7 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 6a1746dd-33b7-464b-b2eb-a5beb2b4a0b7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 6a1746dd-33b7-464b-b2eb-a5beb2b4a0b7
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.38 (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 6a250a37-edee-4bbe-a163-b30a517fcfb5
    linux /boot/vmlinuz-2.6.38 root=UUID=6a250a37-edee-4bbe-a163-b30a517fcfb5 ro text splash nomodeset vga=791
    initrd /boot/initrd.img-2.6.38
}
menuentry "Ubuntu, with Linux 2.6.38 (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 6a250a37-edee-4bbe-a163-b30a517fcfb5
    linux /boot/vmlinuz-2.6.38 root=UUID=6a250a37-edee-4bbe-a163-b30a517fcfb5 ro single
    initrd /boot/initrd.img-2.6.38
}
menuentry "Ubuntu, with Linux 2.6.32-31-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 6a250a37-edee-4bbe-a163-b30a517fcfb5
    linux /boot/vmlinuz-2.6.32-31-generic root=UUID=6a250a37-edee-4bbe-a163-b30a517fcfb5 ro text splash nomodeset vga=791
    initrd /boot/initrd.img-2.6.32-31-generic
}
menuentry "Ubuntu, with Linux 2.6.32-31-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 6a250a37-edee-4bbe-a163-b30a517fcfb5
    linux /boot/vmlinuz-2.6.32-31-generic root=UUID=6a250a37-edee-4bbe-a163-b30a517fcfb5 ro single
    initrd /boot/initrd.img-2.6.32-31-generic
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (on /dev/sdf5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdf,msdos5)'
    search --no-floppy --fs-uuid --set=root dfc2e79b-c312-4672-9ea5-e5261c5d46d0
    linux /boot/vmlinuz-2.6.35-28-generic root=UUID=dfc2e79b-c312-4672-9ea5-e5261c5d46d0 ro quiet splash
    initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (recovery mode) (on /dev/sdf5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdf,msdos5)'
    search --no-floppy --fs-uuid --set=root dfc2e79b-c312-4672-9ea5-e5261c5d46d0
    linux /boot/vmlinuz-2.6.35-28-generic root=UUID=dfc2e79b-c312-4672-9ea5-e5261c5d46d0 ro single
    initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (on /dev/sdf5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdf,msdos5)'
    search --no-floppy --fs-uuid --set=root dfc2e79b-c312-4672-9ea5-e5261c5d46d0
    linux /boot/vmlinuz-2.6.35-25-generic root=UUID=dfc2e79b-c312-4672-9ea5-e5261c5d46d0 ro quiet splash
    initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (recovery mode) (on /dev/sdf5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdf,msdos5)'
    search --no-floppy --fs-uuid --set=root dfc2e79b-c312-4672-9ea5-e5261c5d46d0
    linux /boot/vmlinuz-2.6.35-25-generic root=UUID=dfc2e79b-c312-4672-9ea5-e5261c5d46d0 ro single
    initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sdf5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdf,msdos5)'
    search --no-floppy --fs-uuid --set=root dfc2e79b-c312-4672-9ea5-e5261c5d46d0
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=dfc2e79b-c312-4672-9ea5-e5261c5d46d0 ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sdf5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdf,msdos5)'
    search --no-floppy --fs-uuid --set=root dfc2e79b-c312-4672-9ea5-e5261c5d46d0
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=dfc2e79b-c312-4672-9ea5-e5261c5d46d0 ro single
    initrd /boot/initrd.img-2.6.35-22-generic
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
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=6a1746dd-33b7-464b-b2eb-a5beb2b4a0b7 /               ext4    errors=remount-ro 0       1
#/dev/sda6       none            swap    sw              0       0
# swap was on /dev/sda7 during installation
#UUID=0812399f-11fe-4be6-afbf-d200fd1e7387 none            swap    sw              0       0
# swap was on /dev/sdb6 during installation
#UUID=1388cbee-8ae0-4501-8ecb-c13d1d964ef8 none            swap    sw              0       0
# swap was on /dev/sdb7 during installation
#UUID=474117c7-1aaf-461b-9b28-695b1e293bd4 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
/dev/mapper/cryptswap2 none swap sw 0 0
/dev/mapper/cryptswap3 none swap sw 0 0
/dev/mapper/cryptswap4 none swap sw 0 0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  42.247222900 = 45.362610176   boot/grub/core.img                             1
  20.216270447 = 21.707055104   boot/grub/grub.cfg                             1
   0.571289062 = 0.613416960    boot/initrd.img-2.6.38-8-generic               3
  17.907226562 = 19.227738112   boot/initrd.img-2.6.38-9-generic               2
  42.245494843 = 45.360754688   boot/vmlinuz-2.6.38-8-generic                  1
  17.407531738 = 18.691194880   boot/vmlinuz-2.6.38-9-generic                  2
  17.907226562 = 19.227738112   initrd.img                                     2
   0.571289062 = 0.613416960    initrd.img.old                                 3
  17.407531738 = 18.691194880   vmlinuz                                        2
  42.245494843 = 45.360754688   vmlinuz.old                                    1

=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
search --no-floppy --fs-uuid --set 6a250a37-edee-4bbe-a163-b30a517fcfb5
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1024x768
  set gfxpayload=keep
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
search --no-floppy --fs-uuid --set 6a250a37-edee-4bbe-a163-b30a517fcfb5
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
menuentry 'Ubuntu, with Linux 2.6.38' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 6a250a37-edee-4bbe-a163-b30a517fcfb5
    linux    /boot/vmlinuz-2.6.38 root=UUID=6a250a37-edee-4bbe-a163-b30a517fcfb5 ro   text splash nomodeset vga=791
    initrd    /boot/initrd.img-2.6.38
}
menuentry 'Ubuntu, with Linux 2.6.38 (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 6a250a37-edee-4bbe-a163-b30a517fcfb5
    echo    'Loading Linux 2.6.38 ...'
    linux    /boot/vmlinuz-2.6.38 root=UUID=6a250a37-edee-4bbe-a163-b30a517fcfb5 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 6a250a37-edee-4bbe-a163-b30a517fcfb5
    linux    /boot/vmlinuz-2.6.32-31-generic root=UUID=6a250a37-edee-4bbe-a163-b30a517fcfb5 ro   text splash nomodeset vga=791
    initrd    /boot/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 6a250a37-edee-4bbe-a163-b30a517fcfb5
    echo    'Loading Linux 2.6.32-31-generic ...'
    linux    /boot/vmlinuz-2.6.32-31-generic root=UUID=6a250a37-edee-4bbe-a163-b30a517fcfb5 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-31-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 6a250a37-edee-4bbe-a163-b30a517fcfb5
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 6a250a37-edee-4bbe-a163-b30a517fcfb5
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set df6f18d3-eb5a-4b6a-97d6-7da235c8ff46
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=df6f18d3-eb5a-4b6a-97d6-7da235c8ff46 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set df6f18d3-eb5a-4b6a-97d6-7da235c8ff46
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=df6f18d3-eb5a-4b6a-97d6-7da235c8ff46 ro single
    initrd /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=6a250a37-edee-4bbe-a163-b30a517fcfb5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=8d0f9eff-e8c3-45fb-add5-3da6ff2092fa none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  59.121330261 = 63.481044992   boot/grub/core.img                             1
  55.265148163 = 59.340500992   boot/grub/grub.cfg                             2
  54.645759583 = 58.675437568   boot/initrdf.img-2.6.38                        1
  56.543773651 = 60.713414656   boot/initrd.img-2.6.32-31-generic              2
  57.848499298 = 62.114353152   boot/initrd.img-2.6.38                         1
  54.675285339 = 58.707140608   boot/initrds.img-2.6.38                        1
  59.127822876 = 63.488016384   boot/vmlinuz-2.6.32-31-generic                 1
  58.614238739 = 62.936559616   boot/vmlinuz-2.6.38                            1
  56.543773651 = 60.713414656   initrd.img                                     2
  57.848499298 = 62.114353152   initrd.img.old                                 1
  59.127822876 = 63.488016384   vmlinuz                                        1
  58.614238739 = 62.936559616   vmlinuz.old                                    1

=========================== sdb5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
search --no-floppy --fs-uuid --set dfc2e79b-c312-4672-9ea5-e5261c5d46d0
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set dfc2e79b-c312-4672-9ea5-e5261c5d46d0
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set dfc2e79b-c312-4672-9ea5-e5261c5d46d0
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=dfc2e79b-c312-4672-9ea5-e5261c5d46d0 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set dfc2e79b-c312-4672-9ea5-e5261c5d46d0
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=dfc2e79b-c312-4672-9ea5-e5261c5d46d0 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set dfc2e79b-c312-4672-9ea5-e5261c5d46d0
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=dfc2e79b-c312-4672-9ea5-e5261c5d46d0 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set dfc2e79b-c312-4672-9ea5-e5261c5d46d0
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=dfc2e79b-c312-4672-9ea5-e5261c5d46d0 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set dfc2e79b-c312-4672-9ea5-e5261c5d46d0
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=dfc2e79b-c312-4672-9ea5-e5261c5d46d0 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set dfc2e79b-c312-4672-9ea5-e5261c5d46d0
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=dfc2e79b-c312-4672-9ea5-e5261c5d46d0 ro single 
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
    search --no-floppy --fs-uuid --set dfc2e79b-c312-4672-9ea5-e5261c5d46d0
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set dfc2e79b-c312-4672-9ea5-e5261c5d46d0
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 60ec9cbcec9c8e42
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
--------------------------------------------------------------------------------

=============================== sdb5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=dfc2e79b-c312-4672-9ea5-e5261c5d46d0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=1388cbee-8ae0-4501-8ecb-c13d1d964ef8 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 226.424350739 = 243.121295360  boot/grub/core.img                             1
 348.701961517 = 374.415880192  boot/grub/grub.cfg                             1
 163.064208984 = 175.088861184  boot/initrd.img-2.6.35-22-generic              2
 163.337890625 = 175.382724608  boot/initrd.img-2.6.35-25-generic              2
 170.879173279 = 183.480115200  boot/initrd.img-2.6.35-28-generic              2
 226.428348541 = 243.125587968  boot/vmlinuz-2.6.35-22-generic                 1
 226.422893524 = 243.119730688  boot/vmlinuz-2.6.35-25-generic                 1
 226.441986084 = 243.140231168  boot/vmlinuz-2.6.35-28-generic                 1
 170.879173279 = 183.480115200  initrd.img                                     2
 163.337890625 = 175.382724608  initrd.img.old                                 2
 226.441986084 = 243.140231168  vmlinuz                                        1
 226.422893524 = 243.119730688  vmlinuz.old                                    1

========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error

```


I have actually re-installed ubuntu several times trying to figure out which version i want on each drive, i hope wont cause any probs

Thanks

---

### Post by coffeecat on 2011-06-01
I'll say first that the /dev/mapper/cryptswap references are beyond me. Are these encrypted swap partitions? I have no experience of them, but I believe I may have spotted the problem.

First the UUIDs of the detectable partitions:


```
Device           UUID                                   TYPE       LABEL

/dev/mapper/cryptswap1 5f0907ef-5a66-48aa-89d2-67dc0f18d4ec   swap       
/dev/mapper/cryptswap2 7ef34967-5953-448b-94be-d686203077e4   swap       
/dev/mapper/cryptswap3 de50d45e-7d9a-466c-b511-e0a4060d4d7f   swap       
/dev/mapper/cryptswap4 49ab9e7d-9469-4231-81a1-2db52c37f108   swap       
/dev/sda1        6a1746dd-33b7-464b-b2eb-a5beb2b4a0b7   ext4       
/dev/sda5        6a250a37-edee-4bbe-a163-b30a517fcfb5   ext4       
/dev/sdb1        DB57-6EAB                              vfat       
/dev/sdb5        dfc2e79b-c312-4672-9ea5-e5261c5d46d0   ext4  
```Now the /etc/fstab of your 11.04 installation:

```
=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=6a1746dd-33b7-464b-b2eb-a5beb2b4a0b7 /               ext4    errors=remount-ro 0       1
#/dev/sda6       none            swap    sw              0       0
# swap was on /dev/sda7 during installation
#UUID=0812399f-11fe-4be6-afbf-d200fd1e7387 none            swap    sw              0       0
# swap was on /dev/sdb6 during installation
#UUID=1388cbee-8ae0-4501-8ecb-c13d1d964ef8 none            swap    sw              0       0
# swap was on /dev/sdb7 during installation
#UUID=474117c7-1aaf-461b-9b28-695b1e293bd4 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
/dev/mapper/cryptswap2 none swap sw 0 0
/dev/mapper/cryptswap3 none swap sw 0 0
/dev/mapper/cryptswap4 none swap sw 0 0
```Note how there was a swap partition at sdb6 with a UUID of 1388cbee-8ae0-4501-8ecb-c13d1d964ef8. There is no longer a partition with that UUID and you have commented out that fstab line.

Now your 10.10 /etc/fstab:

```
--------------------------------------------------------------------------------     

=============================== sdb5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=dfc2e79b-c312-4672-9ea5-e5261c5d46d0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=1388cbee-8ae0-4501-8ecb-c13d1d964ef8 none            swap    sw              0       0
--------------------------------------------------------------------------------

```The swap partition in that fstab is the same UUID=1388cbee-8ae0-4501-8ecb-c13d1d964ef8, except that it doesn't exist. Normally, if you have a fstab entry for a non-existent swap you'll simply get a brief error message on bootup which you can ignore, or the system will simply boot up without complaint. I've not seen an "install the headers" message. I wonder if this is to do with encrypted partitions, but I have no experience of them and cannot be sure. It's interesting that your boot script output comes up with "unknown filesystem type" for sda6, sda7, sdb7 and sdb8. Again, all related I suppose.

The only other inconsistency that I can see in the boot script is that the drive you installed 10.10 to, the 500GB one, appears as sdb in various parts of the boot script and in 10.10's fstab, but as sdf in 11.04 grub.cfg. This doesn't really matter since grub.cfg has the correct UUID but it's curious that sdf became sdb between you running update-grub and the boot script.

I guess you need to edit 10.10 /etc/fstab to sort out the swap partition line. You need to do that anyway, but whether this is the source of your problem, I really don't know.

---

### Post by fractalman on 2011-06-01
The home folder on 11:04 and backtrack5 are encrypted but the home folder in 10:10 is not.

Any ideas how i edit the file in 10:10?

Thanks for the replies, hopefully someone will come along who knows what the problem is, fingers crossed

---

### Post by coffeecat on 2011-06-01
Sorry - penny just dropped. /dev/mapper is to do with RAID. Again, RAID is something I've steered clear of, but I know someone who might know what's going on here. I'll pm him, but as it's late in our shared timezone, he may not post for some time.

Editing fstab on 10.10: In essence, mount the partition from 11.04 and use 'gksu gedit /media/mountpoint/etc/fstab', changing 'mountpoint' to whatever it is. But you might want to leave that for the time being, until you get some other opinions.

---

### Post by Quackers on 2011-06-01
Am I correct in thinking that only some of your partitions are in a raid array? 
Did you create identical partitions on 2 hard drives and then make them part of a Linux software raid array? 
Not something I've used to be honest but there are software raid guides on the Ubuntu site iirc.

---

### Post by grewolf on 2011-06-01
I have a similar problem.  I have 2 hard drives one with windows and one with 11.04 Natty on it.  update-grub works for me every time but I have to do it almost every 2 or 3 days.  I have been reading and was wondering do I have to edit line 147 of my grub/grub-mkconfig file like the bug posts are recommending or is there a better way.

---

### Post by fractalman on 2011-06-02
If anything is in a RAID array it was not intentional. 10:10 on the usb was my main install till 11:04 was released, i then wiped xp off my pc drive totally and installed 11:04 as a my main install on the pc drive, which then had to be re-installed and left me unable to boot 10:10,

I can still get all my data from the drive, it just wont boot

thanks for the replies, much appreciated

---

