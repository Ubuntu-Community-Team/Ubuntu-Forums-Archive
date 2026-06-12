---
title: "Windows 7 will not boot after installing Ubuntu 10.10"
date: 2010-12-24
forum: New to Ubuntu
---

### Post by 6msj on 2010-12-24
Hi, new to linux here, decided to install it today and try it out but I ran into a few problems, decided to post here and search on google for help.

Linux boots perfectly and I can access the win7 partition from Linux. When I restart and try to boot win7 from grub though, it gives me the error message,

"windows failed to to start. a recent hardware or software change...etc"

It gives me two options, to start windows regularly or to repair and both restarts the system back to the grub. 


I installed ubuntu with this guide.
[http://www.ubuntugeek.com/step-by-step-guide-installing-ubuntu-10-10-on-a-windows-7-system-dual-booting-with-radeon-graphics-card.html](http://www.ubuntugeek.com/step-by-step-guide-installing-ubuntu-10-10-on-a-windows-7-system-dual-booting-with-radeon-graphics-card.html)

Before I did the installation, I shrank my win7 partition with easeus partition manager. 

Thank you.

---

### Post by amjjawad on 2010-12-24
Hello and welcome :)

Please post back the result of this script here and wrap up the text with "CODE" tags or click "#" after you highlight the text.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Did you use disk defragment before you shrink it? have you removed the temp files, cookies, etc before that?
This is very important step to do before you start shrinking.

---

### Post by matt_symes on 2010-12-24
Hi

Just a thought. Did you run chkdsk on the windows partition after shrinking it?

Did you boot into window after partitioning but before installing Ubuntu?

EDIT: DOH Beaten to it :)

Kind regards

---

### Post by 6msj on 2010-12-24
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for (,msdos3)/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /bootmgr /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   208,925,324   208,923,277   7 HPFS/NTFS
/dev/sda2         291,909,632   312,573,951    20,664,320   7 HPFS/NTFS
/dev/sda3         208,926,720   209,901,567       974,848  83 Linux
/dev/sda4         209,903,614   291,907,583    82,003,970   5 Extended
/dev/sda5         209,903,616   229,433,343    19,529,728  83 Linux
/dev/sda6         229,435,392   241,151,999    11,716,608  82 Linux swap / Solaris
/dev/sda7         241,154,048   291,907,583    50,753,536  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 1,953,525,167 1,953,523,120   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        D888ECF688ECD3D2                       ntfs                                     
/dev/sda2        264A0D454A0D12EB                       ntfs       HP_RECOVERY                   
/dev/sda3        4c552331-20aa-4056-9776-a5e7d908c6c7   ext4                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        e0fa3403-3d95-452f-9d25-43448363070b   ext4                                     
/dev/sda6        db802a42-2720-47b8-8a53-6d13ecbd3659   swap                                     
/dev/sda7        326dd521-9a00-4f2a-b5c1-621d54070bbf   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        0EC08480C084702F                       ntfs       Elements                      
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda3        /boot                    ext4       (rw,commit=0)
/dev/sda5        /home                    ext4       (rw,commit=0)
/dev/sdb1        /media/Elements          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda2/boot.ini: ================================

;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[boot loader]
timeout=2
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT
e:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /CMDCONS

============================= sda3/grub/grub.cfg: =============================

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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 326dd521-9a00-4f2a-b5c1-621d54070bbf
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 4c552331-20aa-4056-9776-a5e7d908c6c7
set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 4c552331-20aa-4056-9776-a5e7d908c6c7
	linux	/vmlinuz-2.6.35-24-generic root=UUID=326dd521-9a00-4f2a-b5c1-621d54070bbf ro   quiet splash
	initrd	/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 4c552331-20aa-4056-9776-a5e7d908c6c7
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/vmlinuz-2.6.35-24-generic root=UUID=326dd521-9a00-4f2a-b5c1-621d54070bbf ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 4c552331-20aa-4056-9776-a5e7d908c6c7
	linux	/vmlinuz-2.6.35-22-generic root=UUID=326dd521-9a00-4f2a-b5c1-621d54070bbf ro   quiet splash
	initrd	/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 4c552331-20aa-4056-9776-a5e7d908c6c7
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/vmlinuz-2.6.35-22-generic root=UUID=326dd521-9a00-4f2a-b5c1-621d54070bbf ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 4c552331-20aa-4056-9776-a5e7d908c6c7
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 4c552331-20aa-4056-9776-a5e7d908c6c7
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d888ecf688ecd3d2
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 264a0d454a0d12eb
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

=================== sda3: Location of files loaded by Grub: ===================


 107.2GB: grub/core.img
 107.2GB: grub/grub.cfg
 107.0GB: initrd.img-2.6.35-22-generic
 107.0GB: initrd.img-2.6.35-24-generic
 107.0GB: vmlinuz-2.6.35-22-generic
 107.0GB: vmlinuz-2.6.35-24-generic

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb7 during installation
UUID=326dd521-9a00-4f2a-b5c1-621d54070bbf /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdb3 during installation
UUID=4c552331-20aa-4056-9776-a5e7d908c6c7 /boot           ext4    defaults        0       2
# /home was on /dev/sdb5 during installation
UUID=e0fa3403-3d95-452f-9d25-43448363070b /home           ext4    defaults        0       2
# swap was on /dev/sdb6 during installation
UUID=db802a42-2720-47b8-8a53-6d13ecbd3659 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 123.5GB: initrd.img
 123.5GB: initrd.img.old
 123.5GB: vmlinuz
 123.5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  08 4e 26 4b a2 a4 90 a0  07 03 a0 82 80 57 08 63  |.N&K.........W.c|
