---
title: "Seems like Ubuntu is half way installed? (if that's even possible)"
date: 2011-01-14
forum: New to Ubuntu
---

### Post by RoxyZ on 2011-01-14
I just got a new Toshiba C660 laptop with Windows 7 and was recommended Ubuntu. I'm a complete beginner and decided to run a dual boot. 
I had the usual Windows C: and Data D: drives. I split the C: drive giving me free space (unallocated) for the Ubuntu installation (or so I thought).
I ran through the Ubuntu installation. I thought I had chosen the free space as the chosen drive. I then continued with the installation except it froze at the last part (where you fill out your details). The progress bar along the bottom said "Ready when you are" but I was not allowed to click the Forward button. I waited and tried going back but to no avail. I had to restart the computer.
I then tried installation again with the CD. It proceeded to show me a drive named Ubuntu as a choice for installation. I cancelled, assuming Ubuntu was in place. But if I try to run Ubuntu without the CD, it stalls and says it cannot find a medium with live information, or something to that effect.
I have checked my drives in Windows and as well as my C: drive being partitioned (into primary and unallocated) my D: drive is now partitioned (into primary and free space). I assume this was done in Ubuntu set-up.
I am still given the choice of a dual boot at start-up. 

1) Is there any way I can get my drives into a semblance of order again?
2) How do I finish my Ubuntu dual boot properly?

I'm sorry for the epic post-I'm just really frustrated (and confused)...

---

### Post by coffeecat on 2011-01-14
> **RoxyZ said:**
> The progress bar along the bottom said "Ready when you are" but I was not allowed to click the Forward button. I waited and tried going back but to no avail. I had to restart the computer.

A FYI for when you get to that bit again - you probably had a capital letter in your account name. That is not permitted and is why it just sat there saying, "Ready when you are." The lack of a helpful explanation in the installer is a usability bug, so  when you get to that stage again make sure your account name is all lower-case.

For the rest, boot up with a live CD, make sure you are connected to the internet and then download and run the boot script from here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Post the RESULTS.txt file in code tags by clicking on the # icon in the message screen toolbar. That will give us your partition layout and other useful information and we can take it from there.

---

### Post by zeroseven0183 on 2011-01-14
I believe what you experienced in your first setup is not installation freezing. The Forward button remained disabled because you are trying to enter a username either with a space or with a capital letter.

You can reinstall Ubuntu on the same partition you used.

---

### Post by zeroseven0183 on 2011-01-14
I believe what you experienced in your first setup is not installation freezing. The Forward button remained disabled because you are trying to enter a username either with a space or with a capital letter.

You can reinstall Ubuntu on the same partition you used.

---

### Post by RoxyZ on 2011-01-14
Thanks for your help!
I just tried booting up from the CD again and I got this:

"Minimal BASH-Like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists the possible completions of a device/filename."

I've tried searching for answers to this, but my tech knowledge is quite limited-any advice?

---

### Post by coffeecat on 2011-01-14
> **RoxyZ said:**
> I just tried booting up from the CD again and I got this:

"Minimal BASH-Like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists the possible completions of a device/filename."

That might be the  Busybox shell, or perhaps grub. If the CD booted up OK before this, then for it to do this now probably means that it is being misread. Try cleaning it (gently), or burn another disc (at a low speed). Did you check the md5sum hash of the downloaded ISO? [See here]("https://help.ubuntu.com/community/HowToMD5SUM").

**EDIT**: Or perhaps it's trying to boot from the HD and can't because of the incomplete installation. Make sure you have the BIOS set to boot from the CD first.

---

### Post by RoxyZ on 2011-01-14
I'm burning a new CD as I type. How would I make sure the BIOS is booting from the CD?

---

