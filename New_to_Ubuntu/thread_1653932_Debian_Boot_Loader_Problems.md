---
title: "Debian Boot Loader Problems"
date: 2010-12-27
forum: New to Ubuntu
---

### Post by McTwitch on 2010-12-27
Alright, I just installed Debian, and that went well. But, I didn't know if I should have it's boot loader thing on the MBR, so instead I had it install on /dev/sdc1, the / partition for Debian that I set up, and now it won't boot. I'm running...or attempting to run, it on an HDD that I also have Ubuntu 10.04 installed on. Then I have Windows Vista on the internal harddrive of my computer.

So, was I supposed to install it onto the MBR? And if so, how do I fix it without redoing the entire install?

---

### Post by garvinrick4 on 2010-12-27
#Run this boot script so we can see drive sdc
#If possible should have not installed grub at all and
booted into Ubuntu install and updated grub. That would
have put debian in grub config and boot menu just fine.
# If has grub-legacy we can remove it in chroot command
   and update-grub with Ubuntu partition.
# Just to be safe run the bootscript only takes a minute.
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/") 
Download above to DESKTOP and then run code below. Copy and paste to this
thread and highlight whole thing after paste and hit # sign in upper right of message
box, puts code tags on it, easier to read.
```
 sudo bash ~/Desktop/boot_info_script*.sh 
```

---

### Post by McTwitch on 2010-12-27
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #6 for /boot/grub.

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
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sdb1 and 
                       looks at sector 19628159 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Operating System:  Debian GNU/Linux 5.0
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2              81,920    30,801,919    30,720,000   7 HPFS/NTFS
/dev/sda3    *     30,801,920   625,140,399   594,338,480   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    20,482,874    20,482,812  83 Linux
/dev/sdb2          81,915,559   625,137,344   543,221,786   5 Extended
/dev/sdb5         615,916,098   625,137,344     9,221,247  82 Linux swap / Solaris
/dev/sdb6          81,915,561   133,114,589    51,199,029  83 Linux
/dev/sdb7         133,114,653   440,309,519   307,194,867  83 Linux
/dev/sdb3          20,482,875    81,915,434    61,432,560  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        68D8B5A5D8B57244                       ntfs       RECOVERY                      
/dev/sda3        4028B7C928B7BBEA                       ntfs       OS                            
/dev/sda: PTTYPE="dos" 
/dev/sdb1        2963e932-74f6-4402-92f4-06079772603f   ext3                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb3        ad013c30-eb8d-47aa-8588-4f73ccdad084   ext3                                     
/dev/sdb5                                               swap                                     
/dev/sdb6        fc534f08-16f9-49bb-b4a2-b67ec506eebc   ext4       10.04-root                    
/dev/sdb7        511b1c51-aab0-4f49-bb6b-a831ee53c9d4   ext4       10.04-home                    
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb6        /                        ext4       (rw,errors=remount-ro)
/dev/sdb7        /home                    ext4       (rw)
/dev/sdb1        /media/2963e932-74f6-4402-92f4-06079772603f ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb3        /media/ad013c30-eb8d-47aa-8588-4f73ccdad084 ext3       (rw,nosuid,nodev,uhelper=udisks)


=========================== sdb1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        5

# Pretty colours
color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/sdc1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(single-user) single
# altoptions=(single-user mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Debian GNU/Linux, kernel 2.6.26-2-amd64
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.26-2-amd64 root=/dev/sdc1 ro quiet
initrd        /boot/initrd.img-2.6.26-2-amd64

