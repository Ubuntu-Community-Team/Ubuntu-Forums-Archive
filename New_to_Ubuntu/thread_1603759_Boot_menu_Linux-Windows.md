---
title: "Boot menu Linux-Windows"
date: 2010-10-23
forum: New to Ubuntu
---

### Post by Linux-is-super on 2010-10-23
Hi !

I am new at linux. I had the windows 7 installed before. Then I installed Ubuntu 10.10 . But when I start my computer I have no boot menu to choose Windows 7 or Linux ubuntu. 

When I type: 
sudo blkid 
I get:
/dev/sda1: LABEL="Novi Podatci" UUID="5850F53F50F52502" TYPE="ntfs" 
/dev/sdb3: UUID="6C1C28F71C28BDC8" TYPE="ntfs" 
/dev/sdb5: LABEL="Windows 7" UUID="A418C97518C946D0" TYPE="ntfs" 
/dev/sdb6: UUID="460d9750-72b9-4933-9c62-278f786cf365" TYPE="ext4" 
/dev/sdb7: UUID="e55d6c7d-e4c7-41f9-ba75-4fa97f71eb9b" TYPE="swap" 
/dev/sdb8: UUID="f9d92037-2e6a-4d4f-98eb-4c9677232ae9" TYPE="ext4" 

sdb5 is holding a bootable Windos and sda1 is HD that holds only data
I check for /boot/grub/menu.lst file and is blank. How can I get boot menu to choose between Windows and Linux
Thank you

---

### Post by Hippytaff on 2010-10-23
Grub2 dosen't have menu.lst like legacy grub. You need to edit /etc/default/grub

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Don't know why you don't automatically get the options though...might be some underlying issue!?

---

### Post by Rubi1200 on 2010-10-23
Hi and welcome to the forums :)

From a LiveCD, post the results of the boot-script linked at the bottom of my post.

If there is a problem with the bootloaders (either for Windows or Ubuntu) it will probably show up in the results.

Thanks.

---

### Post by Linux-is-super on 2010-10-23
Thank you Hippytaff and Rubi1200 for answering my questions .
I v  been doing something, I don t know what :))) and now I have boot menu .  I can load Ubuntu. Still if I want to boot Windows I get only a dark screen with cursor blinking and no operating system is loaded. What should I do ?

---

### Post by drs305 on 2010-10-23
Linux-is-super,

Welcome to the Ubuntu forums.

You may have overwritten the Windows boot files when you installed Ubuntu. Please run the boot info script and post the results as Rubi1200 requested and we can see the status of your system.

---

### Post by Linux-is-super on 2010-10-23
Thank you ! I did not even know what is "Boot Info Script" Now I know :) 
Results are in attached file .
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #8 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /grldr /ntldr 
                       /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 1671. But according to the info from fdisk, 
                       sdb5 starts at sector 101677056.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   976,768,064   976,768,002   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb2               2,046   195,414,015   195,411,970   5 Extended
/dev/sdb5         101,677,056   195,414,015    93,736,960   7 HPFS/NTFS
/dev/sdb6               2,048    28,448,767    28,446,720  83 Linux
/dev/sdb7          28,450,816    32,354,303     3,903,488  82 Linux swap / Solaris
/dev/sdb8          32,356,352   101,675,007    69,318,656  83 Linux
/dev/sdb3    *    195,414,660   488,375,999   292,961,340   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        5850F53F50F52502                       ntfs       Novi Podatci                  
/dev/sda: PTTYPE="dos" 
/dev/sdb2: PTTYPE="dos" 
/dev/sdb3        6C1C28F71C28BDC8                       ntfs                                     
/dev/sdb5        A418C97518C946D0                       ntfs       Windows 7                     
/dev/sdb6        460d9750-72b9-4933-9c62-278f786cf365   ext4                                     
/dev/sdb7        e55d6c7d-e4c7-41f9-ba75-4fa97f71eb9b   swap                                     
/dev/sdb8        f9d92037-2e6a-4d4f-98eb-4c9677232ae9   ext4                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb8        /home                    ext4       (rw,commit=0)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(1)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(1)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

multi(0)disk(0)rdisk(1)partition(4)\WINDOWS.0="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT


=========================== sdb6/boot/grub/grub.cfg: ===========================

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
set default="4"
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
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set 460d9750-72b9-4933-9c62-278f786cf365
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set 460d9750-72b9-4933-9c62-278f786cf365
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
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set 460d9750-72b9-4933-9c62-278f786cf365
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=460d9750-72b9-4933-9c62-278f786cf365 ro  splash  quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set 460d9750-72b9-4933-9c62-278f786cf365
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=460d9750-72b9-4933-9c62-278f786cf365 ro single  splash
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
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set 460d9750-72b9-4933-9c62-278f786cf365
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set 460d9750-72b9-4933-9c62-278f786cf365
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 5850f53f50f52502
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

=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda6       /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda8 during installation
UUID=f9d92037-2e6a-4d4f-98eb-4c9677232ae9 /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=e55d6c7d-e4c7-41f9-ba75-4fa97f71eb9b none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb6: Location of files loaded by Grub: ===================


   2.5GB: boot/grub/core.img
   2.7GB: boot/grub/grub.cfg
    .9GB: boot/initrd.img-2.6.35-22-generic
   2.6GB: boot/vmlinuz-2.6.35-22-generic
    .9GB: initrd.img
   2.6GB: vmlinuz

```

---

### Post by Linux-is-super on 2010-10-23
It seams complicated. I don t know how I installed all these operating systems. The only working is Windows XP. I would like to keep only one Windows XP, the one that I used before because of data on it. And Linux which I intend to learn and to keep as my primary OS.

---

### Post by drs305 on 2010-10-23
One error to fix is your /etc/fstab file in sdb6 (Your default Ubuntu partition):

> 
=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
**[COLOR="Red"]/dev/sda6[/COLOR]**       /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda8 during installation
UUID=f9d92037-2e6a-4d4f-98eb-4c9677232ae9 /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=e55d6c7d-e4c7-41f9-ba75-4fa97f71eb9b none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


This should actually be **/dev/sdb6**. Or even better: 
 **UUID=460d9750-72b9-4933-9c62-278f786cf365**
Open the file for editing:
```
gksu gedit /etc/fstab
```

Also note that the "notes" which indicate where the partitions were during installation are no longer correct. It doesn't effect anything, but it can be misleading. Those are comments that never change after an installation, even if you delete or add partitions/drives.

Since you aren't seeing the Windows option, make the change above, save the file, then run:
```
sudo update-grub
```
and reboot. Sometimes Windows just isn't found unless that command is run after installation.

I don't know enough about Windows any longer to know, but I think it should run. The boot partition is located on a primary partition and has the boot flag. I see that 7 is on an extended partition but it probably doesn't matter as long as the boot partition isn't. A Windows guy will have to answer that.

See if when you now boot you get the Grub menu and Windows option, and let us know what else you need at that point.

Note: As a mod, I went ahead and posted the boot script information within your post as it makes it easier for the helpers. To get it in a window, you press the # icon in the menubar to generate "code" tags, then paste between them.

---

### Post by oldfred on 2010-10-23
It looks like you have a grub4dos file/folder in your windows boot/root. I would remove that file, sometimes it confuses grub or windows.

    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD [COLOR=Red]/grldr[/COLOR] /ntldr 
                       /NTDETECT.COM

Your boot is combined into sda1. The boot.ini shows several windows XP's, but the script does not show the windows BCD details, so we cannot tell what it is doing. If then windows still does not work you may need to do windows repairs. The repairs are different for XP or win7. Which is you last install as it is the version of windows in control.

---

### Post by drs305 on 2010-10-23
*oldfred*,

How does the grub4dos get into the Windows boot folders in the first place? I've often wondered but haven't asked previously.

---

### Post by oldfred on 2010-10-23
I have regularly run across this and do not know how the grldr gets into windows. It is an old issue as I learned that from meierfra. I orignally thought it was leftovers from wubi, but now do not know.

---

### Post by Linux-is-super on 2010-10-24
Thank you "drs305" and "oldfred" !

I have done changes as "drs305" told me ( to change /dev/sda6 /  for  /dev/sdb6 /  ). But it is still the same. 
As I told I am new at Linux, and I am not good enough for this to understand the code, and to change it by my self, so "oldfred" how can I remove the file "grub4dos" as you told me. 
Also I must say, I installed before Windows 7 and 2 times Windows XP and for some unknown reasons I had a Windows 7 boot menu witch allow me to chose between two Win XP and no Windows 7 :) And I let it be that way because I didn´t want to bother with that any more, it was enough good for me. So when I installed Linux I could not boot Windows XP. That is the story :)

---

### Post by oldfred on 2010-10-24
In Ubuntu or Ubuntu's liveCd from Places click on computer. You should see your windows install in the left side. It may just say 46GB drive or something like that. You should be able to see the grldr file or folder in the root of your windows drive. 


You boot.ini points to partitions 2 & 4 but you have XP type installs in sda1 and sdb3 with a win7 install in sdb5 which cannot boot directly from sdb5 as windows will only boot thru primary partitions ( 1 thru 4)

---

### Post by Linux-is-super on 2010-10-25
Hi !
I decided to I reinstall Windows XP and restore the GRUB and thought that I will solve the problem. What hapen ? Before reinstalling GRUB  I had a menu with possibility to choose 3 Windows that I could boot.After reinstalling the GRUB i had the same situation as before i.e. Ubuntu is normally booting but when I choose Windows to boot blank screen shows with cursor blinking and no operating system is loaded.
Results from Boot Info script is in the Results2.txt attached file

---

### Post by Rubi1200 on 2010-10-25
For those concerned:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   976,768,064   976,768,002   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb2               2,046   195,414,015   195,411,970   5 Extended
/dev/sdb5               2,048    28,448,767    28,446,720  83 Linux
/dev/sdb6          28,450,816    32,354,303     3,903,488  82 Linux swap / Solaris
/dev/sdb7          32,356,352   101,675,007    69,318,656  83 Linux
Invalid MBR Signature found
Empty Partition
/dev/sdb3    *    195,414,660   488,375,999   292,961,340   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        5850F53F50F52502                       ntfs       Novi Podatci                  
/dev/sda: PTTYPE="dos" 
/dev/sdb2: PTTYPE="dos" 
/dev/sdb3        C80412500412423C                       ntfs                                     
/dev/sdb5        460d9750-72b9-4933-9c62-278f786cf365   ext4                                     
/dev/sdb6        e55d6c7d-e4c7-41f9-ba75-4fa97f71eb9b   swap                                     
/dev/sdb7        f9d92037-2e6a-4d4f-98eb-4c9677232ae9   ext4                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb7        /home                    ext4       (rw,commit=0)
/dev/sda1        /media/Novi Podatci      fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
multi(0)disk(0)rdisk(1)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
multi(0)disk(0)rdisk(1)partition(4)\WINDOWS.0="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT 

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set default="4"
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
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set 460d9750-72b9-4933-9c62-278f786cf365
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set 460d9750-72b9-4933-9c62-278f786cf365
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
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 460d9750-72b9-4933-9c62-278f786cf365
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=460d9750-72b9-4933-9c62-278f786cf365 ro  splash  quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 460d9750-72b9-4933-9c62-278f786cf365
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=460d9750-72b9-4933-9c62-278f786cf365 ro single  splash
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
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 460d9750-72b9-4933-9c62-278f786cf365
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 460d9750-72b9-4933-9c62-278f786cf365
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 5850f53f50f52502
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

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb6       /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda8 during installation
UUID=f9d92037-2e6a-4d4f-98eb-4c9677232ae9 /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=e55d6c7d-e4c7-41f9-ba75-4fa97f71eb9b none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


   2.6GB: boot/grub/core.img
  13.6GB: boot/grub/grub.cfg
    .9GB: boot/initrd.img-2.6.35-22-generic
   2.6GB: boot/vmlinuz-2.6.35-22-generic
    .9GB: initrd.img
   2.6GB: vmlinuz
```

---

### Post by oldfred on 2010-10-25
Your sda1 partition has boot files for both XP and win7, showing these win7 boot files.
/bootmgr /Boot/BCD
But you do not have a partition with win7 installed. If you do not have win7 you can remove these and then it may boot XP, but you may have to repair the XP install. It does say the boot sector is XP (which is good as if it was win7 that would have to be fixed).

You also have this error which I do not know the solution:
Invalid MBR Signature found
Empty Partition

It is usually related to a partition table issue but I do not see overlaping entries. Maybe someone else will see the specific issue.

---

### Post by drs305 on 2010-10-25
Where did sdb1 go?

---

