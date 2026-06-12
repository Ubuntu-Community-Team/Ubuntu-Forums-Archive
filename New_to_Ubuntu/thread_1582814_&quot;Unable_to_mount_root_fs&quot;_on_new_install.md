---
title: "&quot;Unable to mount root fs&quot; on new installation"
date: 2010-09-27
forum: New to Ubuntu
---

### Post by m237 on 2010-09-27
I just took an old Windows box and installed Ubuntu from CD.  The system worked fine.  I downloaded many applications and libraries I thought useful in my development.  At one point I rebooted, and now the system will not boot.  Here is the error on the loading screen:

[0.753758] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown wn-block (0,0)

When I boot up on the CD again, the file system is fully available, vmlinuz is as it should be, things work fine.  I have run grub-install again as root, and the issue is not fixed.

I will reload the system and rebuild again if necessary, but I would rather no lose all that work.  Has anyone else had this experience?  Does anyone have an idea how to save the system?

---

### Post by jtarin on 2010-09-27
Post the results from the command ```
fdisk -l
```I assume you use Grub2 to boot?

---

### Post by m237 on 2010-09-27
Yes, the system is apparently using grub2.
 
The boot secotr seems to be OK, the kernel is in original condition, the link to kernel is present, but the system will not boot.  Any suggestions greatly apreciated.

---

### Post by andrewthomas on 2010-09-27
Reinstall grub2

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by jtarin on 2010-09-27
> **jtarin said:**
> Post the results from the command ```
fdisk -l
```Run this command as suggested so I can see what we're working with.

---

### Post by m237 on 2010-09-28
Thanks for offering to look, fellas.[FONT=Courier New]

root@ubuntu:/# fdisk -l /dev/sda[/FONT]

[FONT=Courier New]Disk /dev/sda: 160.0 GB, 160041885696 bytes[/FONT]
[FONT=Courier New]255 heads, 63 sectors/track, 19457 cylinders[/FONT]
[FONT=Courier New]Units = cylinders of 16065 * 512 = 8225280 bytes[/FONT]
[FONT=Courier New]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT]
[FONT=Courier New]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT]
[FONT=Courier New]Disk identifier: 0x00011d9f[/FONT]

[FONT=Courier New]   Device Boot      Start         End      Blocks   Id  System[/FONT]
[FONT=Courier New]/dev/sda1   *           1       19272   154801152   83  Linux[/FONT]
[FONT=Courier New]/dev/sda2           19273       19458     1486849    5  Extended[/FONT]
[FONT=Courier New]/dev/sda5           19273       19458     1486848   82  Linux swap / Solaris[/FONT]
[FONT=Courier New]

[/FONT]

---

### Post by andrewthomas on 2010-09-28
Reinstall grub2

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by jtarin on 2010-09-28
Did you use one of these methods? Which one? And where did you place GRUB?

---

### Post by m237 on 2010-09-28
[SIZE=1]This is the output of the boot info script.  Hope it's not too long for this interface.

[email]root@ubuntu:/media/.render[/email]());# bash ./boot_info_script055.sh
Identifying MBRs...
Computing Partition Table of /dev/sda...
Computing Partition Table of /dev/sdb...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda5 for information... 
Searching sdb1 for information... 
Finished. The results are in the file RESULTS.txt located in /media/.render());
[email]root@ubuntu:/media/.render[/email]());# more results.txt
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
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

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   309,604,351   309,602,304  83 Linux
/dev/sda2         309,606,398   312,580,095     2,973,698   5 Extended
/dev/sda5         309,606,400   312,580,095     2,973,696  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4102 MB, 4102887936 bytes
255 heads, 63 sectors/track, 498 cylinders, total 8013453 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  34     7,984,304     7,984,271   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        8f4e0b54-927f-4077-a630-9f2e5aac49ca   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        6477e164-c244-47fb-a774-028d4fb6153e   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        2809-A4D2                              vfat       .render());                   
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /mnt                     ext4       (rw)
/dev/sr1         /media/U3 System         iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=999,gid=999,
iocharset=utf8,mode=0400,dmode=0500)
/dev/sdb1        /media/.render());       vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,
shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 8f4e0b54-927f-4077-a630-9f2e5aac49ca
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 8f4e0b54-927f-4077-a630-9f2e5aac49ca
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class
 os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 8f4e0b54-927f-4077-a630-9f2e5aac49ca
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=8f4e0b54-927f-4077-a630-9f2e5aac49ca ro   q
uiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --c
lass gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 8f4e0b54-927f-4077-a630-9f2e5aac49ca
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=8f4e0b54-927f-4077-a630-9f2e5aac49ca ro sin
gle 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 8f4e0b54-927f-4077-a630-9f2e5aac49ca
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 8f4e0b54-927f-4077-a630-9f2e5aac49ca
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=6477e164-c244-47fb-a774-028d4fb6153e none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   4.4GB: boot/grub/core.img
   4.5GB: boot/grub/grub.cfg
 151.4GB: boot/initrd.img-2.6.32-24-generic
 151.3GB: boot/vmlinuz-2.6.32-24-generic
 151.4GB: initrd.img
 151.3GB: vmlinuz