### Post by Vaphell on 2011-01-14
enter bios as soon as machine starts (hotkey that triggers that varies depending on hardware, PCs usually show it in plain text, but laptops often don't and you need to refer to manual) and look for boot sequence in its options. If CD-ROM is before HDD then you are good to go, if not, reorder list items to achieve that. Either way i don't think you need to check, after all it booting from cd worked once already.

---

### Post by RoxyZ on 2011-01-14
So I found BIOS with F2 and changed the sequence to CD first and the installation worked! Buuuttt...

My start-up screen is black with a white box titled GNU GRUB. There are a few options in the box, firstly Ubuntu and Ubuntu (recovery mode) and lastly Windows 7 (loader). If I choose Ubuntu, it loads no problem. If I choose Windows 7 it loads to the more familiar black screen with two options: Windows and Ubuntu (the screen I've been seeing all along). It is only if I click this Windows option that it then loads.

Have I made a mistake?

---

### Post by coffeecat on 2011-01-14
> **RoxyZ said:**
> Have I made a mistake?

Sort of. It sounds as though you have made two installations of Ubuntu, a conventional one on its own partition and a Wubi installation. [Wubi]("https://help.ubuntu.com/community/Wubi").

Boot into Ubuntu and go to the link I posted in post #2. Run the bootscript and post the RESULTS.txt file. That will tell us exactly what is on your machine and then you can decide what to do about it. You clearly don't need two Ubuntu installations. When you post the RESULTS.txt file, **please** enclose it in code tags, otherwise it is difficult to read.

---

### Post by RoxyZ on 2011-01-14
Here you go!

```
 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       821,247       819,200  27 Hidden HPFS/NTFS
/dev/sda2             821,248   313,389,055   312,567,808   7 HPFS/NTFS
/dev/sda3         313,391,104   430,849,566   117,458,463   7 HPFS/NTFS
/dev/sda4         430,850,046   625,141,759   194,291,714   5 Extended
/dev/sda5         528,271,360   621,086,719    92,815,360  83 Linux
/dev/sda6         621,088,768   625,141,759     4,052,992  82 Linux swap / Solaris
/dev/sda7         430,863,363   528,265,394    97,402,032  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 2,930,277,167 2,930,275,120   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        E21881FD1881D149                       ntfs       SYSTEM                        
/dev/sda2        ACB08583B085552C                       ntfs       WINDOWS                       
/dev/sda3        AAE0874CE0871E27                       ntfs       Data                          
/dev/sda4: PTTYPE="dos" 
/dev/sda6        83dba345-68ee-4240-9a57-714fc099fec3   ext4                                     
/dev/sda7        17f23705-2ba8-4942-b0a1-91eed602ee96   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        244C10584C1026D8                       ntfs       Boris The Great               
/dev/sdb: PTTYPE="dos" 
error: /dev/sda5: No such file or directory

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/Boris The Great   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda3        /media/Data              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 83dba345-68ee-4240-9a57-714fc099fec3
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 83dba345-68ee-4240-9a57-714fc099fec3
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
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 83dba345-68ee-4240-9a57-714fc099fec3
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=83dba345-68ee-4240-9a57-714fc099fec3 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 83dba345-68ee-4240-9a57-714fc099fec3
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=83dba345-68ee-4240-9a57-714fc099fec3 ro single 
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
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 83dba345-68ee-4240-9a57-714fc099fec3
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 83dba345-68ee-4240-9a57-714fc099fec3
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set e21881fd1881d149
	chainloader +1
}
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=83dba345-68ee-4240-9a57-714fc099fec3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=17f23705-2ba8-4942-b0a1-91eed602ee96 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 352.5GB: boot/grub/core.img
 343.9GB: boot/grub/grub.cfg
 350.8GB: boot/initrd.img-2.6.35-22-generic
 318.3GB: boot/vmlinuz-2.6.35-22-generic
 350.8GB: initrd.img
 318.3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 83 fe ff ff 02 88  ce 05 00 40 88 05 00 fe  |...........@....|
000001d0  ff ff 05 fe ff ff 02 c8  56 0b 00 e0 3d 00 00 00  |........V...=...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sda5



=============================== StdErr Messages: ===============================

hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda5: No such file or directory
```

---

### Post by RoxyZ on 2011-01-14
Here you go!

```
 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       821,247       819,200  27 Hidden HPFS/NTFS
/dev/sda2             821,248   313,389,055   312,567,808   7 HPFS/NTFS
/dev/sda3         313,391,104   430,849,566   117,458,463   7 HPFS/NTFS
/dev/sda4         430,850,046   625,141,759   194,291,714   5 Extended
/dev/sda5         528,271,360   621,086,719    92,815,360  83 Linux
/dev/sda6         621,088,768   625,141,759     4,052,992  82 Linux swap / Solaris
/dev/sda7         430,863,363   528,265,394    97,402,032  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 2,930,277,167 2,930,275,120   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        E21881FD1881D149                       ntfs       SYSTEM                        
/dev/sda2        ACB08583B085552C                       ntfs       WINDOWS                       
/dev/sda3        AAE0874CE0871E27                       ntfs       Data                          
/dev/sda4: PTTYPE="dos" 
/dev/sda6        83dba345-68ee-4240-9a57-714fc099fec3   ext4                                     
/dev/sda7        17f23705-2ba8-4942-b0a1-91eed602ee96   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        244C10584C1026D8                       ntfs       Boris The Great               
/dev/sdb: PTTYPE="dos" 
error: /dev/sda5: No such file or directory

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/Boris The Great   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda3        /media/Data              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 83dba345-68ee-4240-9a57-714fc099fec3
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 83dba345-68ee-4240-9a57-714fc099fec3
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
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 83dba345-68ee-4240-9a57-714fc099fec3
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=83dba345-68ee-4240-9a57-714fc099fec3 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 83dba345-68ee-4240-9a57-714fc099fec3
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=83dba345-68ee-4240-9a57-714fc099fec3 ro single 
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
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 83dba345-68ee-4240-9a57-714fc099fec3
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 83dba345-68ee-4240-9a57-714fc099fec3
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set e21881fd1881d149
	chainloader +1
}
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=83dba345-68ee-4240-9a57-714fc099fec3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=17f23705-2ba8-4942-b0a1-91eed602ee96 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 352.5GB: boot/grub/core.img
 343.9GB: boot/grub/grub.cfg
 350.8GB: boot/initrd.img-2.6.35-22-generic
 318.3GB: boot/vmlinuz-2.6.35-22-generic
 350.8GB: initrd.img
 318.3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 83 fe ff ff 02 88  ce 05 00 40 88 05 00 fe  |...........@....|
000001d0  ff ff 05 fe ff ff 02 c8  56 0b 00 e0 3d 00 00 00  |........V...=...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sda5



=============================== StdErr Messages: ===============================

hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda5: No such file or directory
```

---

### Post by RoxyZ on 2011-01-14
Here ya go!

```
 Boot Info Script 0.55    da[LIST=1]
[/LIST]ted February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       821,247       819,200  27 Hidden HPFS/NTFS
/dev/sda2             821,248   313,389,055   312,567,808   7 HPFS/NTFS
/dev/sda3         313,391,104   430,849,566   117,458,463   7 HPFS/NTFS
/dev/sda4         430,850,046   625,141,759   194,291,714   5 Extended
/dev/sda5         528,271,360   621,086,719    92,815,360  83 Linux
/dev/sda6         621,088,768   625,141,759     4,052,992  82 Linux swap / Solaris
/dev/sda7         430,863,363   528,265,394    97,402,032  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 2,930,277,167 2,930,275,120   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        E21881FD1881D149                       ntfs       SYSTEM                        
/dev/sda2        ACB08583B085552C                       ntfs       WINDOWS                       
/dev/sda3        AAE0874CE0871E27                       ntfs       Data                          
/dev/sda4: PTTYPE="dos" 
/dev/sda6        83dba345-68ee-4240-9a57-714fc099fec3   ext4                                     
/dev/sda7        17f23705-2ba8-4942-b0a1-91eed602ee96   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        244C10584C1026D8                       ntfs       Boris The Great               
/dev/sdb: PTTYPE="dos" 
error: /dev/sda5: No such file or directory

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/Boris The Great   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda3        /media/Data              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 83dba345-68ee-4240-9a57-714fc099fec3
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 83dba345-68ee-4240-9a57-714fc099fec3
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
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 83dba345-68ee-4240-9a57-714fc099fec3
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=83dba345-68ee-4240-9a57-714fc099fec3 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 83dba345-68ee-4240-9a57-714fc099fec3
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=83dba345-68ee-4240-9a57-714fc099fec3 ro single 
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
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 83dba345-68ee-4240-9a57-714fc099fec3
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 83dba345-68ee-4240-9a57-714fc099fec3
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set e21881fd1881d149
	chainloader +1
}
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=83dba345-68ee-4240-9a57-714fc099fec3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=17f23705-2ba8-4942-b0a1-91eed602ee96 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 352.5GB: boot/grub/core.img
 343.9GB: boot/grub/grub.cfg
 350.8GB: boot/initrd.img-2.6.35-22-generic
 318.3GB: boot/vmlinuz-2.6.35-22-generic
 350.8GB: initrd.img
 318.3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 83 fe ff ff 02 88  ce 05 00 40 88 05 00 fe  |...........@....|
000001d0  ff ff 05 fe ff ff 02 c8  56 0b 00 e0 3d 00 00 00  |........V...=...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sda5



=============================== StdErr Messages: ===============================

hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda5: No such file or directory
```

---

### Post by coffeecat on 2011-01-14
Yes, you do have two Ubuntus: one Wubi installation which is in a virtual drive within the Windows C: drive, and a conventional Ubuntu installation on its own partitions, probably sda6 and sda7, but herein lies a mystery.

The bootscript output contains a contradiction, all around partitions sda5, sda6 and sda7. This is probably a result of your aborted installation, but the different parts of the bootscript output shouldn't show different things like that. I suggest you do nothing for the moment until I've rustled up a couple of other opinions on this, except the following:

A question: which Ubuntu did you boot into, the one from the menu titled grub, or the second menu, the one you get after choosing Windows from the first? (The first Ubuntu is the conventional install, the second the Wubi install.)

Also do this. Boot into Ubuntu from the first menu. Open a terminal (System > Applications) and please post the output of these two commands:

```
sudo fdisk -lu
sudo blkid
```The first will prompt you for your password and, yes, it is going in, even though you get no visual feeback

I will now pm the two people I want to look at this.

---

### Post by Quackers on 2011-01-14
another duplicate post!

---

### Post by RoxyZ on 2011-01-14
I booted into the first Ubuntu screen for the Results.txt.

For sudo fdisk -lu

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x75d98753

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      821247      409600   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2          821248   313389055   156283904    7  HPFS/NTFS
/dev/sda3       313391104   430849566    58729231+   7  HPFS/NTFS
/dev/sda4       430850046   625141759    97145857    5  Extended
/dev/sda5       528271360   621086719    46407680   83  Linux
/dev/sda6       621088768   625141759     2026496   82  Linux swap / Solaris
/dev/sda7       430863363   528265394    48701016   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002858d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  2930277167  1465137560    7  HPFS/NTFS
roxy@Boris2:~$ 

```

For sudo blkid

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x75d98753

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      821247      409600   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2          821248   313389055   156283904    7  HPFS/NTFS
/dev/sda3       313391104   430849566    58729231+   7  HPFS/NTFS
/dev/sda4       430850046   625141759    97145857    5  Extended
/dev/sda5       528271360   621086719    46407680   83  Linux
/dev/sda6       621088768   625141759     2026496   82  Linux swap / Solaris
/dev/sda7       430863363   528265394    48701016   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002858d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  2930277167  1465137560    7  HPFS/NTFS
roxy@Boris2:~$ sudo blkid
/dev/sda1: LABEL="SYSTEM" UUID="E21881FD1881D149" TYPE="ntfs" 
/dev/sda2: LABEL="WINDOWS" UUID="ACB08583B085552C" TYPE="ntfs" 
/dev/sda3: LABEL="Data" UUID="AAE0874CE0871E27" TYPE="ntfs" 
/dev/sda6: UUID="83dba345-68ee-4240-9a57-714fc099fec3" TYPE="ext4" 
/dev/sda7: UUID="17f23705-2ba8-4942-b0a1-91eed602ee96" TYPE="swap" 
/dev/sdb1: LABEL="Boris The Great" UUID="244C10584C1026D8" TYPE="ntfs" 
```

Thanks for all your help...I would have to screw this up!

---

### Post by Quackers on 2011-01-14
Hmm, interesting. Have you done any partition juggling? 
sda5 shows as not mounting, sda6 shows as a 10.10 root partition, and sda7 shows as swap.
Until you get to the Drive / Partition info!
Then sda5 is a Linux partition, sda6 shows as swap, and sda7 shows as another Linux partition.
Most irregular inconsistency!

As all the Ubuntu installations are new, I would suggest deleting the wubi installation, and then reformatting the extended partition (sda4) and re-installing Ubuntu.
However, as sda5 is not mounting this may prove more difficult than normal.
That's my 2 cents worth :-(

---

### Post by RoxyZ on 2011-01-14
I'm looking at Storage Devices in Ubuntu. sda5 seems to be Free and the only option is to Create a Partition. Would that be of help?
I'm swimming out of my depth here. Also slightly frazzled-this has been going on all day.

---

### Post by RoxyZ on 2011-01-14
I'm looking at Storage Devices in Ubuntu. sda5 seems to be Free and the only option is to Create a Partition. Would that be of help?
I'm swimming out of my depth here. Also slightly frazzled-this has been going on all day.

---

### Post by RoxyZ on 2011-01-14
I'm looking at Storage Devices in Ubuntu. sda5 seems to be Free and the only option is to Create a Partition. Would that be of help?
I'm swimming out of my depth here. Also slightly frazzled-this has been going on all day.

---

### Post by RoxyZ on 2011-01-14
I'm looking at Storage Devices in Ubuntu. sda5 seems to be Free and the only option is to Create a Partition. Would that be of help?
I'm swimming out of my depth here. Also slightly frazzled-this has been going on all day.

---

### Post by RoxyZ on 2011-01-14
I'm looking at Storage Devices in Ubuntu. sda5 seems to be Free and the only option is to Create a Partition. Would that be of help?
I'm swimming out of my depth here. Also slightly frazzled-this has been going on all day.

---

### Post by RoxyZ on 2011-01-14
Sorry about all the reposts-it keeps telling me they're not posting.

---

### Post by Quackers on 2011-01-14
Yes, it's a nuisance at the moment. The original usually gets here - but not always!
I'm still thinking :wink:

---

### Post by Rubi1200 on 2011-01-14
I think you need to boot into Windows and remove all traces of the Wubi install.

See here for manual uninstallation:
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?)

Then rerun the boot script for us to see what is going on.

---

### Post by Quackers on 2011-01-14
That sounds like a good place to start Rubi, :-)

