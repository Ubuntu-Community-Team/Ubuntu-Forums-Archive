---
title: "cannot start machine after Windows consistency check"
date: 2011-02-07
forum: New to Ubuntu
---

### Post by itzoccor on 2011-02-07
Hi

I am new to Ubuntu and not too savvy. I had tried Ubuntu and decided to install it in my Toshiba Satellite laptop. I retained Windows however, so had the dual-boot.
Installation of Ubuntu was successful and was very pleased with it. 

However, when I started Windows again, I got a blue screen and  Windows check for consistency. Windows then started and worked fine. 

After that, when I tried to reboot, the system simply does not start. I get the initial screen with F2 and F12 booting options, but then the machine goes off and restart, over and over again. 

The only thing I can do is inserting the Ubuntu CD and choose "Try Ubuntu". This allows to start Ubuntu from the CD in the "trial" mode (at least it gives me access to the machine so that I can save the files I need to save).

I wonder how to fix this. I have looked for information but could not find a description of this problem.

I thought I could try to 
(a) reinstall Ubuntu (by reinstalling the operating system will I "overwrite" the existing problem?)
(b) delete the partition I made for Ubuntu and try reinstalling Ubuntu
(c) From what I read, GParted may be able to fix this by resintalling the GRUB boot record, but I am not sure how to do this and whether that could be the source of the problem or not.


Please help.
Thanks
Oliver

---

### Post by Tyggna on 2011-02-07
All of your ideas to try are valid, and any of them might work.

Did you install Ubuntu from Wubi?  That could change the way this plays out.  

Here's what I'm gathering is going on:  When Windows trys to start up, one of its key files (a .sys) is corrupted and doesn't execute properly.  If it's one that deals with reading the hard drive, then it'll error out and restart over and over.  If it's graphics drivers and a newer version of Windows (vista or 7) than it'll do the same thing.  The point is, if you used Wubi, then Windows still has control of the boot process, and it's most likely screwed up.

If you didn't use Wubi--then it might actually be pointing to a hardware problem.  This can range from a few single bits not being properly written on your hard drive to something being damaged.

Fact is, there isn't enough information to know for sure.

If you used Wubi, then attempting to reinstall ubuntu will likely fix Ubuntu, but windows will still be broken.

Second option doesn't really do much, other than reinstall Ubuntu in a cleaner fashion.

The third option can be much easier than it seems.  Grub is only a part of Ubuntu (and a critical part) but if you go and get the "Super Grub CD" then it has a menu system you can follow, and it'll automatically repair your system (if Grub is what's failing).  This would be your best option if you didn't use Wubi--and would take the least amount of time.

---

### Post by Rubi1200 on 2011-02-07
To help us diagnose the issue, please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by itzoccor on 2011-02-07
thanks. No,  I did not use Wubi, I suspect that the problem may be related to Windows being broken, as it was giving me problems already (i.e. blue screen error when using multimedia).
Anyway, I have followed the instructions, here is the boot info script.

Thanks again, I really appreciate any help you could provide.

Best
Oliver


