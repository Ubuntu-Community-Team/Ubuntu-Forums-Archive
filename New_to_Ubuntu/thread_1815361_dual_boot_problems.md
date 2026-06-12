---
title: "dual boot problems"
date: 2011-07-31
forum: New to Ubuntu
---

### Post by lavere on 2011-07-31
Hi all,

I originally installed Ubuntu 11.04 onto an external usb drive (/dev/sdb) that was plugged into my laptop usb port.  The laptop internal drive (/dev/sda) was running xp.  This arrangement worked OK, except for that fact that if the usb drive was not present, I got a >grub rescue prompt and couldn't boot into either.  I wanted to change that.  By the way, /dev/sdc is a usb stick that I had plugged in when I ran the boot info script.

From my reading, I installed grub2 on the external drive and installed lilo in the MBR of the internal drive.  Here's the Boot Info Script:

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Lilo is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => MS-DOS 3.30 through Windows 95 (A) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swsuspend
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type 'swsuspend'

sdb6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    78,140,159    78,140,097   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048    58,593,279    58,591,232  83 Linux
/dev/sdb2          58,595,326    78,139,391    19,544,066   5 Extended
/dev/sdb5          68,362,240    78,139,391     9,777,152  82 Linux swap / Solaris
/dev/sdb6          58,595,328    68,360,191     9,764,864  83 Linux


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1002 MB, 1002438144 bytes
32 heads, 63 sectors/track, 971 cylinders, total 1957887 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                 129     1,957,535     1,957,407   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        EE78B09978B0624F                       ntfs       
/dev/sdb1        589b9c53-c473-438f-9ccd-628edabafc79   ext4       
/dev/sdb5        5ce97525-65dd-43bb-80f9-6973e7eecfb2   swsuspend  
/dev/sdb6        4270a45e-0482-4802-b221-cd8a16395491   ext4       
/dev/sdc1        6857-DEF7                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/EE78B09978B0624F  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /mnt                     ext4       (rw)
/dev/sdb6        /media/4270a45e-0482-4802-b221-cd8a16395491 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 
 
[spybotsd] 
timeout.old=30 
 
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/stage2                               1

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
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root 589b9c53-c473-438f-9ccd-628edabafc79
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root 589b9c53-c473-438f-9ccd-628edabafc79
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
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 589b9c53-c473-438f-9ccd-628edabafc79
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=589b9c53-c473-438f-9ccd-628edabafc79 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 589b9c53-c473-438f-9ccd-628edabafc79
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=589b9c53-c473-438f-9ccd-628edabafc79 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 589b9c53-c473-438f-9ccd-628edabafc79
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=589b9c53-c473-438f-9ccd-628edabafc79 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 589b9c53-c473-438f-9ccd-628edabafc79
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=589b9c53-c473-438f-9ccd-628edabafc79 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 589b9c53-c473-438f-9ccd-628edabafc79
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 589b9c53-c473-438f-9ccd-628edabafc79
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root EE78B09978B0624F
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
/dev/sdb1       /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb6 during installation
UUID=4270a45e-0482-4802-b221-cd8a16395491 /home           ext4    defaults,user_xattr        0       2
# swap was on /dev/sdb5 during installation
UUID=5ce97525-65dd-43bb-80f9-6973e7eecfb2 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  20.130897522 = 21.615386624   boot/grub/core.img                             1
  20.175045013 = 21.662789632   boot/grub/grub.cfg                             1
   2.404174805 = 2.581463040    boot/initrd.img-2.6.38-10-generic              2
   1.998516083 = 2.145890304    boot/initrd.img-2.6.38-8-generic               3
   2.130191803 = 2.287276032    boot/vmlinuz-2.6.38-10-generic                 2
  20.151145935 = 21.637128192   boot/vmlinuz-2.6.38-8-generic                  1
   2.404174805 = 2.581463040    initrd.img                                     2
   1.998516083 = 2.145890304    initrd.img.old                                 3
   2.130191803 = 2.287276032    vmlinuz                                        2
  20.151145935 = 21.637128192   vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb2

