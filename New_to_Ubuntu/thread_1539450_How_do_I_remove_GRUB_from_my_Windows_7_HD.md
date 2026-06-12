---
title: "How do I remove GRUB from my Windows 7 HD?"
date: 2010-07-26
forum: New to Ubuntu
---

### Post by Super_Dork_42 on 2010-07-26
I had broken my ubuntu (Karmic) by posting someone's list of all repos, so since that included ones for previous ubuntus, mine wouldn't update to 10.4. However, GRUB did. It somehow got installed, without any direction from me, onto all my hard drives and all partitions. I reinstalled Ubuntu with the 10.4 live cd, but I still cant get GRUB off windows so that I won't have to reinstall it. WHAT DO I DO?:(

---

### Post by Zorgoth on 2010-07-26
If you can boot into Windows, use one of these command-line utilities:

mbrfix (for 32-bit systems ONLY)
mbrfix64 (for 64-bit systems ONLY)

---

### Post by Super_Dork_42 on 2010-07-27
I guess I should have been more specific. How do I remove _a broken _GRUB from my windows 7 HD if I can only boot into ubuntu?
I fear I may have to reinstall windows.

---

### Post by oldfred on 2010-07-27
When the instructions said all drives they meant sda, sdb etc not partitions sda1, sda2 sdb1 etc. You overwrote the windows boot sector in the windows partition.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

If you have more than one windows you need to repair them all.

After rebooting in Ubuntu 
sudo update-grub

---

