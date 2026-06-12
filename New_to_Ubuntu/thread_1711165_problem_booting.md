---
title: "problem booting"
date: 2011-03-20
forum: New to Ubuntu
---

### Post by djyoung4 on 2011-03-20
So i restarted my custom box running ubuntu 10.04 64bit and when it went to boot, all I get is a black screen with the white type line blinking in the top left corner.  Its not a harddrive issue because I popped in the LiveCD and I was able to mount the drive so I'm assuming it has to do with either grub or something else with the boot record.  any ideas?

---

### Post by racie on 2011-03-20
Boot into the LiveCD, run [this boot info script](http://ubuntuforums.org/showthread.php?t=1291280) and post the output here.

---

### Post by djyoung4 on 2011-03-20
> **racie said:**
> Boot into the LiveCD, run [this boot info script](http://ubuntuforums.org/showthread.php?t=1291280) and post the output here.
gladly
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks at sector 2048 of the 
    same hard drive for core.img, but core.img can not be found at this 
    location.
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       Bios Boot Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdc1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63 1,953,520,064 1,953,520,002  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdb1           2,048         4,095         2,048 Bios Boot Partition
/dev/sdb2           4,096 3,883,257,855 3,883,253,760 Linux or Data
/dev/sdb3   3,883,257,856 3,907,028,991    23,771,136 Linux Swap

Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 1,953,520,064 1,953,520,002  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        ff0b20c6-6366-4653-85b8-538b245749fd   ext4       Storage 2                     
/dev/sda: PTTYPE="dos" 
/dev/sdb2        291203e8-8e7d-47b7-9a85-37a391cf6a8a   ext4                                     
/dev/sdb3        753c26f6-c832-4557-8b62-7c4d76ff8bfa   swap                                     
/dev/sdb: PTTYPE="gpt" 
/dev/sdc1        F756-FF06                              vfat       Storage1                      
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sdb2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 291203e8-8e7d-47b7-9a85-37a391cf6a8a
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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 291203e8-8e7d-47b7-9a85-37a391cf6a8a
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
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 291203e8-8e7d-47b7-9a85-37a391cf6a8a
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=291203e8-8e7d-47b7-9a85-37a391cf6a8a ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 291203e8-8e7d-47b7-9a85-37a391cf6a8a
	echo	'Loading Linux 2.6.32-27-generic ...'
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=291203e8-8e7d-47b7-9a85-37a391cf6a8a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 291203e8-8e7d-47b7-9a85-37a391cf6a8a
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=291203e8-8e7d-47b7-9a85-37a391cf6a8a ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 291203e8-8e7d-47b7-9a85-37a391cf6a8a
	echo	'Loading Linux 2.6.32-26-generic ...'
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=291203e8-8e7d-47b7-9a85-37a391cf6a8a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 291203e8-8e7d-47b7-9a85-37a391cf6a8a
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=291203e8-8e7d-47b7-9a85-37a391cf6a8a ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 291203e8-8e7d-47b7-9a85-37a391cf6a8a
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=291203e8-8e7d-47b7-9a85-37a391cf6a8a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 291203e8-8e7d-47b7-9a85-37a391cf6a8a
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=291203e8-8e7d-47b7-9a85-37a391cf6a8a ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 291203e8-8e7d-47b7-9a85-37a391cf6a8a
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=291203e8-8e7d-47b7-9a85-37a391cf6a8a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 291203e8-8e7d-47b7-9a85-37a391cf6a8a
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=291203e8-8e7d-47b7-9a85-37a391cf6a8a ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 291203e8-8e7d-47b7-9a85-37a391cf6a8a
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=291203e8-8e7d-47b7-9a85-37a391cf6a8a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 291203e8-8e7d-47b7-9a85-37a391cf6a8a
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=291203e8-8e7d-47b7-9a85-37a391cf6a8a ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 291203e8-8e7d-47b7-9a85-37a391cf6a8a
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=291203e8-8e7d-47b7-9a85-37a391cf6a8a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 291203e8-8e7d-47b7-9a85-37a391cf6a8a
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=291203e8-8e7d-47b7-9a85-37a391cf6a8a ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 291203e8-8e7d-47b7-9a85-37a391cf6a8a
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=291203e8-8e7d-47b7-9a85-37a391cf6a8a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 291203e8-8e7d-47b7-9a85-37a391cf6a8a
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 291203e8-8e7d-47b7-9a85-37a391cf6a8a
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

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sda2 during installation
UUID=291203e8-8e7d-47b7-9a85-37a391cf6a8a  /            ext4  errors=remount-ro    0  1  
# swap was on /dev/sda3 during installation
UUID=753c26f6-c832-4557-8b62-7c4d76ff8bfa  none         swap  sw                   0  0   

=================== sdb2: Location of files loaded by Grub: ===================


1370.2GB: boot/grub/core.img
 588.7GB: boot/grub/grub.cfg
1370.2GB: boot/initrd.img-2.6.32-21-generic
1370.2GB: boot/initrd.img-2.6.32-22-generic
1370.3GB: boot/initrd.img-2.6.32-23-generic
1372.2GB: boot/initrd.img-2.6.32-24-generic
1372.2GB: boot/initrd.img-2.6.32-25-generic
1372.3GB: boot/initrd.img-2.6.32-26-generic
1372.3GB: boot/initrd.img-2.6.32-27-generic
1370.2GB: boot/vmlinuz-2.6.32-21-generic
    .5GB: boot/vmlinuz-2.6.32-22-generic
1370.2GB: boot/vmlinuz-2.6.32-23-generic
  41.8GB: boot/vmlinuz-2.6.32-24-generic
 793.0GB: boot/vmlinuz-2.6.32-25-generic
1372.3GB: boot/vmlinuz-2.6.32-26-generic
1372.2GB: boot/vmlinuz-2.6.32-27-generic
1372.3GB: initrd.img
1372.3GB: initrd.img.old
1372.2GB: vmlinuz
1372.3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  52 e8 28 01 74 08 56 be  33 81 e8 4c 01 5e bf f4  |R.(.t.V.3..L.^..|
00000010  81 66 8b 2d 83 7d 08 00  0f 84 e9 00 80 7c ff 00  |.f.-.}.......|..|
00000020  74 46 66 8b 1d 66 8b 4d  04 66 31 c0 b0 7f 39 45  |tFf..f.M.f1...9E|
00000030  08 7f 03 8b 45 08 29 45  08 66 01 05 66 83 55 04  |....E.)E.f..f.U.|
00000040  00 c7 04 10 00 89 44 02  66 89 5c 08 66 89 4c 0c  |......D.f.\.f.L.|
00000050  c7 44 06 00 70 50 c7 44  04 00 00 b4 42 cd 13 0f  |.D..pP.D....B...|
00000060  82 bb 00 bb 00 70 eb 68  66 8b 45 04 66 09 c0 0f  |.....p.hf.E.f...|
00000070  85 a3 00 66 8b 05 66 31  d2 66 f7 34 88 54 0a 66  |...f..f1.f.4.T.f|
00000080  31 d2 66 f7 74 04 88 54  0b 89 44 0c 3b 44 08 0f  |1.f.t..T..D.;D..|
00000090  8d 83 00 8b 04 2a 44 0a  39 45 08 7f 03 8b 45 08  |.....*D.9E....E.|
000000a0  29 45 08 66 01 05 66 83  55 04 00 8a 54 0d c0 e2  |)E.f..f.U...T...|
000000b0  06 8a 4c 0a fe c1 08 d1  8a 6c 0c 5a 52 8a 74 0b  |..L......l.ZR.t.|
000000c0  50 bb 00 70 8e c3 31 db  b4 02 cd 13 72 50 8c c3  |P..p..1.....rP..|
000000d0  8e 45 0a 58 c1 e0 05 01  45 0a 60 1e c1 e0 03 89  |.E.X....E.`.....|
000000e0  c1 31 ff 31 f6 8e db fc  f3 a5 1f e8 3e 00 74 06  |.1.1........>.t.|
000000f0  be 3b 81 e8 63 00 61 83  7d 08 00 0f 85 1d ff 83  |.;..c.a.}.......|
00000100  ef 0c e9 0f ff e8 24 00  74 06 be 3d 81 e8 49 00  |......$.t..=..I.|
00000110  5a ea 00 82 00 00 be 40  81 e8 3d 00 eb 06 be 45  |Z......@..=....E|
00000120  81 e8 35 00 be 4a 81 e8  2f 00 eb fe bb 17 04 80  |..5..J../.......|
00000130  27 03 c3 6c 6f 61 64 69  6e 67 00 2e 00 0d 0a 00  |'..loading......|
00000140  47 65 6f 6d 00 52 65 61  64 00 20 45 72 72 6f 72  |Geom.Read. Error|
00000150  00 bb 01 00 b4 0e cd 10  46 8a 04 3c 00 75 f2 c3  |........F..<.u..|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 01 08 00 00  00 00 00 00 2f 00 20 08  |............/. .|
00000200


```
strange.  it says I have windows installed but I have never had any windows cd or dvd near this box