[email]root@ubuntu:/media/.render[/email]());#  
[/SIZE]

---

### Post by jtarin on 2010-09-28
> I downloaded many applications and librariesDid you by any chance download a new kernel? Maybe a update-grub command would be in order. It should do this automatically when a new kernel is installed but....You will have to boot with the CD then chroot into your install. Another possibility is bad ram.Run memtest if you can.
[Interesting read here.]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/578849")

---

### Post by m237 on 2010-10-01
Downloaded new kernel and installed.  Same version as old, 10.04.01 LTD  but just making sure.  Rebooted, No joy.  
Error Cannot read the Lunux header 
Error you need to load the kernel first
Failed to boot both default and fallback entries


De- and re- installed grub as instructed by link above.  De and re apparently full successful with the following lines in response:
Setting up grub-pc (1.98-1ubuntu7) ...

Creating config file /etc/default/grub with new version
Installation finished. No error reported.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.36-020636rc6-generic
Found initrd image: /boot/initrd.img-2.6.36-020636rc6-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found memtest86+ image: /boot/memtest86+.bin
File descriptor 3 (pipe:[14856]) leaked on lvs invocation. Parent PID 5696: /bin/sh
done
ran update-grub just for good measure:
root@ubuntu:/# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.36-020636rc6-generic
Found initrd image: /boot/initrd.img-2.6.36-020636rc6-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Going to reboot now.  Will answer when done.

Getting the same errors as before:
[INDENT]
error: Cannot read the Lunux header 
error: You need to load the kernel first

 Failed to boot both default and fallback entries

Press any key to continue ...
[/INDENT]

In search of the ANY key ...

LATER:
Also downloaded the Ubuntu DVD.iso, found the repair system option.  Ran this, reinstalled grub. Same problem.

---

### Post by jtarin on 2010-10-01
If you uninstalled Ubuntu and then reinstalled....why do you have two kernels??? Maybe you'd like to give LILO a shot as a bootmanager rather than GRUB?

---

### Post by m237 on 2010-10-01
> **jtarin said:**
> If you uninstalled Ubuntu and then reinstalled....why do you have two kernels??? Maybe you'd like to give LILO a shot as a bootmanager rather than GRUB?

I have not unistalled Ubuntu -- Reinstallation is what I am trying to avoid.  I installed the second kernel according to a link I found in the thread above as a possibly remedy.

Following this suggestion, I will try installing LILO.

Memtest just finished without error.

---

### Post by andrewthomas on 2010-10-01
Before you do that, I found a problem with your /etc/fstab

change ```
/dev/sda1 / ext4 errors=remount-ro 0 1
``` to
```
UUID=8f4e0b54-927f-4077-a630-9f2e5aac49ca / ext4 errors=remount-ro 0 1
```

sometimes /dev/sda and /dev/sdb can get switched during mounting

---

### Post by m237 on 2010-10-01
> **andrewthomas said:**
> Before you do that, I found a problem with your /etc/fstab

change ```
/dev/sda1 / ext4 errors=remount-ro 0 1
``` to
```
UUID=8f4e0b54-927f-4077-a630-9f2e5aac49ca / ext4 errors=remount-ro 0 1
```sometimes /dev/sda and /dev/sdb can get switched during mounting

Wow!  Great!  Thanks so much.  I will try it as soon as I can.  Later:  OK, tried that, no joy.  edited /etc/fstab, booted (failed), then rebooted on Knoppix disc to confirm edits to /etc/fstab.  Sure enough, those lines now read:  # The following line was changed on advice of ubuntuforums.org because  # &quot;sometimes /dev/sda and /dev/sdb can get switched during mounting&quot; # /dev/sda1       /               ext4    errors=remount-ro 0       1 UUID=8f4e0b54-927f-4077-a630-9f2e5aac49ca  /               ext4    errors=remount-ro 0       1  So I guess switching to LILO is the final option, eh?  Does Ubuntu have a LILO installation package?  [thanks, Knoppix.  Is that considered Knoppix humor to munge all the lines together?)

---

### Post by m237 on 2010-10-03
Loaded LILO.  Used the steps given in a link elsewhere in this thread to deinstall and reinstall GRUB, omitting only the GRUB specific commands; then sudo chroot /mnt/temp, as given.

Used liloconfig to select master boot record and partition boot record.  Rebooted and ... no joy.

