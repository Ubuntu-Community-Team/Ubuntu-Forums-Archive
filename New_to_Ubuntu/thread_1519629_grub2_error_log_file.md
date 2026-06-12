---
title: "grub2 error log file?"
date: 2010-06-28
forum: New to Ubuntu
---

### Post by dbuehler on 2010-06-28
I have been experiencing an intermittent boot problem and I am not sure how to troubleshoot it. It seems to occur right after grub2 starts.  I hear a beep and the disk drive light comes on for about a second then goes off.  

How would I find out what problem grub2 is experiencing?  Is there a log file or some other method?

This is not only a new install of Ubuntu 10.4 but also a new computer build so it could be a hardware problem but everything seems to test out ok.  I also ran boot_info_script and results are below.

Any help is appreciated.

Dan

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    58,593,279    58,591,232  83 Linux
/dev/sda2          58,593,280   839,843,839   781,250,560  83 Linux
/dev/sda3         839,843,840   869,140,479    29,296,640  82 Linux swap / Solaris
/dev/sda4         869,142,526   976,771,071   107,628,546   5 Extended
/dev/sda5         869,142,528   976,771,071   107,628,544  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,953,520,064 1,953,520,002  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        be8d5289-0cfd-41e1-9da1-90c1e83fd463   ext4                                     
/dev/sda2        95ed5d4d-b505-4af9-a0bd-e1147d3f9945   ext4                                     
/dev/sda3        9ccdb36a-96b9-4c89-b3fe-718728db6233   swap                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        6e11658f-ce4d-4a8b-b86f-11317748e45b   ext4                                     
/dev/sda: PTTYPE="dos"                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    58,593,279    58,591,232  83 Linux
/dev/sda2          58,593,280   839,843,839   781,250,560  83 Linux
/dev/sda3         839,843,840   869,140,479    29,296,640  82 Linux swap / Solaris
/dev/sda4         869,142,526   976,771,071   107,628,546   5 Extended
/dev/sda5         869,142,528   976,771,071   107,628,544  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,953,520,064 1,953,520,002  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        be8d5289-0cfd-41e1-9da1-90c1e83fd463   ext4                                     
/dev/sda2        95ed5d4d-b505-4af9-a0bd-e1147d3f9945   ext4                                     
/dev/sda3        9ccdb36a-96b9-4c89-b3fe-718728db6233   swap                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        6e11658f-ce4d-4a8b-b86f-11317748e45b   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        24c33ab1-fb02-462b-b7d0-1626f052c2a7   ext4       Archive_Disk                  
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sda2        /home                    ext4       (rw)


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
search --no-floppy --fs-uuid --set be8d5289-0cfd-41e1-9da1-90c1e83fd463
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
search --no-floppy --fs-uuid --set be8d5289-0cfd-41e1-9da1-90c1e83fd463
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set be8d5289-0cfd-41e1-9da1-90c1e83fd463
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=be8d5289-0cfd-41e1-9da1-90c1e83fd463 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set be8d5289-0cfd-41e1-9da1-90c1e83fd463
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=be8d5289-0cfd-41e1-9da1-90c1e83fd463 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set be8d5289-0cfd-41e1-9da1-90c1e83fd463
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=be8d5289-0cfd-41e1-9da1-90c1e83fd463 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set be8d5289-0cfd-41e1-9da1-90c1e83fd463
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=be8d5289-0cfd-41e1-9da1-90c1e83fd463 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set be8d5289-0cfd-41e1-9da1-90c1e83fd463
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set be8d5289-0cfd-41e1-9da1-90c1e83fd463
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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
# / was on /dev/sda1 during installation
UUID=be8d5289-0cfd-41e1-9da1-90c1e83fd463 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=95ed5d4d-b505-4af9-a0bd-e1147d3f9945 /home           ext4    defaults        0       2
/dev/sda3       none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


   4.4GB: boot/grub/core.img
  17.4GB: boot/grub/grub.cfg
   4.9GB: boot/initrd.img-2.6.32-21-generic
   4.9GB: boot/initrd.img-2.6.32-22-generic
   4.8GB: boot/vmlinuz-2.6.32-21-generic
   4.9GB: boot/vmlinuz-2.6.32-22-generic
   4.9GB: initrd.img
   4.9GB: initrd.img.old
   4.9GB: vmlinuz
   4.8GB: vmlinuz.old
