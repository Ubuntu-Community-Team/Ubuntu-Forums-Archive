---
title: "XP wont boot after install"
date: 2011-01-13
forum: New to Ubuntu
---

### Post by Impact15 on 2011-01-13
I re-installed Ubuntu Netbook 10.10 on my Acer A150 to dual boot XP and now I can not get XP to boot. I uses Linux for everyday stuff but am required to have XP for class... Help?
 
 
Mark

---

### Post by wilee-nilee on 2011-01-13
I assume you have run in Ubuntu.
sudo update-grub
If this does or has not fixed this then do this. So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between. This can be done from the live install as well.

---

### Post by presence1960 on 2011-01-13
> **wilee-nilee said:**
> I assume you have run in Ubuntu.
sudo update-grub
If this does or has not fixed this then do this. So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between. This can be done from the live install as well.

+1

Without that info we have no way of knowing what your setup and boot process is on the machine.

---

### Post by Impact15 on 2011-01-13
Like this?
 
```
                Boot Info Script 0.55    dated February 15th, 2010                    
============================= Boot Info Summary: ==============================
 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________
    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM
sda2: _________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM
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
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot         Start           End          Size  Id System
/dev/sda1                  63    10,233,404    10,233,342  12 Compaq diagnostics
/dev/sda2    *     10,233,856   175,538,187   165,304,332   7 HPFS/NTFS
/dev/sda3         175,540,222   312,580,095   137,039,874   5 Extended
/dev/sda5         175,540,224   306,903,039   131,362,816  83 Linux
/dev/sda6         306,905,088   312,580,095     5,675,008  82 Linux swap / Solaris

Drive: sdb ___________________ _____________________________________________________
Disk /dev/sdb: 4063 MB, 4063232000 bytes
5 heads, 32 sectors/track, 49600 cylinders, total 7936000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot         Start           End          Size  Id System
/dev/sdb1    *          8,064     7,935,999     7,927,936   b W95 FAT32

blkid -c /dev/null: ____________________________________________________________
Device           UUID                                   TYPE       LABEL                         
/dev/loop0                                              squashfs                                 
/dev/sda1        0159-6699                              vfat       PQSERVICE                     
/dev/sda2        349C63639C631E9C                       ntfs       ACER                          
/dev/sda3: PTTYPE="dos" 
/dev/sda5        e9243692-586d-4a33-9526-56dc913d8f14   ext4                                     
/dev/sda6        c45b715e-7751-4854-8c7e-e006ac7ae3a8   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        F456-F961                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 
============================ "mount | grep ^/dev  output: ===========================
Device           Mount_Point              Type       Options
aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

================================ sda2/boot.ini: ================================
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
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
search --no-floppy --fs-uuid --set e9243692-586d-4a33-9526-56dc913d8f14
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set e9243692-586d-4a33-9526-56dc913d8f14
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos5)'
 search --no-floppy --fs-uuid --set e9243692-586d-4a33-9526-56dc913d8f14
 linux /boot/vmlinuz-2.6.35-24-generic root=UUID=e9243692-586d-4a33-9526-56dc913d8f14 ro   quiet splash
 initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos5)'
 search --no-floppy --fs-uuid --set e9243692-586d-4a33-9526-56dc913d8f14
 echo 'Loading Linux 2.6.35-24-generic ...'
 linux /boot/vmlinuz-2.6.35-24-generic root=UUID=e9243692-586d-4a33-9526-56dc913d8f14 ro single 
 echo 'Loading initial ramdisk ...'
 initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos5)'
 search --no-floppy --fs-uuid --set e9243692-586d-4a33-9526-56dc913d8f14
 linux /boot/vmlinuz-2.6.35-22-generic root=UUID=e9243692-586d-4a33-9526-56dc913d8f14 ro   quiet splash
 initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos5)'
 search --no-floppy --fs-uuid --set e9243692-586d-4a33-9526-56dc913d8f14
 echo 'Loading Linux 2.6.35-22-generic ...'
 linux /boot/vmlinuz-2.6.35-22-generic root=UUID=e9243692-586d-4a33-9526-56dc913d8f14 ro single 
 echo 'Loading initial ramdisk ...'
 initrd /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###
### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###
### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos5)'
 search --no-floppy --fs-uuid --set e9243692-586d-4a33-9526-56dc913d8f14
 linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos5)'
 search --no-floppy --fs-uuid --set e9243692-586d-4a33-9526-56dc913d8f14
 linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
 insmod part_msdos
 insmod fat
 set root='(hd0,msdos1)'
 search --no-floppy --fs-uuid --set 0159-6699
 drivemap -s (hd0) ${root}
 chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" {
 insmod part_msdos
 insmod ntfs
 set root='(hd0,msdos2)'
 search --no-floppy --fs-uuid --set 349c63639c631e9c
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
UUID=e9243692-586d-4a33-9526-56dc913d8f14 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=c45b715e-7751-4854-8c7e-e006ac7ae3a8 none            swap    sw              0       0
=================== sda5: Location of files loaded by Grub: ===================

  94.3GB: boot/grub/core.img
 103.0GB: boot/grub/grub.cfg
  91.2GB: boot/initrd.img-2.6.35-22-generic
  91.2GB: boot/initrd.img-2.6.35-24-generic
  94.3GB: boot/vmlinuz-2.6.35-22-generic
  94.3GB: boot/vmlinuz-2.6.35-24-generic
  91.2GB: initrd.img
  91.2GB: initrd.img.old
  94.3GB: vmlinuz
  94.3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================
Unknown BootLoader  on sda3
00000000  74 d5 e7 ff cc cc cc cc  f0 df f1 ff 4b 00 00 00  |t...........K...|
00000010  8b 0d c8 d7 ee 79 e8 e5  d4 e7 ff 8b f0 ba 00 10  |.....y..........|
00000020  ee 79 b9 2e 39 00 70 e8  54 d5 e7 ff 8b d0 8b ce  |.y..9.p.T.......|
00000030  e8 0b c6 e7 ff 8b ce e8  3c d5 e7 ff 8b 0d c8 d7  |........<.......|
00000040  ee 79 e8 b9 d4 e7 ff 8b  f0 ba 00 10 ee 79 b9 3a  |.y...........y.:|
00000050  39 00 70 e8 28 d5 e7 ff  8b d0 8b ce e8 df c5 e7  |9.p.(...........|
00000060  ff 8b ce e8 10 d5 e7 ff  cc cc cc cc 5c e0 f1 ff  |............\...|
00000070  4a 00 00 00 8b 0d c8 d7  ee 79 e8 81 d4 e7 ff 8b  |J........y......|
00000080  f0 ba 00 10 ee 79 b9 2e  39 00 70 e8 f0 d4 e7 ff  |.....y..9.p.....|
00000090  8b d0 8b ce e8 a7 c5 e7  ff 8b ce e8 d8 d4 e7 ff  |................|
000000a0  8b 0d c8 d7 ee 79 e8 55  d4 e7 ff 8b f0 ba 00 10  |.....y.U........|
000000b0  ee 79 b9 3a 39 00 70 e8  c4 d4 e7 ff 8b d0 8b ce  |.y.:9.p.........|
000000c0  e8 7b c5 e7 ff 8b ce e8  ac d4 e7 ff cc cc cc cc  |.{..............|
000000d0  58 e0 f1 ff 4b 00 00 00  8b 0d c8 d7 ee 79 e8 1d  |X...K........y..|
000000e0  d4 e7 ff 8b f0 ba 00 10  ee 79 b9 2e 39 00 70 e8  |.........y..9.p.|
000000f0  8c d4 e7 ff 8b d0 8b ce  e8 43 c5 e7 ff 8b ce e8  |.........C......|
00000100  74 d4 e7 ff 8b 0d c8 d7  ee 79 e8 f1 d3 e7 ff 8b  |t........y......|
00000110  f0 ba 00 10 ee 79 b9 3a  39 00 70 e8 60 d4 e7 ff  |.....y.:9.p.`...|
00000120  8b d0 8b ce e8 17 c5 e7  ff 8b ce e8 48 d4 e7 ff  |............H...|
00000130  cc cc cc cc c4 e0 f1 ff  35 00 00 00 8b 0d c8 d7  |........5.......|
00000140  ee 79 e8 b9 d3 e7 ff 8b  f0 ba 00 10 ee 79 b9 5a  |.y...........y.Z|
00000150  38 00 70 e8 28 d4 e7 ff  8b d0 8b ce e8 df c4 e7  |8.p.(...........|
00000160  ff 8b ce e8 10 d4 e7 ff  cc cc cc cc 6c e1 f1 ff  |............l...|
00000170  47 02 00 00 8b 0d c8 d7  ee 79 e8 81 d3 e7 ff 8b  |G........y......|
00000180  f0 ba 00 10 ee 79 b9 2e  39 00 70 e8 f0 d3 e7 ff  |.....y..9.p.....|
00000190  8b d0 8b ce e8 a7 c4 e7  ff 8b ce e8 d8 d3 e7 ff  |................|
000001a0  8b 0d c8 d7 ee 79 e8 55  d3 e7 ff 8b f0 ba 00 10  |.....y.U........|
000001b0  ee 79 b9 3a 39 00 70 e8  c4 d3 e7 ff 8b d0 00 fe  |.y.:9.p.........|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 70 d4 07 00 fe  |...........p....|
000001d0  ff ff 05 fe ff ff 02 70  d4 07 00 a0 56 00 00 00  |.......p....V...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
Unknown BootLoader  on sdb1
00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 a2 03  |.X.SYSLINUX.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 80 1f 00 00  |........?.......|
00000020  80 f8 78 00 2f 1e 00 00  00 00 00 00 02 00 00 00  |..x./...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 61 f9 56 f4 4e  4f 20 4e 41 4d 45 20 20  |..)a.V.NO NAME  |
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
00000100  7d 00 66 b8 d0 fd 15 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......|
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