00000010  f2 77 78 81 f9 24 68 92  31 1f 02 28 e8 c4 25 18  |.wx..$h.1..(..%.|
00000020  a8 1e 62 e2 0a a4 a4 b2  7e a3 ee c3 f8 e0 a2 4a  |..b.....~......J|
00000030  2b b6 33 20 38 c5 1f 63  a8 db 2a a6 fb e9 79 a1  |+.3 8..c..*...y.|
00000040  bd 60 04 0d 10 95 a0 ff  15 a1 f0 ec 61 96 a3 43  |.`..........a..C|
00000050  d3 a0 17 2b 5e 2b a6 80  6e 29 ce f2 6c 36 ec 55  |...+^+..n)..l6.U|
00000060  9d ad e1 93 19 a0 f0 7a  77 f2 89 f3 db df 8a bd  |.......zw.......|
00000070  91 2c f3 6f 48 e6 86 7c  d9 a2 1c 8d 80 cc e9 90  |.,.oH..|........|
00000080  4f 2f 6b 62 c9 b4 6e b5  d5 c1 f6 92 54 ab bd 0a  |O/kb..n.....T...|
00000090  ab bb cc 8a 6d dc 48 80  8e ec 29 4c ab b2 25 e5  |....m.H...)L..%.|
000000a0  ec 75 01 af fb 03 0c 4c  a9 cd 01 00 a4 2b fc 45  |.u.....L.....+.E|
000000b0  16 07 ea 5a f6 17 1b 05  86 d8 dd 22 3b dc 62 27  |...Z.......";.b'|
000000c0  d1 43 97 92 13 83 0d 33  e8 c8 37 ac 01 fe 20 4d  |.C.....3..7... M|
000000d0  65 84 4e 8a 4d c2 d5 b9  2a 38 54 6e 20 d7 63 93  |e.N.M...*8Tn .c.|
000000e0  a6 90 cb 62 b1 55 e3 93  17 51 07 f8 e3 0d 5a d9  |...b.U...Q....Z.|
000000f0  4f 19 0a bf e9 b7 f4 c0  76 e9 d8 be 90 83 58 f5  |O.......v.....X.|
00000100  37 a2 04 c3 0e 0d c9 8b  bf f8 72 96 5f c9 d4 a1  |7.........r._...|
00000110  89 95 df 61 05 2f 9f 46  f1 61 ca 8e c9 5a ac a7  |...a./.F.a...Z..|
00000120  e4 0a 25 ea ea c2 01 1d  15 10 32 4e a1 ce cf 7e  |..%.......2N...~|
00000130  dc 47 ee 52 57 57 dc 68  e9 d3 c0 53 51 6e ae 69  |.G.RWW.h...SQn.i|
00000140  d1 04 78 52 42 83 73 bb  d1 8f b0 25 d9 69 96 a0  |..xRB.s....%.i..|
00000150  8c 9a 2b 6d 32 42 82 f7  49 a3 d8 69 33 36 29 b2  |..+m2B..I..i36).|
00000160  b1 e7 1a 68 94 9b 55 9f  9c 13 b4 f2 f9 b7 b8 83  |...h..U.........|
00000170  c0 80 ba 17 dd d7 93 dc  ba 56 0e ce e8 8a fb 6e  |.........V.....n|
00000180  e5 26 84 65 4f ff c3 09  4d 13 7c e2 21 49 68 ce  |.&.eO...M.|.!Ih.|
00000190  94 3f 08 fc e3 ac 76 3b  40 a8 eb bd 87 a0 9c 2d  |.?....v;@......-|
000001a0  8e 5a 18 60 b6 df c8 9a  8d 21 3b 28 fe 37 09 57  |.Z.`.....!;(.7.W|
000001b0  1e 3e 2c 69 26 98 ea 1f  7f 5f 79 95 a3 aa 00 fe  |.>,i&...._y.....|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 00 2a 01 00 fe  |............*...|
000001d0  ff ff 05 fe ff ff 02 00  2a 01 00 d0 b2 00 00 00  |........*.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc 
```

I didn't. :[ 

What a big mistake.

Edit:
I did run chkdsk, I think before I partitioned it and I was also successful in booting into windows7 after I partitioned it.

---

### Post by amjjawad on 2010-12-24
If you did not delete the temp files, cookies, etc and you did not run disk defragment then I'm sorry to say that there's a great chance your Windows will not work.

Also, why did you create /boot partition? this is very very old scheme. You need root, swap and home is recommended.

Check my signature, there's a guide for Dual-Booting and it's new not old.

As for Windows, I'm not sure whether some files are lost or not.
Can you boot into XP? it's on another HDD already.

---

### Post by 6msj on 2010-12-24
I followed another guide on how to do it.

I don't have winxp installed on my computer right now, that must have been from before I installed win7.

---

### Post by theasprint on 2010-12-24
Hi,

However I rather suspect you have Windows XP, or XP based Recovery systems in your computer.
There seems to be a boot.ini, which the feature has been removed from Windows Vista onwards.
From Windows Vista onwards, BCD is used. (BCDEDIT.exe is now the application for changing boot options)

Also, "a recent hardware or software change" can suggest that you did some modification in your PC.
Did you upgrade your RAM or change your HDD or something?
Perhaps something is loose somewhere.

I have not faced this problem before but I can assume that it is not a MBR problem.
Perhaps the "software change" it mentioned is the Windows XP thing?

If you have a Windows Repair Disc, first try Startup Repair first. Then try the "hardware" option (I can't remember what is in those options). Or else just try the rest. But there's no need to use Command Prompt yet.

Windows Repair Discs can be obtained from :[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

I am willing to help you but your condition is a first-timer for me..

Good Luck :D

---

### Post by 6msj on 2010-12-24
The only things I did were 

1. chkdsk
2. partition using easues partition manager
3. boot back into win7
4. restart and start installing ubuntu
5. after it was done i used ubuntu for a while
6. restarted and can't load win7

I'm downloading the recovery disc now, hope for the best. :P

---

### Post by amjjawad on 2010-12-24
> **6msj said:**
> The only things I did were 

1. chkdsk
2. partition using easues partition manager
3. **boot back into win7**
4. restart and start installing ubuntu
5. after it was done i used ubuntu for a while
6. restarted and can't load win7

I'm downloading the recovery disc now, hope for the best. :P

After shrinking and booting back to Windows 7, were you able to boot into Windows 7 and login successfully?

Edit:
If you were able to login successfully to Windows 7 but after installing Ubuntu you couldn't then:
[http://www.ehow.com/how_4836283_repair-mbr-windows.html](http://www.ehow.com/how_4836283_repair-mbr-windows.html)

After that, you'll be able to boot into Windows but not Ubuntu so you need to re-install GRUB2 again: [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

OR ... try to install Ubuntu again without **/boot** partition. Of course you need to format the old partitions.
You'll need:
/ (root) which is ext4
/home which is ext4
swap which is swap-Linux

---

### Post by 6msj on 2010-12-24
Yeah, I was able to boot back in and login successfully. 

Can I use the repair MBR link with a win7 repair disc. I don't have access to a windows7 installation disc right now.

I'm also slightly confused with reinstalling GRUB commands and what to look for.

```
Mount the partition containing the Ubuntu installation. 
sudo mount /dev/sdXY /mnt

Example: sudo mount /dev/sda1 Note: If the user has a separate /boot partition, this must be mounted to /mnt/boot Note: If the user has a separate /home partition, this must be mounted to /mnt/home. Encrypted home partitions should work.
```

If I installed using /boot, /home, /, and swap files as partitions, which partition am I looking for to mount. I'm confused because I have both partitions and they said both must be mounted.

Thanks in advance.:D

---

### Post by Dark_Stang on 2010-12-24
If you can get a Windows Vista or 7 boot disc, you should be able to run
```
bootrec /fixmbr
or...
bootrec /fixboot
```

This will corrupt GRUB as well, so you'll have to reinstall that afterwards. But that might put windows in a good enough mood to fix itself.

---

### Post by amjjawad on 2010-12-24
> **6msj said:**
> Yeah, I was able to boot back in and login successfully. 

Can I use the repair MBR link with a win7 repair disc. I don't have access to a windows7 installation disc right now.

I'm also slightly confused with reinstalling GRUB commands and what to look for.

```
Mount the partition containing the Ubuntu installation. 
sudo mount /dev/sdXY /mnt

Example: sudo mount /dev/sda1 Note: If the user has a separate /boot partition, this must be mounted to /mnt/boot Note: If the user has a separate /home partition, this must be mounted to /mnt/home. Encrypted home partitions should work.
```If I installed using /boot, /home, /, and swap files as partitions, which partition am I looking for to mount. I'm confused because I have both partitions and they said both must be mounted.

Thanks in advance.:D

```
sudo mount /dev/sd**[COLOR=Red]a7[/COLOR]** /mnt
sudo grub-install --root-directory=/mnt/ /dev/sd**[COLOR=Red]a[/COLOR]**
```> Mount the partition containing the **Ubuntu installation**

**Edit:** 
> Can I use the repair MBR link with a win7 repair disc. I don't have access to a windows7 installation disc right now.
I guess you can.

---

### Post by 6msj on 2010-12-24
It works now!

I still have some questions left, after I used the repair disc and used the information from the link you sent me, it fixed what was wrong with my 7 but I can also still access Ubuntu, so i didn't have to fix grub. 

Any idea why that might be?

Thanks again!

Edit:
Hmnn, I'm able to log back into win7 but an annoying thing happens beforehand. After I enter win7 from the grub menu, itll say windows failed to boot(same error message) but after I select start windows normally, it works. Is there a way to make this more seamless. Thanks.

---

### Post by amjjawad on 2010-12-24
> **6msj said:**
> It works now!

I still have some questions left, after I used the repair disc and used the information from the link you sent me, it fixed what was wrong with my 7 but I can also still access Ubuntu, so i didn't have to fix grub. 

Any idea why that might be?

Thanks again!

Edit:
Hmnn, I'm able to log back into win7 but an annoying thing happens beforehand. After I enter win7 from the grub menu, itll say windows failed to boot(same error message) but after I select start windows normally, it works. Is there a way to make this more seamless. Thanks.

Did you re-install GRUB2?
Did you run:

```
sudo update-grub
```

from Terminal?

---

### Post by 6msj on 2010-12-24
I didn't do either, will do it now.

To clarify, I reinstall grub and then use that command to update it? 

Thanks.

---

### Post by amjjawad on 2010-12-24
> **6msj said:**
> I didn't do either, will do it now.

To clarify, I reinstall grub and then use that command to update it? 

Thanks.

My friend, you're posting then you're updating your posts so I'm totally lost :(

I posted on [http://ubuntuforums.org/showpost.php?p=10276049&postcount=12](http://ubuntuforums.org/showpost.php?p=10276049&postcount=12) already how to do it.

You just need to re-install GRUB2 
Reboot
Login to Ubuntu
and do:
```
sudo update-grub

```
Reboot
and Both Windows and Ubuntu should work.

If not, please let me know.

---

### Post by 6msj on 2010-12-24
Sorry for the confusing edits.

I booted up to live cd and went into the terminal and tried to input this command.

sudo mount /dev/sda7 /mnt

It says it doesn't exist and most of my boots are sdc[1-7]

I assume you mount with sdc7 then?

After I mount sdc7, do I still use this command?

sudo grub-install --root-directory=/mnt/ /dev/sda

---

### Post by amjjawad on 2010-12-24
> **6msj said:**
> Sorry for the confusing edits.

I booted up to live cd and went into the terminal and tried to input this command.

sudo mount /dev/sda7 /mnt

It says it doesn't exist and most of my boots are sdc[1-7]

I assume you mount with sdc7 then?

After I mount sdc7, do I still use this command?

sudo grub-install --root-directory=/mnt/ /dev/sda

Oh great!
Please, post back the result of this again:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by amjjawad on 2010-12-24
I hope you still booting from the LiveCD. If yes, please post back the result of Boot Script

Don't run any command as of now. Let me check your boot script first.

---

### Post by 6msj on 2010-12-24
From LiveCD

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #3 for (,msdos3)/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /bootmgr /ntldr /NTDETECT.COM

sdc3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sdc4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048 1,953,525,167 1,953,523,120   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          2,048   208,925,324   208,923,277   7 HPFS/NTFS
/dev/sdc2         291,909,632   312,573,951    20,664,320   7 HPFS/NTFS
/dev/sdc3         208,926,720   209,901,567       974,848  83 Linux
/dev/sdc4         209,903,614   291,907,583    82,003,970   5 Extended
/dev/sdc5         209,903,616   229,433,343    19,529,728  83 Linux
/dev/sdc6         229,435,392   241,151,999    11,716,608  82 Linux swap / Solaris
/dev/sdc7         241,154,048   291,907,583    50,753,536  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        0EC08480C084702F                       ntfs       Elements                      
/dev/sda: PTTYPE="dos" 
/dev/sdc1        D888ECF688ECD3D2                       ntfs                                     
/dev/sdc2        264A0D454A0D12EB                       ntfs       HP_RECOVERY                   
/dev/sdc3        4c552331-20aa-4056-9776-a5e7d908c6c7   ext4                                     
/dev/sdc4: PTTYPE="dos" 
/dev/sdc5        e0fa3403-3d95-452f-9d25-43448363070b   ext4                                     
/dev/sdc6        db802a42-2720-47b8-8a53-6d13ecbd3659   swap                                     
/dev/sdc7        326dd521-9a00-4f2a-b5c1-621d54070bbf   ext4                                     
/dev/sdc: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc7        /mnt                     ext4       (rw)


================================ sdc2/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=2 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT 
e:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /CMDCONS 

============================= sdc3/grub/grub.cfg: =============================

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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 326dd521-9a00-4f2a-b5c1-621d54070bbf
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 4c552331-20aa-4056-9776-a5e7d908c6c7
set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 4c552331-20aa-4056-9776-a5e7d908c6c7
    linux    /vmlinuz-2.6.35-24-generic root=UUID=326dd521-9a00-4f2a-b5c1-621d54070bbf ro   quiet splash
    initrd    /initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 4c552331-20aa-4056-9776-a5e7d908c6c7
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /vmlinuz-2.6.35-24-generic root=UUID=326dd521-9a00-4f2a-b5c1-621d54070bbf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 4c552331-20aa-4056-9776-a5e7d908c6c7
    linux    /vmlinuz-2.6.35-22-generic root=UUID=326dd521-9a00-4f2a-b5c1-621d54070bbf ro   quiet splash
    initrd    /initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 4c552331-20aa-4056-9776-a5e7d908c6c7
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /vmlinuz-2.6.35-22-generic root=UUID=326dd521-9a00-4f2a-b5c1-621d54070bbf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 4c552331-20aa-4056-9776-a5e7d908c6c7
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 4c552331-20aa-4056-9776-a5e7d908c6c7
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set d888ecf688ecd3d2
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 264a0d454a0d12eb
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

=================== sdc3: Location of files loaded by Grub: ===================


 107.2GB: grub/core.img
 107.2GB: grub/grub.cfg
 107.0GB: initrd.img-2.6.35-22-generic
 107.0GB: initrd.img-2.6.35-24-generic
 107.0GB: vmlinuz-2.6.35-22-generic
 107.0GB: vmlinuz-2.6.35-24-generic

=============================== sdc7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb7 during installation
UUID=326dd521-9a00-4f2a-b5c1-621d54070bbf /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdb3 during installation
UUID=4c552331-20aa-4056-9776-a5e7d908c6c7 /boot           ext4    defaults        0       2
# /home was on /dev/sdb5 during installation
UUID=e0fa3403-3d95-452f-9d25-43448363070b /home           ext4    defaults        0       2
# swap was on /dev/sdb6 during installation
UUID=db802a42-2720-47b8-8a53-6d13ecbd3659 none            swap    sw              0       0
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc4

00000000  08 4e 26 4b a2 a4 90 a0  07 03 a0 82 80 57 08 63  |.N&K.........W.c|
00000010  f2 77 78 81 f9 24 68 92  31 1f 02 28 e8 c4 25 18  |.wx..$h.1..(..%.|
00000020  a8 1e 62 e2 0a a4 a4 b2  7e a3 ee c3 f8 e0 a2 4a  |..b.....~......J|
00000030  2b b6 33 20 38 c5 1f 63  a8 db 2a a6 fb e9 79 a1  |+.3 8..c..*...y.|
00000040  bd 60 04 0d 10 95 a0 ff  15 a1 f0 ec 61 96 a3 43  |.`..........a..C|
00000050  d3 a0 17 2b 5e 2b a6 80  6e 29 ce f2 6c 36 ec 55  |...+^+..n)..l6.U|
00000060  9d ad e1 93 19 a0 f0 7a  77 f2 89 f3 db df 8a bd  |.......zw.......|
00000070  91 2c f3 6f 48 e6 86 7c  d9 a2 1c 8d 80 cc e9 90  |.,.oH..|........|
00000080  4f 2f 6b 62 c9 b4 6e b5  d5 c1 f6 92 54 ab bd 0a  |O/kb..n.....T...|
00000090  ab bb cc 8a 6d dc 48 80  8e ec 29 4c ab b2 25 e5  |....m.H...)L..%.|
000000a0  ec 75 01 af fb 03 0c 4c  a9 cd 01 00 a4 2b fc 45  |.u.....L.....+.E|
000000b0  16 07 ea 5a f6 17 1b 05  86 d8 dd 22 3b dc 62 27  |...Z.......";.b'|
000000c0  d1 43 97 92 13 83 0d 33  e8 c8 37 ac 01 fe 20 4d  |.C.....3..7... M|
000000d0  65 84 4e 8a 4d c2 d5 b9  2a 38 54 6e 20 d7 63 93  |e.N.M...*8Tn .c.|
000000e0  a6 90 cb 62 b1 55 e3 93  17 51 07 f8 e3 0d 5a d9  |...b.U...Q....Z.|
000000f0  4f 19 0a bf e9 b7 f4 c0  76 e9 d8 be 90 83 58 f5  |O.......v.....X.|
00000100  37 a2 04 c3 0e 0d c9 8b  bf f8 72 96 5f c9 d4 a1  |7.........r._...|
00000110  89 95 df 61 05 2f 9f 46  f1 61 ca 8e c9 5a ac a7  |...a./.F.a...Z..|
00000120  e4 0a 25 ea ea c2 01 1d  15 10 32 4e a1 ce cf 7e  |..%.......2N...~|
00000130  dc 47 ee 52 57 57 dc 68  e9 d3 c0 53 51 6e ae 69  |.G.RWW.h...SQn.i|
00000140  d1 04 78 52 42 83 73 bb  d1 8f b0 25 d9 69 96 a0  |..xRB.s....%.i..|
00000150  8c 9a 2b 6d 32 42 82 f7  49 a3 d8 69 33 36 29 b2  |..+m2B..I..i36).|
00000160  b1 e7 1a 68 94 9b 55 9f  9c 13 b4 f2 f9 b7 b8 83  |...h..U.........|
00000170  c0 80 ba 17 dd d7 93 dc  ba 56 0e ce e8 8a fb 6e  |.........V.....n|
00000180  e5 26 84 65 4f ff c3 09  4d 13 7c e2 21 49 68 ce  |.&.eO...M.|.!Ih.|
00000190  94 3f 08 fc e3 ac 76 3b  40 a8 eb bd 87 a0 9c 2d  |.?....v;@......-|
000001a0  8e 5a 18 60 b6 df c8 9a  8d 21 3b 28 fe 37 09 57  |.Z.`.....!;(.7.W|
000001b0  1e 3e 2c 69 26 98 ea 1f  7f 5f 79 95 a3 aa 00 fe  |.>,i&...._y.....|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 00 2a 01 00 fe  |............*...|
000001d0  ff ff 05 fe ff ff 02 00  2a 01 00 d0 b2 00 00 00  |........*.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

---

### Post by amjjawad on 2010-12-24
Ok, thanks for posting it again.

One question before we carry on.

You do have two HDDs, one is 160GB and the other is 1TB.

The one with 160GB has Linux while the other one with 1TB has Windows, right?

Have you changed the sequence of booting the HDD in BIOS?

Edit: Please don't reboot. If you're still booting from the LiveCD, stay where you're :)

---

### Post by 6msj on 2010-12-24
My external1TB doesn't have any OS's on it, the 160 gb has both linux and windows7 though. 

I dont think I changed the sequence, my computer boots from cd/dvd drive first so I didn't have to change any sequences before installing.

Thanks for the fast replies. :)

---

### Post by amjjawad on 2010-12-24
> **6msj said:**
> My external1TB doesn't have any OS's on it, the 160 gb has both linux and windows7 though. 

I dont think I changed the sequence, my computer boots from cd/dvd drive first so I didn't have to change any sequences before installing.

Thanks for the fast replies. :)

OMG!
Do me a favor and unplug that external HDD please.

Make sure your BIOS boot from CD first then your 160GB Internal HDD.

Please, post back the result of the boot script without that external HDD.
I'm so much confused now because you did NOT mention that before.
Your first boot script result is quite different from the second one.

Now, please, follow the most recent steps and FORGET everything else.
Let's do this step by step.

---

### Post by 6msj on 2010-12-24
Okay, this is right after unplugging the external without leaving the LiveCD.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #3 for (,msdos3)/grub.

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /bootmgr /ntldr /NTDETECT.COM

sdc3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sdc4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          2,048   208,925,324   208,923,277   7 HPFS/NTFS
/dev/sdc2         291,909,632   312,573,951    20,664,320   7 HPFS/NTFS
/dev/sdc3         208,926,720   209,901,567       974,848  83 Linux
/dev/sdc4         209,903,614   291,907,583    82,003,970   5 Extended
/dev/sdc5         209,903,616   229,433,343    19,529,728  83 Linux
/dev/sdc6         229,435,392   241,151,999    11,716,608  82 Linux swap / Solaris
/dev/sdc7         241,154,048   291,907,583    50,753,536  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sdc1        D888ECF688ECD3D2                       ntfs                                     
/dev/sdc2        264A0D454A0D12EB                       ntfs       HP_RECOVERY                   
/dev/sdc3        4c552331-20aa-4056-9776-a5e7d908c6c7   ext4                                     
/dev/sdc4: PTTYPE="dos" 
/dev/sdc5        e0fa3403-3d95-452f-9d25-43448363070b   ext4                                     
/dev/sdc6        db802a42-2720-47b8-8a53-6d13ecbd3659   swap                                     
/dev/sdc7        326dd521-9a00-4f2a-b5c1-621d54070bbf   ext4                                     
/dev/sdc: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc7        /mnt                     ext4       (rw)


================================ sdc2/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=2 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT 
e:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /CMDCONS 

============================= sdc3/grub/grub.cfg: =============================

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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 326dd521-9a00-4f2a-b5c1-621d54070bbf
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 4c552331-20aa-4056-9776-a5e7d908c6c7
set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 4c552331-20aa-4056-9776-a5e7d908c6c7
    linux    /vmlinuz-2.6.35-24-generic root=UUID=326dd521-9a00-4f2a-b5c1-621d54070bbf ro   quiet splash
    initrd    /initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 4c552331-20aa-4056-9776-a5e7d908c6c7
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /vmlinuz-2.6.35-24-generic root=UUID=326dd521-9a00-4f2a-b5c1-621d54070bbf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 4c552331-20aa-4056-9776-a5e7d908c6c7
    linux    /vmlinuz-2.6.35-22-generic root=UUID=326dd521-9a00-4f2a-b5c1-621d54070bbf ro   quiet splash
    initrd    /initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 4c552331-20aa-4056-9776-a5e7d908c6c7
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /vmlinuz-2.6.35-22-generic root=UUID=326dd521-9a00-4f2a-b5c1-621d54070bbf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 4c552331-20aa-4056-9776-a5e7d908c6c7
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 4c552331-20aa-4056-9776-a5e7d908c6c7
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set d888ecf688ecd3d2
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 264a0d454a0d12eb
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

=================== sdc3: Location of files loaded by Grub: ===================


 107.2GB: grub/core.img
 107.2GB: grub/grub.cfg
 107.0GB: initrd.img-2.6.35-22-generic
 107.0GB: initrd.img-2.6.35-24-generic
 107.0GB: vmlinuz-2.6.35-22-generic
 107.0GB: vmlinuz-2.6.35-24-generic

=============================== sdc7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb7 during installation
UUID=326dd521-9a00-4f2a-b5c1-621d54070bbf /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdb3 during installation
UUID=4c552331-20aa-4056-9776-a5e7d908c6c7 /boot           ext4    defaults        0       2
# /home was on /dev/sdb5 during installation
UUID=e0fa3403-3d95-452f-9d25-43448363070b /home           ext4    defaults        0       2
# swap was on /dev/sdb6 during installation
UUID=db802a42-2720-47b8-8a53-6d13ecbd3659 none            swap    sw              0       0
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc4

00000000  08 4e 26 4b a2 a4 90 a0  07 03 a0 82 80 57 08 63  |.N&K.........W.c|
00000010  f2 77 78 81 f9 24 68 92  31 1f 02 28 e8 c4 25 18  |.wx..$h.1..(..%.|
00000020  a8 1e 62 e2 0a a4 a4 b2  7e a3 ee c3 f8 e0 a2 4a  |..b.....~......J|
00000030  2b b6 33 20 38 c5 1f 63  a8 db 2a a6 fb e9 79 a1  |+.3 8..c..*...y.|
00000040  bd 60 04 0d 10 95 a0 ff  15 a1 f0 ec 61 96 a3 43  |.`..........a..C|
00000050  d3 a0 17 2b 5e 2b a6 80  6e 29 ce f2 6c 36 ec 55  |...+^+..n)..l6.U|
00000060  9d ad e1 93 19 a0 f0 7a  77 f2 89 f3 db df 8a bd  |.......zw.......|
00000070  91 2c f3 6f 48 e6 86 7c  d9 a2 1c 8d 80 cc e9 90  |.,.oH..|........|
00000080  4f 2f 6b 62 c9 b4 6e b5  d5 c1 f6 92 54 ab bd 0a  |O/kb..n.....T...|
00000090  ab bb cc 8a 6d dc 48 80  8e ec 29 4c ab b2 25 e5  |....m.H...)L..%.|
000000a0  ec 75 01 af fb 03 0c 4c  a9 cd 01 00 a4 2b fc 45  |.u.....L.....+.E|
000000b0  16 07 ea 5a f6 17 1b 05  86 d8 dd 22 3b dc 62 27  |...Z.......";.b'|
000000c0  d1 43 97 92 13 83 0d 33  e8 c8 37 ac 01 fe 20 4d  |.C.....3..7... M|
000000d0  65 84 4e 8a 4d c2 d5 b9  2a 38 54 6e 20 d7 63 93  |e.N.M...*8Tn .c.|
000000e0  a6 90 cb 62 b1 55 e3 93  17 51 07 f8 e3 0d 5a d9  |...b.U...Q....Z.|
000000f0  4f 19 0a bf e9 b7 f4 c0  76 e9 d8 be 90 83 58 f5  |O.......v.....X.|
00000100  37 a2 04 c3 0e 0d c9 8b  bf f8 72 96 5f c9 d4 a1  |7.........r._...|
00000110  89 95 df 61 05 2f 9f 46  f1 61 ca 8e c9 5a ac a7  |...a./.F.a...Z..|
00000120  e4 0a 25 ea ea c2 01 1d  15 10 32 4e a1 ce cf 7e  |..%.......2N...~|
00000130  dc 47 ee 52 57 57 dc 68  e9 d3 c0 53 51 6e ae 69  |.G.RWW.h...SQn.i|
00000140  d1 04 78 52 42 83 73 bb  d1 8f b0 25 d9 69 96 a0  |..xRB.s....%.i..|
00000150  8c 9a 2b 6d 32 42 82 f7  49 a3 d8 69 33 36 29 b2  |..+m2B..I..i36).|
00000160  b1 e7 1a 68 94 9b 55 9f  9c 13 b4 f2 f9 b7 b8 83  |...h..U.........|
00000170  c0 80 ba 17 dd d7 93 dc  ba 56 0e ce e8 8a fb 6e  |.........V.....n|
00000180  e5 26 84 65 4f ff c3 09  4d 13 7c e2 21 49 68 ce  |.&.eO...M.|.!Ih.|
00000190  94 3f 08 fc e3 ac 76 3b  40 a8 eb bd 87 a0 9c 2d  |.?....v;@......-|
000001a0  8e 5a 18 60 b6 df c8 9a  8d 21 3b 28 fe 37 09 57  |.Z.`.....!;(.7.W|
000001b0  1e 3e 2c 69 26 98 ea 1f  7f 5f 79 95 a3 aa 00 fe  |.>,i&...._y.....|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 00 2a 01 00 fe  |............*...|
000001d0  ff ff 05 fe ff ff 02 00  2a 01 00 d0 b2 00 00 00  |........*.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

---

### Post by amjjawad on 2010-12-24
> **amjjawad said:**
> OMG!
Do me a favor and unplug that external HDD please.

**Make sure your BIOS boot from CD first then your 160GB Internal HDD.**

Please, post back the result of the boot script without that external HDD.
I'm so much confused now because you did NOT mention that before.
Your first boot script result is quite different from the second one.

Now, please, follow the most recent steps and FORGET everything else.
Let's do this step by step.

I thought you'll reboot!!!!
I asked you to forget the other posts and let's start again.
Anyway, sdc must be sda as long as you have ONLY one HDD in your system.

Now, please, read this carefully:

1- End the Live Session and reboot your system. You'll be asked to take out the Live CD

2- Insert the Windows Repair CD

3- Reboot

4- Enter BIOS

5- Double check your BIOS settings. Make sure CD First then HDD (the internal one - 160GB). DO NOT plug the external HDD please.

6- Use Fix MBR for Windows 7.

7- Reboot and try to login to Windows 7.

8- If you managed to login to Windows 7 successfully, then put the LiveCD for Ubuntu and reboot

9- Before you re-install GRUB2 please post back the result of:

```
sudo fdisk -l

