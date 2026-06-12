---
title: "Can't boot vista after installing LinuxMint"
date: 2010-12-22
forum: New to Ubuntu
---

### Post by hamdimo on 2010-12-22
[SIZE=2]i have a laptop running vista in its perfect condition, i wanted linux  mint on the second partition, everything went ok with Mint installation  but when i restarted i didn't get the choice of which system i wanna  boot!!! it goes automatically to linux mint, :confused:
WHAT SHOULD I DO NOW ? plz help me, i'm really down!!!

[B]now i can't boot to both, nor Vista or Mint, i'm just using Mint LiveCD
help me poeple![/B]
[/SIZE]

---

### Post by wojox on 2010-12-22
Open a terminal and run:

```
sudo update-grub
```

---

### Post by hamdimo on 2010-12-22
> **wojox said:**
> Open a terminal and run:

```
sudo update-grub
```

i had a look before for the file menu.lst in the folder grub, and there was no such thing, now i can see it, i opened it and this is what i see: "hope you understand sth; cuz i just don't"

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=3b8a2c2b-681a-42d7-ac4c-b9635cdc1b4c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3b8a2c2b-681a-42d7-ac4c-b9635cdc1b4c

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Linux Mint 10 Julia, kernel 2.6.35-22-generic
uuid        3b8a2c2b-681a-42d7-ac4c-b9635cdc1b4c
kernel        /boot/vmlinuz-2.6.35-22-generic root=UUID=3b8a2c2b-681a-42d7-ac4c-b9635cdc1b4c ro quiet splash 
initrd        /boot/initrd.img-2.6.35-22-generic

title        Linux Mint 10 Julia, kernel 2.6.35-22-generic (recovery mode)
uuid        3b8a2c2b-681a-42d7-ac4c-b9635cdc1b4c
kernel        /boot/vmlinuz-2.6.35-22-generic root=UUID=3b8a2c2b-681a-42d7-ac4c-b9635cdc1b4c ro  single
initrd        /boot/initrd.img-2.6.35-22-generic

title        Chainload into GRUB 2
root        3b8a2c2b-681a-42d7-ac4c-b9635cdc1b4c
kernel        /boot/grub/core.img

title        Linux Mint 10 Julia, memtest86+
uuid        3b8a2c2b-681a-42d7-ac4c-b9635cdc1b4c
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by wilee-nilee on 2010-12-22
Mnt 10 is grub2 not grub-legacy which would be menu.list it is hard to tell what is going on do this fro a real what is where look so we can help.

So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags paste all the text in between. Don't miss the codetags it is hard to read without them. ;)

---

### Post by hamdimo on 2010-12-22
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 146708711 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /grldr /ntldr 
                       /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 10 Julia
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   135,157,679   135,157,617   7 HPFS/NTFS
/dev/sda2         135,157,741   156,295,439    21,137,699   f W95 Ext d (LBA)
/dev/sda5         135,157,743   156,295,439    21,137,697  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        2608ADDC08ADAAEF                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        3b8a2c2b-681a-42d7-ac4c-b9635cdc1b4c   ext3                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext3       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sda5/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=3b8a2c2b-681a-42d7-ac4c-b9635cdc1b4c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3b8a2c2b-681a-42d7-ac4c-b9635cdc1b4c

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Linux Mint 10 Julia, kernel 2.6.35-22-generic
uuid        3b8a2c2b-681a-42d7-ac4c-b9635cdc1b4c
kernel        /boot/vmlinuz-2.6.35-22-generic root=UUID=3b8a2c2b-681a-42d7-ac4c-b9635cdc1b4c ro quiet splash 
initrd        /boot/initrd.img-2.6.35-22-generic

title        Linux Mint 10 Julia, kernel 2.6.35-22-generic (recovery mode)
uuid        3b8a2c2b-681a-42d7-ac4c-b9635cdc1b4c
kernel        /boot/vmlinuz-2.6.35-22-generic root=UUID=3b8a2c2b-681a-42d7-ac4c-b9635cdc1b4c ro  single
initrd        /boot/initrd.img-2.6.35-22-generic

title        Chainload into GRUB 2
root        3b8a2c2b-681a-42d7-ac4c-b9635cdc1b4c
kernel        /boot/grub/core.img

title        Linux Mint 10 Julia, memtest86+
uuid        3b8a2c2b-681a-42d7-ac4c-b9635cdc1b4c
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

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
search --no-floppy --fs-uuid --set 3b8a2c2b-681a-42d7-ac4c-b9635cdc1b4c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 3b8a2c2b-681a-42d7-ac4c-b9635cdc1b4c
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

### BEGIN /etc/grub.d/06_mint_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 3b8a2c2b-681a-42d7-ac4c-b9635cdc1b4c
insmod png
if background_image /boot/grub/linuxmint.png ; then
  set color_normal=white/black
  set color_highlight=white/light-gray
else
  set menu_color_normal=white/black
  set menu_color_highlight=white/light-gray