/dev/sdb1        24c33ab1-fb02-462b-b7d0-1626f052c2a7   ext4       Archive_Disk                  
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sda2        /home                    ext4       (rw)


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
search --no-floppy --fs-uuid --set be8d5289-0cfd-41e1-9da1-90c1e83fd463
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
search --no-floppy --fs-uuid --set be8d5289-0cfd-41e1-9da1-90c1e83fd463
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set be8d5289-0cfd-41e1-9da1-90c1e83fd463
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=be8d5289-0cfd-41e1-9da1-90c1e83fd463 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set be8d5289-0cfd-41e1-9da1-90c1e83fd463
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=be8d5289-0cfd-41e1-9da1-90c1e83fd463 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set be8d5289-0cfd-41e1-9da1-90c1e83fd463
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=be8d5289-0cfd-41e1-9da1-90c1e83fd463 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set be8d5289-0cfd-41e1-9da1-90c1e83fd463
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=be8d5289-0cfd-41e1-9da1-90c1e83fd463 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set be8d5289-0cfd-41e1-9da1-90c1e83fd463
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set be8d5289-0cfd-41e1-9da1-90c1e83fd463
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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
# / was on /dev/sda1 during installation
UUID=be8d5289-0cfd-41e1-9da1-90c1e83fd463 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=95ed5d4d-b505-4af9-a0bd-e1147d3f9945 /home           ext4    defaults        0       2
/dev/sda3       none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


   4.4GB: boot/grub/core.img
  17.4GB: boot/grub/grub.cfg
   4.9GB: boot/initrd.img-2.6.32-21-generic
   4.9GB: boot/initrd.img-2.6.32-22-generic
   4.8GB: boot/vmlinuz-2.6.32-21-generic
   4.9GB: boot/vmlinuz-2.6.32-22-generic
   4.9GB: initrd.img
   4.9GB: initrd.img.old
   4.9GB: vmlinuz
   4.8GB: vmlinuz.old
```

---

### Post by cariboo on 2010-06-28
If you start in recovery mode, does it stop at a certain point, or does it keep going?

---

### Post by bumanie on 2010-06-28
Even though it is a new computer, what you describe sounds more like a hardware issue rather than a grub 2 issue. At a guess, I would suspect a dodgy power supply with the symptoms you describe if it were a well used machine. You could make sure that everything is plugged in securely etc, it could be a poor connection or any number of things. If it was a professionally built box, get the builder to test it.
New hardware can be faulty - it doesn't sound software related, but is more likely hardware/connection related.

---

### Post by dbuehler on 2010-06-28
> If you start in recovery mode, does it stop at a certain point, or does it keep going?

Right now I just have the one OS installed so I don't normally see the grub menu. When it fails, all I see is a blinking cursor.  Guess I will try holding the shift key down whenever I boot and see if that gives me any clues. I tried that a couple of times but did not get it to fail.

---

### Post by dbuehler on 2010-06-28
> New hardware can be faulty - it doesn't sound software related, but is more likely hardware/connection related.

My thoughts too.  That is why I was asking if there was a log file to aid troubleshooting.  I'm a newbie here and just trying to figure out how to troubleshoot.

---

### Post by bumanie on 2010-06-28
You could try looking at /var/log/ - here is a [knoppmyth tutorial]("http://www.knoppmythwiki.org/index.php?page=CheckingLogFiles") re what the various log files record - hope it helps. It is sort of myth tv related, but the log files are basically the same.

---

### Post by dbuehler on 2010-06-28
Thanks bumanie,

That looks like the information I was looking for and the link was helpful.  Now, next time it happens, I know where to look for clues.

---

### Post by dbuehler on 2010-07-28
Since I last posted I have made some progress troubleshooting this problem:

1)  This is NOT a grub problem.  

2)  Also, it seems to be unique to ubuntu.  I loaded debian 5.05 and did multiple reboots with no problems.  Ubuntu boot seems to hang about 25% of the time.

2)  Booting from the grub command line (so I can see the messages) it always seems to hang about the same place.  The last messages displayed are typically something like: 
[ 4.034270] 456 pages shared
[ 4.034333] 214868 pages non shared

3)  I tried looking in /var/log but there are no files for failed boots.

Has anyone else had similar intermittent boot problems?  

The computer here is an i7-930 with 6 GB and a GEForce 9800 GTX+

Dan

---

### Post by uabassguy on 2013-04-22
> **dbuehler said:**
> Since I last posted I have made some progress troubleshooting this problem:

1)  This is NOT a grub problem.  

2)  Also, it seems to be unique to ubuntu.  I loaded debian 5.05 and did multiple reboots with no problems.  Ubuntu boot seems to hang about 25% of the time.

2)  Booting from the grub command line (so I can see the messages) it always seems to hang about the same place.  The last messages displayed are typically something like: 
[ 4.034270] 456 pages shared
[ 4.034333] 214868 pages non shared

3)  I tried looking in /var/log but there are no files for failed boots.

Has anyone else had similar intermittent boot problems?  

The computer here is an i7-930 with 6 GB and a GEForce 9800 GTX+

Dan

I am also having this issue lately. Every time I cold boot my pc, I get a blinking cursor, I turn it off then back on and it works fine. Every time it does the exact same thing. I can alternately press ctrl alt del instead of turning it off and on, but it's a very strange issue and was looking for logs myself which lead me here.

---

### Post by wildmanne39 on 2013-04-23
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

