---
title: "restoring grub menu"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by patchido on 2009-11-13
well, i installed opensuse and for some reason the grub menu that installed is kind of different and also ubuntu didnt appear on it, windows did appear, i want to restore the grub menu but the ubuntu version one, 

this is the opensuse's grub menu.lst

```
# Modified by YaST2. Last modification on Fri Nov 13 13:09:21 CST 2009
# THIS FILE WILL BE PARTIALLY OVERWRITTEN by perl-Bootloader
# Configure custom boot parameters for updated kernels in /etc/sysconfig/bootloader

default 0
timeout 8
##YaST - generic_mbr
gfxmenu (hd0,2)/boot/message
##YaST - activate

###Don't change this comment - YaST2 identifier: Original name: linux###
title Desktop -- openSUSE 11.2 - 2.6.31.5-0.1
    root (hd0,2)
    kernel /boot/vmlinuz-2.6.31.5-0.1-desktop root=/dev/disk/by-id/ata-ST9500325AS_6VE0441H-part3 resume=/dev/sda6 splash=silent quiet showopts vga=0x317
    initrd /boot/initrd-2.6.31.5-0.1-desktop

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 11.2 - 2.6.31.5-0.1
    root (hd0,2)
    kernel /boot/vmlinuz-2.6.31.5-0.1-desktop root=/dev/disk/by-id/ata-ST9500325AS_6VE0441H-part3 showopts apm=off noresume nosmp maxcpus=0 edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x317
    initrd /boot/initrd-2.6.31.5-0.1-desktop

###Don't change this comment - YaST2 identifier: Original name: windows 1###
title windows 1
    rootnoverify (hd0,0)
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: windows 2###
title windows 2
    rootnoverify (hd0,3)
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: floppy###
title Floppy
    rootnoverify (fd0)
    chainloader +1
```

my fstab

```
linux-4xkn:/home/pato # fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf5f3f5f3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3922    31503433+   7  HPFS/NTFS
/dev/sda2            3923        7958    32419170    5  Extended
/dev/sda3   *        7959       12037    32764567+  83  Linux
/dev/sda4           12038       60801   391696830    7  HPFS/NTFS
/dev/sda5            3923        7691    30274461   83  Linux
/dev/sda6            7692        7958     2144646   82  Linux swap / Solaris
```

---

### Post by ranch hand on 2009-11-13
I would copy paste the the menu entry for your Ubuntu from its menu.lst to the one in openSUSE.  I would boot to Ubuntu and, assuming that the entry worked right, change boot/root to Ubuntu.

The openSUSE grub is weird.

---

### Post by patchido on 2009-11-13
i agree with you, but how do i change the grub to ubuntus?

---

### Post by kansasnoob on 2009-11-13
The quickest way to see what's going on is to boot the Ubuntu Live CD, run the Boot Info script, and post the results as explained here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

That will tell us what version(s) of grub Ubuntu and Suse are using, etc.

---

### Post by patchido on 2009-11-14
here it is


```
============================= Boot Info Summary: ==============================

 => Acer 3 is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

```

---

### Post by Bucky Ball on 2009-11-14
Does Windows boot when you try it?

Just get to 

```
/boot/grub/menu.lst
```on your ubuntu partition and copy the section regarding your Ubuntu install (first on list probably). Plop it into the other grub at the end of the other data. Change the 'root' line to this:

```
root (hd0,4)
```... if it isn't that already, presuming your Ubuntu install is on sda5?

---

### Post by patchido on 2009-11-14
you mean to go into the menu.lst inside opensuse and change it?

because i prefer having the grub menu used in ubuntu but i dont know how to get it back, also i cant find my menu.lst inside ubuntu

---

### Post by patchido on 2009-11-14
please help me, this is kind of urgent

---

### Post by ranch hand on 2009-11-14
That is everything that you got with that script?

That is several pages short of the usual output.

---

### Post by patchido on 2009-11-14
woops, i got the file wrongly copied

corrected

