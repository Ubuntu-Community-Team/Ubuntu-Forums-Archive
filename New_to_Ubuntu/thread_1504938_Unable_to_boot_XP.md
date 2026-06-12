---
title: "Unable to boot XP"
date: 2010-06-08
forum: New to Ubuntu
---

### Post by sturdy on 2010-06-08
Hi,

All worked well with Koala but after update to 10.04 I can no longer dual boot to WinXP. I have attached the results.txt file from BootInfoScript. WinXP is on sdb1 and sdb is drive 1 in the BIOS. TIA...

Sorry, I should have mentioned I have a good grub menu but when I select WinXP, the screen blanks and the cursor moves to the upper left corner and hangs. 


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 277511 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdc1 and 
                       looks at sector 277511 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc4: _________________________________________________________________________

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

/dev/sda1    *             63   976,768,064   976,768,002  42 SFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    40,965,749    40,965,687   7 HPFS/NTFS
/dev/sdb2          40,965,750   112,647,779    71,682,030   7 HPFS/NTFS
/dev/sdb3         112,647,780   215,046,089   102,398,310   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    40,965,749    40,965,687  83 Linux
/dev/sdc2         601,377,210   609,393,644     8,016,435   5 Extended
/dev/sdc5         601,393,275   609,393,644     8,000,370  82 Linux swap / Solaris
/dev/sdc3         204,796,620   400,114,889   195,318,270  83 Linux
/dev/sdc4          40,965,750   204,796,619   163,830,870  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        50F8E5CBF8E5B000                       ntfs       S1P1                          
/dev/sda: PTTYPE="dos" 
/dev/sdb1        EA5087165086E8A1                       ntfs       D0P1_WinXP                    
/dev/sdb2        108C97618C973FE0                       ntfs       D0P2_Data1                    
/dev/sdb3        3CA872C0A872786A                       ntfs       D0P3_Data2                    
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        e0fa880d-1206-4a44-890f-c830d2b48afc   ext4       LinuxRoot                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc3        31e07fc7-db3b-49e8-9b24-9546c1b3b497   ext4       Triple                        
/dev/sdc4        841e3534-7dd9-48a8-a239-4275723b8fae   ext4       LinuxHome                     
/dev/sdc5        6c736363-410a-4e73-ad9d-7af90ca574e8   swap                                     
/dev/sdc: PTTYPE="dos" 
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdc1        /                        ext4       (rw,errors=remount-ro)
/dev/sdc4        /home                    ext4       (rw)
/dev/sdb1        /media/D0P1_WinXP        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sdb1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set e0fa880d-1206-4a44-890f-c830d2b48afc
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=800x600
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd2,1)'
search --no-floppy --fs-uuid --set e0fa880d-1206-4a44-890f-c830d2b48afc
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set e0fa880d-1206-4a44-890f-c830d2b48afc
	linux	/boot/vmlinuz-2.6.32-22-generic-pae root=UUID=e0fa880d-1206-4a44-890f-c830d2b48afc ro  vga=799  quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set e0fa880d-1206-4a44-890f-c830d2b48afc
	echo	'Loading Linux 2.6.32-22-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-22-generic-pae root=UUID=e0fa880d-1206-4a44-890f-c830d2b48afc ro single  vga=799
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set e0fa880d-1206-4a44-890f-c830d2b48afc
	linux	/boot/vmlinuz-2.6.32-21-generic-pae root=UUID=e0fa880d-1206-4a44-890f-c830d2b48afc ro  vga=799  quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set e0fa880d-1206-4a44-890f-c830d2b48afc
	echo	'Loading Linux 2.6.32-21-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-21-generic-pae root=UUID=e0fa880d-1206-4a44-890f-c830d2b48afc ro single  vga=799
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set e0fa880d-1206-4a44-890f-c830d2b48afc
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set e0fa880d-1206-4a44-890f-c830d2b48afc
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
	insmod ntfs
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set ea5087165086e8a1
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=e0fa880d-1206-4a44-890f-c830d2b48afc /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb4 during installation
UUID=841e3534-7dd9-48a8-a239-4275723b8fae /home           ext4    defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=6c736363-410a-4e73-ad9d-7af90ca574e8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


    .1GB: boot/grub/core.img
   9.0GB: boot/grub/grub.cfg
   7.0GB: boot/initrd.img-2.6.32-21-generic-pae
   6.0GB: boot/initrd.img-2.6.32-22-generic-pae
   8.3GB: boot/vmlinuz-2.6.32-21-generic-pae
   5.5GB: boot/vmlinuz-2.6.32-22-generic-pae
   6.0GB: initrd.img
   7.0GB: initrd.img.old
   5.5GB: vmlinuz
   8.3GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg 
