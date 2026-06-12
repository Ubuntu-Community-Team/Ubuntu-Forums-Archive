---
title: "Grub Not Loading"
date: 2011-07-12
forum: New to Ubuntu
---

### Post by gbest5089 on 2011-07-12
Just installed 11.04 on a separate HDD in a WinXP PC.  Grub apparently went to the MBR.
When I rebooted 1st time, the PC hung on the word Grub.  Next time, I don't think it even appeared.
Using Smart Boot Loader, I could get no progress when I switched to the HDD with Linux on it (which is in Linux format) and has whatever the 11.04 ISO put on it under "install".
Do I need to relocate Grub or use a different Grub file?  Do I need to do something to HDD0 to make it bootable?  
The PC is happy to boot XP from HDD1.
Any suggestions appreciated, but please note I am having great difficulty absorbing the strange Linux jargon.  Thanks,
Gordon

---

### Post by Rubi1200 on 2011-07-13
Hi and welcome to the forums :-)

Please do the following so we can get a better overview of what is where on the system:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script which is in a zipped file. There is a link in my signature.
2. Once downloaded, move the boot info script by either copying or dragging and dropping the zipped folder onto the desktop and unzip the contents by using right-click Extract here.
3. Open the folder and copy the script to the desktop (you can also drag and drop if you like)
4. Open a terminal and run the following command

```
sudo bash ~/Desktop/boot_info_script.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by gbest5089 on 2011-07-13
Thanks Rubi1200.  I will try that, although it may take a while.  The CD I have is not (I think) a live CD and does not give me a RUN option, so will have to get my hands on one.  I'll be back .. sometime soon.
GB

---

### Post by gbest5089 on 2011-07-15
Following on from my previous post, I have now done as advised by Rubi1200 and have run boot_script_info, the results of which I attach below (hopefully correctly ##d):

Must say I also ran boot_info_script on a properly working Puppy system on a 10yr old PC, thinking I might get some hints from that and be able to make some sense out of the Results below.  Vain hope!

I'll appreciate your help again, thanks,

Gordon

 ```
                Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => Windows is installed in the MBR of /dev/sdb.
 => Windows is installed in the MBR of /dev/sdh.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdh1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048    76,068,863    76,066,816  83 Linux
/dev/sda2          76,070,910    78,163,967     2,093,058   5 Extended
/dev/sda5          76,070,912    78,163,967     2,093,056  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63    41,785,064    41,785,002   7 NTFS / exFAT / HPFS
/dev/sdb2          41,785,065   390,716,864   348,931,800   7 NTFS / exFAT / HPFS
/dev/sdb3         390,716,865   976,768,064   586,051,200   7 NTFS / exFAT / HPFS


Drive: sdh _____________________________________________________________________

Disk /dev/sdh: 1014 MB, 1014497280 bytes
250 heads, 32 sectors/track, 247 cylinders, total 1981440 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdh1                  32     1,981,437     1,981,406   6 FAT16


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        1490a5ca-3233-4e54-b8ee-c8aecb588b10   ext4       
/dev/sda5        b239901c-e0fd-40a5-90fa-6b432bf497dc   swap       
/dev/sdb1        8CCC30B1CC309782                       ntfs       
/dev/sdb2        18E08614E085F7F0                       ntfs       Local Disc
/dev/sdb3        C6ACEF35ACEF1EA5                       ntfs       Local Disc
/dev/sdh1        8423-718E                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdh1        /media/8423-718E         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 1490a5ca-3233-4e54-b8ee-c8aecb588b10
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 1490a5ca-3233-4e54-b8ee-c8aecb588b10
set locale_dir=($root)/boot/grub/locale
set lang=en_AU
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 1490a5ca-3233-4e54-b8ee-c8aecb588b10
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=1490a5ca-3233-4e54-b8ee-c8aecb588b10 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 1490a5ca-3233-4e54-b8ee-c8aecb588b10
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=1490a5ca-3233-4e54-b8ee-c8aecb588b10 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 1490a5ca-3233-4e54-b8ee-c8aecb588b10
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 1490a5ca-3233-4e54-b8ee-c8aecb588b10
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sdb1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 8CCC30B1CC309782
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
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=1490a5ca-3233-4e54-b8ee-c8aecb588b10 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b239901c-e0fd-40a5-90fa-6b432bf497dc none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  10.130977631 = 10.878054400   boot/grub/core.img                             1
   4.257152557 = 4.571082752    boot/grub/grub.cfg                             1
   1.755104065 = 1.884528640    boot/initrd.img-2.6.38-8-generic               2
   0.204406738 = 0.219480064    boot/vmlinuz-2.6.38-8-generic                  1
   1.755104065 = 1.884528640    initrd.img                                     2
   0.204406738 = 0.219480064    vmlinuz                                        1

