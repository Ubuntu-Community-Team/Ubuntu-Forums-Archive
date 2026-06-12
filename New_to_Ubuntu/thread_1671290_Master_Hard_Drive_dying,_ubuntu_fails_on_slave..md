---
title: "Master Hard Drive dying, ubuntu fails on slave."
date: 2011-01-19
forum: New to Ubuntu
---

### Post by briansbrain on 2011-01-19
So i am a new user to Ubuntu and the Linux world.  I am using a Toshiba laptop with two hard drive: a 100gb Hitachi Primary, and a 120gb Toshiba secondary.  The Hitachi Hard drive started failing with bad sectors multiplying daily.  I downloaded the hitachi repair utility and ran it but it errors out when trying to fix the bad sectors or erase the drive, saying device failure.  I tried DBan to zero out the whole drive possibly rewriting the bad sectors, and that errors out.  I can install ubuntu 10.10 from a live cd on the hitachi but it has hangups and freezes and errors when you try to move files or update or make any change.  Ive got the important stuff backed up so no worries there.  The Disk Utility's Smart Data says the Hitachi has "imminent drive failure", but the secondary Toshiba drive is fine.  So now i tried installing ubuntu 10.10 from the live cd onto my secondary.  The install goes perfect (with or without the updates while installing), i restart and it tries to boot but just has a blinking cursor.  No command lines or anything.  I touch the power button and it shuts off.   I even used F8 to boot from the Toshiba specifically and same thing.  So now im running Ubuntu 10.04 from a live USB and its stable but not ideal.  Another option i have been considering is installing Ubuntu to my 1TB external drive and running it from there.  So my questions are:
1. how do i successfully run Ubuntu from a secondary? 2. what should i do with the primary drive?  3.  Should i just install to an external and give up on the laptop hard drives?

Im pretty sure laptop hard drives are not replaceable because they are integrated with the motherboard.  I have no fund or options to buy a new computer for a while, so i need to come up with a comfortable temporary situation.  Thanks for the help in advance!

---

### Post by sandyd on 2011-01-19
> **briansbrain said:**
> So i am a new user to Ubuntu and the Linux world.  I am using a Toshiba laptop with two hard drive: a 100gb Hitachi Primary, and a 120gb Toshiba secondary.  The Hitachi Hard drive started failing with bad sectors multiplying daily.  I downloaded the hitachi repair utility and ran it but it errors out when trying to fix the bad sectors or erase the drive, saying device failure.  I tried DBan to zero out the whole drive possibly rewriting the bad sectors, and that errors out.  I can install ubuntu 10.10 from a live cd on the hitachi but it has hangups and freezes and errors when you try to move files or update or make any change.  Ive got the important stuff backed up so no worries there.  The Disk Utility's Smart Data says the Hitachi has "imminent drive failure", but the secondary Toshiba drive is fine.  So now i tried installing ubuntu 10.10 from the live cd onto my secondary.  The install goes perfect (with or without the updates while installing), i restart and it tries to boot but just has a blinking cursor.  No command lines or anything.  I touch the power button and it shuts off.   I even used F8 to boot from the Toshiba specifically and same thing.  So now im running Ubuntu 10.04 from a live USB and its stable but not ideal.  Another option i have been considering is installing Ubuntu to my 1TB external drive and running it from there.  So my questions are:
1. how do i successfully run Ubuntu from a secondary? 2. what should i do with the primary drive?  3.  Should i just install to an external and give up on the laptop hard drives?

**Im pretty sure laptop hard drives are not replaceable** because they are integrated with the motherboard.  I have no fund or options to buy a new computer for a while, so i need to come up with a comfortable temporary situation.  Thanks for the help in advance!
A lot are.
whats your toshiba model?
If you want, I can drag up HD replacement instructions for u

---

### Post by srs5694 on 2011-01-19
> **briansbrain said:**
> Im pretty sure laptop hard drives are not replaceable because they are integrated with the motherboard.  I have no fund or options to buy a new computer for a while, so i need to come up with a comfortable temporary situation.  Thanks for the help in advance!

Hard disks are never integrated with the motherboard; they're always separate. How easy they are to replace depends on the computer. The last couple of laptops I've owned have easily-replaced hard disks; just remove a panel on the bottom of the computer, pull out the drive, slide in a new one, and replace the panel. I don't know if this type of setup is universal these days, though. An older laptop of mine requires more thorough disassembly to get at the hard disk, but I managed to replace the hard disk some time ago.

My suspicion is that you've got a boot loader problem with your installation to the good drive. This is probably unrelated to the bad disk, but it's conceivable the bad disk is involved (say, if you put the boot loader on the bad disk's MBR and if that sector happens to be one that's failing). It's likely you can get the computer to boot using [Super GRUB 2 Disk,](http://www.supergrubdisk.org) so give it a try. You might also get more help from forum users by running the [Boot Info Script](http://sourceforge.net/projects/bootinfoscript/) and posting the results file back here. (Be sure to do so between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings to preserve columnar data in the output.)