```

---

### Post by Saint_ on 2010-06-08
Hm that does seem rather odd. Put this in your terminal and post the results here if you could. ```
sudo gedit /boot/grub/menu.lst
```

---

### Post by Tholley on 2010-06-08
Looks to me like grub might need to be installed on sda1, the main hardrive instead of sdb1?

---

### Post by sturdy on 2010-06-08
> **Saint_ said:**
> Hm that does seem rather odd. Put this in your terminal and post the results here if you could. ```
sudo gedit /boot/grub/menu.lst
```

Thanks for the response Saint. /boot/grub/menu.lst doesn't exist.

---

### Post by sturdy on 2010-06-08
> **Tholley said:**
> Looks to me like grub might need to be installed on sda1, the main hardrive instead of sdb1?

Thanks, Tholley...Grub is already installed in the MBR of sda, sdb and sdc. Should it be installed in the partition instead?

---

### Post by Saint_ on 2010-06-08
> **sturdy said:**
> Thanks for the response Saint. /boot/grub/menu.lst doesn't exist.

Hm, that is even more odd lol. I think tholley and I are both aiming in the same direction though, your menu.lst file should be in /boot/grub on your 10.04 partition to be able to boot to XP. I was thinking that something might have been left out lol but it seems the whole file was moved

Edit: Well I suppose that's not entirely true, since it seems you're still able to boot into 10.04. If you use this guide here: [http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=6](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=6) it should hopefully make things a bit clearer. But if it's no help feel free to tell me lol, we'll get this figured out

---

### Post by Tholley on 2010-06-08
I'm not sure, but I was looking at this...
 
>  
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 277511 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM




---

### Post by Darkness Des on 2010-06-08
I had this precise problem a little while ago. I compiled a short list  of instructions to fix your Windows boot loader.

---

### Post by cgroza on 2010-06-08
10.04 does'nt have a menu.lst... it has something with a .conf extension.

---

### Post by Saint_ on 2010-06-08
> **cgroza said:**
> 10.04 does'nt have a menu.lst... it has something with a .conf extension.

Oh really? Well then, scrap my idea.

---

### Post by bcbc on 2010-06-08
You need to run testdisk to recover the boot sector on your windows partition (/dev/sdb1). Instructions are here: [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by wilee-nilee on 2010-06-08
> **bcbc said:**
> You need to run testdisk to recover the boot sector on your windows partition (/dev/sdb1). Instructions are here: [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

This is the answer, we have to be careful not to let our want to help overshadow whether we even know what were talking about. And consider that we are dealing with a persons OS that may contain irreplaceable stuff that may be lost by flailing at the problem; rather then letting the people who know this stuff be the the ones who help.;)

---

### Post by sturdy on 2010-06-09
Testdisk was the answer. However, there are a couple of things I don't understand.

1) What was the clue that identified testdisk as the answer?

2) I think testdisk replaced the boot sector with the backup (true?). However after testdisk ran, the last line of output said something like the files are identical. So what did it do?

3) Anybody know what caused this issue? It occurred immediately after updating to 10.04. Otherwise the update has been clean.

My thanks to all who responded! There is joy in Mudville!

---

### Post by wilee-nilee on 2010-06-09
> **sturdy said:**
> Testdisk was the answer. However, there are a couple of things I don't understand.

1) What was the clue that identified testdisk as the answer?

2) I think testdisk replaced the boot sector with the backup (true?). However after testdisk ran, the last line of output said something like the files are identical. So what did it do?

3) Anybody know what caused this issue? It occurred immediately after updating to 10.04. Otherwise the update has been clean.

My thanks to all who responded! There is joy in Mudville!

I think bcbc will probably have a more definitive answer but if you look at the boot script at your windows partitions sdc1 and sdb1 grub has been put in there. Grub should have only been in the master boot record which isn't a partition but in the 1st 512 mb of the HD and is called in this case sdc, no added numbers.

Test disc removes this grub entry and leaves the windows bootloader intact basically. Testdisk has other uses like doing recovery as well.

In the future if asked where to put grub it goes in the MBR of the device your installing to which could even be a thumbdrive that your putting a full install into, or the HD.

---

### Post by bcbc on 2010-06-09
+1 on what wilee said.

Basically, you can install a bootloader to the MBR or to the PBR (master boot record, or partition boot record), depending on how you are booting your OS. When you ran the upgrade you fell into the trap set by the grub-install program and installed grub to the PBR, but not just any PBR - the windows PBR - thereby destroying the ability for windows to boot.

Testdisk was helpful in identifying that your backup bootsector was different, and you then told it to replace the bad boot sector with the backup. Problem solved. (For some people this is not enough and many never get windows back running - unfortunately).

This sight provides more info on the boot process if you're curious about it: [http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

If you'd like to participate in getting the grub-install program 'fixed' then here's a link to the bug on launchpad: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)

---

### Post by wilee-nilee on 2010-06-09
OP your smart to ask questions like this, a lot of people get helped with this and may not follow up with understanding the whole picture. I just watch the people who are really good at this stuff like bcbc and a handful of regulars who are everyday helping in this area. A lot of people know this stuff but have other things to do so it ends up being really a group of less then 5 people who get this stuff fixed on a day by day basis.

And a huge thanks to **GREAT** creator of the bootscript, without this script it is very tough to fix boot problems. The script has dual uses as well like testdisk. If a person doesn't have boot problems but you need the basic information it provides to confirm some things it is quite useful as well.

---

### Post by sturdy on 2010-06-09
Thanks for the added follow-up guys, really appreciated. I vaguely remember during update, I was asked where to install grub. Why, I don't know. Grub should be smart enough to detect previous install/config. I think I chose something like MBR of each disk. Unfortunately, I don't remember exactly. Another lesson learned! And thanks again for the assist and answers.

---

### Post by crispy_420 on 2010-06-09
> **cgroza said:**
> 10.04 does'nt have a menu.lst... it has something with a .conf extension.

/boot/grub/grub.cfg

---