fi
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Linux Mint 10, 2.6.35-22-generic (/dev/sda5)' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 3b8a2c2b-681a-42d7-ac4c-b9635cdc1b4c
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=3b8a2c2b-681a-42d7-ac4c-b9635cdc1b4c ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Linux Mint 10, 2.6.35-22-generic (/dev/sda5) -- recovery mode' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 3b8a2c2b-681a-42d7-ac4c-b9635cdc1b4c
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=3b8a2c2b-681a-42d7-ac4c-b9635cdc1b4c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 3b8a2c2b-681a-42d7-ac4c-b9635cdc1b4c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 3b8a2c2b-681a-42d7-ac4c-b9635cdc1b4c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 2608addc08adaaef
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
/dev/sda5       /               ext3    errors=remount-ro 0       1

=================== sda5: Location of files loaded by Grub: ===================


  75.1GB: boot/grub/core.img
  75.2GB: boot/grub/grub.cfg
  75.2GB: boot/grub/menu.lst
  75.1GB: boot/initrd.img-2.6.35-22-generic
  75.1GB: boot/vmlinuz-2.6.35-22-generic
  75.1GB: initrd.img
  75.1GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  f0 92 a2 e1 f0 43 97 f0  48 f2 a1 fe 62 b9 0b d5  |.....C..H...b...|
00000010  c5 58 a8 45 e8 8b 65 69  ca 7f 3f 76 31 b2 a6 fc  |.X.E..ei..?v1...|
00000020  36 25 4b fa 5c ab fd 96  e2 2b a6 4b c0 37 3c 24  |6%K.\....+.K.7<$|
00000030  40 83 ee 82 9f cc c2 53  e8 83 c5 02 c1 29 55 0f  |@......S.....)U.|
00000040  66 6e 49 4c 22 14 4a 90  26 07 41 31 e1 15 0f 9c  |fnIL".J.&.A1....|
00000050  b9 a4 74 74 7c 89 b6 c3  d1 f5 d5 7d 1d 1d 2a 96  |..tt|......}..*.|
00000060  d2 ba 6a 9d 28 5d 1c 16  1b f8 64 13 1c 6c cb ab  |..j.(]....d..l..|
00000070  fc 48 33 49 ea 72 83 e2  30 84 5c 10 be 10 01 0c  |.H3I.r..0.\.....|
00000080  4b f1 7c f1 77 ff 07 4a  e7 2f c5 a0 c3 f1 fc 54  |K.|.w..J./.....T|
00000090  10 ef 1b 2f 2e c2 f5 5b  b3 70 66 08 74 14 21 08  |.../...[.pf.t.!.|
000000a0  18 79 67 21 7c 56 7e 89  45 e0 84 5f 00 b6 65 4c  |.yg!|V~.E.._..eL|
000000b0  2d 07 c0 72 aa 33 65 62  e3 9e a4 7e a8 0e 0f 6c  |-..r.3eb...~...l|
000000c0  9f 03 5d e6 ac 42 3e 1f  89 76 64 8d de 7a 2e 4a  |..]..B>..vd..z.J|
000000d0  2e 8a 10 0b 59 fc de 69  c9 55 ff ec 49 16 90 ef  |....Y..i.U..I...|
000000e0  1e f0 4c 2c b5 0a 69 8f  9a a9 97 82 60 30 bc af  |..L,..i.....`0..|
000000f0  fe 54 a3 f7 fc 57 fb 27  1a c6 aa b6 26 d3 52 66  |.T...W.'....&.Rf|
00000100  69 b4 5a 45 34 74 74 5a  82 21 39 ae 24 74 f1 23  |i.ZE4ttZ.!9.$t.#|
00000110  cb b0 5f 47 d1 fd 14 bd  5b 04 c1 5e 09 8d ce 1c  |.._G....[..^....|
00000120  1a 39 b7 e7 79 13 d1 80  34 37 39 1c a1 c1 75 1d  |.9..y...479...u.|
00000130  73 4b 95 6d a1 11 86 6c  4d cd 3c 3e 90 c2 c1 6f  |sK.m...lM.<>...o|
00000140  97 aa f4 f0 fa fc 47 1e  a9 f7 81 92 19 66 df ab  |......G......f..|
00000150  fd b6 de fe f6 d5 f1 69  0c 6f ed bb 47 7f c9 12  |.......i.o..G...|
00000160  3a f8 be 17 59 fc 1d f9  a8 f7 83 e0 16 14 51 ee  |:...Y.........Q.|
00000170  47 17 d0 84 07 b2 eb 95  7e df 8f 2a ef f4 57 fd  |G.......~..*..W.|
00000180  ba d4 a6 47 c0 38 82 c3  8f 62 be 63 a4 96 37 d7  |...G.8...b.c..7.|
00000190  e1 7d b6 ac cd 30 af 76  01 bf 2a 18 83 e0 6b 6d  |.}...0.v..*...km|
000001a0  e7 85 d6 8f 47 99 2a 4d  ec 3e 3f 1f 45 25 df 56  |....G.*M.>?.E%.V|
000001b0  c4 6a 93 d5 22 23 c1 f0  12 72 d9 3f c8 78 00 ef  |.j.."#...r.?.x..|
000001c0  ff ff 83 ef ff ff 02 00  00 00 21 89 42 01 00 00  |..........!.B...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by wilee-nilee on 2010-12-22
The first code tag at the top should look like this [code] :)

---

### Post by wilee-nilee on 2010-12-22
So when you boot the computer now it is still gong to Mint?

If you could remove or codetag your first text post #3 it would be helpful in just shortening the page, you have a fairly messed up setup, but probably fixable. It will take a few post to get you in shape. :)

---

### Post by hamdimo on 2010-12-22
> **wilee-nilee said:**
> So when you boot the computer now it is still gong to Mint?

If you could remove or codetag your first text post #3 it would be helpful in just shortening the page, you have a fairly messed up setup, but probably fixable. It will take a few post to get you in shape. :)

ok, i hope we gonna fix this :) 
and yes it always boot into Mint, :(
i'll also edit the other text

---

### Post by wilee-nilee on 2010-12-22
Windows is installed in the MBR of /dev/sda
this line makes it seem that it should be trying to get to Vista.

Do you have easybcd installed?

Are you seeing a Grub menu, or is it showing a menu, at all.

---

### Post by hamdimo on 2010-12-22
no, i don't have that installed
the only menu i get when restarting is a one from mint, with 5 choices i think, the first one is by default, it starts after 9 seconds, the second one is also Mint and it's recovery mode or such thing, the next two lines are test memory
what kills me is the last line which normally allows Vista to start, but after choosing it... i only get a black screen for 3 seconds then come back the usual Mint boot menu

---

### Post by wilee-nilee on 2010-12-22
sda1: _________________________________________________________________________

    File system:       ntfs
    [B]Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 146708711 of the same hard drive for 
                       core.img, but core.img can not be found at this [/B]
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /grldr /ntldr 
                       /NTDETECT.COM

Theoretically you should not be booting anything, but you have grub in the Vista partition so we need to get that out first follow this link, and repost a newly run script.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by hamdimo on 2010-12-22
during the "testdisk" something happens in the sixth screen, i don't see "backupBS" and this is what i see: 
```
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 80 GB / 74 GiB - CHS 9729 255 63
     Partition                  Start        End    Size in sectors
 1 * HPFS - NTFS              0   1  1  8413  44 63  135157617