---

### Post by briansbrain on 2011-01-19
oh i thought they werent.  i have a toshiba satellite A135-S4487.

---

### Post by briansbrain on 2011-01-19
Here is the result of the boot info script:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks at sector 100944920 
    of the same hard drive for core.img, but core.img can not be found at this 
    location.
 => No boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdd

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System



Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   224,827,391   224,825,344  83 Linux
/dev/sdb2         224,829,438   234,440,703     9,611,266   5 Extended
/dev/sdb5         224,829,440   234,440,703     9,611,264  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63 1,953,520,064 1,953,520,002   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda: PTTYPE="dos" 
/dev/sdb1        8dd6f2df-4f60-4e86-937b-a5be2bf36761   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        e8209255-5c77-4f51-8a27-fe0e133b6fab   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc         50D3-9539                              vfat       DS PRO                        
/dev/sdd1        8525-1B52                              vfat       My Book                       
/dev/sdd: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdc         /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/8dd6f2df-4f60-4e86-937b-a5be2bf36761 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdd1        /media/My Book           vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 8dd6f2df-4f60-4e86-937b-a5be2bf36761
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 8dd6f2df-4f60-4e86-937b-a5be2bf36761
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
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 8dd6f2df-4f60-4e86-937b-a5be2bf36761
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=8dd6f2df-4f60-4e86-937b-a5be2bf36761 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 8dd6f2df-4f60-4e86-937b-a5be2bf36761
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=8dd6f2df-4f60-4e86-937b-a5be2bf36761 ro single 
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
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 8dd6f2df-4f60-4e86-937b-a5be2bf36761
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 8dd6f2df-4f60-4e86-937b-a5be2bf36761
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=8dd6f2df-4f60-4e86-937b-a5be2bf36761 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=e8209255-5c77-4f51-8a27-fe0e133b6fab none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


  51.6GB: boot/grub/core.img
  21.7GB: boot/grub/grub.cfg
    .8GB: boot/initrd.img-2.6.35-22-generic
  51.6GB: boot/vmlinuz-2.6.35-22-generic
    .8GB: initrd.img
  51.6GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  8c 8c 8c 8c 8c 8c 8c 8c  8c 8c 8c 8c 8c 8c 8c 8c  |................|
*
000001b0  8c 8c 8c 8c 8c 8c 8c 8c  8c 8c 8c 8c 8c 8c 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 a8 92 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

---

### Post by srs5694 on 2011-01-20
It looks as if GRUB is installed to the MBR of /dev/sda (your bad drive), but it's trying to continue the boot off of that drive. This is an error and is causing your boot to fail, but the error is unrelated to the failing hard disk (except of course for the fact that GRUB is on the MBR of that drive).

You might be able to get your computer to boot normally with Super GRUB 2 Disk, as I noted in my last post. Try it. If it works, type this command after you've booted:

```

sudo grub-install /dev/sdb

```

You should then be able to use your BIOS configuration tool to set the boot drive to /dev/sdb (your good disk; it won't be identified as "/dev/sdb" in the BIOS), effectively removing /dev/sda from the equation so that if it completely fails you'll still be able to boot. With any luck that'll restore your system to bootability.

That said, it's possible I've missed some other problem in your GRUB configuration. If you have further problems, post back with details.

---

### Post by briansbrain on 2011-01-20
well i looked into supergrub2 but since it didnt fix anything i opted for Rescutux.  It booted and then from the live debian os it put the grub on sdb1 (the good drive with ubuntu 10.10).  then it booted fine into ubuntu from the secondary drive.  once i was inside, i was able to use the disc utility to format the failing drive and put a ext4 file system on it.  so now it mounts under new volume and is blank.  the bad sectors are still there though.  i found out that my failing hitachi hard drive is replaceable, so i may do that in the future.  for now ive got 90gb free and multiple externals for storage.  
my question is will this damaged drive mess with me anymore, or just sit there for storage until it dies?  if its going to be a problem should i just disconnect it from the bios or something so that it doesnt power up or spin?
and thanks for everyones help.  im amazed at how awesome this os is and the people who use these forums are really helpful!

---

### Post by srs5694 on 2011-01-20
Your damaged drive ***is not reliable!*** Drives with bad sectors sometimes produce more and more bad sectors over time, which can damage your data. Furthermore, it's possible that the drive will produce filesystem corruption that will cause the computer to act strangely, even if you barely use it.

My recommendation is to pretend that the bad drive doesn't exist. Use your good internal drive exclusively (or in conjunction with any external storage you've got) until you can replace the bad drive.

---

### Post by Jerry N on 2011-01-20
Remove the bad drive and erase whatever is on it with a powerful magnet, blow torch, or sledge hammer.  Then dumpster it (or take it to your nearest recycling center if you prefer).  That way it won't cause you any more trouble.  You might then want to re-install Ubuntu on your remaining drive. 

I wish I could put two drives in my laptop computer.

Jerry

---

