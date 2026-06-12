---
title: "Grub 2 Problem after upgrading BIOS version in HP Z400 Workstation"
date: 2010-05-28
forum: New to Ubuntu
---

### Post by catle on 2010-05-28
Hi all, 

I have following problems with GRUB 2 after upgrading BIOS version in HP Z400 Workstation. If you have any ideas, solutions, etc for this problem, I am really appreciated.

After upgrading BIOS, I no longer can boot into ubuntu 10.04 lucid x86-64 architecture. Everytime I try to boot, ubuntu 10.04 leads me to BusyBox v1.13.3 and tell me that it can not find root system.

```

Gave up waiting for root device. Common problems: 
 - Boot args (cat /proc/cmdline)
  - Check rootdelay= (did the system wait long enough?)
  - Check root= (did the system wait fro the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/9314dcdc-d86b-4892-806f-d3db7ea7b49d does not exist. Dropping to the shell!

```

Below is the result after running boot_info_script.sh when using ubuntu 10.04 lucid live CD.

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #8 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda1 has 
                       178770176 sectors, but according to the info from 
                       fdisk, it has 183060673 sectors.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda2 and 
                       looks at sector 205642200 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #6 for 
                       /boot/grub/menu.lst.

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda9: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   183,060,736   183,060,674   7 HPFS/NTFS
/dev/sda2    *    183,060,737   488,392,064   305,331,328   f W95 Ext d (LBA)
/dev/sda5         183,060,738   187,269,704     4,208,967  82 Linux swap / Solaris
/dev/sda6         187,269,768   229,199,354    41,929,587  83 Linux
/dev/sda7         229,199,418   271,161,134    41,961,717  83 Linux
/dev/sda8         271,161,198   320,191,514    49,030,317  83 Linux
/dev/sda9         320,191,578   488,392,064   168,200,487   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        86386A6A386A58E7                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        344ce1dc-839c-4006-9056-60f1a1b0cd71   swap                                     
/dev/sda6        4b7365ce-156a-4f07-808b-c3d3997de037   ext4                                     
/dev/sda7        4f79b6bb-d344-4b3b-b6ae-b2a629a64227   ext3                                     
/dev/sda8        9314dcdc-d86b-4892-806f-d3db7ea7b49d   ext4                                     
/dev/sda9        DB70-07A1                              vfat                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda8        /mnt                     ext4       (rw)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda6/boot/grub/grub.cfg: ===========================

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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 4b7365ce-156a-4f07-808b-c3d3997de037
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=4b7365ce-156a-4f07-808b-c3d3997de037 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 4b7365ce-156a-4f07-808b-c3d3997de037
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=4b7365ce-156a-4f07-808b-c3d3997de037 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 4b7365ce-156a-4f07-808b-c3d3997de037
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 4b7365ce-156a-4f07-808b-c3d3997de037
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 86386a6a386a58e7
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 9314dcdc-d86b-4892-806f-d3db7ea7b49d
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=9314dcdc-d86b-4892-806f-d3db7ea7b49d ro quiet splash
	initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 9314dcdc-d86b-4892-806f-d3db7ea7b49d
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=9314dcdc-d86b-4892-806f-d3db7ea7b49d ro single
	initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda6       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=344ce1dc-839c-4006-9056-60f1a1b0cd71 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 108.9GB: boot/grub/grub.cfg
 109.0GB: boot/initrd.img-2.6.32-21-generic
 108.9GB: boot/vmlinuz-2.6.32-21-generic
 109.0GB: initrd.img
 108.9GB: vmlinuz

=========================== sda8/boot/grub/grub.cfg: ===========================

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
set root='(hd0,8)'
search --no-floppy --fs-uuid --set 9314dcdc-d86b-4892-806f-d3db7ea7b49d
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
set root='(hd0,8)'
search --no-floppy --fs-uuid --set 9314dcdc-d86b-4892-806f-d3db7ea7b49d
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 9314dcdc-d86b-4892-806f-d3db7ea7b49d
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=9314dcdc-d86b-4892-806f-d3db7ea7b49d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 9314dcdc-d86b-4892-806f-d3db7ea7b49d
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=9314dcdc-d86b-4892-806f-d3db7ea7b49d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 9314dcdc-d86b-4892-806f-d3db7ea7b49d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 9314dcdc-d86b-4892-806f-d3db7ea7b49d
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 86386a6a386a58e7
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sda6)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 4b7365ce-156a-4f07-808b-c3d3997de037
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=4b7365ce-156a-4f07-808b-c3d3997de037 ro quiet splash
	initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sda6)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 4b7365ce-156a-4f07-808b-c3d3997de037
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=4b7365ce-156a-4f07-808b-c3d3997de037 ro single
	initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=9314dcdc-d86b-4892-806f-d3db7ea7b49d /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=4f79b6bb-d344-4b3b-b6ae-b2a629a64227 /home           ext3    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=344ce1dc-839c-4006-9056-60f1a1b0cd71 none            swap    sw              0       0