Boot sector
Warning: Incorrect number of heads/cylinder 240 (NTFS) != 255 (HD)
Status: OK

Backup boot sector
Status: Bad

Sectors are not identical.

A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.



[  Quit  ]  [  List  ]  [Org. BS ]  [Rebuild BS]  [  Dump  ]
                            Return to Advanced menu

```

---

### Post by wilee-nilee on 2010-12-22
You might download the vista recovery disc and run this command in the repair command line. You can do the same from a straight install disc or run the auto repair 3 times.
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

```
bootrec.exe /fixboot
```

And see if that cleans it, it is the advice on that pages link.

---

### Post by hamdimo on 2010-12-22
> **wilee-nilee said:**
> You might download the vista recovery disc and run this command in the repair command line. You can do the same from a straight install disc or run the auto repair 3 times.
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

```
bootrec.exe /fixboot
```And see if that cleans it, it is the advice on that pages link.

i have to run the aurorepair 3 times??? ok :) i'll do that,
i actually have the "vista recovery disk here with me"i did a startup repair and nothing wrong was detected it said, i also typed sth in the command prompt and it didn't work, now i'll try yours :) it seems easier

---

### Post by wilee-nilee on 2010-12-22
> **hamdimo said:**
> i have to run the aurorepair 3 times??? ok :) i'll do that,
i actually have the "vista recovery disk here with me"i did a startup repair and nothing wrong was detected it said, i also typed sth in the command prompt and it didn't work, now i'll try yours :) it seems easier

You have a upgrade from XP I think right?

---

### Post by hamdimo on 2010-12-22
> **wilee-nilee said:**
> You have a upgrade from XP I think right?
no i don't have an upgrade, and i think i know why you asked that
i tried a tool called super grub----- it's an iso file must be burned on a cd then ........... yeah really hard i couldn't make it work, and somehow there was an option of fixing windows boot files,,i clicked then i had to choose ich version i have, and the problem that vista wasn't in the middle, i i just chose windows xp/2000/ and other versions
i think that's why you can see it there in the text :( SHIIIIIIIT this is ****ed up :(

---

### Post by wilee-nilee on 2010-12-22
So besides the autofix/autoreapir function run three times there is a command set I will give you the whole set for your needs. Notice the Windows7 forum link that goes along with the directions to the command line you have been on the same page/gui, I believe. 

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
BootRec.exe /fixmbr (#updates MBR master boot record...do not run if you still want grub)
chkdsk /r
BootRec.exe /FixBoot (#updates PBR partition boot)
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

---

### Post by hamdimo on 2010-12-23
> **wilee-nilee said:**
> So besides the autofix/autoreapir function run three times there is a command set I will give you the whole set for your needs. Notice the Windows7 forum link that goes along with the directions to the command line you have been on the same page/gui, I believe. 

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
BootRec.exe /fixmbr (#updates MBR master boot record...do not run if you still want grub)
chkdsk /r
BootRec.exe /FixBoot (#updates PBR partition boot)
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

first i hope you are online, so last night i run the recovery disk, in the command prompt i typed this: **bootrec.exe /fixboot**
well... it went succesfully they said but when i restarted notthing booted anymore, even mint didn't boot !! 
so now i'm here using the Mint live cd!! crazy hé. i also tried the command FixMbr and didn't do any good. something somewhere somehow wnet all wrong man! i appreciate your help so much
now... i'll try the commands you suggested and in that order

---

### Post by hamdimo on 2010-12-23
no.... and i still see nothing booting up

i tried also the tips from the windows 7 recovery, and at the end when i type **bootsect /nt60 SYS /mbr** i just get an error message saying that the command isn't recognized

---

### Post by hamdimo on 2010-12-23
plz anyone knows how to fix this? :sad:

---

### Post by drs305 on 2010-12-23
Please rerun the boot info script and let's see what the status of your system is after your  attempts to fix things.

---

### Post by hamdimo on 2010-12-23
> **drs305 said:**
> Please rerun the boot info script and let's see what the status of your system is after your  attempts to fix things.

thanks for answering :) i have two partitions on my laptop, on the first one is vista and on the second one is Mint installed, now i'm running Mlint Live CD 
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /grldr /ntldr 
                       /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 10 Julia
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   135,157,679   135,157,617   7 HPFS/NTFS
/dev/sda2         135,157,741   156,295,439    21,137,699   f W95 Ext d (LBA)
/dev/sda5         135,157,743   156,295,439    21,137,697  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        2608ADDC08ADAAEF                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        3b8a2c2b-681a-42d7-ac4c-b9635cdc1b4c   ext3                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /media/3b8a2c2b-681a-42d7-ac4c-b9635cdc1b4c ext3       (rw,nosuid,nodev,uhelper=udisks)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sda5/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=3b8a2c2b-681a-42d7-ac4c-b9635cdc1b4c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3b8a2c2b-681a-42d7-ac4c-b9635cdc1b4c

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Linux Mint 10 Julia, kernel 2.6.35-22-generic
uuid        3b8a2c2b-681a-42d7-ac4c-b9635cdc1b4c
kernel        /boot/vmlinuz-2.6.35-22-generic root=UUID=3b8a2c2b-681a-42d7-ac4c-b9635cdc1b4c ro quiet splash 
initrd        /boot/initrd.img-2.6.35-22-generic

title        Linux Mint 10 Julia, kernel 2.6.35-22-generic (recovery mode)
uuid        3b8a2c2b-681a-42d7-ac4c-b9635cdc1b4c
kernel        /boot/vmlinuz-2.6.35-22-generic root=UUID=3b8a2c2b-681a-42d7-ac4c-b9635cdc1b4c ro  single
initrd        /boot/initrd.img-2.6.35-22-generic

title        Chainload into GRUB 2
root        3b8a2c2b-681a-42d7-ac4c-b9635cdc1b4c
kernel        /boot/grub/core.img

title        Linux Mint 10 Julia, memtest86+
uuid        3b8a2c2b-681a-42d7-ac4c-b9635cdc1b4c
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

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
search --no-floppy --fs-uuid --set 3b8a2c2b-681a-42d7-ac4c-b9635cdc1b4c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 3b8a2c2b-681a-42d7-ac4c-b9635cdc1b4c
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

### BEGIN /etc/grub.d/06_mint_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 3b8a2c2b-681a-42d7-ac4c-b9635cdc1b4c
insmod png
if background_image /boot/grub/linuxmint.png ; then
  set color_normal=white/black
  set color_highlight=white/light-gray
else
  set menu_color_normal=white/black
  set menu_color_highlight=white/light-gray
fi
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Linux Mint 10, 2.6.35-22-generic (/dev/sda5)' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 3b8a2c2b-681a-42d7-ac4c-b9635cdc1b4c
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=3b8a2c2b-681a-42d7-ac4c-b9635cdc1b4c ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Linux Mint 10, 2.6.35-22-generic (/dev/sda5) -- recovery mode' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 3b8a2c2b-681a-42d7-ac4c-b9635cdc1b4c
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=3b8a2c2b-681a-42d7-ac4c-b9635cdc1b4c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 3b8a2c2b-681a-42d7-ac4c-b9635cdc1b4c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 3b8a2c2b-681a-42d7-ac4c-b9635cdc1b4c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 2608addc08adaaef
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
/dev/sda5       /               ext3    errors=remount-ro 0       1

=================== sda5: Location of files loaded by Grub: ===================


  75.1GB: boot/grub/core.img
  75.2GB: boot/grub/grub.cfg
  75.2GB: boot/grub/menu.lst
  75.1GB: boot/initrd.img-2.6.35-22-generic
  75.1GB: boot/vmlinuz-2.6.35-22-generic
  75.1GB: initrd.img
  75.1GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  f0 92 a2 e1 f0 43 97 f0  48 f2 a1 fe 62 b9 0b d5  |.....C..H...b...|
00000010  c5 58 a8 45 e8 8b 65 69  ca 7f 3f 76 31 b2 a6 fc  |.X.E..ei..?v1...|
00000020  36 25 4b fa 5c ab fd 96  e2 2b a6 4b c0 37 3c 24  |6%K.\....+.K.7<$|
00000030  40 83 ee 82 9f cc c2 53  e8 83 c5 02 c1 29 55 0f  |@......S.....)U.|
00000040  66 6e 49 4c 22 14 4a 90  26 07 41 31 e1 15 0f 9c  |fnIL".J.&.A1....|
00000050  b9 a4 74 74 7c 89 b6 c3  d1 f5 d5 7d 1d 1d 2a 96  |..tt|......}..*.|
00000060  d2 ba 6a 9d 28 5d 1c 16  1b f8 64 13 1c 6c cb ab  |..j.(]....d..l..|
00000070  fc 48 33 49 ea 72 83 e2  30 84 5c 10 be 10 01 0c  |.H3I.r..0.\.....|
00000080  4b f1 7c f1 77 ff 07 4a  e7 2f c5 a0 c3 f1 fc 54  |K.|.w..J./.....T|
00000090  10 ef 1b 2f 2e c2 f5 5b  b3 70 66 08 74 14 21 08  |.../...[.pf.t.!.|
000000a0  18 79 67 21 7c 56 7e 89  45 e0 84 5f 00 b6 65 4c  |.yg!|V~.E.._..eL|
000000b0  2d 07 c0 72 aa 33 65 62  e3 9e a4 7e a8 0e 0f 6c  |-..r.3eb...~...l|
000000c0  9f 03 5d e6 ac 42 3e 1f  89 76 64 8d de 7a 2e 4a  |..]..B>..vd..z.J|
000000d0  2e 8a 10 0b 59 fc de 69  c9 55 ff ec 49 16 90 ef  |....Y..i.U..I...|
000000e0  1e f0 4c 2c b5 0a 69 8f  9a a9 97 82 60 30 bc af  |..L,..i.....`0..|
000000f0  fe 54 a3 f7 fc 57 fb 27  1a c6 aa b6 26 d3 52 66  |.T...W.'....&.Rf|
00000100  69 b4 5a 45 34 74 74 5a  82 21 39 ae 24 74 f1 23  |i.ZE4ttZ.!9.$t.#|
00000110  cb b0 5f 47 d1 fd 14 bd  5b 04 c1 5e 09 8d ce 1c  |.._G....[..^....|
00000120  1a 39 b7 e7 79 13 d1 80  34 37 39 1c a1 c1 75 1d  |.9..y...479...u.|
00000130  73 4b 95 6d a1 11 86 6c  4d cd 3c 3e 90 c2 c1 6f  |sK.m...lM.<>...o|
00000140  97 aa f4 f0 fa fc 47 1e  a9 f7 81 92 19 66 df ab  |......G......f..|
00000150  fd b6 de fe f6 d5 f1 69  0c 6f ed bb 47 7f c9 12  |.......i.o..G...|
00000160  3a f8 be 17 59 fc 1d f9  a8 f7 83 e0 16 14 51 ee  |:...Y.........Q.|
00000170  47 17 d0 84 07 b2 eb 95  7e df 8f 2a ef f4 57 fd  |G.......~..*..W.|
00000180  ba d4 a6 47 c0 38 82 c3  8f 62 be 63 a4 96 37 d7  |...G.8...b.c..7.|
00000190  e1 7d b6 ac cd 30 af 76  01 bf 2a 18 83 e0 6b 6d  |.}...0.v..*...km|
000001a0  e7 85 d6 8f 47 99 2a 4d  ec 3e 3f 1f 45 25 df 56  |....G.*M.>?.E%.V|
000001b0  c4 6a 93 d5 22 23 c1 f0  12 72 d9 3f c8 78 00 ef  |.j.."#...r.?.x..|
000001c0  ff ff 83 ef ff ff 02 00  00 00 21 89 42 01 00 00  |..........!.B...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by drs305 on 2010-12-23
You still have a mixture of Grub legacy and Grub2 on your system. Since we don't know what is causing your problem, I would recommend booting the LiveCD and completely removing grub and grub-pc (Grub2) and then reinstalling them. It will restore Ubuntu/Mint and if you have fixed your Windows boot files, you should also be able to boot to Windows. 

