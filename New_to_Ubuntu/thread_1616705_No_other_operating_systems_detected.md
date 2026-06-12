---
title: "No other operating systems detected"
date: 2010-11-08
forum: New to Ubuntu
---

### Post by mitymows on 2010-11-08
Hey again. ;)

So I made a thread a couple of weeks ago when I had a problem with "no root file system is defined", but I ended up finding no solution, so I decided to try the Alternate CD (thanks for the suggestion Rubi1200 :)) and it ended up working, almost. Hopefully this problem will be much more simple to solve.

Anyways, in an attempt to dual-boot Windows/Ubuntu, I've gone through the Alternate CD installation process (multiple times at this point) but I seem to be messing up at the partitioning part. My main problem and reason for starting this thread is that, once I'm done with the partitioning, a window pops up basically saying no other operating systems were detected, so it should be safe to install GRUB to your master boot record (I know this isn't exactly what it says, but it's something along those lines).

It started doing this the first time I went through the Alternate CD installation. I guess I should mention that I've tried different ways of partitioning (like choosing Guided Partitioning, Manual, etc.), but it does the same thing every time. I can't even boot into Windows anymore, it just starts Ubuntu automatically, no boot menu. Which wouldn't be much of a problem if I wasn't a gamer. :(

If it helps, the pic below is what my partitions look like at the moment.

---

### Post by garvinrick4 on 2010-11-08
First boot into Ubuntu and open a terminal: and copy and paste:
```
sudo update-grub
```
```
grep menuentry /boot/grub/grub.cfg
```
First line was to use os-prober to look for other operating systems
and add to grub menu entry and grub config file.
Second line was to see if they were there. If you see Windows line reboot
and enter Windows.
Let me know.

---

### Post by mitymows on 2010-11-08
No luck. :( First one shows this:

```
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
```Second one shows this:

```
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry "Memory test (memtest86+)" {
menuentry "Memory test (memtest86+, serial console 115200)" {

```

---

### Post by garvinrick4 on 2010-11-08
Have to run this bootscript and copy and paste it to your thread. Takes a minute or so.
Go to this link and download to DESKTOP, must be on desktop. Then run the code I give you and it will put a file called RESULTS on your desktop. Copy and Paste and put in code tags if you would. 
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/") 

 ```
sudo bash ~/Desktop/boot_info_script*.sh
```

By the way your partition table looks good in gparted.

---

### Post by Hippytaff on 2010-11-08
what does
```

sudo fdisk -l

```return
or run this and post the results.txt (which should appear on the desktop)
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by mitymows on 2010-11-08
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 1769637592 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848 1,718,956,847 1,718,750,000   7 HPFS/NTFS
/dev/sda3       1,929,785,344 1,953,122,303    23,336,960   7 HPFS/NTFS
/dev/sda4       1,718,958,078 1,929,785,343   210,827,266   5 Extended
/dev/sda5       1,718,958,080 1,921,124,351   202,166,272  83 Linux
/dev/sda6       1,921,126,400 1,929,785,343     8,658,944  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        42283F60283F5261                       ntfs       SYSTEM                        
/dev/sda2        C04A33364A332894                       ntfs       HP                            
/dev/sda3        2408CF7908CF488E                       ntfs       FACTORY_IMAGE                 
/dev/sda4: PTTYPE="dos" 
/dev/sda5        f897e6c1-7221-42d5-9e7e-5556ac60348f   ext3                                     
/dev/sda6        35fe26bf-249a-4d9d-8524-643cc24dfcfa   swap                                     
/dev/sda                                                promise_fasttrack_raid_member                               
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext3       (rw,errors=remount-ro,commit=0)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set f897e6c1-7221-42d5-9e7e-5556ac60348f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set f897e6c1-7221-42d5-9e7e-5556ac60348f
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set f897e6c1-7221-42d5-9e7e-5556ac60348f
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=f897e6c1-7221-42d5-9e7e-5556ac60348f ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set f897e6c1-7221-42d5-9e7e-5556ac60348f
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=f897e6c1-7221-42d5-9e7e-5556ac60348f ro single 
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set f897e6c1-7221-42d5-9e7e-5556ac60348f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set f897e6c1-7221-42d5-9e7e-5556ac60348f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=f897e6c1-7221-42d5-9e7e-5556ac60348f /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=35fe26bf-249a-4d9d-8524-643cc24dfcfa none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 925.8GB: boot/grub/core.img
 925.7GB: boot/grub/grub.cfg
 925.7GB: boot/initrd.img-2.6.35-22-generic
 925.8GB: boot/vmlinuz-2.6.35-22-generic
 925.7GB: initrd.img
 925.8GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

---

### Post by garvinrick4 on 2010-11-08
Grub2 was installed in sda2 partition instead of sda at one time and over wrote the boot files, you have sda1 which is a dedicate boot partition. So we will go from there. Do you have your windows install dvd or recovery dvd? If not there is another way? Is fixable. If you have Windows disk use this and then we reinstall grub2 to sda next post
From
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708") 

To restore the Windows Vista/7 bootloader, you must first boot off your Windows Vista/7 installation DVD.
If you have one of the many OEM computers that didnt come with a Vista/7  installation disk, you can get the same effect with a Vista recovery  disk, which you can download for [Vista]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download") or [Win 7]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/").
When you get to the Regional settings, select your Location/Keyboard  setting then click next. On the next page you must click on "Repair your  computer."

On the next page, if it finds your Windows Vista/7 installation, make sure it is UNSELECTED before clicking next.
Then click on "Command prompt". From there, type in the folowing:

     Code:
     ```
bootrec.exe /fixboot 
```     Code:
     ```
bootrec.exe /fixmbr 
```Now close the two windows and click "Restart."

Take out your Vista/7 DVD and hopefully, you will be left with your Windows Vista/7 Bootloader.

---

### Post by garvinrick4 on 2010-11-08
To reinstall grub2 to your mbr
```
Using a Live Cd Choose Try Ubuntu and open a Terminal and copy and paste
[CODE]sudo mkdir /media/SYSTEM
``````
sudo mkdir /media/root
``````
sudo mount /dev/sda1 /media/SYSTEM
``````
sudo mount /dev/sda5 /media/root
``````
sudo grub-install --recheck --root-directory=/media/root /dev/sda
``````
sudo umount /media/SYSTEM
``````
sudo umount /media/root
```you have
made 2 directories for boot partition and /
mounted both partitions
installed grub2 into mbr (master boot record)
unmounted both partitions (umount is right)
Now reboot [/code]

---

### Post by garvinrick4 on 2010-11-08
Going out for a while will someone keep an eye on this thread in case OP has
any trouble. Do not know if he had Windows 7 recovery disk, if not I did not
leave him lilo as alternative.

---

### Post by mitymows on 2010-11-08
Well, I ended up getting Windows to boot after using the recovery disc, but after I followed the steps to reinstall grub2, I rebooted and it just went straight to Ubuntu. :-k

> **garvinrick4 said:**
> Going out for a while will someone keep an eye on this thread in case OP has
any trouble. Do not know if he had Windows 7 recovery disk, if not I did not
leave him lilo as alternative.

I actually tried lilo not long before I made this thread, but it ended up giving me an error after I ran liloconfig (it told me to run that after installing):

```
                                                                  
                                                                            
  Your /etc/fstab configuration file gives device                           
  UUID=f897e6c1-7221-42d5-9e7e-5556ac60348f as the root filesystem device.  
  This doesn't look to me like an "ordinary" block device. Either your      
  fstab is broken and you should fix it, or you are using hardware (such    
  as a RAID array) which this simple configuration program does not         
  handle.                                                                   
                                                                            
  You should either repair the situation or hand-roll your own              
  /etc/lilo.conf configuration file; you can then run /usr/sbin/liloconfig  
  again to retry the configuration process. Documentation for LILO can be   
  found in /usr/share/doc/lilo/.
```

---

### Post by arpanaut on 2010-11-08
While in Ubuntu did you run:

```
sudo update-grub
```That "should" get windows detected.

If that doesn't work rerun the boot info script from the live cd and post results.

---

### Post by mitymows on 2010-11-08
Yup, I ran sudo update-grub, but it didn't seem to work. :???:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/mapper/pdc_bcgbjjffba and looks on 
    the same drive in partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 1769637592 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
mount: /dev/sda5 already mounted or sda5 busy

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

pdc_bcgbjjffba1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

pdc_bcgbjjffba2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of 
                       pdc_bcgbjjffba2 and looks at sector 1769637592 of the 
                       same hard drive for core.img, but core.img can not be 
                       found at this location. No errors found in the Boot 
                       Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

pdc_bcgbjjffba3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD

pdc_bcgbjjffba4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

pdc_bcgbjjffba5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

pdc_bcgbjjffba6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848 1,718,956,847 1,718,750,000   7 HPFS/NTFS
/dev/sda3       1,929,785,344 1,953,122,303    23,336,960   7 HPFS/NTFS
/dev/sda4       1,718,958,078 1,929,785,343   210,827,266   5 Extended
/dev/sda5       1,718,958,080 1,921,124,351   202,166,272  83 Linux
/dev/sda6       1,921,126,400 1,929,785,343     8,658,944  82 Linux swap / Solaris


Drive: pdc_bcgbjjffba ___________________ _____________________________________________________

Disk /dev/mapper/pdc_bcgbjjffba: 1000.0 GB, 999999995904 bytes
255 heads, 63 sectors/track, 121576 cylinders, total 1953124992 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/pdc_bcgbjjffba1   *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/mapper/pdc_bcgbjjffba2            206,848 1,718,956,847 1,718,750,000   7 HPFS/NTFS
/dev/mapper/pdc_bcgbjjffba3      1,929,785,344 1,953,122,303    23,336,960   7 HPFS/NTFS
/dev/mapper/pdc_bcgbjjffba4      1,718,958,078 1,929,785,343   210,827,266   5 Extended
/dev/mapper/pdc_bcgbjjffba5      1,718,958,080 1,921,124,351   202,166,272  83 Linux
/dev/mapper/pdc_bcgbjjffba6      1,921,126,400 1,929,785,343     8,658,944  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/pdc_bcgbjjffba1 42283F60283F5261                       ntfs       SYSTEM                        
/dev/mapper/pdc_bcgbjjffba2 C04A33364A332894                       ntfs       HP                            
/dev/mapper/pdc_bcgbjjffba3 2408CF7908CF488E                       ntfs       FACTORY_IMAGE                 
/dev/mapper/pdc_bcgbjjffba5 f897e6c1-7221-42d5-9e7e-5556ac60348f   ext3                                     
/dev/mapper/pdc_bcgbjjffba6 35fe26bf-249a-4d9d-8524-643cc24dfcfa   swap                                     
/dev/mapper/pdc_bcgbjjffba: PTTYPE="dos" 
/dev/sda1        42283F60283F5261                       ntfs       SYSTEM                        
/dev/sda2        C04A33364A332894                       ntfs       HP                            
/dev/sda3        2408CF7908CF488E                       ntfs       FACTORY_IMAGE                 
/dev/sda4: PTTYPE="dos" 
/dev/sda5        f897e6c1-7221-42d5-9e7e-5556ac60348f   ext3                                     
/dev/sda6        35fe26bf-249a-4d9d-8524-643cc24dfcfa   swap                                     
/dev/sda                                                promise_fasttrack_raid_member                               
error: /dev/mapper/pdc_bcgbjjffba4: No such file or directory
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


===================== pdc_bcgbjjffba5/boot/grub/grub.cfg: =====================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set f897e6c1-7221-42d5-9e7e-5556ac60348f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set f897e6c1-7221-42d5-9e7e-5556ac60348f
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set f897e6c1-7221-42d5-9e7e-5556ac60348f
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=f897e6c1-7221-42d5-9e7e-5556ac60348f ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set f897e6c1-7221-42d5-9e7e-5556ac60348f
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=f897e6c1-7221-42d5-9e7e-5556ac60348f ro single 
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set f897e6c1-7221-42d5-9e7e-5556ac60348f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set f897e6c1-7221-42d5-9e7e-5556ac60348f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

========================== pdc_bcgbjjffba5/etc/fstab: ==========================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=f897e6c1-7221-42d5-9e7e-5556ac60348f /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=35fe26bf-249a-4d9d-8524-643cc24dfcfa none            swap    sw              0       0

============== pdc_bcgbjjffba5: Location of files loaded by Grub: ==============


 925.8GB: boot/grub/core.img
 925.8GB: boot/grub/grub.cfg
 925.7GB: boot/initrd.img-2.6.35-22-generic
 925.8GB: boot/vmlinuz-2.6.35-22-generic
 925.7GB: initrd.img
 925.8GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on pdc_bcgbjjffba4



=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
=============================== StdErr Messages: ===============================

hexdump: /dev/mapper/pdc_bcgbjjffba4: No such file or directory
hexdump: /dev/mapper/pdc_bcgbjjffba4: No such file or directory
```

---

### Post by garvinrick4 on 2010-11-08
Well back from dinner that boot script looks ill. Where are you now and what has happened
mitymows. 1 hour ago everything was busy and running is this the bootscript you got with
running the sudo update-grub. Let me know mitymows. You were at running straight into Ubuntu
without a grub-menu two posts ago. Like it only has one Operating System installed. So you use
Windows recovery disk you could boot  Windows, You put grub2 back in and you can only boot Ubuntu.
And sudo update-grub does not probe for other operating systems and put into grub config and menu.
Is that about right.

---

### Post by arpanaut on 2010-11-08
Holy Mackerel?  I have not ever seen results from the script like that.
I "think" that grub has to be removed from sda2 but with the drives in this state I don't know how to proceed.

I do hope all important data is backed up and/or recoverable.
I had a family emergency and had to step out for a couple of hours too, so I couldn't stay on top of this in a timely manner, I apologize for that.  I do hope that the OP gets back here, and this gets sorted.

---

### Post by garvinrick4 on 2010-11-08
That was his script while in Ubuntu !!! Looks like os-prober was running it's
little tail off while script was ran. Still running so looks a lot worse than is I sure
hope. os-prober had to stop running sooner or later.

---

### Post by mitymows on 2010-11-09
Exactly. I ran the recovery disc, got Windows working (still no boot menu though), then rebooted using Live CD, entered all that stuff into the terminal to reinstall grub2 to the mbr, then ran another sudo update-grub. That's basically what happened and where I'm at right now. And atm I'm on Ubuntu (not Live CD) because Windows disappeared again. :(

Any ideas on where to go from here? I'm willing to take risks. :) I don't have much to lose on Windows (been wanting to format actually) and I have recovery/backup CD's.

> **garvinrick4 said:**
> Well back from dinner that boot script looks ill. Where are you now and what has happened
mitymows. 1 hour ago everything was busy and running is this the bootscript you got with
running the sudo update-grub. Let me know mitymows. You were at running straight into Ubuntu
without a grub-menu two posts ago. Like it only has one Operating System installed. So you use
Windows recovery disk you could boot  Windows, You put grub2 back in and you can only boot Ubuntu.
And sudo update-grub does not probe for other operating systems and put into grub config and menu.
Is that about right.

---

### Post by drs305 on 2010-11-09
I haven't seen a results.txt like that, so let's try to get things back to normal. If you are on your normal Ubuntu installation, try running the following commands:

```

sudo grub-mkdevicemap
sudo update-grub
```

Rerun the script and take a look at the results.txt and see if it looks 'normal'. If not, I'd try rebooting into your normal Ubuntu installation and try it again. If the results.txt looks better, please post it.

None of this will restore your Windows but it may get us back to a known stable condition from which we can then proceed.

---

### Post by mitymows on 2010-11-09
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 1769637592 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848 1,718,956,847 1,718,750,000   7 HPFS/NTFS
/dev/sda3       1,929,785,344 1,953,122,303    23,336,960   7 HPFS/NTFS
/dev/sda4       1,718,958,078 1,929,785,343   210,827,266   5 Extended
/dev/sda5       1,718,958,080 1,921,124,351   202,166,272  83 Linux
/dev/sda6       1,921,126,400 1,929,785,343     8,658,944  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        42283F60283F5261                       ntfs       SYSTEM                        
/dev/sda2        C04A33364A332894                       ntfs       HP                            
/dev/sda3        2408CF7908CF488E                       ntfs       FACTORY_IMAGE                 
/dev/sda4: PTTYPE="dos" 
/dev/sda5        f897e6c1-7221-42d5-9e7e-5556ac60348f   ext3                                     
/dev/sda6        35fe26bf-249a-4d9d-8524-643cc24dfcfa   swap                                     
/dev/sda                                                promise_fasttrack_raid_member                               
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext3       (rw,errors=remount-ro,commit=0)
/dev/sda2        /media/HP                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set f897e6c1-7221-42d5-9e7e-5556ac60348f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set f897e6c1-7221-42d5-9e7e-5556ac60348f
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set f897e6c1-7221-42d5-9e7e-5556ac60348f
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=f897e6c1-7221-42d5-9e7e-5556ac60348f ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set f897e6c1-7221-42d5-9e7e-5556ac60348f
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=f897e6c1-7221-42d5-9e7e-5556ac60348f ro single 
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set f897e6c1-7221-42d5-9e7e-5556ac60348f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set f897e6c1-7221-42d5-9e7e-5556ac60348f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=f897e6c1-7221-42d5-9e7e-5556ac60348f /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=35fe26bf-249a-4d9d-8524-643cc24dfcfa none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 925.8GB: boot/grub/core.img
 925.8GB: boot/grub/grub.cfg
 925.7GB: boot/initrd.img-2.6.35-22-generic
 925.8GB: boot/vmlinuz-2.6.35-22-generic
 925.7GB: initrd.img
 925.8GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

---

### Post by mitymows on 2010-11-09
Alright, it seems to have been fixed. A quick overview of steps I had to take to fix the problem:

1. Ran the sudo grub-mkdevicemap and sudo update-grub commands that drs305 provided.

2. Opened the 40_custom file via the terminal:

```
gksu gedit /etc/grub.d/40_custom
```and edited the file to say:

```
#!/bin/sh
echo "Adding 40_custom." >&2
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.


menuentry "Windows 7 (loader) (on /dev/sda1)" {
        insmod ntfs
        set root='(hd0,1)'
        search --no-floppy --fs-uuid --set 42283F60283F5261
        chainloader +1
}                      
```then updated grub and rebooted, with still no boot menu (at least for me)

3. Ran grep "menuentry" /boot/grub/grub.cfg to make sure grub2 was detecting Windows.

4. Ran gksu gedit /etc/default/grub, and added a **#** in front of GRUB_HIDDEN_TIMEOUT=0, saved the file, then updated grub.

```
GRUB_DEFAULT=0
**#**GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10                      
```5. Ran gksu gedit +56 /boot/grub/grub.cfg to edit the grub.cfg and add **recordfail = 1** to this part of the file:

```
insmod gettext
**recordfail = 1**
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###                      
```rebooted, and it worked.

Hopefully this helps people in the future. Thanks for the help guys. :)

---

