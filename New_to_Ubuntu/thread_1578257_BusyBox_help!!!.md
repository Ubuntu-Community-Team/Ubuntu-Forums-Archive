---
title: "BusyBox help!!!"
date: 2010-09-20
forum: New to Ubuntu
---

### Post by JPS77 on 2010-09-20
Hi,
i am an absolute begginer... i dont know any commands.
I was using Kubuntu when suddenly something went wrong, so i removed my RAM and put it, my conp started working, but when i boot into linux "busybox 1.3" opens up. i don't care if i need to reload my OS. I need some files that are there on the partition which i am not able to access even through a live cd. Whenever i try to mount the partition it just dosen't get mounted, I think it's b'coz it wasn't unmounted properly the lat time.
Hope you understood my problem.....
Thank in advance.

JPS

---

### Post by andrewthomas on 2010-09-20
Reinstall grub.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by Rubi1200 on 2010-09-20
> **andrewthomas said:**
> Reinstall grub.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")
Without knowing any other details of the setup?

What if the OP has other operating systems?

What if it is not a GRUB issue?

@ JPS77
You need to give us some more to go on, like what you were doing that things got messed up, what are the computer specifications, what operating systems you have installed etc. and from the LiveCD please post the results of the bootscript linked to at the bottom of my post.

Thanks.

---

### Post by JPS77 on 2010-09-20
Thanks for replying
i have a 
P4 dual core -3Ghz x 2
1GB RAM
Nvidia GeForce 8400

I've got Win XP installed on one partition, I really don't use XP at all, I booted up XP just to check if it was a a common problem. But it booted up fine. I've tried to to mount my ext4 parttion using puppy, open suse and Ubuntu 9.04

And the kubuntu i've got is 10.04

this what happens when i try to mount....

```
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /media
mount: wrong fs type, bad option, bad superblock on /dev/sda6,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

I've begun the Boot script download will surely fill you on what it says...

---

### Post by Rubi1200 on 2010-09-20
It would be good to see the results of the bootscript, but also take a look here:
[http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html](http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html)

---

### Post by JPS77 on 2010-09-21
I did what the website said and this is what  got:
When I typed 'y' it just kept on asking the same thing for 1,2,3......
then i closed the terminal.

```
ubuntu@ubuntu:~$ sudo e2fsck -f -b 32768  /dev/sda6
e2fsck 1.41.4 (27-Jan-2009)
Group descriptor 0 checksum is invalid.  Fix<y>? 

```

:(

---

### Post by Rubi1200 on 2010-09-21
Is sda6 the Kubuntu installation? 
And what is this 
> 32768 

I still think it would help if you post the results of the bootscript for us please.

---

### Post by JPS77 on 2010-09-21
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x08430842

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    40,596,254    40,596,192   7 HPFS/NTFS
/dev/sda2    *     40,596,316   156,280,319   115,684,004   f W95 Ext d (LBA)
/dev/sda5          40,596,318    78,381,134    37,784,817   7 HPFS/NTFS
/dev/sda6          78,381,198   115,025,399    36,644,202  83 Linux
/dev/sda7         115,025,463   116,085,689     1,060,227  82 Linux swap / Solaris
/dev/sda8         116,085,753   156,280,319    40,194,567   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        28E0AC99E0AC6F2E                       ntfs                                     
/dev/sda5        3664C2DB64C29D4D                       ntfs       Media                         
/dev/sda6        c3facbfc-57dd-445d-ade0-592f94791dc4   ext4                                     
/dev/sda7        1cc5cd6a-adcd-4395-94b3-15915e2f6f5e   swap                                     
/dev/sda8        82C42363C4235925                       ntfs       My Files                      

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /media/CDROM             iso9660    (ro,nosuid,nodev,uhelper=hal,uid=999,utf8)
/dev/sda5        /media/Media             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1        /media/disk              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda8        /media/My Files          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


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
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set c3facbfc-57dd-445d-ade0-592f94791dc4
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set c3facbfc-57dd-445d-ade0-592f94791dc4
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
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set c3facbfc-57dd-445d-ade0-592f94791dc4
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=c3facbfc-57dd-445d-ade0-592f94791dc4 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set c3facbfc-57dd-445d-ade0-592f94791dc4
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=c3facbfc-57dd-445d-ade0-592f94791dc4 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set c3facbfc-57dd-445d-ade0-592f94791dc4
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set c3facbfc-57dd-445d-ade0-592f94791dc4
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 28e0ac99e0ac6f2e
	drivemap -s (hd0) ${root}
	chainloader +1
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
# / was on /dev/sda6 during installation
UUID=c3facbfc-57dd-445d-ade0-592f94791dc4 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=1cc5cd6a-adcd-4395-94b3-15915e2f6f5e none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


  53.2GB: boot/grub/core.img
  47.2GB: boot/grub/grub.cfg
  55.2GB: boot/initrd.img-2.6.32-21-generic
  53.2GB: boot/vmlinuz-2.6.32-21-generic
  55.2GB: initrd.img
  53.2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda6

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000000e0  ff ff ff 3f 00 00 04 00  00 00 00 00 00 00 00 00  |...?............|
000000f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000100  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
00000150  ff ff ff ff ff ff ff ff  ff ff ff ff ff 3f ff ff  |.............?..|
00000160  ff ff ff ff ff ff ff ff  ff 0f 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001a0  ff ff ff ff ff ff ff 7f  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001c0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
000001d0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff 01  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 f8 ff 7f  00 00 00 fe ff ff ff ff  |................|
00000200


```

---

### Post by JPS77 on 2010-09-21
very sorry i gotta go

---

### Post by JPS77 on 2010-09-21
> Is sda6 the Kubuntu installation?
And what is this
Quote:
32768 

sda6 is the kubuntu installation (ext4)

32768 is the location where a backup the superblock is stored
the article you gave got me this far, i heard about superblocks there

---

### Post by JPS77 on 2010-09-22
Thank God it worked!!!!!!!!!!

---

### Post by Rubi1200 on 2010-09-22
Nice!! :)

---