Loading Lin_2.6.36img1 ....................................
........................................................

And then it simply stops.

If there are no more suggestions, I will try reloading with the Ubuntu DVD 10.4 later this weekend.

---

### Post by jtarin on 2010-10-03
> Lin_2.6.36img1That does not look like a typical readout for a kernel.Did you install Lilo in a Live CD environment? Did you CHROOT into your permanent Ubuntu installation to install LILO? Can you post your /etc/lilo.conf?
Your lilo.conf should look similar to this```
# 
#Linux bootable partition config begins
  image = /boot/vmlinuz
  root = /dev/sdaX 
  label = Ubuntu
  read-only
```Where"X" is the number of your / partition.

---

### Post by jtarin on 2010-10-03
**This assumes you installed Lilo to the correct partition:If not uninstall and reinstall Lilo to the correct partition.**

This method of installation uses the chroot command to gain access to the broken system's files. Once the chroot command is issued, the LiveCD treats the broken system's / as its own. Commands run in a chroot environment will affect the broken systems filesystems and not those of the LiveCD.

**1.**Boot to the LiveCD Desktop (Ubuntu 9.10 or later). Please note that the Live CD must be the same as the system you are fixing - either 32-bit or 64-bit (if not then the chroot will fail).
**2.**Open a terminal - Applications, Accessories, Terminal.
**3.**Determine your normal system partition - (the switch is a lowercase "L")
sudo fdisk -l
If you aren't sure, run
df -Th. Look for the correct disk size and ext3 or ext4 format.
**4.**Mount your normal system partition:
Substitute the correct partition: sda1, sdb5, etc.
sudo mount /dev/sdXX /mnt # Example: sudo mount /dev/sda1 /mnt
**5.**Only if you have a separate boot partition:
sdYY is the /boot partition designation (for example sdb3)
sudo mount /dev/sdYY /mnt/boot
**6.**Mount the critical virtual filesystems:
sudo mount --bind /dev  /mnt/dev
sudo mount --bind /dev/pts  /mnt/dev/pts
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys  /mnt/sys
**7.**Chroot into your normal system device:
sudo chroot /mnt
**8.**Correct your lilo.conf
**9.**Run the command lilo -v (this will give you verbose output)
**10.**Exit chroot: CTRL-D on keyboard
**11.**Unmount virtual filesystems:
sudo umount /mnt/dev/pts
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt/sys
*****If you mounted a separate /boot partition:
sudo umount /mnt/boot
**12.**Unmount the LiveCD's /usr directory:
sudo umount /mnt/usr
**13.**Unmount last device:
sudo umount /mnt
**14.**Reboot.
sudo reboot

---

### Post by m237 on 2010-10-03
> **jtarin said:**
> That does not look like a typical readout for a kernel.Did you install Lilo in a Live CD environment? Did you CHROOT into your permanent Ubuntu installation to install LILO? Can you post your /etc/lilo.conf?
Your lilo.conf should look similar to this```
# 
#Linux bootable partition config begins
  image = /boot/vmlinuz
  root = /dev/sdaX 
  label = Ubuntu
  read-only
```Where"X" is the number of your / partition.


To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo bash
mkroot@ubuntu:~# mkdir /mnt/temp
root@ubuntu:~# mount /dev/sda1 /mnt/temp
root@ubuntu:~# ls /mnt/temp/etc/lilo*
/mnt/temp/etc/lilo.conf
root@ubuntu:~# cat /mnt/temp/etc/lilo.conf
# Generated by liloconfig

# This allows booting from any partition on disks with more than 1024
# cylinders.
lba32

# Specifies the boot device
boot=/dev/sda1

# Specifies the device that should be mounted as root.
# If the special name CURRENT is used, the root device is set to the
# device on which the root file system is currently mounted. If the root
# has been changed with  -r , the respective device is used. If the
# variable ROOT is omitted, the root device setting contained in the
# kernel image is used. It can be changed with the rdev program.
root=/dev/sda1

# Bitmap configuration for /boot/coffee.bmp
bitmap=/boot/coffee.bmp
bmp-colors=12,,11,15,,8
bmp-table=385p,100p,1,10
bmp-timer=38,2,13,1

# Enables map compaction:
# Tries to merge read requests for adjacent sectors into a single
# read request. This drastically reduces load time and keeps the map
# smaller. Using COMPACT is especially recommended when booting from a
# floppy disk.
# compact

# Install the specified file as the new boot sector.
# LILO supports built in boot sectory, you only need
# to specify the type, choose one from 'text', 'menu' or 'bitmap'.
# new: install=bmp      old: install=/boot/boot-bmp.b
# new: install=text     old: install=/boot/boot-text.b
# new: install=menu     old: install=/boot/boot-menu.b or boot.b
# default: 'menu' is default, unless you have a bitmap= line
# Note: install=bmp must be used to see the bitmap menu.
# install=menu
install=bmp