```

That's small "L" at the end.

Hope we don't need to run that script again ;)
I know you'll kill me but I have to do the same :D hahaha. Just kidding :)

Waiting for you.

Please, DO NOT use your external HDD now. Just put it 10m far from you ;)

---

### Post by amjjawad on 2010-12-24
Buddy, it's too late here and I might fall asleep at anytime.
However, I'd like to post something very useful. In case I'm still awake, I'll be with you step by step but in case I'll fall asleep on the keyboard, then ... :)

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
Check #13.

This is much better than the official guide I have previously posted.
It's clearly mentioned that if you have /boot then you need to mount it.

Thus, you need to replace sdXY with sda3 and sdX with sda.

And to be in the same side, I'm going to copy that here.

[COLOR=Red][B]NOTE: It's not from me, it's written by drs305.
[/B][/COLOR] 

**[COLOR=Navy][SIZE=3]Reinstalling GRUB 2 from LiveCD[/SIZE][/COLOR] **
If you cannot boot from GRUB 2 and need to reinstall it, here is the  simple method. For more details or for advanced options, refer to the  Ubuntu community documentation here: [Grub2 - Reinstalling GRUB 2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202"):
[LIST]
[*]Boot the Ubuntu Live CD (Try without installing).
[*]From the Desktop, open a terminal - Applications, Accessories, Terminal.
[*]Determine your normal system partition - `sudo fdisk -l`  (That is a lowercase L)
[*]If you aren't sure, run `df -Th`. Look for the correct disk size and ext3 or ext4 format.
[*]Mount your normal system partition:      Code:
     sudo mount /dev/sdXY /mnt
[LIST]
[*]If you aren't sure if you mounted the correct partition,  once it's mounted run "nautilus /mnt" to inspect the partition. If it is  the correct partition, you should see the normal Ubuntu folders such as  /bin, /boot, /etc, /home, etc
[/LIST]

[LIST]
[*]Example: sudo mount /dev/sd*a1* /mnt
[*]Note: The partition to mount is normally the partition on which  Ubuntu was installed: sda1, sdb5, etc. If you have a separate /boot  partition, use the device on which the /boot partition is located. Grub 2  works best when installed in the MBR of the drive to which BIOS boots.  Also remember that you *mount* the partition (including the number) in this step, but you do *not* include the partition number when you run the "sudo grub-install" command later.
[*]Note: GRUB 2 counts the first drive (X) as "0", but the first partition (Y) as "1"
[/LIST]
 
[*]Only if you have a separate boot partition:
[LIST]
[*]     Code:
     sudo mount /dev/sdXY /mnt/boot 
 with sdXY being your /boot partition designation.
[/LIST]
 
[*]Reinstall GRUB 2:      Code:
     sudo grub-install --root-directory=/mnt /dev/sdX 
  Do NOT include the partition number.
[*]
[LIST]
[*]Example: sudo grub-install --root-directory=/mnt /dev/sd*a*
[*]Note: Substitute the device on which Ubuntu was installed - sda, sdb, etc. Do *not* specify a partition number.
[/LIST]
 
[*]Unmount the partition *:       Code:
     sudo umount /mnt
[LIST]
[*]* Note: If you mounted a separate /boot partition, unmount it first:  
     Code:
     sudo umount /mnt/boot
[/LIST]
 
[*]Reboot.
[/LIST]

---

### Post by 6msj on 2010-12-24
[http://img30.imageshack.us/img30/5213/screenshotwq.png](http://img30.imageshack.us/img30/5213/screenshotwq.png)

Hope you're still awake lol.

Edit:

Forgot to mention, I was able to boot to win7 without any errors.

---

### Post by amjjawad on 2010-12-24
> **6msj said:**
> [http://img30.imageshack.us/img30/5213/screenshotwq.png](http://img30.imageshack.us/img30/5213/screenshotwq.png)

Hope you're still awake lol.

Edit:

Forgot to mention, I was able to boot to win7 without any errors.

I just washed my face and ate some chocolate so hope I could stay awake for a bit more :)

Now, did you plug the external HDD again? why your drives letters are keep changing? now, you have sdb.
Anyway,

It's time to re-install GRUB. But to be in the safest side and please don't kill me ... the script thingy again please :)
want to make sure that Windows Boot Loader is installed now in the same drive. Because before, it was installed in the MBR of the external HDD.

I know you managed to boot into Windows without any problems but can't understand why your drives letters are changing. That's why I'm asking you to do the boot script for the 5th time :D

---

### Post by 6msj on 2010-12-24
The External has stayed unplugged.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #3 for (,msdos3)/grub.

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /bootmgr /ntldr /NTDETECT.COM

sdb3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   208,925,324   208,923,277   7 HPFS/NTFS
/dev/sdb2         291,909,632   312,573,951    20,664,320   7 HPFS/NTFS
/dev/sdb3         208,926,720   209,901,567       974,848  83 Linux
/dev/sdb4         209,903,614   291,907,583    82,003,970   5 Extended
/dev/sdb5         209,903,616   229,433,343    19,529,728  83 Linux
/dev/sdb6         229,435,392   241,151,999    11,716,608  82 Linux swap / Solaris
/dev/sdb7         241,154,048   291,907,583    50,753,536  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sdb1        D888ECF688ECD3D2                       ntfs                                     
/dev/sdb2        264A0D454A0D12EB                       ntfs       HP_RECOVERY                   
/dev/sdb3        4c552331-20aa-4056-9776-a5e7d908c6c7   ext4                                     
/dev/sdb4: PTTYPE="dos" 
/dev/sdb5        e0fa3403-3d95-452f-9d25-43448363070b   ext4                                     
/dev/sdb6        db802a42-2720-47b8-8a53-6d13ecbd3659   swap                                     
/dev/sdb7        326dd521-9a00-4f2a-b5c1-621d54070bbf   ext4                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sda: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb3        /mnt                     ext4       (rw)


================================ sdb2/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=2 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT 
e:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /CMDCONS 

============================= sdb3/grub/grub.cfg: =============================

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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 326dd521-9a00-4f2a-b5c1-621d54070bbf
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 4c552331-20aa-4056-9776-a5e7d908c6c7
set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 4c552331-20aa-4056-9776-a5e7d908c6c7
    linux    /vmlinuz-2.6.35-24-generic root=UUID=326dd521-9a00-4f2a-b5c1-621d54070bbf ro   quiet splash
    initrd    /initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 4c552331-20aa-4056-9776-a5e7d908c6c7
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /vmlinuz-2.6.35-24-generic root=UUID=326dd521-9a00-4f2a-b5c1-621d54070bbf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 4c552331-20aa-4056-9776-a5e7d908c6c7
    linux    /vmlinuz-2.6.35-22-generic root=UUID=326dd521-9a00-4f2a-b5c1-621d54070bbf ro   quiet splash
    initrd    /initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 4c552331-20aa-4056-9776-a5e7d908c6c7
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /vmlinuz-2.6.35-22-generic root=UUID=326dd521-9a00-4f2a-b5c1-621d54070bbf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 4c552331-20aa-4056-9776-a5e7d908c6c7
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 4c552331-20aa-4056-9776-a5e7d908c6c7
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set d888ecf688ecd3d2
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 264a0d454a0d12eb
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

=================== sdb3: Location of files loaded by Grub: ===================


 107.2GB: grub/core.img
 107.2GB: grub/grub.cfg
 107.0GB: initrd.img-2.6.35-22-generic
 107.0GB: initrd.img-2.6.35-24-generic
 107.0GB: vmlinuz-2.6.35-22-generic
 107.0GB: vmlinuz-2.6.35-24-generic

=============================== sdb7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb7 during installation
UUID=326dd521-9a00-4f2a-b5c1-621d54070bbf /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdb3 during installation
UUID=4c552331-20aa-4056-9776-a5e7d908c6c7 /boot           ext4    defaults        0       2
# /home was on /dev/sdb5 during installation
UUID=e0fa3403-3d95-452f-9d25-43448363070b /home           ext4    defaults        0       2
# swap was on /dev/sdb6 during installation
UUID=db802a42-2720-47b8-8a53-6d13ecbd3659 none            swap    sw              0       0
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb4

00000000  08 4e 26 4b a2 a4 90 a0  07 03 a0 82 80 57 08 63  |.N&K.........W.c|
00000010  f2 77 78 81 f9 24 68 92  31 1f 02 28 e8 c4 25 18  |.wx..$h.1..(..%.|
00000020  a8 1e 62 e2 0a a4 a4 b2  7e a3 ee c3 f8 e0 a2 4a  |..b.....~......J|
00000030  2b b6 33 20 38 c5 1f 63  a8 db 2a a6 fb e9 79 a1  |+.3 8..c..*...y.|
00000040  bd 60 04 0d 10 95 a0 ff  15 a1 f0 ec 61 96 a3 43  |.`..........a..C|
00000050  d3 a0 17 2b 5e 2b a6 80  6e 29 ce f2 6c 36 ec 55  |...+^+..n)..l6.U|
00000060  9d ad e1 93 19 a0 f0 7a  77 f2 89 f3 db df 8a bd  |.......zw.......|
00000070  91 2c f3 6f 48 e6 86 7c  d9 a2 1c 8d 80 cc e9 90  |.,.oH..|........|
00000080  4f 2f 6b 62 c9 b4 6e b5  d5 c1 f6 92 54 ab bd 0a  |O/kb..n.....T...|
00000090  ab bb cc 8a 6d dc 48 80  8e ec 29 4c ab b2 25 e5  |....m.H...)L..%.|
000000a0  ec 75 01 af fb 03 0c 4c  a9 cd 01 00 a4 2b fc 45  |.u.....L.....+.E|
000000b0  16 07 ea 5a f6 17 1b 05  86 d8 dd 22 3b dc 62 27  |...Z.......";.b'|
000000c0  d1 43 97 92 13 83 0d 33  e8 c8 37 ac 01 fe 20 4d  |.C.....3..7... M|
000000d0  65 84 4e 8a 4d c2 d5 b9  2a 38 54 6e 20 d7 63 93  |e.N.M...*8Tn .c.|
000000e0  a6 90 cb 62 b1 55 e3 93  17 51 07 f8 e3 0d 5a d9  |...b.U...Q....Z.|
000000f0  4f 19 0a bf e9 b7 f4 c0  76 e9 d8 be 90 83 58 f5  |O.......v.....X.|
00000100  37 a2 04 c3 0e 0d c9 8b  bf f8 72 96 5f c9 d4 a1  |7.........r._...|
00000110  89 95 df 61 05 2f 9f 46  f1 61 ca 8e c9 5a ac a7  |...a./.F.a...Z..|
00000120  e4 0a 25 ea ea c2 01 1d  15 10 32 4e a1 ce cf 7e  |..%.......2N...~|
00000130  dc 47 ee 52 57 57 dc 68  e9 d3 c0 53 51 6e ae 69  |.G.RWW.h...SQn.i|
00000140  d1 04 78 52 42 83 73 bb  d1 8f b0 25 d9 69 96 a0  |..xRB.s....%.i..|
00000150  8c 9a 2b 6d 32 42 82 f7  49 a3 d8 69 33 36 29 b2  |..+m2B..I..i36).|
00000160  b1 e7 1a 68 94 9b 55 9f  9c 13 b4 f2 f9 b7 b8 83  |...h..U.........|
00000170  c0 80 ba 17 dd d7 93 dc  ba 56 0e ce e8 8a fb 6e  |.........V.....n|
00000180  e5 26 84 65 4f ff c3 09  4d 13 7c e2 21 49 68 ce  |.&.eO...M.|.!Ih.|
00000190  94 3f 08 fc e3 ac 76 3b  40 a8 eb bd 87 a0 9c 2d  |.?....v;@......-|
000001a0  8e 5a 18 60 b6 df c8 9a  8d 21 3b 28 fe 37 09 57  |.Z.`.....!;(.7.W|
000001b0  1e 3e 2c 69 26 98 ea 1f  7f 5f 79 95 a3 aa 00 fe  |.>,i&...._y.....|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 00 2a 01 00 fe  |............*...|
000001d0  ff ff 05 fe ff ff 02 00  2a 01 00 d0 b2 00 00 00  |........*.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sda 
```