================================ sdb1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  17 21 12 16 1f 10 16 1e  0e 13 1b 0d 12 19 0c 14  |.!..............|
00000010  14 09 1f 1d 0a 23 26 0a  10 16 05 10 1e 04 16 38  |.....#&........8|
00000020  07 1b 44 0d 24 54 18 2d  5a 1c 2a 52 1a 1f 3f 14  |..D.$T.-Z.*R..?.|
00000030  14 2e 0d 13 27 0f 0e 1f  0d 08 12 08 07 0e 08 08  |....'...........|
00000040  12 08 0f 1e 09 18 2b 0e  1b 2a 06 1d 2d 07 22 33  |......+..*..-."3|
00000050  09 30 4a 11 4f 6f 2c 3b  5c 16 44 5f 1f 57 68 36  |.0J.Oo,;\.D_.Wh6|
00000060  43 47 28 23 14 13 13 09  0d 09 08 07 12 10 0d 16  |CG(#............|
00000070  14 0f 0c 0c 09 03 03 02  00 00 00 01 01 01 06 04  |................|
00000080  04 0a 07 06 09 07 05 07  06 04 0b 0c 05 16 19 0a  |................|
00000090  15 1b 0a 15 1c 0a 12 1e  09 24 34 10 29 39 11 1e  |.........$4.)9..|
000000a0  2e 0c 1b 2b 11 11 1d 12  12 21 13 13 26 10 0b 18  |...+.....!..&...|
000000b0  06 0e 1e 04 1a 33 08 30  54 1c 36 5e 22 2d 4d 16  |.....3.0T.6^"-M.|
000000c0  28 3e 13 19 29 0a 16 24  0a 16 26 0f 1b 2a 12 19  |(>..)..$..&..*..|
000000d0  27 11 1b 24 0f 1a 23 0e  0e 10 08 09 0a 05 08 09  |'..$..#.........|
000000e0  05 0b 0b 08 0d 0d 0a 12  13 0e 15 19 10 0d 12 0a  |................|
000000f0  0a 0c 07 0a 0e 08 17 1e  10 18 21 11 12 19 0c 0b  |..........!.....|
00000100  0f 06 06 08 03 06 07 03  0e 13 08 22 39 13 19 33  |..........."9..3|
00000110  08 19 3e 07 45 72 25 3e  67 1c 26 53 0a 27 59 0b  |..>.Er%>g.&S.'Y.|
00000120  2b 61 0e 42 76 1e 4e 7d  23 42 61 16 2d 39 0d 18  |+a.Bv.N}#Ba.-9..|
00000130  1a 08 23 29 10 26 34 16  1f 2c 11 14 22 0b 10 21  |..#).&4..,.."..!|
00000140  0a 0d 16 0a 0c 12 09 0c  12 0a 12 1a 0b 12 19 08  |................|
00000150  10 15 05 10 15 06 10 18  06 12 1e 06 20 34 10 2c  |............ 4.,|
00000160  41 1c 1b 30 10 0b 18 05  0b 18 05 22 3e 0f 2d 4a  |A..0.......">.-J|
00000170  16 1f 39 09 17 2c 01 19  30 02 23 3a 11 24 3a 17  |..9..,..0.#:.$:.|
00000180  12 20 0f 05 08 03 06 08  04 08 0c 07 0c 13 0a 0d  |. ..............|
00000190  17 0c 0d 15 0b 09 0f 06  0a 12 08 0a 12 09 0d 17  |................|
000001a0  08 16 21 0a 15 21 09 11  17 06 13 1d 07 14 1d 06  |..!..!..........|
000001b0  11 13 05 0f 10 06 19 1b  0f 16 1a 10 0e 10 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 f0 1f 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf sdg 

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by s.fox on 2011-07-15
Please do not create seperate threads when posting follow up information. It makes it harder for people to follow, and thus help you.  Thank you

Threads merged.

---

### Post by aleksans on 2011-07-15
I too have the same problem after doing a fresh install of Ubuntu 11.04 on a brand new HP Compaq 6200 Pro.

After installing, reinstalling, booting into LiveCD and installing and running 'boot-repair' to no avail, I followed the the tip above and downloaded and ran BootInfoScript.