---

### Post by RoxyZ on 2011-01-14
Restarted computer to get to Windows.

NOW the only thing that comes up is:

error: unknown filesystem.
grub rescue> (blinking cursor)

Please *please* do not tell me my day old computer is screwed.

---

### Post by RoxyZ on 2011-01-14
Restarted computer to get to Windows.

NOW the only thing that comes up is:

error: unknown filesystem.
grub rescue> (blinking cursor)

Please *please* do not tell me my day old computer is screwed.

---

### Post by RoxyZ on 2011-01-14
Restarted computer to get to Windows.

NOW the only thing that comes up is:

error: unknown filesystem.
grub rescue> (blinking cursor)

Please *please* do not tell me my day old computer is screwed.

---

### Post by Quackers on 2011-01-14
Do you have a Windows 7 repair/installation disc?
Your computer is not screwed, it's just messed up a bit :-)

---

### Post by coffeecat on 2011-01-14
> **RoxyZ said:**
> NOW the only thing that comes up is:

error: unknown filesystem.
grub rescue> (blinking cursor)

Grub, the bootloader, is trying to find its own files in partition sda6 or sda7 (whichever) and can't. Which suggests you may need to scrub the Ubuntu in its own partition as well as the Wubi one, but first:

> **RoxyZ said:**
> Please *please* do not tell me my day old computer is screwed.

