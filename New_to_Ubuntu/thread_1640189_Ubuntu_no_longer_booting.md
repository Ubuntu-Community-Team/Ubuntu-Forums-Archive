---
title: "Ubuntu no longer booting"
date: 2010-12-07
forum: New to Ubuntu
---

### Post by MetalMikey666 on 2010-12-07
Hi guys,

Ever since doing the last ubuntu update (a few days ago) I am experiencing the following problem;

* turn on PC
* select Ubuntu from boot manager screen
* computer restarts

I can boot to vista okay if i select it from the menu, it's just ubuntu that's the problem. I'm a bit of a linux newbie, here's an attempt to roughly explain my setup;

I originally instaled using WUBI, dual booting vista and ubuntu. I had boot manager problems after an update a few weeks ago, and this helped me with that problem;

[http://ubuntuforums.org/showthread.php?t=1549194](http://ubuntuforums.org/showthread.php?t=1549194)

Whether that is at all relevant i have no idea. Computer has been absolutely fine for a few weeks, and now this! Other people seem to have been having this problem too;

[http://ubuntuforums.org/showthread.php?t=1629755](http://ubuntuforums.org/showthread.php?t=1629755)

someone in that thread reccomended I start my own, so here it is. If anyone can help it'd be greatly appreciated. I'm going to keep searching anyway.

Thanks,

-Mikey

---

### Post by karthick87 on 2010-12-07
Can you post the results of [[COLOR=DarkOrange]**bootscript**[/COLOR]]("http://bootinfoscript.sourceforge.net/")

---

### Post by MetalMikey666 on 2010-12-07
Thanks for replying (am completely new to this). I booted from a live CD (as can't boot normally any more) and here's what the bootscript came back with;


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #256 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /wubildr.mbr /wubildr

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sdb1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   952,188,614   952,188,552   7 HPFS/NTFS
/dev/sda4         952,188,615   976,768,064    24,579,450   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   976,768,064   976,768,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       6ec33ed0-34b6-4070-bec8-53fa53e367cb   ext4                                     
/dev/sda1        5AF87154F8712EFF                       ntfs       HP                            
/dev/sda4        949CA48C9CA46A86                       ntfs       FACTORY_IMAGE                 
/dev/sda: PTTYPE="dos" 
/dev/sdb1        220E51610E512ED3                       ntfs       HP2                           
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


======================== sdb1/Wubi/boot/grub/grub.cfg: ========================

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
insmod ntfs
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 220e51610e512ed3
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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
insmod ntfs
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 220e51610e512ed3
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-26-generic" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 220e51610e512ed3
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-26-generic root=/dev/sdb1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, Linux 2.6.32-26-generic (recovery mode)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 220e51610e512ed3
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-26-generic root=/dev/sdb1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, Linux 2.6.32-25-generic" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 220e51610e512ed3
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sdb1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, Linux 2.6.32-25-generic (recovery mode)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 220e51610e512ed3
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sdb1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 220e51610e512ed3
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sdb1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic (recovery mode)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 220e51610e512ed3
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sdb1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 5af87154f8712eff
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda4)" {
    insmod ntfs
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 949ca48c9ca46a86
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sdb1/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sdb1/Wubi: Location of files loaded by Grub: =================


   8.9GB: boot/grub/core.img
   3.3GB: boot/grub/grub.cfg
   4.1GB: boot/initrd.img-2.6.32-24-generic
   6.0GB: boot/initrd.img-2.6.32-25-generic
   5.1GB: boot/initrd.img-2.6.32-26-generic
   3.6GB: boot/vmlinuz-2.6.32-24-generic
   9.6GB: boot/vmlinuz-2.6.32-25-generic
   9.7GB: boot/vmlinuz-2.6.32-26-generic
   5.1GB: initrd.img
   6.0GB: initrd.img.old
   9.7GB: vmlinuz
   9.6GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

I hope this makes sense to someone because it's total double dutch to me!

---

### Post by bcbc on 2010-12-07
Have you tried [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198) (Problem #2, Solution #1)?

It looks (from your grub.cfg) that you are suffering this problem. Change /dev/sda1 to /dev/sdb1 (as that's where your Ubuntu is installed).

There is a permanent fix further down in that thread (cleaning up /boot/grub). Also, avoid updates to packages grub-pc and grub-common in the future.

---

### Post by MetalMikey666 on 2010-12-07
Thank you that worked, I'm now back in Ubuntu! Will look into the permanent fix at the weekend. 

Out of curiosity: Every problem i get with this install seems to be related to the fact that it's been a WUBI install - would you reccomend just doing the standard install instead (the only reason i went with wubi was due to fear of the unknown)

---

### Post by bcbc on 2010-12-07
> **MetalMikey666 said:**
> Thank you that worked, I'm now back in Ubuntu! Will look into the permanent fix at the weekend. 

Out of curiosity: Every problem i get with this install seems to be related to the fact that it's been a WUBI install - would you reccomend just doing the standard install instead (the only reason i went with wubi was due to fear of the unknown)

If you are comfortable partitioning your drive and having grub2 as your main bootloader, then yes it's preferable to Wubi. Wubi is more to introduce users who have limited Windows-only experience and may not understand bootloaders and partitions (which is extremely ironic given how screwed up Wubi is right now thanks to poorly tested grub updates)](*,). So, yeah, not much argument for Wubi right now ;)

---

### Post by MetalMikey666 on 2010-12-07
lol, thanks man. I've just implemented your permenant fix too and managed to boot back into ubuntu. Come to think about it, it was a grub update that stuffed it up last time too, so i guess it's best that those are locked.

Yes: will stick with wubi. I pretty much only use ubuntu for general web etc.., rails dev and android dev so still need windows for other stuff (games and visual studio basically).

Thank you so much for the help!

-Mikey

---

### Post by heroface101 on 2010-12-07
hi  i know this threads solved  but im kinda having a similar issue  and im really new to Linux 
 i just tryed to login to Ubuntu 10.10  and in the boot menu it  just says ' error: no suitable mode found'
 then goes blank  and goes back to the boot menu.

it was working fine before the last update but i think i might have shutdown   while it was still updating
im running Ubuntu of a usb stick from the boot menu at the minute but   how do i sort it out ?

---

### Post by bcbc on 2010-12-07
> **heroface101 said:**
> hi  i know this threads solved  but im kinda having a similar issue  and im really new to Linux 
 i just tryed to login to Ubuntu 10.10  and in the boot menu it  just says ' error: no suitable mode found'
 then goes blank  and goes back to the boot menu.

it was working fine before the last update but i think i might have shutdown   while it was still updating
im running Ubuntu of a usb stick from the boot menu at the minute but   how do i sort it out ?

This will probably work for you as well [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198) (Problem #2, Solution #1). Permanent fix afterwards.

You just need to figure out which partition your root.disk is on to make it work.

---

### Post by heroface101 on 2010-12-08
ok thanks man, i dont really have any idea how to do that, but ill give it a go lol.

is a live cd the same as a liveusb becuase thats all i have ?
also how do i find  out which partition your root.disk is on?
sorry im like a total noob

---

### Post by bcbc on 2010-12-08
> **heroface101 said:**
> ok thanks man, i dont really have any idea how to do that, but ill give it a go lol.

is a live cd the same as a liveusb becuase thats all i have ?
also how do i find  out which partition your root.disk is on?
sorry im like a total noob

Run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/").Right near the top you'll see something like:
> **sda2**: _________________________________________________________________________

    File system:       ntfs
...
    Boot files/dirs:   /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

---

### Post by heroface101 on 2010-12-08
i didnt understand/ couldnt  get the fixes to work on  [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198) 
so i just took my laptop to the tech guys my  uni and showed them the fixes on there and they sorted it form me but thanks for the help 
cheerrss

---

