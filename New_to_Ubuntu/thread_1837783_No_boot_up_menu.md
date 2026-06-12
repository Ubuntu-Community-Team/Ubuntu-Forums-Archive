---
title: "No boot up menu"
date: 2011-09-02
forum: New to Ubuntu
---

### Post by Brianret on 2011-09-02
I have installed Ubuntu 10.10 but  my pc boots straight into windows 7, there is no menu choice. Without getting too technical, could anyone tell me how I can recover this item?
Many thanks.

---

### Post by Rex Bouwense on 2011-09-02
Is this a dual boot install or a WUBI install?  Also can you get a boot menu when you hold down the shift key during boot?

---

### Post by sanderd17 on 2011-09-02
If it's not a Wubi installation, give us the output of the boot info script. Follow the instructions on this page from a Live CD/USB: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Brianret on 2011-09-02
Here is the output you requested, sorry for the delay -  


Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for (,msdos5)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
224 heads, 19 sectors/track, 459004 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *        206,848   507,996,749   507,789,902   7 NTFS / exFAT / HPFS
/dev/sda2         507,998,206 1,953,523,711 1,445,525,506   5 Extended
/dev/sda5         507,998,208 1,917,618,175 1,409,619,968  83 Linux
/dev/sda6       1,917,620,224 1,953,523,711    35,903,488  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   312,560,639   312,560,577  83 Linux


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 4004 MB, 4004511744 bytes
116 heads, 51 sectors/track, 1322 cylinders, total 7821312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  32     7,821,311     7,821,280   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        523488BB3488A397                       ntfs       
/dev/sda5        7b38e764-6915-4a6d-a3b1-ad6da92c8099   ext4       
/dev/sda6        dc340e28-c1e8-45f0-95f2-89fe895dd9c7   swap       
/dev/sdb1        307549ff-92a5-4e0c-84b6-c900123a814e   ext3       
/dev/sdc1        B07B-634D                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/B07B-634D         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set 7b38e764-6915-4a6d-a3b1-ad6da92c8099
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set 7b38e764-6915-4a6d-a3b1-ad6da92c8099
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
    search --no-floppy --fs-uuid --set 7b38e764-6915-4a6d-a3b1-ad6da92c8099
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=7b38e764-6915-4a6d-a3b1-ad6da92c8099 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 7b38e764-6915-4a6d-a3b1-ad6da92c8099
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=7b38e764-6915-4a6d-a3b1-ad6da92c8099 ro single 
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
    search --no-floppy --fs-uuid --set 7b38e764-6915-4a6d-a3b1-ad6da92c8099
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 7b38e764-6915-4a6d-a3b1-ad6da92c8099
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 523488bb3488a397
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
# / was on /dev/sdb5 during installation
UUID=7b38e764-6915-4a6d-a3b1-ad6da92c8099 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=dc340e28-c1e8-45f0-95f2-89fe895dd9c7 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 752.366264343 = 807.847124992  boot/grub/core.img                             1
 602.371826172 = 646.791823360  boot/grub/grub.cfg                             1
 888.997947693 = 954.554277888  boot/initrd.img-2.6.35-22-generic              2
 752.364730835 = 807.845478400  boot/vmlinuz-2.6.35-22-generic                 1
 888.997947693 = 954.554277888  initrd.img                                     2
 752.364730835 = 807.845478400  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  6d 2c 6d 2c 6d 2c 6d 2c  6d 2c 6d 2c 6d 2c 6d 2c  |m,m,m,m,m,m,m,m,|
*
00000040  6d 2c 6d 2c 6d 2c 6d 2c  9f 17 16 ac 6d 2c 6d 2c  |m,m,m,m,....m,m,|
00000050  6d 2c 6d 2c 6d 2c 6d 2c  6d 2c 6d 2c 6d 2c 6d 2c  |m,m,m,m,m,m,m,m,|
*
00000090  6d 2c 6d 2c 6d 2c 6d 2c  9f 17 17 ac 6d 2c 6d 2c  |m,m,m,m,....m,m,|
000000a0  6d 2c 6d 2c 6d 2c 6d 2c  6d 2c 6d 2c 6d 2c 6d 2c  |m,m,m,m,m,m,m,m,|
*
000000e0  6d 2c 6d 2c 6d 2c 6d 2c  9f 17 18 ac 6d 2c 6d 2c  |m,m,m,m,....m,m,|
000000f0  6d 2c 6d 2c 6d 2c 6d 2c  6d 2c 6d 2c 6d 2c 6d 2c  |m,m,m,m,m,m,m,m,|
*
00000130  6d 2c 6d 2c 6d 2c 6d 2c  9f 17 19 ac 6d 2c 6d 2c  |m,m,m,m,....m,m,|
00000140  6d 2c 6d 2c 6d 2c 6d 2c  6d 2c 6d 2c 6d 2c 6d 2c  |m,m,m,m,m,m,m,m,|
*
00000180  6d 2c 6d 2c 6d 2c 6d 2c  9f 17 1a ac 6d 2c 6d 2c  |m,m,m,m,....m,m,|
00000190  6d 2c 6d 2c 6d 2c 6d 2c  6d 2c 6d 2c 6d 2c 6d 2c  |m,m,m,m,m,m,m,m,|
*
000001b0  6d 2c 6d 2c 6d 2c 6d 2c  6d 2c 6d 2c 6d 2c 00 df  |m,m,m,m,m,m,m,..|
000001c0  d3 ff 83 df d3 ff 02 00  00 00 00 18 05 54 00 df  |.............T..|
000001d0  d3 ff 05 df d3 ff 02 18  05 54 00 e0 23 02 00 00  |.........T..#...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by Johnb0y on 2011-09-02
was it a dual boot install or a WUBI install?