=================== sda8: Location of files loaded by Grub: ===================


 141.2GB: boot/grub/core.img
 141.9GB: boot/grub/grub.cfg
 142.0GB: boot/initrd.img-2.6.32-21-generic
 141.4GB: boot/vmlinuz-2.6.32-21-generic
 142.0GB: initrd.img
 141.4GB: vmlinuz

```

Note that:

I have two ubuntu lucid on /dev/sda8 and /dev/sda6. The ubuntu on /dev/sda8 is my working OS; the other on /dev/sda6 is for testing software only. In other work, /dev/sda8 is the main root partition.

The error says:

```

ALERT! /dev/disk/by-uuid/9314dcdc-d86b-4892-806f-d3db7ea7b49d does not exist. Dropping to the shell!  

```

But after reading through the boot_info_scripts.sh result, i think the above uuid of /dev/sda8 is ok. I wonder why ubuntu can not find it.

Another thing I notice when editing Ubuntu selection in Grub 2 Menu is "record fail". Does it cause the problem ?

Regards

Cat Le

---

### Post by Ozymandias_117 on 2010-05-28
Two possible solutions I've found:

Get to your GRUB menu, press 'e' to edit the line and change your UUID to just /dev/sda8 - Supposedly this will "unhang" it and will boot fine from then on. Found at: [http://forums.linuxmint.com/viewtopic.php?f=46&t=47594&p=274526#p274526]("http://forums.linuxmint.com/viewtopic.php?f=46&t=47594&p=274526#p274526")


Get to your GRUB menu, press 'e' to edit the line and add "all_generic_ide" to the end of the kernel line.

---

### Post by catle on 2010-05-28
> **Ozymandias_117 said:**
> Two possible solutions I've found:

Get to your GRUB menu, press 'e' to edit the line and change your UUID to just /dev/sda8 - Supposedly this will "unhang" it and will boot fine from then on. Found at: [http://forums.linuxmint.com/viewtopic.php?f=46&t=47594&p=274526#p274526]("http://forums.linuxmint.com/viewtopic.php?f=46&t=47594&p=274526#p274526")


Get to your GRUB menu, press 'e' to edit the line and add "all_generic_ide" to the end of the kernel line.

Thanks Ozymandias_117, I will try it tomorrow and let you know what I got.

---

### Post by kansasnoob on 2010-05-28
You have a boot flag set on sda2 which is an extended partition:

```
/dev/sda1                  63   183,060,736   183,060,674   7 HPFS/NTFS
/dev/sda2    **[COLOR="Red"]*[/COLOR]**    183,060,737   488,392,064   305,331,328   f W95 Ext d (LBA)
/dev/sda5         183,060,738   187,269,704     4,208,967  82 Linux swap / Solaris
/dev/sda6         187,269,768   229,199,354    41,929,587  83 Linux
/dev/sda7         229,199,418   271,161,134    41,961,717  83 Linux
/dev/sda8         271,161,198   320,191,514    49,030,317  83 Linux
/dev/sda9         320,191,578   488,392,064   168,200,487   b W95 FAT32

```

That's wrong. The boot flag should be on the Win XP partition "/dev/sda1" only. You can do that in the Live Desktop using Gparted.

[ATTACH]158551[/ATTACH]

[http://gparted.sourceforge.net/screens/gparted_11.png](http://gparted.sourceforge.net/screens/gparted_11.png)

After correcting that we'll reinstall grub 2, packages and all. You would be doing me a huge favor if you'd copy-n-paste the full terminal output back here whether or not this works :)

First take a brief look here just so you understand the basics of my chroot procedure:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

Also, some commands are horribly long so please copy-n-paste all commands. So, from the Live Desktop Live CD or Live USB):

```
sudo mount /dev/sda8 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```

```
dpkg-divert --local --rename --add /sbin/initctl
```

```
ln -s /bin/true /sbin/initctl
```

```
grub-install -v && aptitude show grub|head -2 && aptitude show grub-pc|head -2 && aptitude show grub-common|head -2 && aptitude show os-prober|head -2
```

```
apt-get update
```

```
apt-get install --reinstall grub-pc
```

```
grub-mkconfig -o /boot/grub/grub.cfg
```

```
grub-install /dev/sda
```

Note: if that "grub-install" commands produces errors then also run:

```
grub-install --recheck /dev/sda
```

```
exit
```

```
sudo umount /mnt/dev/pts && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt/dev && sudo umount /mnt
```

Hopefully that does it, if not I'll really need to see the full terminal output to troubleshoot things.

One other thing I should mention is that the Lucid on sda6 is missing some boot files:

> sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

What can you tell me about that Lucid?

---

### Post by catle on 2010-05-31
Thanks kansasnoob for your advice, 

I followed their advice and done them successfully in order to fix my GRUB issue. Following is the boot script information that I got.

```


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #8 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda1 has 
                       178770176 sectors, but according to the info from 
                       fdisk, it has 183060673 sectors.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda9: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   183,060,736   183,060,674   7 HPFS/NTFS