---

### Post by djyoung4 on 2011-03-21
any ideas?

---

### Post by srs5694 on 2011-03-21
The "Windows is installed" message is poorly phrased; that means that a standard DOS/Windows boot loader is installed there. It could be that the disk was once used with DOS/Windows or that some completely unrelated utility installed the DOS/Windows boot loader. Don't worry about this.

I note that there's no boot loader on /dev/sda. If your computer is configured to boot from /dev/sda, that explains your symptoms. There are at least three possible solutions:


[list]
[*]Use your BIOS utility to reconfigure the computer to boot from /dev/sdb.
[*]Swap your hard drive cables so that /dev/sda becomes /dev/sdb and vice-versa.
[*]Use an emergency boot system to install GRUB to /dev/sda.
[/list]

---

### Post by djyoung4 on 2011-03-22
> **srs5694 said:**
> The "Windows is installed" message is poorly phrased; that means that a standard DOS/Windows boot loader is installed there. It could be that the disk was once used with DOS/Windows or that some completely unrelated utility installed the DOS/Windows boot loader. Don't worry about this.

I note that there's no boot loader on /dev/sda. If your computer is configured to boot from /dev/sda, that explains your symptoms. There are at least three possible solutions:


[list]
[*]Use your BIOS utility to reconfigure the computer to boot from /dev/sdb.
[*]Swap your hard drive cables so that /dev/sda becomes /dev/sdb and vice-versa.
[*]Use an emergency boot system to install GRUB to /dev/sda.
[/list]
swapping the hard drive cables fixed it. strange that they flipped.  how would that even happen