title        Debian GNU/Linux, kernel 2.6.26-2-amd64 (single-user mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.26-2-amd64 root=/dev/sdc1 ro single
initrd        /boot/initrd.img-2.6.26-2-amd64

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title        Windows Vista/Longhorn (loader)
root        (hd0,2)
savedefault
chainloader    +1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sdc1       /               ext3    errors=remount-ro 0       1
/dev/sdc3       /home           ext3    defaults        0       2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

=================== sdb1: Location of files loaded by Grub: ===================


  10.0GB: boot/grub/menu.lst
  10.0GB: boot/grub/stage2
   2.0GB: boot/initrd.img-2.6.26-2-amd64
   8.3GB: boot/initrd.img-2.6.26-2-amd64.bak
   8.3GB: boot/vmlinuz-2.6.26-2-amd64
   2.0GB: initrd.img
   8.3GB: vmlinuz

=========================== sdb6/boot/grub/grub.cfg: ===========================

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
set root='(hd1,6)'
search --no-floppy --fs-uuid --set fc534f08-16f9-49bb-b4a2-b67ec506eebc
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
set root='(hd1,6)'
search --no-floppy --fs-uuid --set fc534f08-16f9-49bb-b4a2-b67ec506eebc
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set fc534f08-16f9-49bb-b4a2-b67ec506eebc
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=fc534f08-16f9-49bb-b4a2-b67ec506eebc ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set fc534f08-16f9-49bb-b4a2-b67ec506eebc
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=fc534f08-16f9-49bb-b4a2-b67ec506eebc ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set fc534f08-16f9-49bb-b4a2-b67ec506eebc
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=fc534f08-16f9-49bb-b4a2-b67ec506eebc ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set fc534f08-16f9-49bb-b4a2-b67ec506eebc
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=fc534f08-16f9-49bb-b4a2-b67ec506eebc ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set fc534f08-16f9-49bb-b4a2-b67ec506eebc
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set fc534f08-16f9-49bb-b4a2-b67ec506eebc
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 4028b7c928b7bbea
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Debian GNU/Linux, kernel 2.6.26-2-amd64 (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 2963e932-74f6-4402-92f4-06079772603f
    linux /boot/vmlinuz-2.6.26-2-amd64 root=/dev/sdc1 ro quiet
    initrd /boot/initrd.img-2.6.26-2-amd64
}
menuentry "Debian GNU/Linux, kernel 2.6.26-2-amd64 (single-user mode) (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 2963e932-74f6-4402-92f4-06079772603f
    linux /boot/vmlinuz-2.6.26-2-amd64 root=/dev/sdc1 ro single
    initrd /boot/initrd.img-2.6.26-2-amd64
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb6 during installation
UUID=fc534f08-16f9-49bb-b4a2-b67ec506eebc /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb7 during installation
UUID=511b1c51-aab0-4f49-bb6b-a831ee53c9d4 /home           ext4    defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=10fd3aa7-2241-45ed-b0bb-4299647b7950 none            swap    sw              0       0

=================== sdb6: Location of files loaded by Grub: ===================


  59.2GB: boot/grub/core.img
  60.0GB: boot/grub/grub.cfg
  59.4GB: boot/initrd.img-2.6.32-21-generic
  60.2GB: boot/initrd.img-2.6.32-24-generic
  59.3GB: boot/vmlinuz-2.6.32-21-generic
  59.9GB: boot/vmlinuz-2.6.32-24-generic
  60.2GB: initrd.img
  59.4GB: initrd.img.old
  59.9GB: vmlinuz
  59.3GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc 
```

---

### Post by garvinrick4 on 2010-12-27
In live cd: with internet connection: Open a terminal:
                   ```

[CODE]sudo mount /dev/sdb1 /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /proc /mnt/proc && sudo mount -o bind /sys /mnt/sys && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt

``` ```
apt-get purge grub grub-common grub-pc
``````
exit
```                      ```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt/sys && sudo umount /mnt
 
``````
sudo mount /dev/sdb6 /mnt
``````
sudo grub-install --recheck --root-directory=/mnt /dev/sdb
``````
sudo umount /mnt
``````
sudo reboot
```Go into ubuntu install and
```
sudo update-grub
```[/code]We are removing all grub files from sdb1 (debian install)

Installing grub2 to mbr of sdb looking in sdb6 for boot files.
Updating sdb6 to add sdb1 in grub config and make boot menu entry

---

### Post by McTwitch on 2010-12-27
Alright. Computer's a bit tied up at the moment, but I'll get back to you as soon as I'm able to do it.

---

### Post by McTwitch on 2010-12-27
Alright, when I entered the command 
```

sudo grub-install --recheck --root-directory=/mnt /dev/sdb 
```I received this as an output:
```
sudo: grub-install: command not found

```

---

### Post by garvinrick4 on 2010-12-27
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html")

Did you use a device that made the external drive go from sdb in your bootscript to
sdc at time of running code. run this to make sure before re running code.
```
sudo fdisk -l
``` (lower case L)
IF So change all sdb to sdc in code.
What boots right now on your external drive? anything.

---

### Post by McTwitch on 2010-12-27
For what ever reason, it seems to be read as SDC constantly. I switched it while I was typing in the code. 
And on my External I have Ubuntu 10.04

---

### Post by garvinrick4 on 2010-12-27
I hope you are copy and pasting the long ones. Are you using a usb flash device as a live usb or is Ubuntu booting? If Ubuntu booting run:
```
sudo update-grub 
```# As long as you mount the right one sdb or sdc whatever the right one is. In bootscript said sdb. But can change if you plug in another usb device to sdc
# So if debian partition is mounted and grub removed then ubuntu has grub-updated
should put into ubuntu's grub2 config files and grub menu entry will be made so you
can boot into it. 
 # Debian has older grub called grub legacy and we do not need it at all. Ubuntu will always
be the grub files used to boot.
 # Your internal drive has windows and if you boot off of that will only get Windows to boot.
 # if you boot off of external USB drive will show Ubuntu, Debian, Windows.
    Can choose in Bios which one to boot off of.
# This is not theory it is practical, I have 4 grub2 and 3 grub legacy installs and have no grub-legacy installed
in any of those installs. Such as Fedora, OpenSuse, Red Hat Beta. Ubuntu is my main installs and what I use most
all the time.

---

### Post by McTwitch on 2010-12-30
Tried it again (this time everything loaded as either SDB for my HDD or SDA for the internal harddrive) and at that one bit of code, it went wrong again. 
I'll switch over to my actual Ubuntu install and try update-grub. Sorry it took me so long to reply.

---

### Post by garvinrick4 on 2010-12-31
> **McTwitch said:**
> Tried it again (this time everything loaded as either SDB for my HDD or SDA for the internal harddrive) and at that one bit of code, it went wrong again. 
I'll switch over to my actual Ubuntu install and try update-grub. Sorry it took me so long to reply. If you removed grub-legacy going into Ubuntu and updating grub is the right thought.
chroot command worked so have no idea why a normal command like grub-install is giving a problem. Hope it is working correctly now.

---

### Post by McTwitch on 2010-12-31
Update-grub didn't work. I'm going to try that string of commands you gave me, with a full understanding that insanity is doing the same thing repeatedly, each time expecting a different result.

---

### Post by McTwitch on 2010-12-31
Alright, I ran the string of codes again. This time I noticed something, not sure if it happened the previous times, though:

```
sudo mount /dev/sdb1 /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /proc /mnt/proc && sudo mount -o bind /sys /mnt/sys && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
chroot: cannot run command `/bin/bash': Exec format error

```

---

### Post by garvinrick4 on 2010-12-31
# Are you using the same architecture of Live CD that your install is (64 bit or 32 bit)?
That certainly would explain why?
# Use one with same architecture and I think you will be surprised.

---

### Post by McTwitch on 2010-12-31
I'm pretty sure that I am, but my choices are slightly limited. I had a home-burned Livedisk, and one ordered from the actual Ubuntu company. The one from the company won't boot anymore, so I'm stuck with the home-burned one (which I'm fairly certain is the one I used to install). How do I find out if I am?