/dev/sda2         183,060,737   488,392,064   305,331,328   f W95 Ext d (LBA)
/dev/sda5         183,060,738   187,269,704     4,208,967  82 Linux swap / Solaris
/dev/sda6         187,269,768   229,199,354    41,929,587  83 Linux
/dev/sda7         229,199,418   271,161,134    41,961,717  83 Linux
/dev/sda8         271,161,198   320,191,514    49,030,317  83 Linux
/dev/sda9         320,191,578   488,392,064   168,200,487   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        86386A6A386A58E7                       ntfs                                     
/dev/sda5        344ce1dc-839c-4006-9056-60f1a1b0cd71   swap                                     
/dev/sda6        4b7365ce-156a-4f07-808b-c3d3997de037   ext4                                     
/dev/sda7        4f79b6bb-d344-4b3b-b6ae-b2a629a64227   ext3                                     
/dev/sda8        9314dcdc-d86b-4892-806f-d3db7ea7b49d   ext4                                     
/dev/sda9        DB70-07A1                              vfat                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sda2: No such file or directory

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda6/boot/grub/grub.cfg: ===========================

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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 4b7365ce-156a-4f07-808b-c3d3997de037
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=4b7365ce-156a-4f07-808b-c3d3997de037 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 4b7365ce-156a-4f07-808b-c3d3997de037
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=4b7365ce-156a-4f07-808b-c3d3997de037 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 4b7365ce-156a-4f07-808b-c3d3997de037
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 4b7365ce-156a-4f07-808b-c3d3997de037
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 86386a6a386a58e7
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 9314dcdc-d86b-4892-806f-d3db7ea7b49d
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=9314dcdc-d86b-4892-806f-d3db7ea7b49d ro quiet splash
	initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 9314dcdc-d86b-4892-806f-d3db7ea7b49d
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=9314dcdc-d86b-4892-806f-d3db7ea7b49d ro single
	initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda6       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=344ce1dc-839c-4006-9056-60f1a1b0cd71 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 108.9GB: boot/grub/grub.cfg
 109.0GB: boot/initrd.img-2.6.32-21-generic
 108.9GB: boot/vmlinuz-2.6.32-21-generic
 109.0GB: initrd.img
 108.9GB: vmlinuz

=========================== sda8/boot/grub/grub.cfg: ===========================

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
set root='(hd0,8)'
search --no-floppy --fs-uuid --set 9314dcdc-d86b-4892-806f-d3db7ea7b49d
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
set root='(hd0,8)'
search --no-floppy --fs-uuid --set 9314dcdc-d86b-4892-806f-d3db7ea7b49d
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
insmod ext2
set root='(hd0,8)'
search --no-floppy --fs-uuid --set 9314dcdc-d86b-4892-806f-d3db7ea7b49d
insmod tga
if background_image /usr/share/images/grub/Windbuchencom.tga ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 9314dcdc-d86b-4892-806f-d3db7ea7b49d
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=9314dcdc-d86b-4892-806f-d3db7ea7b49d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 9314dcdc-d86b-4892-806f-d3db7ea7b49d
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=9314dcdc-d86b-4892-806f-d3db7ea7b49d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 9314dcdc-d86b-4892-806f-d3db7ea7b49d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 9314dcdc-d86b-4892-806f-d3db7ea7b49d
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 86386a6a386a58e7
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sda6)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 4b7365ce-156a-4f07-808b-c3d3997de037
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=4b7365ce-156a-4f07-808b-c3d3997de037 ro quiet splash
	initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sda6)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 4b7365ce-156a-4f07-808b-c3d3997de037
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=4b7365ce-156a-4f07-808b-c3d3997de037 ro single
	initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=9314dcdc-d86b-4892-806f-d3db7ea7b49d /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=4f79b6bb-d344-4b3b-b6ae-b2a629a64227 /home           ext3    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=344ce1dc-839c-4006-9056-60f1a1b0cd71 none            swap    sw              0       0

=================== sda8: Location of files loaded by Grub: ===================


 141.2GB: boot/grub/core.img
 143.5GB: boot/grub/grub.cfg
 142.0GB: boot/initrd.img-2.6.32-21-generic
 141.4GB: boot/vmlinuz-2.6.32-21-generic
 142.0GB: initrd.img
 141.4GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2



=============================== StdErr Messages: ===============================

hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory


```

Although all things are done right for /dev/sda8 partition, I still have the problem when booting into /dev/sda8. Sometime it is successful. But when I restart to try going into again, the system is stuck into 

```

Gave up waiting for root device. Common problems: 
 - Boot args (cat /proc/cmdline)
  - Check rootdelay= (did the system wait long enough?)
  - Check root= (did the system wait fro the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/9314dcdc-d86b-4892-806f-d3db7ea7b49d does not exist. Dropping to the shell!

```

I am beginning to think it is not problem of the GRUB bios but the BIOS since it just happens after my bios upgrading. Moreover, the system is not stable. Sometimes it is boot successfully, but so it is not.

---

### Post by oldfred on 2010-05-31
This has some workarounds if the UUID's are correct.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)

---