```
============================= Boot Info Summary: ==============================

 => Acer 3 is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  
sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:      Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  
sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda3 and 
                       looks at sector 128192150 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #3 for 
                       /boot/grub/menu.lst.
    Operating System:  Welcome to openSUSE 11.2 
                       "Emerald" - Kernel ().
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   
=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf5f3f5f3

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    63,006,929    63,006,867   7 HPFS/NTFS
/dev/sda2          63,006,930   127,845,269    64,838,340   5 Extended
/dev/sda5          63,006,993   123,555,914    60,548,922  83 Linux
/dev/sda6         123,555,978   127,845,269     4,289,292  82 Linux swap / Solaris
/dev/sda3    *    127,845,270   193,374,404    65,529,135  83 Linux
/dev/sda4         193,374,405   976,768,064   783,393,660   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="4A2CC53C2CC52433" TYPE="ntfs" 
/dev/sda3: LABEL="OpenSuSE" UUID="a4eff572-7853-4bdd-8662-08822e5c8b31" TYPE="ext4" 
/dev/sda4: UUID="1821E9D014C199B8" LABEL="Data" TYPE="ntfs" 
/dev/sda5: LABEL="Ubuntu" UUID="c926f321-4a61-41bd-97b5-26051391ca1e" TYPE="ext4" 
/dev/sda6: UUID="954f2d1c-06d0-4ac1-869a-03b8b4186c52" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda3 on / type ext4 (rw,acl,user_xattr)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
debugfs on /sys/kernel/debug type debugfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,mode=0620,gid=5)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/pato/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=pato)
rpc_pipefs on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
/dev/sr0 on /media/Ubuntu 9.10 i386 type iso9660 (ro,nosuid,nodev,uhelper=devkit,uid=1000,gid=100,iocharset=utf8,mode=0400,dmode=0500)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set c926f321-4a61-41bd-97b5-26051391ca1e
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set c926f321-4a61-41bd-97b5-26051391ca1e
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=c926f321-4a61-41bd-97b5-26051391ca1e ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set c926f321-4a61-41bd-97b5-26051391ca1e
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=c926f321-4a61-41bd-97b5-26051391ca1e ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 4a2cc53c2cc52433
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=c926f321-4a61-41bd-97b5-26051391ca1e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=954f2d1c-06d0-4ac1-869a-03b8b4186c52 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda4   /media/Data   ntfs-3g  defaults 0 0

=================== sda5: Location of files loaded by Grub: ===================


  32.2GB: boot/grub/grub.cfg
  32.2GB: boot/initrd.img-2.6.31-14-generic
  32.2GB: boot/vmlinuz-2.6.31-14-generic
  32.2GB: initrd.img
  32.2GB: vmlinuz

=========================== sda3/boot/grub/menu.lst: ===========================

# Modified by YaST2. Last modification on Sat Nov 14 12:30:07 CST 2009
# THIS FILE WILL BE PARTIALLY OVERWRITTEN by perl-Bootloader
# Configure custom boot parameters for updated kernels in /etc/sysconfig/bootloader

default 0
timeout 8
##YaST - generic_mbr
gfxmenu (hd0,2)/boot/message
##YaST - activate

###Don't change this comment - YaST2 identifier: Original name: linux###
title Desktop -- openSUSE 11.2 - 2.6.31.5-0.1
    root (hd0,2)
    kernel /boot/vmlinuz-2.6.31.5-0.1-desktop root=/dev/disk/by-id/ata-ST9500325AS_6VE0441H-part3 resume=/dev/sda6 splash=silent quiet showopts vga=0x317
    initrd /boot/initrd-2.6.31.5-0.1-desktop

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 11.2 - 2.6.31.5-0.1
    root (hd0,2)
    kernel /boot/vmlinuz-2.6.31.5-0.1-desktop root=/dev/disk/by-id/ata-ST9500325AS_6VE0441H-part3 showopts apm=off noresume nosmp maxcpus=0 edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x317
    initrd /boot/initrd-2.6.31.5-0.1-desktop

###Don't change this comment - YaST2 identifier: Original name: windows 1###
title windows 1
    rootnoverify (hd0,0)
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: windows 2###
title ubuntu
    rootnoverify (hd0,4)
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: floppy###
title Floppy
    rootnoverify (fd0)
    chainloader +1

=============================== sda3/etc/fstab: ===============================

/dev/disk/by-id/ata-ST9500325AS_6VE0441H-part6 swap                 swap       defaults              0 0
/dev/disk/by-id/ata-ST9500325AS_6VE0441H-part3 /                    ext4       acl,user_xattr        1 1
proc                 /proc                proc       defaults              0 0
sysfs                /sys                 sysfs      noauto                0 0
debugfs              /sys/kernel/debug    debugfs    noauto                0 0
usbfs                /proc/bus/usb        usbfs      noauto                0 0
devpts               /dev/pts             devpts     mode=0620,gid=5       0 0

=================== sda3: Location of files loaded by Grub: ===================


  65.4GB: boot/grub/menu.lst
  65.4GB: boot/grub/stage2
  65.4GB: boot/initrd
  65.4GB: boot/initrd-2.6.31.5-0.1-desktop
  65.4GB: boot/vmlinuz
  65.4GB: boot/vmlinuz-2.6.31.5-0.1-desktop
```