It isn't; be assured. The mbr (the first few hundred bytes of the HD) needs repairing for you to be able to boot into Windows. Quackers has suggested the Windows repair disk because you can run 'bootrec /fixmbr' from that to do this. If you don't have the Windows repair disc don't despair. There's an alternative using the Ubuntu live CD.

Boot into the Ubuntu CD and make sure you are connected to the internet. Now open a terminal (Applications > Accessories) and:

```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```Ignore any warnings and let it be installed to the mbr. Now reboot and you should reboot straight into Windows. Uninstall Wubi following the instructions in the link Rubi1200 posted.

Now boot back into the live CD again and run the bootscript again and post it. We can go from there.

---

### Post by coffeecat on 2011-01-14
Unintended duplicate - forum trouble again.

---

### Post by Rubi1200 on 2011-01-14
> **coffeecat said:**
> Grub, the bootloader, is trying to find its own files in partition sda6 or sda7 (whichever) and can't. Which suggests you may need to scrub the Ubuntu in its own partition as well as the Wubi one, but first:



It isn't; be assured. The mbr (the first few hundred bytes of the HD) needs repairing for you to be able to boot into Windows. Quackers has suggested the Windows repair disk because you can run 'bootrec /fixmbr' from that to do this. If you don't have the Windows repair disc don't despair. There's an alternative using the Ubuntu live CD.

Boot into the Ubuntu CD and make sure you are connected to the internet. Now open a terminal (Applications > Accessories) and:

