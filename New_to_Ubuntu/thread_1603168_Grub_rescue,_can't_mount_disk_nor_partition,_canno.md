---
title: "Grub rescue, can't mount disk nor partition, cannot change grub directory, missing .."
date: 2010-10-22
forum: New to Ubuntu
---

### Post by CesarOscar on 2010-10-22
This is what is happening. I have ubuntu 10.10, linux mint 9 and ubuntu 10.04 installed in that same order. Grub selection menu was managed by ubuntu 10.04, but i didn't know until i deleted that partition to make more space on my hard drive. Every time that i get directed to grub rescue mode. I tried changing the grub direction to ubuntu 10.10 on sda1 but it says "grub_xputs" is missing. Then i tried using the live cd to mount sda1 or sda6 (linux mint) but they couldn't be mount. 

```
ubuntu@ubuntu:~$ sudo mount /dev/sda1
mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab
ubuntu@ubuntu:~$ sudo mount /dev/sda6
mount: can't find /dev/sda6 in /etc/fstab or /etc/mtab
```Even though the system recognize it:

```
ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (9)

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c2b95

  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1305    10476532   83  Linux
/dev/sda2            1305       14594   106742785    5  Extended
/dev/sda5           14223       14594     2977792   82  Linux swap / Solaris
/dev/sda6            7386       13938    52625408   83  Linux
/dev/sda7           13938       14223     2284544   82  Linux swap / Solaris
/dev/sda8            7132        7386     2036736   82  Linux swap / Solaris
```Partition 9 had ubuntu 10.04

What could i do to solve this issue?

---

### Post by ironic.demise on 2010-10-22
If you installed the bootloader onto 10.04, did it EVER boot up?
Just wondering if you know this atleast worked at some point.
 
My advice would be to find which hdd 10.04 is on and then check the boot order of BIOS.

---

### Post by CesarOscar on 2010-10-22
Yes, it boot perfectly until i deleted it. 10.04 was on sda9, it became the deafult boot loader after i installed it, happened the same when i installed linux mint.

---

### Post by Rubi1200 on 2010-10-22
Try using the method outlined in this thread:
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

You need to mount the 10.10 partition on sda1 and then reinstall GRUB to the MBR of sda.

EDIT:
the error grub_xputs means that GRUB is missing some files it needs, just thought you might like to know for future reference. As I said above, the fix is to chroot into the system and reinstall.

---

### Post by psusi on 2010-10-22
You have to tell mount WHERE you want to mount that partition.  Try looking at the man page.

---

### Post by CesarOscar on 2010-10-22
I get an error, it says i do not have any signature

---

### Post by Rubi1200 on 2010-10-22
I don't understand what that means; sorry :(

Could you please explain what steps you went through before you got this error.

---

### Post by CesarOscar on 2010-10-22
```
sudo mount /dev/sd**a1** /mnt
sudo grub-install --root-directory=/mnt /dev/sda
/usr/sbin/grub-setup: error: no signature.
```

That's what happened

---

### Post by drs305 on 2010-10-22
> **CesarOscar said:**
> ```
sudo mount /dev/sd**a1** /mnt
sudo grub-install --root-directory=/mnt /dev/sda
/usr/sbin/grub-setup: error: no signature.
```

That's what happened

Are you doing this from the LiveCD?
Do you happen to have a separate /boot directory?



If you still have problems:

Please run forum member *meierfra's* boot info script from the LiveCd and post the results here between "code" texts (using the # icon in the menubar).
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by Rubi1200 on 2010-10-23
It appears you did not use the chroot method I suggested previously (and I apologize if that was not clear enough).

However, under the circumstances, it might be prudent to follow the advice given by drs305 and post the results of the boot-script.

---