---

### Post by amjjawad on 2010-12-24
> **6msj said:**
> The External has stayed unplugged.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #3 for (,msdos3)/grub.

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /bootmgr /ntldr /NTDETECT.COM

sdb3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   208,925,324   208,923,277   7 HPFS/NTFS
/dev/sdb2         291,909,632   312,573,951    20,664,320   7 HPFS/NTFS
/dev/sdb3         208,926,720   209,901,567       974,848  83 Linux
/dev/sdb4         209,903,614   291,907,583    82,003,970   5 Extended
/dev/sdb5         209,903,616   229,433,343    19,529,728  83 Linux
/dev/sdb6         229,435,392   241,151,999    11,716,608  82 Linux swap / Solaris
/dev/sdb7         241,154,048   291,907,583    50,753,536  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sdb1        D888ECF688ECD3D2                       ntfs                                     
/dev/sdb2        264A0D454A0D12EB                       ntfs       HP_RECOVERY                   
/dev/sdb3        4c552331-20aa-4056-9776-a5e7d908c6c7   ext4                                     
/dev/sdb4: PTTYPE="dos" 
/dev/sdb5        e0fa3403-3d95-452f-9d25-43448363070b   ext4                                     
/dev/sdb6        db802a42-2720-47b8-8a53-6d13ecbd3659   swap                                     
/dev/sdb7        326dd521-9a00-4f2a-b5c1-621d54070bbf   ext4                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sda: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb3        /mnt                     ext4       (rw)