# Specifies the number of _tenths_ of a second LILO should
# wait before booting the first image.  LILO
# doesn't wait if DELAY is omitted or if DELAY is set to zero.
# delay=20

# Prompt to use certaing image. If prompt is specified without timeout,
# boot will not take place unless you hit RETURN
prompt
timeout=50

# Enable large memory mode.
large-memory

# Specifies the location of the map file. If MAP is
# omitted, a file /boot/map is used.
map=/boot/map

# Specifies the VGA text mode that should be selected when
# booting. The following values are recognized (case is ignored):
#   NORMAL  select normal 80x25 text mode.
#   EXTENDED  select 80x50 text mode. The word EXTENDED can be
#     abbreviated to EXT.
#   ASK  stop and ask for user input (at boot time).
#   <number>  use the corresponding text mode. A list of available modes
#     can be obtained by booting with  vga=ask  and pressing [Enter].
vga=normal

# Defines non-standard parameters for the specified disk.
#disk=/dev/sda
#    bios=0x80

# If you are using removable USB drivers (with mass-storage)
# you will need to tell LILO to not use these devices even
# if defined in /etc/fstab and referenced in /proc/partitions.
# Adjust these lines to your devices:
#
# disk=/dev/sda inaccessible
# disk=/dev/sdb inaccessible

# These images were automagically added. You may need to edit something.

image=/vmlinuz
    label="Linux"
    initrd=/initrd.img
    read-only

image=/boot/vmlinuz-2.6.32-24-generic
    label="Lin 2.6.32img0"
    initrd=/boot/initrd.img-2.6.32-24-generic
    read-only

image=/boot/vmlinuz-2.6.36-020636rc6-generic
    label="Lin 2.6.36img1"
    initrd=/boot/initrd.img-2.6.36-020636rc6-generic
    read-only

image=/boot/memtest86+.bin
    label="Memory Test+"
    read-only

# If you have another OS on this machine (say DOS),
# you can boot if by uncommenting the following lines
# (Of course, change /dev/hda2 to wherever your DOS partition is.)
# other=/dev/hda2
#   label="MS Windows"


The boot menu comes up with three image options;  i have tried all three and just posted the third.
I am trying the text you suggest for the first config.

image=/vmlinuz
  image = /boot/vmlinuz-2.6.32-21-generic
  root = /dev/sda1
  label = Ubuntu
  read-only

================================================
<Bonk! > Lilo -v indicates I have wrong file name for kernel file.

Corrected that and ran lilo.config.  Here is the results.  I have 3 warnings.  I presume none are serious.

ILO version 22.8, Copyright (C) 1992-1998 Werner Almesberger
Development beyond version 21 Copyright (C) 1999-2006 John Coffman
Released 19-Feb-2007, and compiled at 10:52:38 on Aug 25 2009
Ubuntu

Reading boot sector from /dev/sda1
Warning: /proc/partitions references Experimental major device 251.
Warning: Unable to determine video adapter in use in the present system.
Using BITMAP secondary loader
Calling map_insert_data
Mapping bitmap file /boot/coffee.bmp
Warning: Video adapter does not support VESA BIOS extensions needed for
  display of 256 colors.  Boot loader will fall back to TEXT only operation.
Calling map_insert_file

Boot image: /vmlinuz
Added vmlinuz *

Boot image: /boot/vmlinuz-2.6.32-24-generic
Added Ubuntu

Boot image: /boot/vmlinuz-2.6.32-24-generic
Mapping RAM disk /boot/initrd.img-2.6.32-24-generic
Added Lin_2.6.32img0

Boot image: /boot/vmlinuz-2.6.36-020636rc6-generic
Mapping RAM disk /boot/initrd.img-2.6.36-020636rc6-generic
Added Lin_2.6.36img1

Boot image: /boot/memtest86+.bin
Added Memory_Test+

Writing boot sector.
/boot/boot.0801 exists - no boot sector backup copy made.
3 warnings were issued.
root@ubuntu:/# 

rebooting now for final trial of the evening.

---

### Post by m237 on 2010-10-05
I have worked with the LILO config and the LILO manual, but the boot is still not successful.  Given the time investment at this point, I have cut my losses and reinstalled Ubuntu from the DVD.
 
Thanks for all your help, everyone.  Please consider this issue closed.

---

### Post by m237 on 2010-10-06
On further study, prior to re-installation, it seems to have been an anomaly in the disk partitioning.  Disk manager reported in the error message that a second swap space had some DOS formatting attributes, and the partition could not be deleted.  Reformatting the entire device seems to have solved the problem.

---