Here is the RESULT.txt content:
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sdb2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   954,025,983   953,819,136   7 NTFS / exFAT / HPFS
/dev/sda3         954,025,984   976,771,071    22,745,088   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                   1   234,441,647   234,441,647  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1              34   230,535,190   230,535,157 Data partition (Windows/Linux)
/dev/sdb2     230,535,191   234,441,441     3,906,251 Swap partition (Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        D21ECCAC1ECC8B45                       ntfs       SYSTEM
/dev/sda2        9CF47B51F47B2CA0                       ntfs       OS
/dev/sda3        B62636102635D1DB                       ntfs       HP_RECOVERY
/dev/sdb1        e4f3c2d3-be37-43e2-829b-fc51a2786544   ext4       
/dev/sdb2        15eb4cdf-4b3c-4ddf-80d0-679f6a71707d   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
  insmod efi_gop
  insmod efi_uga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_gpt
insmod ext2
set root='(/dev/sdb,gpt1)'
search --no-floppy --fs-uuid --set=root e4f3c2d3-be37-43e2-829b-fc51a2786544
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_gpt
insmod ext2
set root='(/dev/sdb,gpt1)'
search --no-floppy --fs-uuid --set=root e4f3c2d3-be37-43e2-829b-fc51a2786544
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_gpt
	insmod ext2
	set root='(/dev/sdb,gpt1)'
	search --no-floppy --fs-uuid --set=root e4f3c2d3-be37-43e2-829b-fc51a2786544
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=e4f3c2d3-be37-43e2-829b-fc51a2786544 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_gpt
	insmod ext2
	set root='(/dev/sdb,gpt1)'
	search --no-floppy --fs-uuid --set=root e4f3c2d3-be37-43e2-829b-fc51a2786544
	echo	'Loading Linux 2.6.38-10-generic ...'
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=e4f3c2d3-be37-43e2-829b-fc51a2786544 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_gpt
	insmod ext2
	set root='(/dev/sdb,gpt1)'
	search --no-floppy --fs-uuid --set=root e4f3c2d3-be37-43e2-829b-fc51a2786544
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=e4f3c2d3-be37-43e2-829b-fc51a2786544 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_gpt
	insmod ext2
	set root='(/dev/sdb,gpt1)'
	search --no-floppy --fs-uuid --set=root e4f3c2d3-be37-43e2-829b-fc51a2786544
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=e4f3c2d3-be37-43e2-829b-fc51a2786544 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_gpt
	insmod ext2
	set root='(/dev/sdb,gpt1)'
	search --no-floppy --fs-uuid --set=root e4f3c2d3-be37-43e2-829b-fc51a2786544
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_gpt
	insmod ext2
	set root='(/dev/sdb,gpt1)'
	search --no-floppy --fs-uuid --set=root e4f3c2d3-be37-43e2-829b-fc51a2786544
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root D21ECCAC1ECC8B45
	chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root B62636102635D1DB
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
--------------------------------------------------------------------------------

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=e4f3c2d3-be37-43e2-829b-fc51a2786544 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb2 during installation
UUID=15eb4cdf-4b3c-4ddf-80d0-679f6a71707d none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  56.132836342 = 60.272174080   boot/grub/grub.cfg                             1
  64.843766212 = 69.625463808   boot/initrd.img-2.6.38-10-generic              2
   1.535687447 = 1.648931840    boot/initrd.img-2.6.38-8-generic               1
   1.680016518 = 1.803904000    boot/vmlinuz-2.6.38-10-generic                 1
  56.132771492 = 60.272104448   boot/vmlinuz-2.6.38-8-generic                  1
  64.843766212 = 69.625463808   initrd.img                                     2
   1.535687447 = 1.648931840    initrd.img.old                                 1
   1.680016518 = 1.803904000    vmlinuz                                        1
  56.132771492 = 60.272104448   vmlinuz.old                                    1

========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf sdg 

```

From what I can tell Grub is unable to install itself into the MBR for sda. When installing, or running 'boot-repair' no error messages indicating that Grub was unable to install did appear. 

Does anyone have a tip as to where to go from here?

---

### Post by Rubi1200 on 2011-07-15
> **gbest5089 said:**
> Following on from my previous post, I have now done as advised by Rubi1200 and have run boot_script_info, the results of which I attach below (hopefully correctly ##d):

Must say I also ran boot_info_script on a properly working Puppy system on a 10yr old PC, thinking I might get some hints from that and be able to make some sense out of the Results below.  Vain hope!

I'll appreciate your help again, thanks,

Gordon

Did you try changing the boot device priority in BIOS?

---

### Post by gbest5089 on 2011-07-17
Rubi1K2 You are a genius!   Well, I eventually decoded your recommendation after studying boot_info again and then did battle with my old Award BIOS to find out how to do it.... But it worked and my problem is now fixed.  Thank you.

Am I allowed one further iteration on this one?   I note that Grub very conveniently boots into Ubuntu if not responded to for a few seconds.  Is there a way to change that so it boots into Windows instead.  Terrible question, I know, to ask in a Ubuntu forum, but it would make life somewhat easier for my wife when she uses this PC. 

Many thanks again for the solution to my insurmountable problem.

Gordon

---

### Post by Rubi1200 on 2011-07-17
Hi gbest5089,
I am really glad you managed to get this sorted out :-)

I think the best tool for the job to achieve what you want is using Grub Customizer.

Here is a tutorial:
 [http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

Please mark this Solved using the Thread Tools near the top of the page.

Enjoy!

---

### Post by oldfred on 2011-07-17
@aleksans
You should start your own thread. You issues are different as you have gpt partitions and no bios_grub partition.

---