```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```Ignore any warnings and let it be installed to the mbr. Now reboot and you should reboot straight into Windows. Uninstall Wubi following the instructions in the link Rubi1200 posted.

Now boot back into the live CD again and run the bootscript again and post it. We can go from there.
I'm with coffeecat on this one. Let's first get some cleaning up done and then review the situation again.

Keep us posted please.

---

### Post by RoxyZ on 2011-01-15
Hey sorry for delay-had to hunt down a laptop.

So I booted Ubuntu from the CD and ran the commands. The partition in the set up was:
sda5: Ubuntu 10.10 (12 G)
sda6: Ubuntu (35.5 G)

I restarted and got the choice of Windows 7 or Ubuntu (the screen I had seen originally). I chose Windows and deleted C:\ubuntu and C:\wubildr. 
The thing is I'm supposed to edit the boot menu and delete the Wubi line. I can't seem to find it (I've included a jpeg of where I'm told it's *supposed* to be). I thought I could try restarting and pressing F2 but am reluctant to try anything unless expressly told to :D.

So I'm currently running Windows, waiting on yer advice.

Thanks guys!

---

### Post by Rubi1200 on 2011-01-15
Well, if it is not there in the drop-down list then it was probably removed.

I would say, go for it and restart.

Don't forget we would like to see the new boot script to see what things look like without the Wubi stuff.

---

### Post by RoxyZ on 2011-01-15
Ok! So I know at least one place where I'm screwing up. Booting from the CD has given me multiple installations on different drives.  The last time I booted I tried to place Ubuntu on a few different drives (from previous installations) rather than keep partitioning into smaller pieces. I got this message:

"No root system is defined. Please correct this from partitioning menu."

So now I have multiple installations and a crazy amount of partitions. Will I have to use gparted to fix this?

Heres the code too:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #10 for (,msdos10)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda11: _________________________________________________________________________

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

/dev/sda1    *          2,048       821,247       819,200  27 Hidden HPFS/NTFS
/dev/sda2             821,248   313,389,055   312,567,808   7 HPFS/NTFS
/dev/sda3         313,391,104   390,920,344    77,529,241   7 HPFS/NTFS
/dev/sda4         390,922,238   625,141,759   234,219,522   5 Extended
/dev/sda5         528,271,360   551,803,866    23,532,507  83 Linux
/dev/sda6         621,088,768   625,141,759     4,052,992  82 Linux swap / Solaris
/dev/sda7         430,863,363   528,265,394    97,402,032  83 Linux
/dev/sda8         551,804,928   618,131,455    66,326,528  83 Linux
/dev/sda9         618,133,504   621,072,383     2,938,880  82 Linux swap / Solaris
/dev/sda10        390,922,240   429,105,151    38,182,912  83 Linux
/dev/sda11        429,107,200   430,862,335     1,755,136  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda10       e6cdcac6-0ba8-4900-9e7c-30db3f3e6297   ext4                                     
/dev/sda11       92d54594-a317-405b-8120-74a90cf00dc1   swap                                     
/dev/sda1        E21881FD1881D149                       ntfs       SYSTEM                        
/dev/sda2        ACB08583B085552C                       ntfs       WINDOWS                       
/dev/sda3        AAE0874CE0871E27                       ntfs       Data                          
/dev/sda4: PTTYPE="dos" 
/dev/sda5        83dba345-68ee-4240-9a57-714fc099fec3   ext4                                     
/dev/sda6        17f23705-2ba8-4942-b0a1-91eed602ee96   swap                                     
/dev/sda8        3256fb7b-41b1-4239-89a0-ce7ce6cab2ee   ext4                                     
/dev/sda9        206402b5-10e2-4be1-9e78-b43ce7e60893   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda10       /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda3        /media/Data              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 83dba345-68ee-4240-9a57-714fc099fec3
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 83dba345-68ee-4240-9a57-714fc099fec3
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
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 83dba345-68ee-4240-9a57-714fc099fec3
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=83dba345-68ee-4240-9a57-714fc099fec3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 83dba345-68ee-4240-9a57-714fc099fec3
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=83dba345-68ee-4240-9a57-714fc099fec3 ro single 
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
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 83dba345-68ee-4240-9a57-714fc099fec3
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 83dba345-68ee-4240-9a57-714fc099fec3
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set e21881fd1881d149
    chainloader +1
}
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
# / was on /dev/sda6 during installation
UUID=83dba345-68ee-4240-9a57-714fc099fec3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=17f23705-2ba8-4942-b0a1-91eed602ee96 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 272.5GB: boot/grub/core.img
 272.1GB: boot/grub/grub.cfg
 272.4GB: boot/initrd.img-2.6.35-22-generic
 270.7GB: boot/vmlinuz-2.6.35-22-generic
 272.4GB: initrd.img
 270.7GB: vmlinuz

=========================== sda8/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set 3256fb7b-41b1-4239-89a0-ce7ce6cab2ee
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set 3256fb7b-41b1-4239-89a0-ce7ce6cab2ee
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
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 3256fb7b-41b1-4239-89a0-ce7ce6cab2ee
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=3256fb7b-41b1-4239-89a0-ce7ce6cab2ee ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 3256fb7b-41b1-4239-89a0-ce7ce6cab2ee
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=3256fb7b-41b1-4239-89a0-ce7ce6cab2ee ro single 
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
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 3256fb7b-41b1-4239-89a0-ce7ce6cab2ee
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 3256fb7b-41b1-4239-89a0-ce7ce6cab2ee
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set e21881fd1881d149
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 83dba345-68ee-4240-9a57-714fc099fec3
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=83dba345-68ee-4240-9a57-714fc099fec3 ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 83dba345-68ee-4240-9a57-714fc099fec3
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=83dba345-68ee-4240-9a57-714fc099fec3 ro single
    initrd /boot/initrd.img-2.6.35-22-generic
}
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
UUID=3256fb7b-41b1-4239-89a0-ce7ce6cab2ee /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=206402b5-10e2-4be1-9e78-b43ce7e60893 none            swap    sw              0       0