00000000  18 00 00 00 08 00 00 00  20 00 00 00 7f 00 00 00  |........ .......|
00000010  00 00 00 00 00 00 00 00  00 a0 02 40 00 00 00 00  |...........@....|
00000020  00 00 00 00 00 c8 05 40  00 00 00 00 00 00 00 00  |.......@........|
00000030  00 fa 08 40 00 00 00 00  00 00 00 00 40 9c 0c 40  |...@........@..@|
00000040  00 00 00 00 00 00 00 00  50 c3 0f 40 00 00 00 00  |........P..@....|
00000050  00 00 00 00 24 f4 12 40  00 00 00 00 00 00 00 80  |....$..@........|
00000060  96 98 16 40 00 00 00 00  00 00 00 20 bc be 19 40  |...@....... ...@|
00000070  00 00 00 00 00 04 bf c9  1b 8e 34 40 00 00 00 a1  |..........4@....|
00000080  ed cc ce 1b c2 d3 4e 40  20 f0 9e b5 70 2b a8 ad  |......N@ ...p+..|
00000090  c5 9d 69 40 d0 5d fd 25  e5 1a 8e 4f 19 eb 83 40  |..i@.].%...O...@|
000000a0  71 96 d7 95 43 0e 05 8d  29 af 9e 40 f9 bf a0 44  |q...C...)..@...D|
000000b0  ed 81 12 8f 81 82 b9 40  bf 3c d5 a6 cf ff 49 1f  |.......@.<....I.|
000000c0  78 c2 d3 40 6f c6 e0 8c  e9 80 c9 47 ba 93 a8 41  |x..@o......G...A|
000000d0  bc 85 6b 55 27 39 8d f7  70 e0 7c 42 bc dd 8e de  |..kU'9..p.|B....|
000000e0  f9 9d fb eb 7e aa 51 43  a1 e6 76 e3 cc f2 29 2f  |....~.QC..v...)/|
000000f0  84 81 26 44 28 10 17 aa  f8 ae 10 e3 c5 c4 fa 44  |..&D(..........D|
00000100  eb a7 d4 f3 f7 eb e1 4a  7a 95 cf 45 65 cc c7 91  |.......Jz..Ee...|
00000110  0e a6 ae a0 19 e3 a3 46  0d 65 17 0c 75 81 86 75  |.......F.e..u..u|
00000120  76 c9 48 4d 58 42 e4 a7  93 39 3b 35 b8 b2 ed 53  |v.HMXB...9;5...S|
00000130  4d a7 e5 5d 3d c5 5d 3b  8b 9e 92 5a ff 5d a6 f0  |M..]=.];...Z.]..|
00000140  a1 20 c0 54 a5 8c 37 61  d1 fd 8b 5a 8b d8 25 5d  |. .T..7a...Z..%]|
00000150  89 f9 db 67 aa 95 f8 f3  27 bf a2 c8 5d dd 80 6e  |...g....'...]..n|
00000160  4c c9 9b 97 20 8a 02 52  60 c4 25 75 00 00 00 00  |L... ..R`.%u....|
00000170  cd cc cd cc cc cc cc cc  cc cc fb 3f 71 3d 0a d7  |...........?q=..|
00000180  a3 70 3d 0a d7 a3 f8 3f  5a 64 3b df 4f 8d 97 6e  |.p=....?Zd;.O..n|
00000190  12 83 f5 3f c3 d3 2c 65  19 e2 58 17 b7 d1 f1 3f  |...?..,e..X....?|
000001a0  d0 0f 23 84 47 1b 47 ac  c5 a7 ee 3f 40 a6 b6 69  |..#.G.G....?@..i|
000001b0  6c af 05 bd 37 86 eb 3f  33 3d bc 42 7a e5 00 fe  |l...7..?3=.Bz...|
000001c0  ff ff 82 fe ff ff 02 08  95 00 00 30 95 00 00 fe  |...........0....|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 00 95 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

I don't seem to be able to set my BIOS to boot from the USB drive.  It defaults back to the internal drive and I can only boot into Windows.  I'm never given the option to boot into Natty.  I can use the live CD to see the Ubuntu drive, but I'm unsure what to do next.  

I don't want to lose my Ubuntu installation as I had invested a lot of time setting it up the way I wanted it. 

Is there a way to save it?

---

### Post by lavere on 2011-07-31
I found the answer.  There *was* a way to boot from the external drive.  I just wasn't looking in the right place in the BIOS.

---

### Post by westie457 on 2011-07-31
Hi I think this is the cause of your situation.> --------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/stage2                               1

=========================== sdb1/boot/grub/grub.cfg: ===========================


The Grub files have been installed to a partition - sda1. Those files should be in the MBR of the drive - sda.

I am not sure of the best way to remedy this, so I suggest you wait a while for someone who does know what to do.

Only being cautious as I do not want to suggest some course of action that would be most likely to turn your computer into a brick.

---

### Post by westie457 on 2011-07-31
Glad you got it sorted. disregard my first reply unless there are problems in the future.

Could you mark as solved please. Using thread tools top right of the page.

---

### Post by lavere on 2011-07-31
Hi Westy,

I think those fragments must be left over from the original installation of Ubuntu.  The first part of the grub was on /dev/sda1 and the second part on /dev/sdb1.  I believe that's what caused the boot failure if the external (/dev/sdb1) was not present.

I'm reading a lot and learning, but still have only scratched the surface.

Thanks for taking the time to reply.

---

