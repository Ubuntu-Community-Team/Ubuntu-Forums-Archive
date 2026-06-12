---
title: "grub directly loading ubuntu, not showing menu for other operating systems"
date: 2011-01-26
forum: New to Ubuntu
---

### Post by cyberbandya007 on 2011-01-26
Hi,

I have installed ubuntu10.10 on my Dell laptop. I have windows Vista installed on it.

When I start the machine, it directly boots to ubuntu. It does not show options to boot into windows. I have tried pressing ESC while starting but no use.

I have gone through posts and found one similar post ```
**instaled lubuntu side-by-side ubuntu. now grub only show lubuntu, other OS disappear**
```. In this post, the person has asked to download boot info script bash file from ```
http://sourceforge.net/projects/bootinfoscript/
``` site and attach the result of it over here.

I have run the boot info script file on my machine. The result is :
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #8 for (,msdos8)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sda3': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sda3': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 8. But according to the info from fdisk, 
                       sda6 starts at sector 518457344.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2              81,920    20,561,919    20,480,000   7 HPFS/NTFS
/dev/sda3    *     20,561,920   455,432,871   434,870,952   7 HPFS/NTFS
/dev/sda4         455,436,286   625,141,759   169,705,474   f W95 Ext d (LBA)
/dev/sda5         455,436,288   518,457,335    63,021,048   7 HPFS/NTFS
/dev/sda6         518,457,344   581,277,687    62,820,344   7 HPFS/NTFS
/dev/sda7         581,277,696   585,183,231     3,905,536  82 Linux swap / Solaris
/dev/sda8         585,185,280   625,141,759    39,956,480  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 4072 MB, 4072668672 bytes
255 heads, 63 sectors/track, 495 cylinders, total 7954431 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             38     7,839,719     7,839,682   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07D7-0615                              vfat       DellUtility                   
/dev/sda2        AAB6D921B6D8EEB7                       ntfs       RECOVERY                      
/dev/sda3        2C6EDB496EDB0B0A                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        C894E18094E170FC                       ntfs       New Volume                    
/dev/sda6        F496CDF196CDB500                       ntfs       New Volume                    
/dev/sda7        07f2ccc4-a9b9-4137-bb65-b32f4f16817b   swap                                     
/dev/sda8        4bf00392-9926-4378-98e2-75cdda6841f5   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdc1        1314-2475                              vfat       PENDRIVE                      
/dev/sdc: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda8        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdc1        /media/PENDRIVE          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


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
search --no-floppy --fs-uuid --set 4bf00392-9926-4378-98e2-75cdda6841f5
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set 4bf00392-9926-4378-98e2-75cdda6841f5
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
    search --no-floppy --fs-uuid --set 4bf00392-9926-4378-98e2-75cdda6841f5
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=4bf00392-9926-4378-98e2-75cdda6841f5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 4bf00392-9926-4378-98e2-75cdda6841f5
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=4bf00392-9926-4378-98e2-75cdda6841f5 ro single 
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
    search --no-floppy --fs-uuid --set 4bf00392-9926-4378-98e2-75cdda6841f5
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 4bf00392-9926-4378-98e2-75cdda6841f5
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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
UUID=4bf00392-9926-4378-98e2-75cdda6841f5 /               ext4    errors=remount-ro 0       1
/dev/sda7       none            swap    sw              0       0

=================== sda8: Location of files loaded by Grub: ===================


 315.3GB: boot/grub/core.img
 304.2GB: boot/grub/grub.cfg
 300.3GB: boot/initrd.img-2.6.35-22-generic
 315.3GB: boot/vmlinuz-2.6.35-22-generic
 300.3GB: initrd.img
 315.3GB: vmlinuz

=========================== sdc1/boot/grub/grub.cfg: ===========================


if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}

=================== sdc1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/grub.cfg
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 26 00 00 00  |........?...&...|
00000020  c2 9f 77 00 d9 1d 00 00  00 00 00 00 02 00 00 00  |..w.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 75 24 14 13 4e  4f 20 4e 41 4d 45 20 20  |..)u$..NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
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
00000100  7d 00 66 b8 da 3b 00 00  66 ba 00 00 00 00 bb 00  |}.f..;..f.......|
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


=======Devices which don't seem to have a corresponding hard drive==============

sdb 


```

Can someone help me to restore booting options for windows? I want the machine to boot to windows by default. I am a newbie in this. Please help.

Thanks in advance.

---

### Post by khamil8686 on 2011-01-26
will you post the contents of your /etc/default/grub file here?

---

### Post by cyberbandya007 on 2011-01-27
contents of /etc/default/grub : 

```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"


```

---

### Post by khamil8686 on 2011-01-27
ok before editing this file go ahead and make a backup by running
```
sudo cp /etc/default/grub /etc/default/grub.backup
```

the line
```
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
```

sets grub2 to show a blank screen for 0 seconds and boot the default operating system which for you is whatever is entry 0 (probably ubuntu) because of the line
```
GRUB_DEFAULT=0
```

change the GRUB_HIDDEN_TIMEOUT_QUIET=true to false, save the file and run
```
sudo update-grub2
```

now you should see your list of OSes when you start your computer, reboot and then check your list of OSes and make a note of which one is your vista installation and subtract this number by 1
(so the first entry would be entry 0, the second would be entry 1, and the third would be entry 2)
edit the /etc/default/grub file again and change GRUB_DEFAULT=0 to GRUB_DEFAULT=*the # from the last step*
and that will set your computer to automatically boot into vista. if you want you can also change GRUB_TIMEOUT=10 to be a lesser number so the menu screen doesnt show for 10 seconds before booting automatically then save the file and run
```
sudo update-grub2
```
again and then you should be able to reboot and it will automatically boot into vista and show the os choice screen every time! :) post back if you have trouble!

---

### Post by oldfred on 2011-01-27
From a windows repair CD you need to try to repair sda3. Run chkdsk until there are no errors:

    Mounting failed:
$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sda3': Input/output error

Vista/7 CHKDSK
chkdsk [drive] /f /r
chkdsk C: /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Repair Disc at the following links:
Windows Vista Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
Windows 7 Disc - for repairs only
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista/7 will not repair XP (they create the boot sectors differently) but can run chkdsk on any NTFS partition.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by presence1960 on 2011-01-27
> **oldfred said:**
> From a windows repair CD you need to try to repair sda3. Run chkdsk until there are no errors:

    Mounting failed:
$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sda3': Input/output error

Vista/7 CHKDSK
chkdsk [drive] /f /r
chkdsk C: /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Repair Disc at the following links:
Windows Vista Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
Windows 7 Disc - for repairs only
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista/7 will not repair XP (they create the boot sectors differently) but can run chkdsk on any NTFS partition.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

+1

oldfred is right on the money. sda3 is your Vista OS. sda2 is your Recovery partition. You can run sudo update-grub all you want but until sda3 is able to be mounted and read GRUB will never find the files necessary to boot Vista.

---

### Post by cyberbandya007 on 2011-01-28
It is now working very well... :guitar:
Thanks khamil8686, oldfred, presence1960. :popcorn:

---