=================== sda8: Location of files loaded by Grub: ===================


 284.8GB: boot/grub/core.img
 312.7GB: boot/grub/grub.cfg
 300.4GB: boot/initrd.img-2.6.35-22-generic
 284.8GB: boot/vmlinuz-2.6.35-22-generic
 300.4GB: initrd.img
 284.8GB: vmlinuz

========================== sda10/boot/grub/grub.cfg: ==========================

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
set root='(hd0,msdos10)'
search --no-floppy --fs-uuid --set e6cdcac6-0ba8-4900-9e7c-30db3f3e6297
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos10)'
search --no-floppy --fs-uuid --set e6cdcac6-0ba8-4900-9e7c-30db3f3e6297
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
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set e6cdcac6-0ba8-4900-9e7c-30db3f3e6297
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=e6cdcac6-0ba8-4900-9e7c-30db3f3e6297 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set e6cdcac6-0ba8-4900-9e7c-30db3f3e6297
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=e6cdcac6-0ba8-4900-9e7c-30db3f3e6297 ro single 
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
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set e6cdcac6-0ba8-4900-9e7c-30db3f3e6297
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set e6cdcac6-0ba8-4900-9e7c-30db3f3e6297
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set e21881fd1881d149
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 83dba345-68ee-4240-9a57-714fc099fec3
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=83dba345-68ee-4240-9a57-714fc099fec3 ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 83dba345-68ee-4240-9a57-714fc099fec3
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=83dba345-68ee-4240-9a57-714fc099fec3 ro single
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda8)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 3256fb7b-41b1-4239-89a0-ce7ce6cab2ee
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=3256fb7b-41b1-4239-89a0-ce7ce6cab2ee ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda8)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 3256fb7b-41b1-4239-89a0-ce7ce6cab2ee
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=3256fb7b-41b1-4239-89a0-ce7ce6cab2ee ro single
    initrd /boot/initrd.img-2.6.35-22-generic
}
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

=============================== sda10/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda10 during installation
UUID=e6cdcac6-0ba8-4900-9e7c-30db3f3e6297 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda11 during installation
UUID=92d54594-a317-405b-8120-74a90cf00dc1 none            swap    sw              0       0

=================== sda10: Location of files loaded by Grub: ===================


 204.5GB: boot/grub/core.img
 217.5GB: boot/grub/grub.cfg
 213.9GB: boot/initrd.img-2.6.35-22-generic
 204.5GB: boot/vmlinuz-2.6.35-22-generic
 213.9GB: initrd.img
 204.5GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 83 fe ff ff 02 c8  2f 08 db 13 67 01 00 fe  |......../...g...|
000001d0  ff ff 05 fe ff ff 06 d2  b7 0d fc 15 3e 00 00 00  |............>...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by coffeecat on 2011-01-15
As you say, you now have a large number of Linux logical partitions contained in the extended partition sda4, which includes no less than three swap partitions. Are you sure you haven't run the installer each time you've booted the live Ubuntu CD?

Yes, I would suggest the best way forward is to remove all the Linux partitions and then start over. This is what to do. Boot up the live CD and choose 'try Ubuntu'. **Don't** start the installer. Open Gparted. Before you can delete any partitions you will have to unmount the swap partitions which will have been automounted. Right-click on each in turn and choose 'swapoff'. Now select each partition from the bottom and select delete - including the extended sda4 partition last of all. Remember to click on apply before you quit Gparted. That will leave you approx 120GiB unallocated space.

Before you do anything to install Ubuntu there are a couple of things to think about. Your Windows C: partition is 160GiB which is OK, but your second NTFS partition (sda3) is only 40GiB - I guess this might be your Windows D: partition. You might want to consider enlarging this at the expense of the unallocated space. You could use this NTFS partition for personal data to be shared between Windows and Ubuntu in which case you don't need anything like 120GiB for Ubuntu. If you do enlarge the NTFS sda3 partition, use Disk Management in Windows.

The second thing is that when you come to re-install Ubuntu, you can (in theory) leave the unallocated space as is and choose 'install alongside' at the partitioning stage of the installer. Beware though. It has a nasty design flaw that can wipe out your Windows installation if you make the wrong of several choices it gives you. For more details, I'll rely on the others who have posted in this thread who know more about this particular issue.

---

### Post by Quackers on 2011-01-15
I agree with coffeecat about the "install alongside" option in the 10.10 installer. It has a nasty habit of eating operating systems. Instead choose the "specify manually" option and set up your partitions (/root and swap - and /home if required) with appropriate mount points.

---

### Post by RoxyZ on 2011-01-16
I booted from the CD and clicked "Try Ubuntu". I then chose GParted from the Administration menu.
Thing is it keeps crashing-when I try to report the bug it says "Program crashed on assertion failure, but the message could not be retrieved."
Can I try deleting everything through WIndows? I feel like this computer is out to get me :D