### Post by Super_Dork_42 on 2010-07-28
I ran boot info script and copied and pasted 'results.txt' here. It says:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 578183 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    74,864,639    74,862,592  83 Linux
/dev/sda2          74,866,686    78,163,967     3,297,282   5 Extended
/dev/sda5          74,866,688    78,163,967     3,297,280  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   160,826,714   160,826,652   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        04332aae-26e0-4760-b160-70ffa2a578e3   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        2812bb2d-054a-4525-aebf-6c7bbd7f3325   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        61608766128CEF1C                       ntfs                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 04332aae-26e0-4760-b160-70ffa2a578e3
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 04332aae-26e0-4760-b160-70ffa2a578e3
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
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 04332aae-26e0-4760-b160-70ffa2a578e3
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=04332aae-26e0-4760-b160-70ffa2a578e3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 04332aae-26e0-4760-b160-70ffa2a578e3
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=04332aae-26e0-4760-b160-70ffa2a578e3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 04332aae-26e0-4760-b160-70ffa2a578e3
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 04332aae-26e0-4760-b160-70ffa2a578e3
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 61608766128cef1c
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=04332aae-26e0-4760-b160-70ffa2a578e3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=2812bb2d-054a-4525-aebf-6c7bbd7f3325 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  21.6GB: boot/grub/core.img
  23.7GB: boot/grub/grub.cfg
  21.7GB: boot/initrd.img-2.6.32-21-generic
  21.6GB: boot/vmlinuz-2.6.32-21-generic
  21.7GB: initrd.img
  21.6GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  ff 8b 86 98 01 00 00 66  83 60 4c fb 83 7d dc 00  |.......f.`L..}..|
00000010  0f 85 2d 01 00 00 8b 55  e4 89 f0 e8 b0 e3 ff ff  |..-....U........|
00000020  8b 86 98 01 00 00 ba 68  1f 6b c0 8b 40 3c 25 00  |.......h.k..@<%.|
00000030  0c 00 00 3d 00 04 00 00  74 11 3d 00 08 00 00 ba  |...=....t.=.....|
00000040  cc 28 6b c0 74 05 ba da  28 6b c0 89 54 24 04 c7  |.(k.t...(k..T$..|
00000050  04 24 44 84 6b c0 e8 a9  14 32 00 e8 70 3b 32 00  |.$D.k....2..p;2.|
00000060  c7 45 e4 00 00 00 00 e9  ec f4 ff ff 8b 4d ec 89  |.E...........M..|
00000070  f0 8b 55 e4 e8 07 ee ff  ff 85 c0 0f 85 63 fe ff  |..U..........c..|
00000080  ff e9 8f fe ff ff 8b 83  f4 00 00 00 31 c9 31 d2  |............1.1.|
00000090  c7 04 24 01 00 00 00 e8  c4 8c 04 00 85 c0 0f 84  |..$.............|
000000a0  24 02 00 00 8b 86 98 01  00 00 8b 40 3c e9 bc fe  |$..........@<...|
000000b0  ff ff 81 4b 3c 00 04 00  00 8b 86 98 01 00 00 8b  |...K<...........|
000000c0  40 3c e9 a7 fe ff ff c7  04 24 00 84 6b c0 e8 31  |@<.......$..k..1|
000000d0  14 32 00 89 f8 e8 c6 cf  fa ff c7 45 e4 f4 ff ff  |.2.........E....|
000000e0  ff 8b 83 f4 00 00 00 e8  b4 95 04 00 e9 6f fc ff  |.............o..|
000000f0  ff 8d 86 78 01 00 00 89  44 24 04 c7 04 24 78 84  |...x....D$...$x.|
00000100  6b c0 e8 fd 13 32 00 c7  45 e4 ea ff ff ff e9 e6  |k....2..E.......|
00000110  f3 ff ff c7 04 24 1c 7f  6b c0 e8 e5 13 32 00 c7  |.....$..k....2..|
00000120  45 e4 ea ff ff ff e9 0c  f4 ff ff c7 04 24 f4 7e  |E............$.~|
00000130  6b c0 e8 cd 13 32 00 c7  45 e4 ea ff ff ff e9 f4  |k....2..E.......|
00000140  f3 ff ff c7 04 24 24 84  6b c0 e8 b5 13 32 00 e9  |.....$$.k....2..|
00000150  c2 fe ff ff 8b 15 e8 81  78 c0 85 d2 89 55 d8 0f  |........x....U..|
00000160  84 97 f2 ff ff 8b 0a 89  4d d4 8b 45 e4 89 da b9  |........M..E....|
00000170  14 01 00 00 c7 44 24 04  d0 80 00 00 89 04 24 b8  |.....D$.......$.|
00000180  c7 c9 24 c0 ff 55 d4 83  45 d8 04 8b 55 d8 8b 12  |..$..U..E...U...|
00000190  85 d2 89 55 d4 75 d3 e9  60 f2 ff ff 8b 4d cc c7  |...U.u..`....M..|
000001a0  04 24 b4 80 6b c0 89 4c  24 04 e8 55 13 32 00 c7  |.$..k..L$..U.2..|
000001b0  45 e4 ea ff ff ff e9 7c  f3 ff ff 89 44 24 00 fe  |E......|....D$..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 50 32 00 00 00  |...........P2...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```
Also, I wish this forum had thanks.

---

### Post by wilee-nilee on 2010-07-28
Never mind lets let better minds work on this.

---

### Post by Super_Dork_42 on 2010-07-28
That was why I asked the whole forum, not just you.

---

### Post by uRock on 2010-07-28
> **presence1960 said:**
> you can repair the mbr to a windows mbr from  ubuntu or the ubuntu live cd. Install lilo by running in terminal  ```
sudo apt-get install lilo
```ignore the warning and next run in  terminal ```
sudo lilo -m /dev/sdx mbr
```where is sdx is your  disk/device, i.e. Sda, sdb,sdc, etc:d

---

### Post by oldfred on 2010-07-28
See post #4 as the fix for this problem, You cannot have grub2 in the window boot sector:

sdb1: __________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  [COLOR=Red]Grub 2 is installed in the boot sector of sdb1[/COLOR] and 
                       looks at sector 578183 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

---

### Post by wilee-nilee on 2010-07-29
> **Super_Dork_42 said:**
> That was why I asked the whole forum, not just you.

Follow post 9 which directs you to post 4 this is what I suggested originally and is correct.

---

### Post by Super_Dork_42 on 2010-07-30
THANKS OLD FRED, you are the BOMB!
Also, SOLVED.

---