---

### Post by Brianret on 2011-09-02
Dual boot

---

### Post by Johnb0y on 2011-09-02
what was the software you used to create partitions/install? unbuntu or windows or 3rd party?

---

### Post by sanderd17 on 2011-09-02
It's better to place such outputs between CODE tags (click on the #-symbol in advanced editing mode). Now, there are certain parts not readable.

From what I can read: you installed the bootloader to the second hard disk (sdb, stands for Solid Disk B). I assume sdc is your USB stick? That means you have 2 hard disks.

In your BIOS, you can configure the primary hard disk (the hard disk that is run at boot time). If you change the order, than Ubuntu would normally boot.

As an alternative, you can install the bootloader to sda using this method: [https://help.ubuntu.com/community/Grub2#ChRoot](https://help.ubuntu.com/community/Grub2#ChRoot)

Changing the order in the BIOS is easier (and also easier to undo), so I would suggest you try that first.

---

### Post by Brianret on 2011-09-02
I downloaded an iso from ubuntu, burned it to a cd and installed 10.10 from the result. It installed to my Hdrive ok, partitioned as needed. I have win 7 and ubuntu but I can only access win7.

---

### Post by oldfred on 2011-09-02
Is your 160GB drive IDE/PATA and the 1TB drive SATA? BIOS often promote IDE drives to sda and grub defaults its install to sda as that assumes you boot from sda.

If you change BIOS to boot the 160GB drive or use your one time boot key (f12 on my system but it varies) to choose to boot from the 160GB drive does it boot Ubuntu?

---

### Post by Brianret on 2011-09-02
I seem to have created a whole lot of problems for myself and managed to share them with all of you! A big sorrryy from me. Sanderd17 may have hit the nail on the head because after his reply I found that I had left a usb stick attached whilst I downloaded and installed 10.10 last night and the bios, for some reason, was set to boot from it (although it didn't as I have only just removed it). 
Can it be that the Ubuntu installation put the boot on to my errant usb stick but not on to my installed system? I have since tested the usb as a boot and it doesn't work (I just left it in the pc!). It does seem to me that boot is  on the stick and not on the installed system as removing it has no effect.

---

### Post by oldfred on 2011-09-02
A few systems make USB flash drives sda not whichever drive would be after the hard drive(s). In those cases the grub default install of sda does install to the flash drive. But your grub looks like it is on the 160GB drive. Is it also a USB drive?

---

### Post by Brianret on 2011-09-02
The 160gb drive is a single ide drive beside my 1tg sata. I have just tried to boot from the usb stick with it as No 1 on the bios but no luck.
The 160gb drive was booted for Ubuntu originally so windows cannot see it. I am about to fire up 10.10 from my cd and take a look at the contents. Will keep you posted.
Brian

---

### Post by Brianret on 2011-09-02
I am now in Ubuntu and can confirm that the 160gb drive does not have a boot system on it. It looks as though my boot file is on my usb (which won't boot) stick and the rest of the ubuntu 10.10 is on my pc.
Can I reinstall ubuntu on my pc over the existing faulty copy?
Brian

---

### Post by sanderd17 on 2011-09-02
> **Brianret said:**
> I am now in Ubuntu and can confirm that the 160gb drive does not have a boot system on it. It looks as though my boot file is on my usb (which won't boot) stick and the rest of the ubuntu 10.10 is on my pc.
Can I reinstall ubuntu on my pc over the existing faulty copy?
Brian

Yes, you can reinstall it, but you will probably have to go into manual mode because the default is to install next to everything else (and you probably don't want 2 ubuntu installations, although, that can be handy).

If you go in manual mode, you should know that an ext4 filesystem is a Linux one, and NTFS is windows. So you do not want to format any NTFS filesystem, but formatting ext4 filesystems can't hurt (because there is no linux you want to keep).

---

### Post by oldfred on 2011-09-02
You can just reinstall grub2's boot loader to the MBR of sda or sdb. You may need to check which drive is sda with the liveCD. And you do not have to install to the install drive. I prefer to have different system on each drive and have its bootloader in the MBR of that drive.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If grub 1.99 with Natty uses boot not root.
sudo grub-install --boot-directory=/mnt/boot /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

#More info here
#How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
#Reinstall grub2 - Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by Brianret on 2011-09-02
Problem solved. Could I say a big thank you to those who helped me out of the hole, I really was stuck. Particular thanks to oldfred who eventually provided the solution. Good on yer, mate!

---