---

### Post by coffeecat on 2011-01-16
> **RoxyZ said:**
> Can I try deleting everything through WIndows?

Um - probably. :? So long as you have repaired the Windows mbr either with the Windows disc or with lilo. I've never had Gparted crash like that from a live CD. It might be worth burning another disc. It might be something as simple as a read error from the disc.

---

### Post by RoxyZ on 2011-01-16
Windows runs fine. I mean I still get two screens I have to bypass to get in (I can't find the wubi line to delete it in boot menu-post 26). So I'll try deleting partitions with Windows disk manager I guess?
I've searched that Gparted bug in forums and found a few instances of it but no concrete solution.

---

### Post by coffeecat on 2011-01-16
> **RoxyZ said:**
> I mean I still get two screens I have to bypass to get in

Whoa! Stop right there! If you are getting the grub menu before the Wubi menu, then you will make your system unbootable if you remove the Linux partitions. From what you posted earlier it sounded as though you had repaired the Windows mbr, but perhaps not. Did you repair the Windows mbr with the Windows disk or with lilo?

---

### Post by RoxyZ on 2011-01-16
Ok so I performed all of this:

> Boot into the Ubuntu CD and make sure you are connected to the internet. Now open a terminal (Applications > Accessories) and:

Code:
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
Ignore any warnings and let it be installed to the mbr. Now reboot and you should reboot straight into Windows. 

Then I followed the manual install posted by Rubi1200:

> How do I manually uninstall Wubi?

Remove C:\ubuntu and C:\wubildr*

In Windows XP you need to edit C:\boot.ini and delete the Ubuntu/Wubi line. For Vista, you can use EasyBCD to edit the boot menu. Alternatively you can modify the boot menu via Control Panel > System > Advanced > Startup and Recovery and pressing "Edit". For Windows 98 you have to edit C:\config.sys and remove the Wubi block.

To remove Wubi from the add/remove list, delete the registry key: HKLM\Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi

An easy method of removing this registry key is to paste the following text into a plain editor such as Notepad, close and save the file as something like removeWubiKey.reg (you may wish to go to Folder Options > View and disable the "Hide file extensions for known file types" option to check that the .reg extension has been applied correctly). Then you can perform the rest automatically by opening the file in the normal Windows manner, or choosing the "Merge" option from the right click context menu. Note: The formatting is rather strict, so copy the text exactly for best results. You may need to be logged in as the administrator to delete the key, depending on the version of Windows you are using. User Account Control in Vista may also ask for permission, in the typical fashion.


REGEDIT4

[-HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall\Wubi]
After deleting the registry key, Ubuntu may still appear in the program list.

I could do everything except:

> Alternatively you can modify the boot menu via Control Panel > System > Advanced > Startup and Recovery and pressing "Edit".

I'm running Windows 7-is there somewhere else I should be looking? I posted the screenshot of what I found in post #26. 
If I click Ubuntu on the second menu screen I reach on start-up, it can't run.

---

### Post by coffeecat on 2011-01-16
If your first screen is showing "grub", then this didn't work:

> **RoxyZ said:**
> ```

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
Ignore any warnings and let it be installed to the mbr.
```

Do you have a Windows 7 installation disc or repair disc? Can you boot into Windows 7? If you can, you can create a repair disc for Windows 7 from within Windows 7. With this you can repair the Windows mbr.

---

### Post by Rubi1200 on 2011-01-16
I know you already did this, but I think it might be a good idea to run the boot info script again and post the results so we can see the current state of things.

---

### Post by RoxyZ on 2011-01-16
Just burning the Windows repair CD. I'll run that and then run the bootscript.

Not sure why the code didn't work-I got all the warnings and password requests mentioned.

---

### Post by RoxyZ on 2011-01-16
I ran the Windows CD; it told me it was successful

But when I restarted the computer I'm back to:

```
error:no such partition
grub rescue> 
```

---

### Post by RoxyZ on 2011-01-16
And here's RESULTS.txt:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #10 for (,msdos10)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

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

/dev/sda1    *          2,048       821,247       819,200  27 Hidden HPFS/NTFS
/dev/sda2             821,248   313,391,103   312,569,856   7 HPFS/NTFS
/dev/sda3         313,391,104   390,920,344    77,529,241   7 HPFS/NTFS
/dev/sda4         390,922,238   625,141,759   234,219,522   5 Extended
/dev/sda5         528,271,360   551,803,866    23,532,507  83 Linux
/dev/sda6         551,804,928   618,131,455    66,326,528  83 Linux
/dev/sda7         618,133,504   621,072,383     2,938,880  82 Linux swap / Solaris
/dev/sda8         621,088,768   625,141,759     4,052,992  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        DCBE5497BE546C50                       ntfs       SYSTEM                        
/dev/sda2        DCAE58EAAE58BF28                       ntfs       WINDOWS                       
/dev/sda3        AAE0874CE0871E27                       ntfs       Data                          
/dev/sda4: PTTYPE="dos" 
/dev/sda5        83dba345-68ee-4240-9a57-714fc099fec3   ext4                                     
/dev/sda6        3256fb7b-41b1-4239-89a0-ce7ce6cab2ee   ext4                                     
/dev/sda7        206402b5-10e2-4be1-9e78-b43ce7e60893   swap                                     
/dev/sda8        17f23705-2ba8-4942-b0a1-91eed602ee96   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 83dba345-68ee-4240-9a57-714fc099fec3
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 83dba345-68ee-4240-9a57-714fc099fec3
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
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 83dba345-68ee-4240-9a57-714fc099fec3
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=83dba345-68ee-4240-9a57-714fc099fec3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 83dba345-68ee-4240-9a57-714fc099fec3
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=83dba345-68ee-4240-9a57-714fc099fec3 ro single 
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
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 83dba345-68ee-4240-9a57-714fc099fec3
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 83dba345-68ee-4240-9a57-714fc099fec3
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set e21881fd1881d149
    chainloader +1
}
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
# / was on /dev/sda6 during installation
UUID=83dba345-68ee-4240-9a57-714fc099fec3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=17f23705-2ba8-4942-b0a1-91eed602ee96 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 272.5GB: boot/grub/core.img
 272.1GB: boot/grub/grub.cfg
 272.4GB: boot/initrd.img-2.6.35-22-generic
 270.7GB: boot/vmlinuz-2.6.35-22-generic
 272.4GB: initrd.img
 270.7GB: vmlinuz

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set 3256fb7b-41b1-4239-89a0-ce7ce6cab2ee
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set 3256fb7b-41b1-4239-89a0-ce7ce6cab2ee
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
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 3256fb7b-41b1-4239-89a0-ce7ce6cab2ee
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=3256fb7b-41b1-4239-89a0-ce7ce6cab2ee ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 3256fb7b-41b1-4239-89a0-ce7ce6cab2ee
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=3256fb7b-41b1-4239-89a0-ce7ce6cab2ee ro single 
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
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 3256fb7b-41b1-4239-89a0-ce7ce6cab2ee
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 3256fb7b-41b1-4239-89a0-ce7ce6cab2ee
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set e21881fd1881d149
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 83dba345-68ee-4240-9a57-714fc099fec3
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=83dba345-68ee-4240-9a57-714fc099fec3 ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 83dba345-68ee-4240-9a57-714fc099fec3
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=83dba345-68ee-4240-9a57-714fc099fec3 ro single
    initrd /boot/initrd.img-2.6.35-22-generic
}
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=3256fb7b-41b1-4239-89a0-ce7ce6cab2ee /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=206402b5-10e2-4be1-9e78-b43ce7e60893 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 284.8GB: boot/grub/core.img
 312.7GB: boot/grub/grub.cfg
 300.4GB: boot/initrd.img-2.6.35-22-generic
 284.8GB: boot/vmlinuz-2.6.35-22-generic
 300.4GB: initrd.img
 284.8GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 83 fe ff ff 02 c8  2f 08 db 13 67 01 00 fe  |......../...g...|
