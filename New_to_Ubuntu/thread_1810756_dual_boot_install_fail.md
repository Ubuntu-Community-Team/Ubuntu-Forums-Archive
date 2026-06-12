---
title: "dual boot install fail"
date: 2011-07-23
forum: New to Ubuntu
---

### Post by now0pen on 2011-07-23
I recently upgraded my system because of a motherboard problem. I already have windows 7 installed, installed ubuntu as dual boot without any error. After restart, windows 7 immediately started without going into grub.

I installed ubuntu using the ISO I downloaded from ubuntu.com on my usb stick.

Looking for answers, my situation is almost similar to this[ thread]("http://ubuntuforums.org/showthread.php?t=1774523"), except the results.txt that I got were differernt.

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos7)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /grldr /bootmgr /Boot/BCD /grldr

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.02 debian-20101016 ...........>...r>....... ......0...~.k...~...f...M.f.f....f..8~....>2}
    Boot sector info:   Syslinux looks at sector 1437504 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. According 
                       to the info in the boot sector, sdb1 starts at sector 
                       0. But according to the info from fdisk, sdb1 starts 
                       at sector 62.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   312,578,047   312,371,200   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2011 MB, 2011168768 bytes
62 heads, 62 sectors/track, 1021 cylinders, total 3928064 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             62     3,924,723     3,924,662   c W95 FAT32 (LBA)


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000202043392 bytes
255 heads, 63 sectors/track, 121600 cylinders, total 1953519616 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          2,048   974,447,360   974,445,313   7 NTFS / exFAT / HPFS
/dev/sdc2         974,448,638 1,953,503,999   979,055,362   5 Extended
/dev/sdc5       1,936,828,593 1,953,503,999    16,675,407  82 Linux swap / Solaris
/dev/sdc6       1,928,968,192 1,936,828,415     7,860,224  82 Linux swap / Solaris
/dev/sdc7         974,448,640 1,921,105,919   946,657,280  83 Linux
/dev/sdc8       1,921,107,968 1,928,955,903     7,847,936  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        BE6C17B86C176B03                       ntfs       System Reserved
/dev/sda2        3C581B5A581B126E                       ntfs       
/dev/sdb1        21E6-8331                              vfat       
/dev/sdc1        AE2A56682A562D99                       ntfs       Elements
/dev/sdc5        12a14847-138c-4961-a0d1-89f34aa040f2   swap       
/dev/sdc6        59d35b05-fab9-43e1-9432-e79da0a3c9ed   swap       
/dev/sdc7        fcf75a1d-8333-4e8a-8468-35384d8f82de   ext4       
/dev/sdc8        6503446e-0413-44d6-8973-fa8bbf296175   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sdc1        /media/Elements          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc7        /media/fcf75a1d-8333-4e8a-8468-35384d8f82de ext4       (rw,nosuid,nodev,uhelper=udisks)


========================== sda1/grldr embedded menu: ===========================

--------------------------------------------------------------------------------
--------------------------------------------------------------------------------

=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=========================== sdc7/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdb,msdos7)'
search --no-floppy --fs-uuid --set=root fcf75a1d-8333-4e8a-8468-35384d8f82de
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos7)'
search --no-floppy --fs-uuid --set=root fcf75a1d-8333-4e8a-8468-35384d8f82de
set locale_dir=($root)/boot/grub/locale
set lang=en_NZ
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos7)'
    search --no-floppy --fs-uuid --set=root fcf75a1d-8333-4e8a-8468-35384d8f82de
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=fcf75a1d-8333-4e8a-8468-35384d8f82de ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos7)'
    search --no-floppy --fs-uuid --set=root fcf75a1d-8333-4e8a-8468-35384d8f82de
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=fcf75a1d-8333-4e8a-8468-35384d8f82de ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos7)'
    search --no-floppy --fs-uuid --set=root fcf75a1d-8333-4e8a-8468-35384d8f82de
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos7)'
    search --no-floppy --fs-uuid --set=root fcf75a1d-8333-4e8a-8468-35384d8f82de
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root BE6C17B86C176B03
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

=============================== sdc7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb7 during installation
UUID=fcf75a1d-8333-4e8a-8468-35384d8f82de /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb8 during installation
UUID=6503446e-0413-44d6-8973-fa8bbf296175 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdc7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 672.787857056 = 722.400460800  boot/grub/core.img                             1
 892.820220947 = 958.658412544  boot/grub/grub.cfg                             1
 466.333007812 = 500.721254400  boot/initrd.img-2.6.38-8-generic               2
 672.786136627 = 722.398613504  boot/vmlinuz-2.6.38-8-generic                  1
 466.333007812 = 500.721254400  initrd.img                                     2
 672.786136627 = 722.398613504  vmlinuz                                        1

========= Devices which don't seem to have a corresponding hard drive: =========

sdd sde sdf sdg 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected


```Can you help me?

Thanks!

---

### Post by now0pen on 2011-07-23
installing ubuntu, i selected the option--install ubuntu with windows 7 side by side (or something like that).

---

### Post by Tea4all on 2011-07-23
Hold the right shift key when your computer is starting up and it should show the grub menu.

---

### Post by mikewhatever on 2011-07-23
Change the boot order in the BIOS so that you boot from /dev/sdc - presumably the second hdd. That's where Ubuntu's bootloader is installed and it should offer the choice of booting Ubuntu or Windows.

---

### Post by now0pen on 2011-07-23
THANKS--I will give those a try and post here what happens.

---

### Post by now0pen on 2011-07-23
UPDATE--

I checked into BIOS, but I couldn't find where I can change the boot order in the BIOS so that you boot from /dev/sdc. Frankly, I am not comfortable messing with my BIOS. If you can be patient and give me step by step howto's, I'll have a second look. 

I tried holding right shift on restart, nothing. It went to windows 7.

Alternatively, looking at the thread I mentioned above, can't I just run terminal and run the script--

> 
sudo mount /dev/sdc /mnt 
sudo grub-install --root-directory=/mnt /dev/sdc


after reboot, then do--

> sudo update-grub?

---

### Post by oldfred on 2011-07-23
Besides BIOS you should also have a one time boot key (mine is f12) that the BIOS boot screen tells you about. You can try that before changing BIOS.

Is 1TB drive a USB drive. It seems strange that is is after the flash drive.

Only if you do not want windows boot loader in sda should you reinstall grub. I always suggest keeping the boot loader on the same drive as the operating system except for those older (usually IDE) hardware system that only boot sda or primary master.

---

### Post by now0pen on 2011-07-23
> **oldfred said:**
> Besides BIOS you should also have a one time boot key (mine is f12) that the BIOS boot screen tells you about. You can try that before changing BIOS.

Is 1TB drive a USB drive. It seems strange that is is after the flash drive.

I think mine is F8. I'll do that. Thanks!

The 1TB drive is a USB external hard drive.

---

### Post by now0pen on 2011-07-23
> **oldfred said:**
> Besides BIOS you should also have a one time boot key (mine is f12) that the BIOS boot screen tells you about. You can try that before changing BIOS.

Is 1TB drive a USB drive. It seems strange that is is after the flash drive.

Only if you do not want windows boot loader in sda should you reinstall grub. I always suggest keeping the boot loader on the same drive as the operating system except for those older (usually IDE) hardware system that only boot sda or primary master.

I did the one time boot key--F8, and these are what I found--

> 
Please select boot device:
SATA 4MST31608159s
CDROM...
USB EXT HDD
USB (my usb stick)
USB generic...
... CF
... SD
... SM
... MS


I selected SATA and got back into windows 7, still no GRUB.

What's next?

---

### Post by now0pen on 2011-07-23
still looking for answers, should I give this a try-- [http://goo.gl/11csF](http://goo.gl/11csF)

---

### Post by now0pen on 2011-07-23
> **now0pen said:**
> still looking for answers, should I give this a try-- [http://goo.gl/11csF](http://goo.gl/11csF)

Running [sudo fdisk -l] gave me these--

```

ubuntu@ubuntu:~$ sudo fdisk-l
sudo: fdisk-l: command not found
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002f393

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       19458   156185600    7  HPFS/NTFS

Disk /dev/sdb: 2011 MB, 2011168768 bytes
62 heads, 62 sectors/track, 1021 cylinders
Units = cylinders of 3844 * 512 = 1968128 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f2ab9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1021     1962331    c  W95 FAT32 (LBA)

Disk /dev/sdc: 1000.2 GB, 1000202043392 bytes
255 heads, 63 sectors/track, 121600 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00261ddd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60657   487222656+   7  HPFS/NTFS
/dev/sdc2           60657      121600   489527681    5  Extended
/dev/sdc5          120563      121600     8337703+  82  Linux swap / Solaris
/dev/sdc6          120073      120562     3930112   82  Linux swap / Solaris
/dev/sdc7           60657      119584   473328640   83  Linux
/dev/sdc8          119584      120072     3923968   82  Linux swap / Solaris

```

---

### Post by now0pen on 2011-07-23
given the information above, should I now proceed with these--

> 
- Assuming Ubuntu 11.04 was installed on device sdb1, do this [sudo mount /dev/sdb1 /mnt]
- Now, do this [sudo grub-install --root-directory=/mnt /dev/sdb],  notice there are two dashes in front of root-directory, and I&#8217;d not  using sdb1 but sdb.
- Since the command in step 15 had reinstalled Grub 2, now we need to  unmount the /mnt (i.e., sdb1) to clean up.  Do this [sudo umount /mnt]
- Reboot and remove Ubuntu 11.04 CD/DVD from disk tray.
- Log into Ubuntu 11.04 (you have no choice but it will make you log into Ubuntu 11.04 at this point).
- Open up a terminal in Ubuntu 11.04 (using real installation, not live CD/DVD).
- Execute this command [sudo update-grub].
- Reboot machine
?

---

### Post by oldfred on 2011-07-23
Do not install grub to any other device. Since your sdc is a removeable device installing grub any place else will require you to always have it plugged in.

When you chose the SATA drive that was your internal. Is your external one of the USB-HDs? I only have USB flash drives on my USB and they actually do not appear under USB, but under hard drive choices. You may have to experiment to get it to boot.

Often having the flash drive and the USB plugged in can cause confusion. I might reboot without flash drive but with just USB external and see what choices you have to boot.

---

### Post by now0pen on 2011-07-26
After three days, I decided to reformat, reinstall windows 7 (first), then ubuntu following these [instructions]("http://www.hackourlife.com/dual-boot-windows-7-and-ubuntu-11-04-natty-narwhal/"). Today, I have a dual boot pc running ubuntu 11.04 by default, and windows 7. 
  

What was different this time, was that I partitioned my hard drive  using gparted while inside ubuntu trial mode, then installed ubuntu from  there. Immediately after the reboot, I got my grub.

---