================================ sdb2/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=2 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT 
e:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /CMDCONS 

============================= sdb3/grub/grub.cfg: =============================

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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 326dd521-9a00-4f2a-b5c1-621d54070bbf
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 4c552331-20aa-4056-9776-a5e7d908c6c7
set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 4c552331-20aa-4056-9776-a5e7d908c6c7
    linux    /vmlinuz-2.6.35-24-generic root=UUID=326dd521-9a00-4f2a-b5c1-621d54070bbf ro   quiet splash
    initrd    /initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 4c552331-20aa-4056-9776-a5e7d908c6c7
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /vmlinuz-2.6.35-24-generic root=UUID=326dd521-9a00-4f2a-b5c1-621d54070bbf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 4c552331-20aa-4056-9776-a5e7d908c6c7
    linux    /vmlinuz-2.6.35-22-generic root=UUID=326dd521-9a00-4f2a-b5c1-621d54070bbf ro   quiet splash
    initrd    /initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 4c552331-20aa-4056-9776-a5e7d908c6c7
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /vmlinuz-2.6.35-22-generic root=UUID=326dd521-9a00-4f2a-b5c1-621d54070bbf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 4c552331-20aa-4056-9776-a5e7d908c6c7
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 4c552331-20aa-4056-9776-a5e7d908c6c7
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set d888ecf688ecd3d2
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 264a0d454a0d12eb
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

