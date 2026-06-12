---
title: "dual boot with 7: windows does not boot"
date: 2010-11-30
forum: New to Ubuntu
---

### Post by nuddernuby on 2010-11-30
LG T380
Windows Home Premium
Loaded Ubuntu 10.04.1
On boot-up: Menu shows OK
Select Ubuntu -> works fine
Select Windows 7 -> nothing happens - boot menu stays up
(Had to reload windows - lost everything - don't want to do that again)
Anybody have any ideas?
Tx

---

### Post by nuddernuby on 2010-11-30
And here is the output of Boot Info script:
(attached)

---

### Post by nuddernuby on 2010-11-30
Correction: Please ignore Results.txt and consider Results1.txt.
Thank you

---

### Post by spydeyrch on 2010-11-30
You didn't have to lose everything. Sorry to hear that you did though.

How are you setting up your dual boot? Single HDD, multiple partition? Multi HDD single partition? Is it windows 7 or windows vista (you didn't mention which :) )

Depending on how you are setting it up, there are different steps.

-Spydey

---

### Post by nuddernuby on 2010-11-30
Sorry, Windows 7 Home Premium
One 500GB hard disc
Also use external 500GB for backup, but this is incidental
Multiple partitions as per Results1.txt
I would be very grateful to have the boot menu work properly, but cannot afford to go through the reload windows procedure again
I need to find out how to do it right this time
Tx

---

### Post by Quackers on 2010-11-30
Your boot script in CODE tags!
```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

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

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63     3,148,739     3,148,677  12 Compaq diagnostics
/dev/sda2    *      3,148,740   796,887,039   793,738,300   7 HPFS/NTFS
/dev/sda3         796,887,040   828,102,655    31,215,616  12 Compaq diagnostics
/dev/sda4         828,104,702   976,771,071   148,666,370   5 Extended
/dev/sda5         828,104,704   933,801,969   105,697,266  83 Linux
/dev/sda6         933,801,984   972,863,487    39,061,504  83 Linux
/dev/sda7         972,867,584   976,771,071     3,903,488  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        7AFE9526FE94DBA7                       ntfs       RECOVERY                      
/dev/sda2        44F297DCF297D092                       ntfs                                     
/dev/sda3        32AAB255AAB21577                       ntfs       LG_RECOVERY                   
/dev/sda4: PTTYPE="dos" 
/dev/sda5        f1a90d88-22dc-4a03-a808-ab5492c9e8bf   ext4                                     
/dev/sda6        97b6e6f2-e9aa-4246-839b-f81ba5fc2ffe   ext4                                     
/dev/sda7        45b72879-7cab-496b-85ca-c916c78acc49   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sda6        /home                    ext4       (rw)


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
search --no-floppy --fs-uuid --set f1a90d88-22dc-4a03-a808-ab5492c9e8bf
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
search --no-floppy --fs-uuid --set f1a90d88-22dc-4a03-a808-ab5492c9e8bf
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
menuentry 'Ubuntu, with Linux 2.6.32-26-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set f1a90d88-22dc-4a03-a808-ab5492c9e8bf
	linux	/boot/vmlinuz-2.6.32-26-generic-pae root=UUID=f1a90d88-22dc-4a03-a808-ab5492c9e8bf ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-26-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set f1a90d88-22dc-4a03-a808-ab5492c9e8bf
	echo	'Loading Linux 2.6.32-26-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-26-generic-pae root=UUID=f1a90d88-22dc-4a03-a808-ab5492c9e8bf ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-26-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set f1a90d88-22dc-4a03-a808-ab5492c9e8bf
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set f1a90d88-22dc-4a03-a808-ab5492c9e8bf
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 7afe9526fe94dba7
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 44f297dcf297d092
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=f1a90d88-22dc-4a03-a808-ab5492c9e8bf /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=97b6e6f2-e9aa-4246-839b-f81ba5fc2ffe /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=45b72879-7cab-496b-85ca-c916c78acc49 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 462.7GB: boot/grub/core.img
 430.6GB: boot/grub/grub.cfg
 462.8GB: boot/initrd.img-2.6.32-26-generic-pae
 462.7GB: boot/vmlinuz-2.6.32-26-generic-pae
 462.8GB: initrd.img
 462.7GB: vmlinuz
```

---

### Post by Quackers on 2010-11-30
Grub is not installed to the mbr of sda - Syslinux is
```
 => Syslinux is installed in the MBR of /dev/sda
```

---

### Post by nuddernuby on 2010-11-30
Is this better?

```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

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

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63     3,148,739     3,148,677  12 Compaq diagnostics
/dev/sda2    *      3,148,740   796,887,039   793,738,300   7 HPFS/NTFS
/dev/sda3         796,887,040   828,102,655    31,215,616  12 Compaq diagnostics
/dev/sda4         828,104,702   976,771,071   148,666,370   5 Extended
/dev/sda5         828,104,704   933,801,969   105,697,266  83 Linux
/dev/sda6         933,801,984   972,863,487    39,061,504  83 Linux
/dev/sda7         972,867,584   976,771,071     3,903,488  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        7AFE9526FE94DBA7                       ntfs       RECOVERY                      
/dev/sda2        44F297DCF297D092                       ntfs                                     
/dev/sda3        32AAB255AAB21577                       ntfs       LG_RECOVERY                   
/dev/sda4: PTTYPE="dos" 
/dev/sda5        f1a90d88-22dc-4a03-a808-ab5492c9e8bf   ext4                                     
/dev/sda6        97b6e6f2-e9aa-4246-839b-f81ba5fc2ffe   ext4                                     
/dev/sda7        45b72879-7cab-496b-85ca-c916c78acc49   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sda6        /home                    ext4       (rw)


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
search --no-floppy --fs-uuid --set f1a90d88-22dc-4a03-a808-ab5492c9e8bf
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
search --no-floppy --fs-uuid --set f1a90d88-22dc-4a03-a808-ab5492c9e8bf
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
menuentry 'Ubuntu, with Linux 2.6.32-26-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set f1a90d88-22dc-4a03-a808-ab5492c9e8bf
	linux	/boot/vmlinuz-2.6.32-26-generic-pae root=UUID=f1a90d88-22dc-4a03-a808-ab5492c9e8bf ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-26-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set f1a90d88-22dc-4a03-a808-ab5492c9e8bf
	echo	'Loading Linux 2.6.32-26-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-26-generic-pae root=UUID=f1a90d88-22dc-4a03-a808-ab5492c9e8bf ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-26-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set f1a90d88-22dc-4a03-a808-ab5492c9e8bf
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set f1a90d88-22dc-4a03-a808-ab5492c9e8bf
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 7afe9526fe94dba7
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 44f297dcf297d092
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=f1a90d88-22dc-4a03-a808-ab5492c9e8bf /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=97b6e6f2-e9aa-4246-839b-f81ba5fc2ffe /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=45b72879-7cab-496b-85ca-c916c78acc49 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 462.7GB: boot/grub/core.img
 430.6GB: boot/grub/grub.cfg
 462.8GB: boot/initrd.img-2.6.32-26-generic-pae
 462.7GB: boot/vmlinuz-2.6.32-26-generic-pae
 462.8GB: initrd.img
 462.7GB: vmlinuz
```

---

### Post by nuddernuby on 2010-11-30
So, I had Grub2 installed to sda2
No idea what syslinux is doing where it is
Presumably, when windows was reloaded it took out Grub2
Before I try this again, I would like to be better prepared for when things go wrong
Your advice appreciated

---

### Post by Quackers on 2010-11-30
> **nuddernuby said:**
> So, I had Grub2 installed to sda2
No idea what syslinux is doing where it is
Presumably, when windows was reloaded it took out Grub2
Before I try this again, I would like to be better prepared for when things go wrong
Your advice appreciated

I don't see grub2 in sda2!!!
If Windows took out grub Windows should be installed in the mbr of sda. It isn't, Syslinux is!

I am unclear here.
What are you getting when you cold boot the system?
What screen appears, with what options? 
Does the boot screen (if you still get one) have a heading at the top of the screen?

---

### Post by nolag on 2010-11-30
Did you restore windows?  If so what can you boot to right now?
 
If you can only boot to windows, use the ubuntu disk and follow [http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7](http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7).

---

### Post by nuddernuby on 2010-11-30
At the moment (after having reloaded windows) the unit boots straight into windows.
To get into Ubuntu (where I am now) I use a Grub2 disc to boot.
When the dual boot was in place, everything looked quite normal - although Unfortunately, I can't tell what the heading of the boot menu page was.

---

### Post by Quackers on 2010-11-30
Please boot from the Ubuntu Live cd/usb and choose "try ubuntu" then ensure that you are connected to the internet. 
Then open up a terminal and copy/paste these lines into the terminal and press enter after each line.
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
then reboot. 
Please report what happens on reboot.

---

### Post by nuddernuby on 2010-11-30
Did this. On reboot got a black screen with:

error: file not found
grub rescue >

Booted up with Grub2 disc again to be able to carry on this conversation..

---

### Post by Quackers on 2010-11-30
Did you select "try ubuntu" while booting from the live cd? Sorry I edited my previous post.
If you did will you please run the bootscript again and post in code tags. Thanks.

---

### Post by c00lwaterz on 2010-11-30
i think you have problem with grub (boot loader for ubuntu that you can select windows and other options), but then you have boot loader for your windows 7. as for my experience you have boot loader for windows 7 and grub when you install ubuntu (boot loader for ubuntu)

maybe you accidentaly delete the boot loader for windows. did you try to download boot disk for windows 7? if not then try this [http://www.bootdisk.com/bootdisk.htm]("http://www.bootdisk.com/bootdisk.htm") , it would be better if you can get windows 7 boot disk but if not then you can use xp boot disk and give it a try. 

hope this help ;)

ps. i use boot disk before when there is floppy. I did not try using cd's. you can get some tutorial over the internet using cd as boot disk or usb.

---

### Post by nuddernuby on 2010-11-30
As i said, I booted up with a Grub2 disc
here is the bootscript result again:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

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

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63     3,148,739     3,148,677  12 Compaq diagnostics
/dev/sda2    *      3,148,740   796,887,039   793,738,300   7 HPFS/NTFS
/dev/sda3         796,887,040   828,102,655    31,215,616  12 Compaq diagnostics
/dev/sda4         828,104,702   976,771,071   148,666,370   5 Extended
/dev/sda5         828,104,704   933,801,969   105,697,266  83 Linux
/dev/sda6         933,801,984   972,863,487    39,061,504  83 Linux
/dev/sda7         972,867,584   976,771,071     3,903,488  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        7AFE9526FE94DBA7                       ntfs       RECOVERY                      
/dev/sda2        44F297DCF297D092                       ntfs                                     
/dev/sda3        32AAB255AAB21577                       ntfs       LG_RECOVERY                   
/dev/sda4: PTTYPE="dos" 
/dev/sda5        f1a90d88-22dc-4a03-a808-ab5492c9e8bf   ext4                                     
/dev/sda6        97b6e6f2-e9aa-4246-839b-f81ba5fc2ffe   ext4                                     
/dev/sda7        45b72879-7cab-496b-85ca-c916c78acc49   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sda6        /home                    ext4       (rw)


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
search --no-floppy --fs-uuid --set f1a90d88-22dc-4a03-a808-ab5492c9e8bf
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
search --no-floppy --fs-uuid --set f1a90d88-22dc-4a03-a808-ab5492c9e8bf
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
menuentry 'Ubuntu, with Linux 2.6.32-26-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set f1a90d88-22dc-4a03-a808-ab5492c9e8bf
	linux	/boot/vmlinuz-2.6.32-26-generic-pae root=UUID=f1a90d88-22dc-4a03-a808-ab5492c9e8bf ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-26-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set f1a90d88-22dc-4a03-a808-ab5492c9e8bf
	echo	'Loading Linux 2.6.32-26-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-26-generic-pae root=UUID=f1a90d88-22dc-4a03-a808-ab5492c9e8bf ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-26-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set f1a90d88-22dc-4a03-a808-ab5492c9e8bf
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set f1a90d88-22dc-4a03-a808-ab5492c9e8bf
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 7afe9526fe94dba7
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 44f297dcf297d092
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=f1a90d88-22dc-4a03-a808-ab5492c9e8bf /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=97b6e6f2-e9aa-4246-839b-f81ba5fc2ffe /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=45b72879-7cab-496b-85ca-c916c78acc49 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 462.7GB: boot/grub/core.img
 430.6GB: boot/grub/grub.cfg
 462.8GB: boot/initrd.img-2.6.32-26-generic-pae
 462.7GB: boot/vmlinuz-2.6.32-26-generic-pae
 462.8GB: initrd.img
 462.7GB: vmlinuz
```

---

### Post by nuddernuby on 2010-11-30
..and here is the result after the last changes:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /mnt/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

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

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63     3,148,739     3,148,677  12 Compaq diagnostics
/dev/sda2    *      3,148,740   796,887,039   793,738,300   7 HPFS/NTFS
/dev/sda3         796,887,040   828,102,655    31,215,616  12 Compaq diagnostics
/dev/sda4         828,104,702   976,771,071   148,666,370   5 Extended
/dev/sda5         828,104,704   933,801,969   105,697,266  83 Linux
/dev/sda6         933,801,984   972,863,487    39,061,504  83 Linux
/dev/sda7         972,867,584   976,771,071     3,903,488  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        7AFE9526FE94DBA7                       ntfs       RECOVERY                      
/dev/sda2        44F297DCF297D092                       ntfs                                     
/dev/sda3        32AAB255AAB21577                       ntfs       LG_RECOVERY                   
/dev/sda4: PTTYPE="dos" 
/dev/sda5        f1a90d88-22dc-4a03-a808-ab5492c9e8bf   ext4                                     
/dev/sda6        97b6e6f2-e9aa-4246-839b-f81ba5fc2ffe   ext4                                     
/dev/sda7        45b72879-7cab-496b-85ca-c916c78acc49   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sda6        /home                    ext4       (rw)


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
search --no-floppy --fs-uuid --set f1a90d88-22dc-4a03-a808-ab5492c9e8bf
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
search --no-floppy --fs-uuid --set f1a90d88-22dc-4a03-a808-ab5492c9e8bf
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
menuentry 'Ubuntu, with Linux 2.6.32-26-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set f1a90d88-22dc-4a03-a808-ab5492c9e8bf
	linux	/boot/vmlinuz-2.6.32-26-generic-pae root=UUID=f1a90d88-22dc-4a03-a808-ab5492c9e8bf ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-26-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set f1a90d88-22dc-4a03-a808-ab5492c9e8bf
	echo	'Loading Linux 2.6.32-26-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-26-generic-pae root=UUID=f1a90d88-22dc-4a03-a808-ab5492c9e8bf ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-26-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set f1a90d88-22dc-4a03-a808-ab5492c9e8bf
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set f1a90d88-22dc-4a03-a808-ab5492c9e8bf
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 7afe9526fe94dba7
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 44f297dcf297d092
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=f1a90d88-22dc-4a03-a808-ab5492c9e8bf /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=97b6e6f2-e9aa-4246-839b-f81ba5fc2ffe /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=45b72879-7cab-496b-85ca-c916c78acc49 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 462.7GB: boot/grub/core.img
 430.6GB: boot/grub/grub.cfg
 462.8GB: boot/initrd.img-2.6.32-26-generic-pae
 462.7GB: boot/vmlinuz-2.6.32-26-generic-pae
 462.8GB: initrd.img
 462.7GB: vmlinuz
```

---

### Post by c00lwaterz on 2010-11-30
> **nuddernuby said:**
> ..and here is the result after the last changes:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /mnt/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

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

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63     3,148,739     3,148,677  12 Compaq diagnostics
/dev/sda2    *      3,148,740   796,887,039   793,738,300   7 HPFS/NTFS
/dev/sda3         796,887,040   828,102,655    31,215,616  12 Compaq diagnostics
/dev/sda4         828,104,702   976,771,071   148,666,370   5 Extended
/dev/sda5         828,104,704   933,801,969   105,697,266  83 Linux
/dev/sda6         933,801,984   972,863,487    39,061,504  83 Linux
/dev/sda7         972,867,584   976,771,071     3,903,488  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        7AFE9526FE94DBA7                       ntfs       RECOVERY                      
/dev/sda2        44F297DCF297D092                       ntfs                                     
/dev/sda3        32AAB255AAB21577                       ntfs       LG_RECOVERY                   
/dev/sda4: PTTYPE="dos" 
/dev/sda5        f1a90d88-22dc-4a03-a808-ab5492c9e8bf   ext4                                     
/dev/sda6        97b6e6f2-e9aa-4246-839b-f81ba5fc2ffe   ext4                                     
/dev/sda7        45b72879-7cab-496b-85ca-c916c78acc49   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sda6        /home                    ext4       (rw)


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
search --no-floppy --fs-uuid --set f1a90d88-22dc-4a03-a808-ab5492c9e8bf
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
search --no-floppy --fs-uuid --set f1a90d88-22dc-4a03-a808-ab5492c9e8bf
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
menuentry 'Ubuntu, with Linux 2.6.32-26-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set f1a90d88-22dc-4a03-a808-ab5492c9e8bf
	linux	/boot/vmlinuz-2.6.32-26-generic-pae root=UUID=f1a90d88-22dc-4a03-a808-ab5492c9e8bf ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-26-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set f1a90d88-22dc-4a03-a808-ab5492c9e8bf
	echo	'Loading Linux 2.6.32-26-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-26-generic-pae root=UUID=f1a90d88-22dc-4a03-a808-ab5492c9e8bf ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-26-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set f1a90d88-22dc-4a03-a808-ab5492c9e8bf
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set f1a90d88-22dc-4a03-a808-ab5492c9e8bf
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 7afe9526fe94dba7
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 44f297dcf297d092
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=f1a90d88-22dc-4a03-a808-ab5492c9e8bf /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=97b6e6f2-e9aa-4246-839b-f81ba5fc2ffe /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=45b72879-7cab-496b-85ca-c916c78acc49 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 462.7GB: boot/grub/core.img
 430.6GB: boot/grub/grub.cfg
 462.8GB: boot/initrd.img-2.6.32-26-generic-pae
 462.7GB: boot/vmlinuz-2.6.32-26-generic-pae
 462.8GB: initrd.img
 462.7GB: vmlinuz
```

i know what you are saying. you load in grub, if this not work then try the windows boot disk. if you don't try then, i can't help anymore. this is the most easiest way. and i can't answer anymore more than this.

---

### Post by Quackers on 2010-11-30
I suspect you didn't copy/paste the commands I gave you. Did you type them in? It seems that a space may have been missing near the end of the second line.

---

### Post by nuddernuby on 2010-11-30
Thanks, c00lwaterz. I have tried the windows rescue disc before - it just took me back to the grub boot menu, with the same cycle over and over again.  This not about restoring windows - this is about trying to get the grub boot to work - so that I don't get back to the position that I'm in again now.

Maybe someone can advise how to reverse the last steps...?

---

### Post by c00lwaterz on 2010-11-30
maybe your grub and grub2 did mixed up or conflict? i don't know if im correct at this but it can happen. did you try reinstall ubuntu?

---

### Post by nuddernuby on 2010-11-30
I copied and pasted your instructions, Quacker
Should I insert a space somewhere and try again?

---

### Post by Quackers on 2010-11-30
If you typed the commands as I have suggested, you can just run them again from the live cd. This will over-write what you did before.

---

### Post by nuddernuby on 2010-11-30
Where must the space go?
And, as a matter of interest, must I use Live Disc? Can I not work from the existing installation as I am now?

---

### Post by Quackers on 2010-11-30
In that case I don't know what happened. Grub is now installed in the MBR of sda but it is looking for /mnt/boot/grub when it should be looking for /boot/grub
A typing mistake may have explained this.
I can only suggest that you try the commands again from the Live cd environment copy/pasting each line one at a time and pressing enter after each line.

---

### Post by nuddernuby on 2010-11-30
That's what I did last time.

---

### Post by nuddernuby on 2010-11-30
Could you perhaps tell me where grub should be installed? In sda or in sda2?
tx

---

### Post by Quackers on 2010-11-30
It should be installed in sda.
Grub is now installed in sda (whereas before Syslinux was installed there) so that ran correctly.
The problem is that grub is looking for the wrong name for its boot files.It is looking for /mnt/boot/grub when it should be looking for /boot/grub.
This could be explained if the last command had become
```
sudo grub-install --root-directory=/mnt/dev/sda
```

instead of the correct version
```
sudo grub-install --root-directory=/mnt /dev/sda
```

ie with a space after /mnt and before /dev/sda

---

### Post by nuddernuby on 2010-11-30
Thanks, Quackers.  I have now booted up with the Live disc and repeated the commands. And viola!  All is well. I don't know what did it, but it worked the 3rd time. 
Thanks for your patience.

---

### Post by Quackers on 2010-11-30
Aha! That's excellent news! I'm quite worn out :-)
But we haven't quite finished yet.

Please open a terminal and run
```
sudo update-grub
```

and as grub.cfg is configured in the terminal please watch to see if your Windows Loader is picked up. If it is please reboot and you should get a grub menu with the option to boot Windows. Please select that option and see if Windows boots ok.

---

### Post by nuddernuby on 2010-11-30
Yes,thanks, Windows boots up now.
Cheers!

---

