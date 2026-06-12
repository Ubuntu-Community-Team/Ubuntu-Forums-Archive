---
title: "Trouble booting Ubuntu 10.10"
date: 2011-04-19
forum: New to Ubuntu
---

### Post by SnowWhite on 2011-04-19
I am currently having problems with booting Ubuntu 10.10.  I get an error message that says, "Gave up waiting for root device."

It took a few tries, but I finally managed to boot the live Ubuntu CD that I have.  I also followed the boot info script directions from [SourceForge.]("http://bootinfoscript.sourceforge.net/")

The code I got is this:
```


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         81,920    30,801,919    30,720,000   7 HPFS/NTFS
/dev/sda3          30,801,920   410,617,238   379,815,319   7 HPFS/NTFS
/dev/sda4         410,617,854   488,396,799    77,778,946   5 Extended
/dev/sda5         485,115,904   488,396,799     3,280,896  82 Linux swap / Solaris
/dev/sda6         410,617,856   485,115,903    74,498,048  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 16.0 GB, 16039018496 bytes
255 heads, 63 sectors/track, 1949 cylinders, total 31326208 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               8,192    31,326,207    31,318,016   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        82721BA4721B9BCB                       ntfs       RECOVERY                      
/dev/sda3        46161DA2161D9451                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        5ef355f8-6c94-484a-beb0-21356ce0a81c   swap                                     
/dev/sda6        16586be2-c219-4bda-ab5d-bed5e243b02d   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        148E-5817                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/148E-5817         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sr0         /media/apt               iso9660    (ro)
/dev/sda3        /media/OS                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda6        /media/16586be2-c219-4bda-ab5d-bed5e243b02d ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 16586be2-c219-4bda-ab5d-bed5e243b02d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 16586be2-c219-4bda-ab5d-bed5e243b02d
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
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 16586be2-c219-4bda-ab5d-bed5e243b02d
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=16586be2-c219-4bda-ab5d-bed5e243b02d ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 16586be2-c219-4bda-ab5d-bed5e243b02d
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=16586be2-c219-4bda-ab5d-bed5e243b02d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 16586be2-c219-4bda-ab5d-bed5e243b02d
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=16586be2-c219-4bda-ab5d-bed5e243b02d ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 16586be2-c219-4bda-ab5d-bed5e243b02d
    echo    'Loading Linux 2.6.35-27-generic ...'
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=16586be2-c219-4bda-ab5d-bed5e243b02d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 16586be2-c219-4bda-ab5d-bed5e243b02d
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=16586be2-c219-4bda-ab5d-bed5e243b02d ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 16586be2-c219-4bda-ab5d-bed5e243b02d
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=16586be2-c219-4bda-ab5d-bed5e243b02d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 16586be2-c219-4bda-ab5d-bed5e243b02d
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=16586be2-c219-4bda-ab5d-bed5e243b02d ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 16586be2-c219-4bda-ab5d-bed5e243b02d
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=16586be2-c219-4bda-ab5d-bed5e243b02d ro single 
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
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 16586be2-c219-4bda-ab5d-bed5e243b02d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 16586be2-c219-4bda-ab5d-bed5e243b02d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 82721ba4721b9bcb
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda6       /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 223.2GB: boot/grub/core.img
 217.2GB: boot/grub/grub.cfg
 217.1GB: boot/initrd.img-2.6.35-22-generic
 236.3GB: boot/initrd.img-2.6.35-25-generic
 217.8GB: boot/initrd.img-2.6.35-27-generic
 220.1GB: boot/initrd.img-2.6.35-28-generic
 223.2GB: boot/vmlinuz-2.6.35-22-generic
 223.2GB: boot/vmlinuz-2.6.35-25-generic
 223.2GB: boot/vmlinuz-2.6.35-27-generic
 223.3GB: boot/vmlinuz-2.6.35-28-generic
 220.1GB: initrd.img
 217.8GB: initrd.img.old
 223.3GB: vmlinuz
 223.2GB: vmlinuz.old


```


Any help would be wonderfully appreciated.  :)

---

### Post by fabricator4 on 2011-04-19
Does Grub actually start? I think so, because normally you get this message after grub, when it's trying to find the kernel.  Try booting one of the older kernels, or choose the Ubuntu recovery option and then run update-grub (with sudo) and see if that fixes it.

The procedure for fixing it if you can't boot one of the older kernels or even Ubuntu in recovery mode is a little more complex and I'm hardly an expert.  There's some good information [here]("http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html"). Basically you have to boot off the LiveCD, chroot the filesystem, install grub, then mkconfig.

Chris

---

### Post by jtarin on 2011-04-19
How long have you had Ubuntu installed before this problem arose?

---

### Post by SnowWhite on 2011-04-19
I've had Ubuntu installed since mid-February, but I had a similar issue in mid-March when there was an update, but my battery died before I could restart the computer properly.  Another helped me fix the issue at the time, but I didn't exactly see what he did, and he's not available to help again this time.  There was something wrong with the kernel.

Anyway, since then, I've made sure to restart the computer right after receiving updates to avoid this problem.

None of the earlier versions are booting (neither this nor last time), but I have been using a live CD.  Last time I couldn't access anything on my Ubuntu partition, but this time I can if that helps at all.  I'm taking a look at the link though, and I'll try working with that.

Thanks for the advice!

---

### Post by Quackers on 2011-04-19
On the screen where it says it gave up waiting, leave it for 10 seconds or so and then type in "exit" and press enter  Does it boot now?

---

### Post by SnowWhite on 2011-04-19
I saw the same tip elsewhere, and typing exit did not boot the system unfortunately.

---