=================== sdb3: Location of files loaded by Grub: ===================


 107.2GB: grub/core.img
 107.2GB: grub/grub.cfg
 107.0GB: initrd.img-2.6.35-22-generic
 107.0GB: initrd.img-2.6.35-24-generic
 107.0GB: vmlinuz-2.6.35-22-generic
 107.0GB: vmlinuz-2.6.35-24-generic

=============================== sdb7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb7 during installation
UUID=326dd521-9a00-4f2a-b5c1-621d54070bbf /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdb3 during installation
UUID=4c552331-20aa-4056-9776-a5e7d908c6c7 /boot           ext4    defaults        0       2
# /home was on /dev/sdb5 during installation
UUID=e0fa3403-3d95-452f-9d25-43448363070b /home           ext4    defaults        0       2
# swap was on /dev/sdb6 during installation
UUID=db802a42-2720-47b8-8a53-6d13ecbd3659 none            swap    sw              0       0
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb4

00000000  08 4e 26 4b a2 a4 90 a0  07 03 a0 82 80 57 08 63  |.N&K.........W.c|
00000010  f2 77 78 81 f9 24 68 92  31 1f 02 28 e8 c4 25 18  |.wx..$h.1..(..%.|
00000020  a8 1e 62 e2 0a a4 a4 b2  7e a3 ee c3 f8 e0 a2 4a  |..b.....~......J|
00000030  2b b6 33 20 38 c5 1f 63  a8 db 2a a6 fb e9 79 a1  |+.3 8..c..*...y.|
00000040  bd 60 04 0d 10 95 a0 ff  15 a1 f0 ec 61 96 a3 43  |.`..........a..C|
00000050  d3 a0 17 2b 5e 2b a6 80  6e 29 ce f2 6c 36 ec 55  |...+^+..n)..l6.U|
00000060  9d ad e1 93 19 a0 f0 7a  77 f2 89 f3 db df 8a bd  |.......zw.......|
00000070  91 2c f3 6f 48 e6 86 7c  d9 a2 1c 8d 80 cc e9 90  |.,.oH..|........|
00000080  4f 2f 6b 62 c9 b4 6e b5  d5 c1 f6 92 54 ab bd 0a  |O/kb..n.....T...|
00000090  ab bb cc 8a 6d dc 48 80  8e ec 29 4c ab b2 25 e5  |....m.H...)L..%.|
000000a0  ec 75 01 af fb 03 0c 4c  a9 cd 01 00 a4 2b fc 45  |.u.....L.....+.E|
000000b0  16 07 ea 5a f6 17 1b 05  86 d8 dd 22 3b dc 62 27  |...Z.......";.b'|
000000c0  d1 43 97 92 13 83 0d 33  e8 c8 37 ac 01 fe 20 4d  |.C.....3..7... M|
000000d0  65 84 4e 8a 4d c2 d5 b9  2a 38 54 6e 20 d7 63 93  |e.N.M...*8Tn .c.|
000000e0  a6 90 cb 62 b1 55 e3 93  17 51 07 f8 e3 0d 5a d9  |...b.U...Q....Z.|
000000f0  4f 19 0a bf e9 b7 f4 c0  76 e9 d8 be 90 83 58 f5  |O.......v.....X.|
00000100  37 a2 04 c3 0e 0d c9 8b  bf f8 72 96 5f c9 d4 a1  |7.........r._...|
00000110  89 95 df 61 05 2f 9f 46  f1 61 ca 8e c9 5a ac a7  |...a./.F.a...Z..|
00000120  e4 0a 25 ea ea c2 01 1d  15 10 32 4e a1 ce cf 7e  |..%.......2N...~|
00000130  dc 47 ee 52 57 57 dc 68  e9 d3 c0 53 51 6e ae 69  |.G.RWW.h...SQn.i|
00000140  d1 04 78 52 42 83 73 bb  d1 8f b0 25 d9 69 96 a0  |..xRB.s....%.i..|
00000150  8c 9a 2b 6d 32 42 82 f7  49 a3 d8 69 33 36 29 b2  |..+m2B..I..i36).|
00000160  b1 e7 1a 68 94 9b 55 9f  9c 13 b4 f2 f9 b7 b8 83  |...h..U.........|
00000170  c0 80 ba 17 dd d7 93 dc  ba 56 0e ce e8 8a fb 6e  |.........V.....n|
00000180  e5 26 84 65 4f ff c3 09  4d 13 7c e2 21 49 68 ce  |.&.eO...M.|.!Ih.|
00000190  94 3f 08 fc e3 ac 76 3b  40 a8 eb bd 87 a0 9c 2d  |.?....v;@......-|
000001a0  8e 5a 18 60 b6 df c8 9a  8d 21 3b 28 fe 37 09 57  |.Z.`.....!;(.7.W|
000001b0  1e 3e 2c 69 26 98 ea 1f  7f 5f 79 95 a3 aa 00 fe  |.>,i&...._y.....|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 00 2a 01 00 fe  |............*...|
000001d0  ff ff 05 fe ff ff 02 00  2a 01 00 d0 b2 00 00 00  |........*.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sda 
```

You already fixed Windows MBR right?
Did you re-install GRUB2 then you posted this script result? or that's before?

When you managed to login to Windows, did you see GRUB2 menu? because if you see it and you logged in to Windows from it then you don't need to re-install GRUB.

---

### Post by 6msj on 2010-12-24
I fixed windows mbr and that was before grub install.

I saw the grub menu before accessing windows 7.

So I guess I'm done?!

Thanks!

---

### Post by amjjawad on 2010-12-24
> **6msj said:**
> I fixed windows mbr and that was before grub install.

I saw the grub menu before accessing windows 7.

So I guess I'm done?!

Thanks!

One way to find out.
Reboot now and login to Windows then reboot again and login to Ubuntu.
If everything is okay, please post back while you're from Ubuntu.

---

### Post by 6msj on 2010-12-24
Booted into both successfully, everythings perfect.!

---

### Post by amjjawad on 2010-12-24
> **6msj said:**
> Booted into both successfully, everythings perfect.!

Are you sure? :D

WELL DONE!

Now, guess I can sleep with a smile ;)

---

### Post by 6msj on 2010-12-24
Thanks for the quick replies and informative help. I feel like I learned more about Linux, messing up my OS than just using it. Good night!

---

### Post by amjjawad on 2010-12-24
> **6msj said:**
> Thanks for the quick replies and informative help. I feel like I learned more about Linux, messing up my OS than just using it. Good night!

Thank you for your patience and cooperation :)
Without that, we will never be able to fix it. Glad that I was helpful and more glad you managed to fix it.

Merry Christmas and Happy New Year (not sure if you're celebrating that or not).

Good night :)

---

### Post by 6msj on 2010-12-24
Very weird, after I used Ubuntu for a while and installed a few applications, I restarted and turned on win7 again, and the same thing happened. Error message + restart and then it asks me to repair or start windows normally. I start windows normally and it works.

A little annoying but at least I can enter windows now. :D

---