To purge/restore Grub2, you will need to follow the Chroot procedures in this guide:
[http://ubuntuforums.org/showthread.php?t=1581099]("http://ubuntuforums.org/showthread.php?t=1581099")

Before you do that, if you want to get an idea of whether your Windows will be able to boot, you can use an alternate bootloader (lilo) to restore your MBR. If you run the following commands, Windows should be bootable. If it doesn't work, your Windows boot files are still having problems. In that case if you run the chroot procedures from the previous link you should at least have Mint back.
```
sudo apt-get install lilo
sudo lilo -M /dev/sda /mbr
```
As you run the commands you will be notified that lilo is not completely installed. Just disregard the messages, as we are not fully installing lilo.

Whether or not the second set of instructions work, if you want Mint use the guidance in the first link.

---

### Post by hamdimo on 2010-12-24
> **drs305 said:**
> You still have a mixture of Grub legacy and Grub2 on your system. Since we don't know what is causing your problem, I would recommend booting the LiveCD and completely removing grub and grub-pc (Grub2) and then reinstalling them. It will restore Ubuntu/Mint and if you have fixed your Windows boot files, you should also be able to boot to Windows. 

To purge/restore Grub2, you will need to follow the Chroot procedures in this guide:
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Before you do that, if you want to get an idea of whether your Windows will be able to boot, you can use an alternate bootloader (lilo) to restore your MBR. If you run the following commands, Windows should be bootable. If it doesn't work, your Windows boot files are still having problems. In that case if you run the chroot procedures from the previous link you should at least have Mint back.
```
sudo apt-get install lilo
sudo lilo -M /dev/sda /mbr
```As you run the commands you will be notified that lilo is not completely installed. Just disregard the messages, as we are not fully installing lilo.

Whether or not the second set of instructions work, if you want Mint use the guidance in the first link.
i know this will sound stupid, but... how can i just remove grub AND grub2 :) i've googles this for too long, there are tons of threads about this, but it seems that no one fits mine, and after removing them, how can i install them again, and why installing them both  again(if i might ask :) )
i installed lilo, and the problem still persists.
and what are the right commands for me exactly from that chroot procedures? i don't get it :)
this is all new to me man, i'm only one month old with linux, can't believe myself working with Terminal, it's crazy but i LOVE it, and i really wanna make it work. :)

