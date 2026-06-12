---
title: "Error growing Ubuntu partition with gparted via live CD"
date: 2011-01-17
forum: New to Ubuntu
---

### Post by raequin on 2011-01-17
My goal was to change which OS on my hard drive has the most disk space.  So I shrunk the Vista partition while in Ubuntu 10.04 using gparted.  Here's the result:

[IMG]http://raequin.uuuq.com/forLinkingTo/gparted01.png[/IMG]

Then I rebooted into the live CD (10.10) and ran gparted in order to move my Linux partition (/dev/sda2) into the unallocated space.  I tried "move/resize" in gparted to accomplish this.  The attempt to move it to the left and grow it resulted in error.  Here are the details:

GParted 0.6.2

Libparted 2.3

Move /dev/sda2 to the left and grow it from 13.10 GiB to 248.45 GiB  00:00:00    ( ERROR )
    	
calibrate /dev/sda2  00:00:00    ( SUCCESS )
    	
path: /dev/sda2
start: 597666195
end: 625137344
size: 27471150 (13.10 GiB)
move partition to the left and grow it from 13.10 GiB to 248.45 GiB  00:00:00    ( ERROR )
    	
old start: 597666195
old end: 625137344
old size: 27471150 (13.10 GiB)
libparted messages    ( INFO )
    	
Unable to satisfy all constraints on the partition.
========================================

I would greatly appreciate suggestions for how to complete this task.

---

### Post by Quackers on 2011-01-17
I would try booting Windows, and if it boots run a chkdsk.
It is safer to use Windows tools to manipulate Windows partitions and it is recommended to defragment at least once first. It's also much quicker.
Linux partitions should be manipulated with Linux tools.

---

### Post by raequin on 2011-01-18
I rebooted Windows.  Chkdisk ran automatically.  It returned no errors.  Vista booted without problem.  Then I rebooted using the live CD and still had the same response when trying to grow the Linux partition.

I'd like for this to succeed for the Slingbox (or rather Slingplayer) since it doesn't work as well in Linux.  If I can't get this to work, do you think I could just delete the Vista partition and make Linux take the entire HDD?  I'd hate to delete Windows and then have the same problem in GParted.  So to reiterate, first choice is to get this dual-boot system worked out but am wondering if I could even get a Linux-only system (using the entire HDD) working.  Thanks.

---

### Post by QLee on 2011-01-18
[QUOTE=raequin]I rebooted Windows.  Chkdisk ran automatically.  It returned no errors.  Vista booted without problem.  Then I rebooted using the live CD and still had the same response when trying to grow the Linux partition.
...[/QUOTE]

From your description I would say that, when you booted the live CD, it used the swap on partition 6 and thus the extended partition was in use, not allowing GParted to do the grow operation.

---

### Post by Mark Phelps on 2011-01-18
> **QLee said:**
> From your description I would say that, when you booted the live CD, it used the swap on partition 6 and thus the extended partition was in use, not allowing GParted to do the grow operation.

+1  Check the partition details in GParted.  IF it allows it, select Swapoff.  Then, you should be able to resize the containing Extended partition.

But, be advised, if you then decide to resize sda5 to take up the new space, it could take a while.  GParted is not very fast.

---

### Post by raequin on 2011-01-18
I should have mentioned it originally, but I had to select Swapoff in order to even request the move-grow operation.  So I chose that, then scheduled the move-grow, and performed the action but received the error detailed above.  Thanks.

---

### Post by plucky on 2011-01-18
> **raequin said:**
> I should have mentioned it originally, but I had to select Swapoff in order to even request the move-grow operation.  So I chose that, then scheduled the move-grow, and performed the action but received the error detailed above.  Thanks.

With swap turned off you should be able to just resize the start of the sda2 partition.This will move the un-allocated space into the extended partition.

Then you can move the start of /sda5 to the left and then grow it into the un-allocated space,which would have moved to the rear of the sda5 partition.

This all has to be done in sequence.

Good Luck

---

### Post by Quackers on 2011-01-18
In the live cd, and in gparted, are there keys showing next to sda2/sda5 etc?
Those keys may mean the partitions are mounted (not sure). Try right-clicking on sda5 and then sda2 and select "unmount" if it is available. Then try the resize.

---

### Post by raequin on 2011-01-18
> With swap turned off you should be able to just resize the start of the sda2 partition.This will move the un-allocated space into the extended partition.

That sounds like what I asked GParted to perform, but got an error.

> In the live cd, and in gparted, are there keys showing next to sda2/sda5 etc?

That image, above, is from Ubuntu booted off the HDD, not from the live CD.  When I run GParted from the live CD there are keys next to /sda2 and /sda6.  To get these to go away I choose swapoff on /sda6.  There are then no keys and I am able to request the move-grow action.  This action returns errors, though.  I appreciate your time thus far.

---

### Post by Quackers on 2011-01-18
I'm struggling to understand what "Unable to satisfy all constraints on the partition." means. 
When you are next in the live cd desktop please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by srs5694 on 2011-01-18
I've seen several reports of this error in recent days. I've seen it myself, too. My suspicion is that libparted (upon which GParted relies) is trying to adjust the partition start and/or end points to match cylinder (old-style) or 1 MiB (new-style) alignment, but in doing so it adjusts the partition in such a way that it overlaps a nearby partition. This then causes it to abort and give you that error message.