### Post by CesarOscar on 2010-10-25
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 9 Isadora
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    20,955,111    20,953,064  83 Linux
/dev/sda2          20,955,134   234,440,703   213,485,570   5 Extended
/dev/sda5         228,485,120   234,440,703     5,955,584  82 Linux swap / Solaris
/dev/sda6         118,654,976   223,905,791   105,250,816  83 Linux
/dev/sda7         223,907,840   228,476,927     4,569,088  82 Linux swap / Solaris
/dev/sda8         114,567,168   118,640,639     4,073,472  82 Linux swap / Solaris
Invalid MBR Signature found
Empty Partition


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        388c1c54-d5df-47ec-88b3-0bddcb88d4fc   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        d3ff3515-ebaf-4e58-a6f1-9f100c81d856   swap                                     
/dev/sda6        7837a042-61c2-47fc-9b50-63e2a5286b44   ext4                                     
/dev/sda7        911293a7-17e9-46f3-9c99-1978ff575a2e   swap                                     
/dev/sda8        09b31815-3a1a-4f59-b9d8-ee90e7126f48   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda6        /mnt                     ext4       (rw)


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
UUID=388c1c54-d5df-47ec-88b3-0bddcb88d4fc /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=d3ff3515-ebaf-4e58-a6f1-9f100c81d856 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


   5.8GB: boot/initrd.img-2.6.35-22-generic
   5.7GB: boot/vmlinuz-2.6.35-22-generic
   5.8GB: initrd.img
   5.7GB: vmlinuz

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
search --no-floppy --fs-uuid --set 7837a042-61c2-47fc-9b50-63e2a5286b44
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1024x768
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
search --no-floppy --fs-uuid --set 7837a042-61c2-47fc-9b50-63e2a5286b44
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

### BEGIN /etc/grub.d/06_mint_theme ###
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 7837a042-61c2-47fc-9b50-63e2a5286b44
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
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda6)" --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 7837a042-61c2-47fc-9b50-63e2a5286b44
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=7837a042-61c2-47fc-9b50-63e2a5286b44 ro  splash quiet  quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda6) -- recovery mode" --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 7837a042-61c2-47fc-9b50-63e2a5286b44
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=7837a042-61c2-47fc-9b50-63e2a5286b44 ro single  splash quiet
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 7837a042-61c2-47fc-9b50-63e2a5286b44
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 7837a042-61c2-47fc-9b50-63e2a5286b44
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 388c1c54-d5df-47ec-88b3-0bddcb88d4fc
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=388c1c54-d5df-47ec-88b3-0bddcb88d4fc ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 388c1c54-d5df-47ec-88b3-0bddcb88d4fc
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=388c1c54-d5df-47ec-88b3-0bddcb88d4fc ro single
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sda8)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 84522214-1b91-4ec1-8516-91df8d1b944f
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=84522214-1b91-4ec1-8516-91df8d1b944f ro quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/sda8)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 84522214-1b91-4ec1-8516-91df8d1b944f
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=84522214-1b91-4ec1-8516-91df8d1b944f ro single
    initrd /boot/initrd.img-2.6.32-24-generic
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
UUID=7837a042-61c2-47fc-9b50-63e2a5286b44 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=911293a7-17e9-46f3-9c99-1978ff575a2e none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


  69.4GB: boot/grub/core.img
  71.9GB: boot/grub/grub.cfg
  70.5GB: boot/initrd.img-2.6.32-21-generic
  70.3GB: boot/vmlinuz-2.6.32-21-generic
  70.5GB: initrd.img
  70.3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  a3 48 d7 00 17 c1 15 fe  a0 29 ba 2b e7 29 2d 3c  |.H.......).+.)-<|