---

### Post by ranch hand on 2009-11-14
Well, I think that you are lucky.  Everything looks alright to me.  Try these instructions;

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

You do not need to edit any files.  Just "update-grub" and "grub-install".

---

### Post by kansasnoob on 2009-11-14
> **patchido said:**
> please help me, this is kind of urgent

I realize that but I'm just now able to follow up. It'll take me a while to parse all the info.

---

### Post by kansasnoob on 2009-11-14
Actually ranch hand has this nailed unless you need specifics as far as what partition to mount and chroot.

If so I'll be glad to type out the specifics. Let me know.

Basically if you restore Ubuntu's grub2 and run "update-grub" you should be able to boot everything.

---

### Post by patchido on 2009-11-14
i dont know what to do in this step, do i have to modify anything?```
    *

      Now you need to edit the /etc/default/grub file to fit your system 

$ nano /etc/default/grub
```

---

### Post by ranch hand on 2009-11-14
As I said in my last post, I do not believe that there is anything you need to edit.  Just skip the bugger.

---

### Post by patchido on 2009-11-14
worked, now i am inside my ubuntu, but windows xp and opensuse dont appear on the grub, im not familiar into this new grub, how do i edit it?? before it was menu.lst now??

---

### Post by ranch hand on 2009-11-14
Well, this is good.  I am surprised MS is not on the list.

The firlst thing to do is;
```

sudo update-grub

```
The next thing to do is read the link in my sig.  The first 3 links in it are great, in depth information.

If that does not help we will start in again tomorrow (I will be shocked if MS is not on your menu after the above command).

---

### Post by Lateralis on 2009-11-14
Funnily enough, I had some similar problems yesterday with this.  I decided to give the latest openSUSE a go - you know, expand my horizons a bit - and ran into big difficulties with grub.  I've solved these today, but I have along the way learned a thing or two or along the way.  Specifically, I have added a couple of lines to openSUSE's (the now default) grub menu.lst which points to my Ubuntu grub as a menu option and **not** boot Ubuntu directly; I am chainloading Ubuntu through the openSUSE grub.  This is because kernel updates in Ubuntu will not appear in the openSUSE grub menu, but will in the Ubuntu grub menu and vice versa.  It adds about an extra 2 seconds to the boot time, but will mean I can use newer kernels in Ubuntu without having to manually edit openSUSE's grub menu.lst.

---

### Post by jakebros1 on 2009-11-14
im having problems with the booting from cd its not working much it used to boot from cd like week ago and now it just stopped booting from cd.on the cd is windows 7 installation im trying to install windows 7 because ubuntu is very complicated few weeks ago when i restarted my computer it would boot from cd but i wanted to try out ubuntu and now it wont boot anymore i think it just skips it and when i went to BIOS setting the booting to cd is before hard drive i dont know what problem is if u know what i should do tell me plz

---