---

### Post by drs305 on 2010-12-24
> **hamdimo said:**
> i know this will sound stupid, but... how can i just remove grub AND grub2 :) i've googles this for too long, there are tons of threads about this, but it seems that no one fits mine, and after removing them, how can i install them again, and why installing them both  again(if i might ask :) )

Just follow the steps in the link I provided in the previous post. Use the "Why Chroot" section.  In the first part of Section 1, use the two commands in 1C (do not use 1A or 1B). The second command in 1C would be:
```
sudo mount /dev/sda5 /mnt/temp
```
Then continue with the **Continue from A, B or C.** and accomplish the rest of the steps (2, 3, 4 and the rest ...)

Once you have 'chrooted' into your Ubuntu installation via the LiveCD, this is the actual command that removes Grub and Grub2:
```
apt-get purge grub grub-pc grub-common
```
Note you have to run all the previous commands to set up the environment for this command to work properly.

> 
i installed lilo, and the problem still persists.

This means that your attempt to repair the Windows boot files did not succeed. You still have work to do to get Windows to work. What you did by installing lilo was to rewrite the MBR and point it to the Windows boot partition. Assuming the two lilo commands ran without errors, it means that the MBR pointed to Windows, but the Windows files are still corrupted for some reason.

I'm not a Windows user but here is a post that provides most of the links on how to fix Windows. You have tried some of them already I know. 