00000010  ca d8 23 02 17 9c 85 eb  fd 84 83 30 32 92 a2 5c  |..#........02..\|
00000020  a8 4a fd 7d 83 9b 6f 50  db 60 e5 80 c6 d5 c1 bd  |.J.}..oP.`......|
00000030  a3 a9 c2 65 02 62 d3 20  00 f6 24 20 b0 ae 19 65  |...e.b. ..$ ...e|
00000040  59 0e 65 b8 91 32 e6 e6  21 23 7c c9 49 22 0a 90  |Y.e..2..!#|.I"..|
00000050  1d 13 46 32 f3 16 ab 37  2a c9 c4 28 ca ac 11 19  |..F2...7*..(....|
00000060  55 aa f2 a8 41 d5 5a b5  5e 5d 76 b6 98 0f 2f ca  |U...A.Z.^]v.../.|
00000070  5c 0e 00 d0 c8 28 bf e4  9c 74 ac 2d f9 4f fb bb  |\....(...t.-.O..|
00000080  61 ab 7f 3b 5a a6 e5 45  02 0b db 46 09 5d 47 30  |a..;Z..E...F.]G0|
00000090  3c c0 e4 c8 b4 e1 92 0a  5c a9 ff 1e 56 2a 95 08  |<.......\...V*..|
000000a0  3a 80 5b d2 75 05 5d 10  20 39 66 8b 44 45 16 8f  |:.[.u.]. 9f.DE..|
000000b0  1f a5 01 c8 19 81 c2 09  10 cb fa 10 f7 5c 50 13  |.............\P.|
000000c0  fe 30 90 20 04 f8 97 42  68 29 f9 75 2a c4 29 81  |.0. ...Bh).u*.).|
000000d0  22 b0 80 94 41 45 59 47  90 52 15 7c 44 02 97 6a  |"...AEYG.R.|D..j|
000000e0  89 81 c5 45 42 16 4a 9c  cb 24 92 04 fb c3 21 d4  |...EB.J..$....!.|
000000f0  8a ea 41 63 12 82 33 1a  91 b8 48 f3 69 c3 5a 09  |..Ac..3...H.i.Z.|
00000100  21 9d d4 2f 44 b9 8c 02  25 c2 ec ca 00 57 56 54  |!../D...%....WVT|
00000110  28 e3 02 24 6e bf dc 9a  90 52 05 12 34 55 90 e2  |(..$n....R..4U..|
00000120  e0 5a 7f f1 d0 34 29 19  28 ba 10 e1 fd 3f 54 00  |.Z...4).(....?T.|
00000130  aa 94 09 11 1c c0 e4 28  fc 20 8f 32 e5 9f ca 06  |.......(. .2....|
00000140  0d 40 a0 22 2e e7 14 0a  c6 b9 cc 83 2c 23 c6 ad  |.@."........,#..|
00000150  36 5a 15 05 d2 a8 86 03  b7 42 bf ab f9 f5 62 c1  |6Z.......B....b.|
00000160  ed cb a8 14 af 4e 76 c2  c4 e3 48 1b b9 01 6a 70  |.....Nv...H...jp|
00000170  cc c8 dc c3 b6 9c f3 d1  74 41 78 94 91 0c 5c 98  |........tAx...\.|
00000180  0e 99 f9 06 be d2 69 7c  c6 a8 60 71 70 62 f8 48  |......i|..`qpb.H|
00000190  11 80 09 20 68 74 ac 50  2d 3e 85 7c 30 e0 0c c5  |... ht.P->.|0...|
000001a0  5c 5c 06 08 c9 8a 49 04  a4 a1 4a ae 08 a8 07 18  |\\....I...J.....|
000001b0  9a 72 54 6d ea 4a 4a 4b  d9 95 40 04 12 cb 00 fe  |.rTm.JJK..@.....|
000001c0  ff ff 82 fe ff ff 02 a8  5e 0c 00 e0 5a 00 00 fe  |........^...Z...|
000001d0  ff ff 05 fe ff ff 02 90  d2 05 00 38 46 06 00 00  |...........8F...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by psusi on 2010-10-25
> **CesarOscar said:**
> 
 => Lilo is installed in the MBR of /dev/sda


You have replaced grub with lilo.  Don't do that.  Reinstall grub.

---

### Post by drs305 on 2010-10-25
Grub is not installed in the MBR. Since executing commands is resulting in 'no signature' error messages, I would recommend you completely purge/reinstall Grub using the *chroot* procedure *Rubi1200* recommended.

Here is the link:
[HOWTO: Purge and Reinstall Grub 2 from the Live CD]("http://ubuntuforums.org/showthread.php?t=1581099")

Mount your sda6 partition if you want to Mint to be the default or sda1 if you want Ubuntu. When you run the purge command just disregard any 'not found' messages.

---