000001d0  ff ff 05 fe ff ff dd db  96 09 25 14 f4 03 00 00  |..........%.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

---

### Post by coffeecat on 2011-01-16
> **RoxyZ said:**
> I ran the Windows CD; it told me it was successful

What did you run? It hasn't repaired the mbr. Grub is still in the mbr. You need to drop to a command prompt in the Windows rescue CD and run 'bootrec /FixMbr'.

See here:

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by Rubi1200 on 2011-01-16
I would wait for coffeecat to respond, but GRUB is still messed up because you have 2 installs there and it is confused about where to look.

If it was me, I would get Windows up and running properly then delete everything from the extended partition and start over with a fresh install.

As I said, wait for other opinions please.

---

### Post by coffeecat on 2011-01-16
> **Rubi1200 said:**
> If it was me, I would get Windows up and running properly then delete everything from the extended partition and start over with a fresh install.

Agreed. 

@RoxyZ, at the moment grub is in the mbr (which means that lilo was not installed as a Windows mbr substitute) and is looking for partition #10 - which doesn't exist.

I think 'bootrec /FixMbr' from the Windows disc is the way to go to get Windows running again.

---

### Post by RoxyZ on 2011-01-16
Ok! I ran the bootrec and reinstalled Windows. The computer is now booting directly into Windows.
As GParted wouldn't run, should I just delete straight from disk manager? (jpeg attached)
 
Ideally, I would like to shrink Windows a *lot, *make D: bigger and recombine the other partitions. I would then install Ubuntu on this third drive.

---

### Post by coffeecat on 2011-01-16
> **RoxyZ said:**
> Ok! I ran the bootrec and reinstalled Windows. The computer is now booting directly into Windows.
As GParted wouldn't run, should I just delete straight from disk manager? (jpeg attached)
 
Ideally, I would like to shrink Windows a *lot, *make D: bigger and recombine the other partitions. I would then install Ubuntu on this third drive.

Don't try to make partitions for Linux with the Windows Disk Manager - it can't create Linux filesystems. You could delete all the partitions to the right of the green free space. That will leave you with a load of unallocated space to use later. And you should be able to do what you want with C: and D: with Windows Disc Manager. But beyond that point you need to find out why Gparted was crashing - or get around that problem. You'll need it for future use. I would suggest burning a new Ubuntu disc and/or having a go with Gparted Live. Link here:

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by RoxyZ on 2011-01-16
I've cleaned up my drives a bit and took a gander at GParted. I'm going to wait till I read up and fully understand partitioning before I install again. I think after the last three days it would be wise :D

Thanks so much! Ye have saved me from my own idiocy :D

---

### Post by coffeecat on 2011-01-16
Good luck!

> **RoxyZ said:**
>  I'm going to wait till I read up and fully understand partitioning before I install again. 

Here's good place to start. Follow all the links.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