```
             Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

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

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
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

/dev/sda1    *             63    62,573,174    62,573,112   7 HPFS/NTFS
/dev/sda2          62,573,175   351,467,726   288,894,552   7 HPFS/NTFS
/dev/sda3         351,469,566   488,396,799   136,927,234   5 Extended
/dev/sda5         351,469,568   482,721,791   131,252,224  83 Linux
/dev/sda6         482,723,840   488,396,799     5,672,960  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2002 MB, 2002780160 bytes
16 heads, 32 sectors/track, 7640 cylinders, total 3911680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          8,064     3,911,679     3,903,616   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        8AD4ABDBD4ABC7B1                       ntfs                                     
/dev/sda2        159E208F68624B71                       ntfs       data                          
/dev/sda3: PTTYPE="dos" 
/dev/sda5        17108371-1234-4df4-8c14-566cb745fe78   ext4                                     
/dev/sda6        d7d1efad-9b51-452b-a90e-9f8fe05f9ae1   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        B589-FA30                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/data              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /media/PENDRIVE          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sda1        /media/8AD4ABDBD4ABC7B1  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /media/17108371-1234-4df4-8c14-566cb745fe78 ext4       (rw,nosuid,nodev,uhelper=udisks)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /forceresetreg 

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 17108371-1234-4df4-8c14-566cb745fe78
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 17108371-1234-4df4-8c14-566cb745fe78
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 17108371-1234-4df4-8c14-566cb745fe78
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=17108371-1234-4df4-8c14-566cb745fe78 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 17108371-1234-4df4-8c14-566cb745fe78
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=17108371-1234-4df4-8c14-566cb745fe78 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 17108371-1234-4df4-8c14-566cb745fe78
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=17108371-1234-4df4-8c14-566cb745fe78 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 17108371-1234-4df4-8c14-566cb745fe78
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=17108371-1234-4df4-8c14-566cb745fe78 ro single 
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 17108371-1234-4df4-8c14-566cb745fe78
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 17108371-1234-4df4-8c14-566cb745fe78
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 8ad4abdbd4abc7b1
    drivemap -s (hd0) ${root}
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
# / was on /dev/sda5 during installation
UUID=17108371-1234-4df4-8c14-566cb745fe78 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=d7d1efad-9b51-452b-a90e-9f8fe05f9ae1 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 184.3GB: boot/grub/core.img
 205.9GB: boot/grub/grub.cfg
 181.0GB: boot/initrd.img-2.6.35-22-generic
 205.9GB: boot/initrd.img-2.6.35-25-generic
 184.3GB: boot/vmlinuz-2.6.35-22-generic
 184.3GB: boot/vmlinuz-2.6.35-25-generic
 205.9GB: initrd.img
 181.0GB: initrd.img.old
 184.3GB: vmlinuz
 184.3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 c0 d2 07 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 c0  d2 07 00 98 56 00 00 00  |............V...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 40 20 00  |.X.SYSLINUX..@ .|
00000010  02 00 02 00 00 f8 00 01  20 00 10 00 80 1f 00 00  |........ .......|
00000020  80 90 3b 00 00 00 29 30  fa 89 b5 55 53 42 32 20  |..;...)0...USB2 |
00000030  20 20 20 20 20 20 46 41  54 31 36 20 20 20 f1 7d  |      FAT16   .}|
00000040  fa 33 c9 8e d1 bc fc 7b  16 07 bd 78 00 c5 76 00  |.3.....{...x..v.|
00000050  1e 56 16 55 bf 22 05 89  7e 00 fa fc 31 c9 8e d1  |.V.U."..~...1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 40 02 00 00  66 ba 00 00 00 00 bb 00  |}.f.@...f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by Rubi1200 on 2011-02-08
The results appear to be fairly normal, so I assume this is a problem either with Windows or the hard-drive.

You can use the Disk Utility on the LiveCD to check the SMART status and see if the drive is reported as healthy or not.

Other than that, I hope others users have some ideas to help you.

---

### Post by Clever_Username on 2011-02-08
I noticed a pen drive reference in the boot info script. Is it possible his machine's bios is set to boot from it and that is where the error is coming from?

---

### Post by itzoccor on 2011-02-08
thanks, 

I had pressed the F2 key during the failing attempts to boot, and the order of drivers to boot from sees the HDD as the first choice. I do not think this could be the cause of the problem therefore, but I may be wrong.

Best

---

### Post by Rubi1200 on 2011-02-08
Have you tried doing a repair install with the Windows CD?

Have you checked RAM for defects?

There is an option on the Ubuntu CD to use memtest, which will run a check for you.

The symptoms you describe might have been caused by faulty memory; I certainly think it is worth investigating.

---

### Post by Clever_Username on 2011-02-08
Wow. This is a toughie. Seems like if it was a memory issue, you would have problems booting from the live cd as well.

Have you tried
```
sudo update-grub
```

That little gem has bailed me out once or twice.

---

### Post by itzoccor on 2011-02-24
Hi all

sorry for not replying earlier, I have been away. 

I tried re-installing Ubuntu on the machine, and it has worked. Or at least now I have a new Ubuntu partition and I can access the newly-installed Ubuntu. 

I am afraid though the problem may re-occur should I start Windows again,  as I am pretty confident Windows installation had issues to start with (frequent blue-screen error).

I will try using memtest to see if I can get some help, but from what I gather the best thing would be to re-install windows from the disk. I wonder, if do a new installation of Windows, would that affect the existing Ubuntu?

The second issue is that when I reinstalled Ubuntu, it retained the old partion, so I have now one Ubuntu installation I do not need. I guess I can delete this using G-part without incurring in any problem or issue, is that correct?

Best regards

---