### Post by CesarOscar on 2010-10-25
```
 ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
/usr/sbin/grub-setup: error: no signature.
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
/usr/sbin/grub-setup: error: no signature.
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
/usr/sbin/grub-setup: error: no signature. 
```I skipped it and moved on


```
ubuntu@ubuntu:~$ sudo mkdir /mnt/temp
mkdir: cannot create directory `/mnt/temp': File exists
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/temp
ubuntu@ubuntu:~$ i in /dev /dev/pts /proc /sys; sudo mount -B $i /mnt/temp$i
105 0x69 0151 0b1101001 'i'
110 0x6E 0156 0b1101110 'n'
47 0x2F 057 0b101111 '/'
100 0x64 0144 0b1100100 'd'
101 0x65 0145 0b1100101 'e'
118 0x76 0166 0b1110110 'v'
47 0x2F 057 0b101111 '/'
100 0x64 0144 0b1100100 'd'
101 0x65 0145 0b1100101 'e'
118 0x76 0166 0b1110110 'v'
47 0x2F 057 0b101111 '/'
112 0x70 0160 0b1110000 'p'
116 0x74 0164 0b1110100 't'
115 0x73 0163 0b1110011 's'
47 0x2F 057 0b101111 '/'
112 0x70 0160 0b1110000 'p'
114 0x72 0162 0b1110010 'r'
111 0x6F 0157 0b1101111 'o'
99 0x63 0143 0b1100011 'c'
47 0x2F 057 0b101111 '/'
115 0x73 0163 0b1110011 's'
121 0x79 0171 0b1111001 'y'
115 0x73 0163 0b1110011 's'
mount: Not a directory 
```Move on, again

```
root@ubuntu:/# apt-get purge grub grub-pc grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub is not installed, so not removed
The following packages will be REMOVED:
  grub-common* grub-pc*
0 upgraded, 0 newly installed, 2 to remove and 47 not upgraded.
After this operation, 5,804kB disk space will be freed.
Do you want to continue [Y/n]? y
Can not write log, openpty() failed (/dev/pts not mounted?)
(Reading database ... 158729 files and directories currently installed.)
Removing grub-pc ...
Purging configuration files for grub-pc ...
Removing grub-common ...
Purging configuration files for grub-common ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Processing triggers for install-info ...
root@ubuntu:/# apt-get install grub-common grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  multiboot-doc grub-emu xorriso desktop-base
The following NEW packages will be installed:
  grub-common grub-pc
0 upgraded, 2 newly installed, 0 to remove and 47 not upgraded.
Need to get 0B/2,204kB of archives.
After this operation, 5,804kB of additional disk space will be used.
Preconfiguring packages ...
Can not write log, openpty() failed (/dev/pts not mounted?)
Selecting previously deselected package grub-common.
(Reading database ... 158450 files and directories currently installed.)
Unpacking grub-common (from .../grub-common_1.98+20100804-5ubuntu3_i386.deb) ...
Selecting previously deselected package grub-pc.
Unpacking grub-pc (from .../grub-pc_1.98+20100804-5ubuntu3_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Processing triggers for ureadahead ...
Can not write log, openpty() failed (/dev/pts not mounted?)
Setting up grub-common (1.98+20100804-5ubuntu3) ...
Setting up grub-pc (1.98+20100804-5ubuntu3) ...

Creating config file /etc/default/grub with new version
grub-probe: error: cannot find a device for / (is /dev mounted?).
grub-probe: error: cannot find a device for /boot (is /dev mounted?).
grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?). 
```

In the attached images are what appeared during installation process

Don't know what to do :(

---

### Post by Rubi1200 on 2010-10-25
This line:
> i in /dev /dev/pts /proc /sys; sudo mount -B $i /mnt/temp$i
is not the same as this:
> for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
You may want to try it again.

Then,
> sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf

followed by > sudo chroot /mnt/temp
Then follow the rest of the guide to purge and reinstall GRUB.

---

### Post by CesarOscar on 2010-11-13
Thanks, i try it again and worked :)

---

### Post by Rubi1200 on 2010-11-14
Excellent! I am really pleased everything worked out for you :)

Enjoy!

---