You would ideally want to fix Windows first, since doing it second will erase some of the things you will do during the Grub purge/reinstall section.

---

### Post by hamdimo on 2010-12-25
[QUOTE=drs305;10275145]Just follow the steps in the link I provided in the previous post. Use the "Why Chroot" section.  In the first part of Section 1, use the two commands in 1C (do not use 1A or 1B). The second command in 1C would be:
```
sudo mount /dev/sda5 /mnt/temp
```Then continue with the **Continue from A, B or C.** and accomplish the rest of the steps (2, 3, 4 and the rest ...)

i think removing grub and grub pc went alright, but this is what i try to reinstall
```
mount: /dev/sda5 already mounted or /mnt/temp busy
mount: according to mtab, /dev/sda5 is already mounted on /mnt/temp

```
it means i've already mounted it, ok... next step is really awful!! look:
```
mint@mint ~ $ for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
mint@mint ~ $ sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf
mint@mint ~ $ apt-get update   # ***
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
mint@mint ~ $ 

```

---

### Post by hamdimo on 2010-12-25
this is crazy, look what happened after reinstalling grub again
```
                GNU GRUB version 1.98+20100804-5ubuntu3-1mint1
minimal BASH-LIKE line editing is supported for the first time.
for the first word, TAB lists possible command completions. Anywhere else TAB lists possible

grub>_
```i got fed up from this so i turned back to see what else i can do to repair Vista, i run the startup Repair 5 time i think, and somehow... there was something, i was told that some repairs were done then asked to restart (after two days of trying) ok i restarted and what i get? the code from GRUB you see above

what do you think? do i have to remove grub again? to see if Vista can boot or not?
do you think that this GRUB error prevented Vista from booting?

---

### Post by hamdimo on 2010-12-25
ALRIGHT, no LIVE cd anymore, Mint booted and everything looks fine,
all i need now is booooooooting Vista, :)

---

### Post by drs305 on 2010-12-25
From post #26, it looks like you never ran, or unsuccessfully ran, the command that would actually put you into the chroot environment (sudo chroot /mnt/temp). If you were successful, you would have been at a "root" prompt when you ran the purge/reinstall commands. 

In any case, if you are now booting to Ubuntu without a CD, try opening a terminal and running "sudo update-grub". Some times the Windows OS isn't picked up immediately after a Grub2 installation.

