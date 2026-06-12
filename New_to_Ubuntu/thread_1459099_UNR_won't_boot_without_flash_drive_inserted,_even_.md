---
title: "UNR won't boot without flash drive inserted, even though it's installed."
date: 2010-04-21
forum: New to Ubuntu
---

### Post by Rick 250 on 2010-04-21
So I just installed Ubuntu Netbook Remix on my Acer Aspire One AOD250-1955, I have a few other issues, but the most important being that the grub just leads to a single horizontal blinking white line instead of booting up, that is unless I have the flash drive with the UNR image on it.

The method I used to install UNR is:
I used Unetbootin to put it on my flash drive
I then booted up into the live mode of UNR and then selected install UNR
I had previously shrunk my Windows 7 partition so I had 140GB of free space that I told the installation to install to (Upgraded the hard drive to 500GB about a month ago).
After that I rebooted the computer as instructed

Selecting Windows 7 in GRUB works just fine.  I tried the GRUB Linux Recovery Option, and that also did not help.  

It boots up just fine if I have my flash drive in, but I was under the impression that I don't constantly need the flash drive, and could UNR as a full OS, not just a live OS.

Any help is appreciated (also I would greatly like to know where to go to Modify the choices and order of the GRUB boot menu).

---

### Post by undecim on 2010-04-21
Are you given the option to boot Windows 7 all the time, or just when the flash drive is in? Also, run the [boot info script]("http://sourceforge.net/projects/bootinfoscript/") (from live USB) and post the output here.

---

### Post by SkyNet2029 on 2010-04-21
It sounds like you inadvertently installed grub to the MBR of the flash drive, instead of your installation drive. Not too hard to remedy if thats the case though. Try this:

```
sudo grub-install /dev/XXX
```

where XXX is your primary hard drive. This will install grub to the MBR of that drive to allow booting off of it instead of the thumb drive.
Next, we need to make grub see your other OS, so do:

```
sudo grub-mkconfig
```

This will show alot off output but the end result is 
Grub will be installed on the MBR of your primary drive, allowing you to boot off of that.
AND
Grub will be forced to probe for any other OS you have installed, adding a boot entry for it.

Reboot and see how cool grub can be.
Hope this helps.

Cheers!

---

### Post by Rick 250 on 2010-04-21
I tried messing around with it a bit more last night.  The grub boots every time, even if the the flash drive isn't inserted, and I can always boot to Windows 7.
Also, I did a whole bunch of updates which included a grub update, now I must have the flash drive and select the Linux that ends in 20 instead of 14.

Also, the most confusing thing about it all, is that I have to leave my flash drive as the first boot device, which means it doesn't go to the grub.  So I start the computer with the removable drive as the first boot device, but WITHOUT the flash drive inserted, then once it gets to the grub, I have to insert the flash drive, before selecting the Linux option that ends in 20, and then it boots up, and it would appear this is the only way I can get it to boot up. 
Should I try the methods above, or am I having a different problem?  I'm pretty sure the GRUB isn't installed on my flash drive, since I can only get to the GRUB when the flash drive isn't inserted.