---

### Post by garvinrick4 on 2010-12-31
```
uname -a
```
The only time I have had the chroot command not work is with wrong architecture.

---

### Post by McTwitch on 2011-01-01
Right, they're both i686. If I'm not mistaken that 64-bit, right? There are other numbers that are included that aren't the same. My install says 2.6.32-24, whereas the Livedisk says 2.6.32-21. That's not important, though, is it?

---

### Post by QLee on 2011-01-01
[QUOTE=McTwitch]... 
I'll switch over to my actual Ubuntu install and try update-grub. Sorry it took me so long to reply.[/QUOTE]

This would have been the correct way to proceed. However if the Debian (stable), codename Lenny, install still had a menu.lst file in /boot/grub I think GRUB2 update takes the incorrect harddrive device node notation from it. Lenny kernels identify IDE drives as hdxx, not sdxx. (I'm not sure if GRUB2 would also look at the fstab on the Lenny install, but probably not) So, when you have done an update-grub from the Ubuntu install, have a look at /boot/grub/grub.cfg and see if the stanza for the Lenny install is trying to use /dev/hdb1 type of notation. If it is, try the kernel line with "UUID= "style of notation. You'll probably have to make a custom menu entry if you want to boot Lenny in this way. Alternately, you could have left things as they were on the Lenny partition and chainloaded to it. Note: Squeeze, which will be the new (stable) Debian release, soon, when it is ready, does use GRUB2 and the sdxx notation.

Lots in the above for a beginner. No problem if you didn't understand it. Follow the information on this link and post the results of the boot info script, it will show enough about how your system is currently configured so that you can get the help you need.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Easiest thing to do is wait until Debian Squeeze is released, it shouldn't be too long, and install it instead of Lenny. Squeeze will be closer to Ubuntu in function and the applications will be more modern versions than Lenny. That's what I recommend to a beginner.

[Edit] By beginner, I mean Debian beginner, I can see you're not an Ubuntu beginner.

---

### Post by McTwitch on 2011-01-01
Right. I understood most of that in theory, but not in practice. I'm not going to have much time to work on it in the next week or so, so I think I'll just go with waiting until Squeeze is released and installing that.

---

### Post by QLee on 2011-01-01
[QUOTE=McTwitch]... so I think I'll just go with waiting until Squeeze is released and installing that.[/QUOTE]

They wanted to get it out before the end of the year but Debian policy is to release when it is ready, although there is pressure to follow a set release schedule but it's not likely to ever be as short as Ubuntu's. 

The boot info script could still help garvinrick4 to help you but I think you have made the correct decision to wait for Squeeze (6.0).

---

### Post by garvinrick4 on 2011-01-01
> **McTwitch said:**
> Right, they're both i686. If I'm not mistaken that 64-bit, right? There are other numbers that are included that aren't the same. My install says 2.6.32-24, whereas the Livedisk says 2.6.32-21. That's not important, though, is it?
They are 32 bit, this is a 64 bit?
rick@rick-laptop:/$ uname -a
Linux rick-laptop 2.6.37-11-generic #25-Ubuntu SMP Tue Dec 21 23:42:56 UTC 2010 x86_64 GNU/Linux
## No kernel does not matter.

---

### Post by garvinrick4 on 2011-01-01
If in fact the 2 operating systems Debian and Ubuntu are the same architecture and you are say in Ubuntu you can chroot into Debian from Ubuntu install or vice-versa. With chroot
just meaning to get into root of a install so as to make changes without booting into or not being able to boot into that install. By mounting in /mnt or in /media and then using chroot command. This is not that big of a deal just need same 32 or 64 bit architecture and a few commands but something seems to be amiss.

---

### Post by McTwitch on 2011-01-01
Well, I don't really have the time to be figuring this out, so I'm just going to wait until Squeeze comes out and install that.

---

### Post by garvinrick4 on 2011-01-01
Sounds good, I cannot stand it when I cannot figure something out drives me nuts but then I have the time.

---

### Post by QLee on 2011-01-02
> **garvinrick4 said:**
> Sounds good, I cannot stand it when I cannot figure something out drives me nuts but then I have the time.

You had most of it figured out, garvenrick4.

When I looked back far enough (big oops) I saw most of my previous reply was incorrect, it was not a second internal, it was a USB drive which would have used sdxx notation in Lenny. However, the part about device node still applies. Somehow when Lenny was installed the system picked the drive up as sdc and the GRUB2 update picked that up from the legacy GRUB menu.lst thus causing the kernel line for the Lenny install in Ubuntu's grub.cfg to be trying to load the kernel from a drive that didn't exist. The fstab from the Lenny install was also incorrect so /home for Lenny wouldn't have mounted in any case. 

So, still a case where changing the root=/dev/sdc1 to root=UUID=2963e932-74f6-4402-92f4-06079772603f in the kernel line in Ubuntu's grub.cfg and amending the fstab in the Lenny install would have probably let the system boot. And you could have made a custom entry.

Why was it sdc in Lenny? Who knows, maybe computer has a card reader or there was thumb drive attached during install or...

Bottom line: I still think McTwitch made a wise choice. If I remember this correctly a default Lenny install used "stable" in the sources list rather than codename, "lenny" and this would trigger a big surprise for the user on the update and upgrade following Squeeze release when it then becomes "stable" and Lenny is sent to oldstable repositories.

Squeeze is going to a bit more familiar as far as application version goes and there will already be enough differences between Debian and Ubuntu to provide learning experiences for McTwitch.

---