To fix it, change the alignment constraints. Old versions had a check box to align to cylinders; uncheck it. New versions have a three-way option button (align to cylinder, align to 1 MiB boundary, or don't align); change it to the other alignment value, or disable it entirely.

If that doesn't help, try leaving a small gap between partitions; that'll give it the wiggle room it needs to tweak the partition start and/or end points to its satisfaction.

---

### Post by raequin on 2011-01-18
> This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post

Here it is:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   104,101,199   104,101,137   7 HPFS/NTFS
/dev/sda2         597,666,195   625,137,344    27,471,150   5 Extended
/dev/sda5         597,666,258   623,884,274    26,218,017  83 Linux
/dev/sda6         623,884,338   625,137,344     1,253,007  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        F85E19525E190AD0                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        128f0979-48b5-44ed-a662-396cf93ff3ef   ext4                                     
/dev/sda6        1a6d0fc2-8474-4507-b78e-f627b4c98b0f   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 128f0979-48b5-44ed-a662-396cf93ff3ef
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 128f0979-48b5-44ed-a662-396cf93ff3ef
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
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 128f0979-48b5-44ed-a662-396cf93ff3ef
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=128f0979-48b5-44ed-a662-396cf93ff3ef ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 128f0979-48b5-44ed-a662-396cf93ff3ef
    echo    'Loading Linux 2.6.32-27-generic ...'
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=128f0979-48b5-44ed-a662-396cf93ff3ef ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 128f0979-48b5-44ed-a662-396cf93ff3ef
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=128f0979-48b5-44ed-a662-396cf93ff3ef ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 128f0979-48b5-44ed-a662-396cf93ff3ef
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=128f0979-48b5-44ed-a662-396cf93ff3ef ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 128f0979-48b5-44ed-a662-396cf93ff3ef
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=128f0979-48b5-44ed-a662-396cf93ff3ef ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 128f0979-48b5-44ed-a662-396cf93ff3ef
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=128f0979-48b5-44ed-a662-396cf93ff3ef ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 128f0979-48b5-44ed-a662-396cf93ff3ef
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=128f0979-48b5-44ed-a662-396cf93ff3ef ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 128f0979-48b5-44ed-a662-396cf93ff3ef
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=128f0979-48b5-44ed-a662-396cf93ff3ef ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 128f0979-48b5-44ed-a662-396cf93ff3ef
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=128f0979-48b5-44ed-a662-396cf93ff3ef ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 128f0979-48b5-44ed-a662-396cf93ff3ef
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=128f0979-48b5-44ed-a662-396cf93ff3ef ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 128f0979-48b5-44ed-a662-396cf93ff3ef
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 128f0979-48b5-44ed-a662-396cf93ff3ef
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set f85e19525e190ad0
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
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    defaults    0    0
#Entry for /dev/sda5 :
UUID=128f0979-48b5-44ed-a662-396cf93ff3ef    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sda1 :
#UUID=F85E19525E190AD0    /media/sda1    ntfs    defaults,nls=utf8,umask=0222    0    0
#Entry for /dev/sda6 :
UUID=1a6d0fc2-8474-4507-b78e-f627b4c98b0f    none    swap    sw    0    0
/dev/scd0    /media/cdrom0    udf,iso9660    user,noauto,exec,utf8    0    0



=================== sda5: Location of files loaded by Grub: ===================


 306.7GB: boot/grub/core.img
 309.2GB: boot/grub/grub.cfg
 316.5GB: boot/initrd.img-2.6.32-23-generic
 310.1GB: boot/initrd.img-2.6.32-24-generic
 311.5GB: boot/initrd.img-2.6.32-25-generic
 314.2GB: boot/initrd.img-2.6.32-26-generic
 311.2GB: boot/initrd.img-2.6.32-27-generic
 317.9GB: boot/vmlinuz-2.6.32-23-generic
 307.8GB: boot/vmlinuz-2.6.32-24-generic
 314.2GB: boot/vmlinuz-2.6.32-25-generic
 314.3GB: boot/vmlinuz-2.6.32-26-generic
 313.9GB: boot/vmlinuz-2.6.32-27-generic
 311.2GB: initrd.img
 314.2GB: initrd.img.old
 313.9GB: vmlinuz
 314.3GB: vmlinuz.old
```

---

### Post by Quackers on 2011-01-18
Thanks raequin, that looks ok.
Did you see srs5694's post - one up from your boot script?

---

### Post by raequin on 2011-01-18
Thanks all.

> To fix it, change the alignment constraints. . . . or disable it entirely.

If that doesn't help, try leaving a small gap between partitions; that'll give it the wiggle room it needs to tweak the partition start and/or end points to its satisfaction.

I had already tried leaving a small gap between partitions, it did not work.  After reading the above post I changed the alignment constraints to "none" for sda2.  The move-resize worked.  Then I performed a move-resize for sda5, this time leaving the alignment constraints set at MiB.  This, too, worked.  So here's the result (after booting into Ubuntu, not the live CD), please let me know if there are any problems with it --- things seem to work fine.

[IMG]http://raequin.uuuq.com/forLinkingTo/gparted02.png[/IMG]

---

### Post by Quackers on 2011-01-18
That looks good to me :-)
If it works, it's good!

---

### Post by srs5694 on 2011-01-19
I'll just comment that those unallocated spaces on either side of /dev/sda5 look significant in the diagram, but if you check their sizes in the listing below it, you'll see that they're quite tiny -- barely over 1 MiB each (less than two 3.5-inch floppy disks' capacity total). If you're thinking of trying to close those gaps and reclaim the space, *don't!* It might not be possible with GParted, and an attempt could take a long time and risk your data. It's just not worth the hassle for such a small amount of disk space.

---

### Post by sange666 on 2011-05-01
just  resize your sda5 and put some space on its left. atleast 1mb perhaps. it will act as a glue to the unallocated space. hope it works =)

---