### Post by Quackers on 2011-01-13
os-prober is picking up your Windows installation on sda2. I can't see anything wrong with the boot script output.
When you boot are you getting a grub menu on which Windows is listed?

---

### Post by presence1960 on 2011-01-13
looks OK to me. Please elaborate more when you say "can not boot to XP." Exactly what is happening when you boot your machine?

---

### Post by Impact15 on 2011-01-13
GRUB gives me:
Microsoft NT/2000/XP (on /dev/sda1)
Microsoft Windows XP Home Edition (on /dev/sda2)
 
When I select Windows XP I get a flashing cursor and nothing else............

---

### Post by wilee-nilee on 2011-01-13
> **Impact15 said:**
> GRUB gives me:
Microsoft NT/2000/XP (on /dev/sda1)
Microsoft Windows XP Home Edition (on /dev/sda2)
 
When I select Windows XP I get a flashing cursor and nothing else............

I am assuming your choosing sda2, that is the one that should boot. Have you tried hitting f8=safemode immediately on choosing XP?

Have tried booting to the command line on the XP install disk and running a chkdsk /f/r

---

### Post by Impact15 on 2011-01-13
Yes, I am using sda2, yes I have used "f8" and still nothing... I have no CD for this netbook so using the XP install disk is kinda not going to work for me. :(

---

### Post by wilee-nilee on 2011-01-13
> **Impact15 said:**
> Yes, I am using sda2, yes I have used "f8" and still nothing... I have no CD for this netbook so using the XP install disk is kinda not going to work for me. :(

How did you reinstall?

---

### Post by Impact15 on 2011-01-14
Magic! LOL I used a thumb drive and booted from the USB.

---