---

### Post by JKyleOKC on 2011-03-22
> **djyoung4 said:**
> swapping the hard drive cables fixed it. strange that they flipped.  how would that even happenThe drive names in /dev are assigned in the order that the drives are detected during the boot sequence. If the two drives are almost identical, then which one replies first to the boot sequence can easily be a random choice beyond anyone's control. That means that the drive known as /dev/sda today can become /dev/sdb tomorrow, and vice versa. Your switch of the cables may have to be changed back at any time in the future.

To prevent this, the use of UUID for drives was introduced quite a while ago. The UUID, which is a long string of numbers and letters, gets stored on the drive in its Master Boot Record, and won't change like the sda/sdb designations may. You can get the UUID for each drive with the command "blkid", and then replace all instances of the /dev/sd? names with the corresponding "UUID=" string in all of the boot files: these include /etc/fstab and /etc/default/grub among others. Search the forums here for "UUID" to get more detailed instructions on making the changes.

Of course, so long as all is working properly, no change is really necessary; treat this as information for the future in case it happens again!

EDIT: Note that your results.txt file already shows the UUID values for the system drives, so you only need to make the boot files use them to prevent any recurrence.

---

### Post by srs5694 on 2011-03-22
JKyleOKC, I believe you're heading off on an incorrect tangent. The problem, as I understand it, is that the *BIOS* was looking at the wrong drive. This has nothing to do with Linux or Linux device filenames. My hypothesis is that something changed the drive order in the BIOS -- an accidental change by the user, a reset to factory defaults because of some software "event," or whatever. When this happened, the boot loader stopped loading. Swapping the drive cables corrected the problem via a solution other than the method that created the problem, given what djyoung4 has said.

---

### Post by JKyleOKC on 2011-03-22
You're absolutely right! The results.txt file clearly shows that both grub.cfg and fstab refer to the drives by UUID, so even if a transposition of sda and sdb had happened, it would not have caused the problem. The BIOS had to be looking to the wrong drive, as you say.

However I don't see how swapping the cables could fix it; does a SATA controller actually route the drives by something like the cable-select option of PATA? I know that the master/slave jumpers are no longer there on SATA devices, but had the impression that the addressing was handled in a similar manner to USB or SCSI usage, with an address sent as control data. In that case I would expect the control data to go out over all connected cables.

Obviously it did do the trick, so my understanding must not be correct. Can you go into a bit more detail about how it really does work? Thanks!

---

### Post by srs5694 on 2011-03-23
My understanding is that the BIOS numbers different SATA drives according to the plugs to which they're connected. That is, one physical plug is drive #1, another one is drive #2, etc. By default, the BIOS boots in that order -- drive #1, then drive #2, etc. Modern BIOSes enable you to change this order, though. Because SATA cables connect just one disk to one controller (vs. up to two disks for PATA or 7 or 15 for SCSI), there's no need for any sort of device ID number, so the BIOS just goes by the plug number. Note that the BIOS might tell you what type of device is connected to a given plug, but AFAIK that's just informational; the BIOS selects the boot device based on the port, not any sort of identification of the device itself.

---

### Post by djyoung4 on 2011-03-23
Thats exactly what happened.  I had to select the actual drive from the BIOS in order to boot.  So something happened where the boot order changed and it tried to boot from a different drive in my system and I figured out I had to change which drive it was booting to first.  How that happened though I have no idea

---

