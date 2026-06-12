---
title: "grub rescue"
date: 2011-01-27
forum: New to Ubuntu
---

### Post by PermNoob on 2011-01-27
So I have a HDD that i started moving some files onto from my pc.  It was 1 giant partition.  I then put it into my laptop and tried to install lubunutu 10.10 from CD (a cd I had used the day before to install on a friends laptop, so it works)  In doing so i modified the partion table:

~155gb ext3 containing hte original data on the drive, about 20 gig used, mounted as /usr/local
3 gb, ext4 mounted as / and formatted
1 gb swap

install seemed to go fine, whent to reboot, ejected my cd and hung at somethting like:
sending all system kill signal now, system going down for reboot
not verbatim but close.  it sat there quietly for about 10 minutes, then i decided it wasn't going down and reboooted it with the power button.  when it came back up I got

Unknown filesystem
grub rescue>

I thought somthing got botched and did a full reinstall, this time w/ the / directory formatted as ext 3, same error.  ls returns

(hd0) (hd0,msdos2) (hd0,msdos1) (fd0)

now ls hd0 returns "error: unknown filesystem"
ls (hd0,0)/
error: no such partition
ls (hd0,1)/
returns the files that should be there, a copy of an old home folder
ls (hd0,2)/
error: unknown filesystem
ls (hd0,3)/
error: no such partition

i can not return to normal mode, any help appreciated.  I am reading the grub2 wiki, but this is all pretty far past my abilities.  I am good at following directions and guessing my way thru something, but I really don't want to loose the data on that partition, so i figure it is time to ask for help.  also all the above is hand typed, not copy pasta, so any errors or oddities are probably me miss typing, so please ask for clarification.  I checked it, but i have been known to be blind as a bat.

machine in question:
toshiba satellite
WAS running ubuntu 9.04 iirc on its old harddrive, which i clearly removed for this new one, so its happy to run ubununtu.

---

### Post by wojox on 2011-01-27
This should do it:

```

grub> root (hd0,1)    (Specify where your /boot partition resides)
grub> setup (hd0)     (Install GRUB in the MBR)
grub> quit            (Exit the GRUB shell)

```

---

### Post by pkristoff on 2011-01-27
i have a similar problem so i thought i would give your solution a try.  i tried the following:

grub rescue> root (Hd0,msdos5)
Unknown command 'root'

what am i doing wrong?

---

### Post by PermNoob on 2011-01-27
grub doesn't recoginze my linux install partition (0,3 i THINK) as a filesystem.  to avoid confusion, let me be super clear

Partition A EXT3, 155gb, has some data written to it when it was slaved to another machine, want to perserve
Partition B EXT3, 3gb, Newly created for Lubuntu to live in
Partition C Swap 1 gb

currently grub recovery only can read parition A, which it lists as hd0,1.  it seems to think the other two partitoins are Msdos, or something bizzare. 
now your instructions want to add grub to partition A, which does not contain my OS, is that ok?

---

### Post by PermNoob on 2011-01-27
you wrote that as I was writing mine i guess, I am having trouble stayign logged in it seems.  anyways can you enter 
ls
and tell me what it returns?  We do seem to be in very similar boats.

---

### Post by Quackers on 2011-01-28
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by PermNoob on 2011-01-28
just a reminder I am installing lubunutu, but i am not sure that makes any difference whatsoever in the grub bit.  I just like to be thorough in my sitrep

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for (,msdos2)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   304,763,734   304,763,672  83 Linux
/dev/sda2    *    304,764,928   310,626,303     5,861,376  83 Linux
/dev/sda3         310,628,350   312,580,095     1,951,746   5 Extended
/dev/sda5         310,628,352   312,580,095     1,951,744  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        696067e8-ae6f-450f-870a-641c6b7bf06d   ext3                                     
/dev/sda2        2d49c4f6-04d2-4db9-92a7-680a63faac96   ext3                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        488fb24f-f9c7-4162-9629-b0b8c97c7ee3   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 2d49c4f6-04d2-4db9-92a7-680a63faac96
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 2d49c4f6-04d2-4db9-92a7-680a63faac96
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
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 2d49c4f6-04d2-4db9-92a7-680a63faac96
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=2d49c4f6-04d2-4db9-92a7-680a63faac96 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 2d49c4f6-04d2-4db9-92a7-680a63faac96
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=2d49c4f6-04d2-4db9-92a7-680a63faac96 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 2d49c4f6-04d2-4db9-92a7-680a63faac96
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 2d49c4f6-04d2-4db9-92a7-680a63faac96
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda2       /               ext3    errors=remount-ro 0       1
# /usr/local was on /dev/sda1 during installation
UUID=696067e8-ae6f-450f-870a-641c6b7bf06d /usr/local      ext3    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=488fb24f-f9c7-4162-9629-b0b8c97c7ee3 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


 157.2GB: boot/grub/core.img
 157.2GB: boot/grub/grub.cfg
 157.2GB: boot/initrd.img-2.6.35-22-generic
 157.2GB: boot/vmlinuz-2.6.35-22-generic
 157.2GB: initrd.img
 157.2GB: vmlinuz
```

---

### Post by Quackers on 2011-01-28
You've installed Lubuntu to sda2. I don't know how much space Lubuntu needs, but 3GB doesn't sound enough, though I may be wrong. What's in sda1?

---

### Post by PermNoob on 2011-01-29
sda1 contains data that was saved on there prior to making this a boot drive.  lubuntu is pretty small. its not listed on thier site but i recall the installer reccomending 3, i could give it more no problem though, but shouldn't it have complained?

---

### Post by PermNoob on 2011-01-29
oh and as an FYI, i had to rename the script from .download to .sh. or .somethingNotSh

obvious to me after a few seconds, maybe not to other people.

---

### Post by PermNoob on 2011-01-29
a quick check shows 1.5 gig used in SDA2, according to the partitioner in the installer.  I was gonna reinstall with more drive space but that doesn't seem to b e the issue.

---

### Post by PermNoob on 2011-01-31
the installer splash screen recommends a minimum of 3.2 gigs free, but i think that includes swap space considerations.  however i reinstalled with
3.5 gig for os
1 gig for swap

and same errors exist.  Any help would be appreciated.

---

### Post by PermNoob on 2011-02-04
bump for grub justice

---