If you still aren't seeing a Windows menu entry but G2 is somehow working for you anyway, take a look at the following guide to see if it helps put Windows on the menu:
[http://ubuntuforums.org/showthread.php?t=1014708]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by hamdimo on 2010-12-26
> **drs305 said:**
> From post #26, it looks like you never ran, or unsuccessfully ran, the command that would actually put you into the chroot environment (sudo chroot /mnt/temp). If you were successful, you would have been at a "root" prompt when you ran the purge/reinstall commands. 

In any case, if you are now booting to Ubuntu without a CD, try opening a terminal and running "sudo update-grub". Some times the Windows OS isn't picked up immediately after a Grub2 installation.

If you still aren't seeing a Windows menu entry but G2 is somehow working for you anyway, take a look at the following guide to see if it helps put Windows on the menu:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

i'm back using the live cd now...  after the succesful boot of Mint, i turned to Vista and went the furthest i can, i've tried this and exactly the **Step Four: Nuclear Holocaust  **[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD) 
i restarted like i had to then ... nothing boots.
i know it looks weird how i could make a successful boot of Mint, that's why i saved everything i ran in Terminal in a text file, and it was this that made Mint boot:
```
**mint@mint ~ $** sudo mkdir /mnt/temp
**mint@mint ~ $** sudo mount /dev/sda5 /mnt/temp
**mint@mint ~ $** for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
**mint@mint ~ $** sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf
m**int@mint ~ $** sudo chroot /mnt/temp
 _________________________________________
/ A hundred years from now it is very     \
| likely that [of Twain's works] "The     |
| Jumping Frog" alone will be remembered. |
|                                         |
| -- Harry Thurston Peck (Editor of "The  |;int
\ Bookman"), January 1901.                /
 -----------------------------------------
   \
    \
        .--.
       |o_o |
       |:_/ |
      //   \ \
     (|     | )
    /'\_   _/`\
    \___)=(___/

**mint / #** apt-get update   # ***
Ign file: binary/ Release.gpg
Ign file:/usr/share/local-repository/ binary/ Translation-en                   
Ign file:/usr/share/local-repository/ binary/ Translation-en_US                
Ign file: binary/ Release                                                      
Ign file: binary/ Packages                                                     
Ign file: binary/ Packages                                                     
Get:1 http://archive.canonical.com maverick Release.gpg [198B]                 
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en       
Get:2 http://security.ubuntu.com maverick-security Release.gpg [198B]          
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en   
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_US    
Hit http://archive.canonical.com maverick Release                              
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Hit http://security.ubuntu.com maverick-security Release                       
Get:3 http://packages.linuxmint.com julia Release.gpg [198B]                   
Ign http://packages.linuxmint.com/ julia/import Translation-en                 
Ign http://packages.linuxmint.com/ julia/import Translation-en_US              
Ign http://packages.linuxmint.com/ julia/main Translation-en                   
Get:4 http://packages.medibuntu.org maverick Release.gpg [197B]                
Ign http://packages.linuxmint.com/ julia/main Translation-en_US                
Ign http://packages.linuxmint.com/ julia/upstream Translation-en               
Ign http://packages.linuxmint.com/ julia/upstream Translation-en_US            
Get:5 http://packages.linuxmint.com julia Release [7,231B]                     
Hit http://archive.canonical.com maverick/partner i386 Packages                
Get:6 http://archive.ubuntu.com maverick Release.gpg [198B]                    
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en             
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US          
Hit http://security.ubuntu.com maverick-security/main i386 Packages            
Ign http://packages.medibuntu.org/ maverick/free Translation-en      
Ign http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en       
Ign http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US    
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en       
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US    
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en         
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US      
Get:7 http://archive.ubuntu.com maverick-updates Release.gpg [198B]            
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en     
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US  
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://packages.linuxmint.com julia/main i386 Packages                     
Hit http://security.ubuntu.com maverick-security/restricted i386 Packages      
Hit http://security.ubuntu.com maverick-security/universe i386 Packages        
Hit http://security.ubuntu.com maverick-security/multiverse i386 Packages      
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://archive.ubuntu.com maverick Release                       
Ign http://packages.medibuntu.org/ maverick/free Translation-en_US             
Hit http://archive.ubuntu.com maverick-updates Release                         
Ign http://packages.linuxmint.com julia/upstream i386 Packages                 
Hit http://archive.ubuntu.com maverick/main i386 Packages                      
Ign http://packages.linuxmint.com julia/import i386 Packages         
Hit http://archive.ubuntu.com maverick/restricted i386 Packages      
Hit http://archive.ubuntu.com maverick/universe i386 Packages        
Hit http://archive.ubuntu.com maverick/multiverse i386 Packages      
Ign http://packages.medibuntu.org/ maverick/non-free Translation-en  
Ign http://packages.linuxmint.com julia/main i386 Packages                     
Hit http://archive.ubuntu.com maverick-updates/main i386 Packages              
Hit http://archive.ubuntu.com maverick-updates/restricted i386 Packages        
Hit http://archive.ubuntu.com maverick-updates/universe i386 Packages          
Hit http://archive.ubuntu.com maverick-updates/multiverse i386 Packages        
Ign http://packages.linuxmint.com julia/upstream i386 Packages                 
Ign http://packages.medibuntu.org/ maverick/non-free Translation-en_US         
Ign http://packages.linuxmint.com julia/import i386 Packages                   
Hit http://packages.linuxmint.com julia/main i386 Packages                     
Hit http://packages.medibuntu.org maverick Release                             
Hit http://packages.linuxmint.com julia/upstream i386 Packages                 
Hit http://packages.medibuntu.org maverick/free i386 Packages                  
Hit http://packages.linuxmint.com julia/import i386 Packages                   
Hit http://packages.medibuntu.org maverick/non-free i386 Packages
Fetched 8,418B in 1s (5,373B/s)                           
Reading package lists... Done
**mint / #** apt-get purge grub grub-pc grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub-common is not installed, so not removed
Package grub-pc is not installed, so not removed
Package grub is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
**mint / #** apt-get install grub-common grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  multiboot-doc grub-emu xorriso desktop-base
The following NEW packages will be installed:
  grub-common grub-pc
0 upgraded, 2 newly installed, 0 to remove and 9 not upgraded.
Need to get 2,326kB of archives.
After this operation, 6,300kB of additional disk space will be used.
Get:1 http://packages.linuxmint.com/ julia/upstream grub-common i386 1.98+20100804-5ubuntu3-1mint1 [1,540kB]
Get:2 http://packages.linuxmint.com/ julia/upstream grub-pc i386 1.98+20100804-5ubuntu3-1mint1 [786kB]
Fetched 2,326kB in 5s (401kB/s)        
Preconfiguring packages ...
Selecting previously deselected package grub-common.
(Reading database ... 138098 files and directories currently installed.)
Unpacking grub-common (from .../grub-common_1.98+20100804-5ubuntu3-1mint1_i386.deb) ...
Selecting previously deselected package grub-pc.
Unpacking grub-pc (from .../grub-pc_1.98+20100804-5ubuntu3-1mint1_i386.deb) ...
Processing triggers for install-info ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Setting up grub-common (1.98+20100804-5ubuntu3-1mint1) ...
Setting up grub-pc (1.98+20100804-5ubuntu3-1mint1) ...

Creating config file /etc/default/grub with new version
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
Installation finished. No error reported.
Generating grub.cfg ...
Found Debian background: linuxmint.png
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /media/2608ADDC08ADAAEF: No such file or directory
ls: cannot access /media/2608ADDC08ADAAEF: No such file or directory
ls: cannot access /media/2608ADDC08ADAAEF: No such file or directory
ls: cannot access /media/2608ADDC08ADAAEF: No such file or directory
done
```at the end i also ran
```
sudo update-grub
```the nightmare is that i tried this to see if i can do it again.... no! it simply doesn't work! :confused:

---

### Post by drs305 on 2010-12-26
*handimo*,

These messages:
> 
Creating config file /etc/default/grub with new version
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
Installation finished. No error reported.

would indicate you selected the partition rather than the drive. When you get to the grub installation page which has you designate where you want G2 installed, you should select *only* the drive (sda) and not the partition (sda5). Although G2 can be installed on a partition, it won't do so automatically and generally it should be done that way only if the user has a good reason to do so. If you only had sda5 selected, it did not install. If you had both sda and sda5 selected, apparently it didn't install to sda as well (or it should have booted).

On the installation page, only the top entry (sda) should have an * next to it before you tab to OK and press ENTER.

Also in the last line you mention "sudo update-grub". Remember you should still be in the 'chroot' environment and "sudo" should not be used. Running the update outside the 'chroot' unless you booted normally will not update your real system files.

---

### Post by hamdimo on 2010-12-26
> **drs305 said:**
> *handimo*,

These messages:

would indicate you selected the partition rather than the drive. When you get to the grub installation page which has you designate where you want G2 installed, you should select *only* the drive (sda) and not the partition (sda5). Although G2 can be installed on a partition, it won't do so automatically and generally it should be done that way only if the user has a good reason to do so. If you only had sda5 selected, it did not install. If you had both sda and sda5 selected, apparently it didn't install to sda as well (or it should have booted).

On the installation page, only the top entry (sda) should have an * next to it before you tab to OK and press ENTER.

Also in the last line you mention "sudo update-grub". Remember you should still be in the 'chroot' environment and "sudo" should not be used. Running the update outside the 'chroot' unless you booted normally will not update your real system files.
WOW :) this is really interesting, i would never realize this, i thought i wanna boot the dead Mint in sda5 so i installed it there, ok i'll do it again, and this time just as you said !

---

### Post by hamdimo on 2010-12-26
yup!! i've booted Mint successfully, after all these days trying. but i  don't dare trying to fix Vista, first cuz all my trying failed, second  cuz it always screws Mint boot files,
i'm thinking about formating and installing Vista ll over again, i wish i have another solution :sad: but i won't do this no till i'm totally hopeless : ) 
and i know i'm not in a windows forum here

---