(Also after the update the background is white and changing it under the appearance section doesn't seem to do anything.)

---

### Post by Rick 250 on 2010-04-21
ok, now I'm having trouble to get it to boot at all (UNR that is, Windows 7 still boots up fine), so I am running UNR from the flash drive, here is the Boot Info Script results:
>                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

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

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9a92f804

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    20,980,889    20,980,827  12 Compaq diagnostics
/dev/sda2    *     20,981,760   683,165,695   662,183,936   7 HPFS/NTFS
/dev/sda3         683,180,190   976,768,064   293,587,875   5 Extended
/dev/sda5         683,180,253   964,767,509   281,587,257  83 Linux
/dev/sda6         964,767,573   976,768,064    12,000,492  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4026 MB, 4026531328 bytes
124 heads, 62 sectors/track, 1022 cylinders, total 7864319 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62     7,857,135     7,857,074   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda2        480E37940E377A50                       ntfs       Windows 7                     
/dev/sda5        efdd125e-c6fa-4ef8-951f-09b005c6a64f   ext4                                     
/dev/sda6        718bab6a-730c-4ccb-ae69-23391dd53e49   swap                                     
/dev/sdb1        0AF8-F17E                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sr0         /media/U3 System         iso9660    (ro,nosuid,nodev,uhelper=devkit,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500)


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
search --no-floppy --fs-uuid --set efdd125e-c6fa-4ef8-951f-09b005c6a64f
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
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set efdd125e-c6fa-4ef8-951f-09b005c6a64f
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=efdd125e-c6fa-4ef8-951f-09b005c6a64f ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set efdd125e-c6fa-4ef8-951f-09b005c6a64f
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=efdd125e-c6fa-4ef8-951f-09b005c6a64f ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set efdd125e-c6fa-4ef8-951f-09b005c6a64f
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=efdd125e-c6fa-4ef8-951f-09b005c6a64f ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set efdd125e-c6fa-4ef8-951f-09b005c6a64f
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=efdd125e-c6fa-4ef8-951f-09b005c6a64f ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 480e37940e377a50
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
UUID=efdd125e-c6fa-4ef8-951f-09b005c6a64f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=718bab6a-730c-4ccb-ae69-23391dd53e49 none            swap    sw              0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 358.5GB: boot/grub/core.img
 358.5GB: boot/grub/grub.cfg
 350.1GB: boot/initrd.img-2.6.31-14-generic
 350.3GB: boot/initrd.img-2.6.31-20-generic
 350.1GB: boot/vmlinuz-2.6.31-14-generic
 350.1GB: boot/vmlinuz-2.6.31-20-generic
 350.3GB: initrd.img
 350.1GB: initrd.img.old
 350.1GB: vmlinuz
 350.1GB: vmlinuz.old

---

### Post by undecim on 2010-04-21
When booting from grub, highlight the UNR option that ends in 20, press "e" to edit the entry, and remove the line that starts "search". Then press ctrl+x and see if that boots.

---

### Post by Rick 250 on 2010-04-21
Ok, I did that, and it boots, half the time, I tried it several times, it boots into UNR every other time for some reason.

When it doesn't boot, the Horizontal Blinking White Bar moves from the top left of the screen to down a few lines.

---

### Post by undecim on 2010-04-21
So then I guess the "search" line must be part at least part of it.

Bear in mind that the edit will only affect the one boot, so unless you did the edit every time you tested, the "search" line comes back each time you boot.

...Strange... I figure the part of update-grub that adds the search line would be in /etc/grub.d, but I can't find it.

I'll have to do some research to find out how to make that change permanent.

---

### Post by Rick 250 on 2010-04-21
Yes, I made sure to delete the line that begins with search every time, and that's why I was very confused when it would only boot every other time.

Is there a UNR coming out next week with 10.04?  I could just wait and reinstall it with that.

---

### Post by undecim on 2010-04-21
> **Rick 250 said:**
> Yes, I made sure to delete the line that begins with search every time, and that's why I was very confused when it would only boot every other time.

Is there a UNR coming out next week with 10.04?  I could just wait and reinstall it with that.

Yes, there will be a 10.04 UNR, although I think they are going to call it Ubuntu Netbook Edition.

You are likely to have the same issue though.

Try doing the edit again, but this time, also remove 

```
recordfail=1
if [ -n ${have_grubenv} ]; then save_env recordfail; fi
set quiet=1
insmod ext2
```

and we'll see if this is an issue that can be solved with grub configuration.

---

### Post by Rick 250 on 2010-04-21
Ok, I tried deleting that as well as the search line.  I did it about 5 times, it booted up only once.

Why am I having these issues in the first place? I've never had this kind of trouble when using Ubuntu before.

---

### Post by undecim on 2010-04-21
> **Rick 250 said:**
> Ok, I tried deleting that as well as the search line.  I did it about 5 times, it booted up only once.

Why am I having these issues in the first place? I've never had this kind of trouble when using Ubuntu before.

That's exactly what I'm trying to deduce. I can't see any reason for this behavior, but we need to figure out where exactly the problem lies so that we can find what the problem is.

The problem appears to be with Grub, so perhaps reverting to Grub Legacy will solve the issue. Have a look at [http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

---

### Post by Rick 250 on 2010-04-21
Ok, so I just wiped that partition of UNR and installed it again, this time using Linux Live USB Creator 2.4.  I then did all updates and didn't allow GRUB to be updated.  I noticed this before, but it wanted me to upgrade to grub-pc 1.97 beta 4.  Could the problem be in the beta version of the grub?  

Regardless, I'm not having any issues on boot up now, it boots up every time.

---

### Post by undecim on 2010-04-21
> **Rick 250 said:**
> Ok, so I just wiped that partition of UNR and installed it again, this time using Linux Live USB Creator 2.4.  I then did all updates and didn't allow GRUB to be updated.  I noticed this before, but it wanted me to upgrade to grub-pc 1.97 beta 4.  Could the problem be in the beta version of the grub?  

Regardless, I'm not having any issues on boot up now, it boots up every time.

9.10 and later comes with 1.97 by default. Even if you upgrade from an older Ubuntu, it will leave the old Grub there.

But maybe it was a bug introduced with the new grub 1.97, or just a bad install. Either way, good to hear it's working now.

EDIT: If you don't have any more questions/problems, please mark this thread as solved.

---

### Post by Rick 250 on 2010-04-21
Well, my microphone isn't working, should I make a new thread, continue this one, or just do some searching on these forums for the solution?

---

### Post by undecim on 2010-04-21
Probably best to make a new thread. It will attract people who know about the sound system.

---

### Post by Rick 250 on 2010-04-21
Ok, thanks for all of your help.


Found what I was looking for in the Microphone problem:
[https://help.ubuntu.com/community/AspireOneAOD250#Fixing%20the%20microphone](https://help.ubuntu.com/community/AspireOneAOD250#Fixing%20the%20microphone)

---

