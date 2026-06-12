---
title: "gave up waiting for root device ubuntu 10.10 one more..."
date: 2011-01-22
forum: New to Ubuntu
---

### Post by gadikas on 2011-01-22
Same trouble as this one...
[gave up waiting for root device ubuntu 10.10](http://ubuntuforums.org/showthread.php?t=1634203)

Have installed Ubuntu server 10.10 on a A-Data CF card and added a 2tb disk for storage. 
And this is the result from boot_info_script055.sh
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/grub.
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/menu.lst

MediaHubb-root: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

MediaHubb-swap_1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048 3,907,028,991 3,907,026,944  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8019 MB, 8019099648 bytes
255 heads, 63 sectors/track, 974 cylinders, total 15662304 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048       499,711       497,664  83 Linux
/dev/sdb2             501,758    15,661,055    15,159,298   5 Extended
/dev/sdb5             501,760    15,661,055    15,159,296  8e Linux LVM


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 8000 MB, 8000110592 bytes
160 heads, 19 sectors/track, 5139 cylinders, total 15625216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             32    15,625,215    15,625,184   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/dm-0        8f89c2f6-fadc-40b1-a2ce-f49a7323dbcb   ext4                                     
/dev/dm-1        bf68e8d7-6268-4213-9237-be768146a07b   swap                                     
/dev/loop0                                              squashfs                                 
/dev/mapper/MediaHubb-root 8f89c2f6-fadc-40b1-a2ce-f49a7323dbcb   ext4                                     
/dev/mapper/MediaHubb-swap_1 bf68e8d7-6268-4213-9237-be768146a07b   swap                                     
/dev/sda1        78def89e-d85e-4af7-97fe-d4e896574290   ext2       Media                         
/dev/sda: PTTYPE="dos" 
/dev/sdb1        ea50b026-4b9a-457e-8b4e-4bc179ad9f24   ext2                                     
/dev/sdb2: PTTYPE="dos" PART_ENTRY_SCHEME="dos" PART_ENTRY_TYPE="0x5" PART_ENTRY_NUMBER="2" 
/dev/sdb5        CWd4t2-t101-5Xdi-FtNn-7L1d-PvxD-px6mGP LVM2_member                               
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        D82E-266C                              vfat       PENDRIVE                      
/dev/sdc: PTTYPE="dos" 

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
MediaHubb-root
MediaHubb-swap_1

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options



============================= sdb1/grub/grub.cfg: =============================

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

insmod lvm
insmod part_msdos
insmod ext2
set root='(MediaHubb-root)'
search --no-floppy --fs-uuid --set 8f89c2f6-fadc-40b1-a2ce-f49a7323dbcb
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set ea50b026-4b9a-457e-8b4e-4bc179ad9f24
set locale_dir=($root)/grub/locale
set lang=sv
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=2
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-server' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set ea50b026-4b9a-457e-8b4e-4bc179ad9f24
	linux	/vmlinuz-2.6.35-22-server root=/dev/mapper/MediaHubb-root ro   quiet
	initrd	/initrd.img-2.6.35-22-server
}
menuentry 'Ubuntu, with Linux 2.6.35-22-server (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set ea50b026-4b9a-457e-8b4e-4bc179ad9f24
	echo	'Loading Linux 2.6.35-22-server ...'
	linux	/vmlinuz-2.6.35-22-server root=/dev/mapper/MediaHubb-root ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-22-server
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set ea50b026-4b9a-457e-8b4e-4bc179ad9f24
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set ea50b026-4b9a-457e-8b4e-4bc179ad9f24
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: grub/core.img
    .0GB: grub/grub.cfg
    .0GB: initrd.img-2.6.35-22-server
    .0GB: vmlinuz-2.6.35-22-server

=========================== sdc1/boot/grub/menu.lst: ===========================

configfile /ubcd/menus/grub4dos/main.lst

=================== sdc1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/menu.lst

========================== MediaHubb-root/etc/fstab: ==========================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/MediaHubb-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=ea50b026-4b9a-457e-8b4e-4bc179ad9f24 /boot           ext2    defaults        0       2
/dev/mapper/MediaHubb-swap_1 none            swap    sw              0       0
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 3b  |...............;|
000001c0  1d 1f 8e da cc ce 02 00  00 00 00 50 e7 00 00 00  |...........P....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdc1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 20 16 00  |.X.SYSLINUX.. ..|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 20 00 00 00  |........?... ...|
00000020  e0 6b ee 00 e5 0e 00 00  00 00 00 00 02 00 00 00  |.k..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 6c 26 2e d8 4e  4f 20 4e 41 4d 45 20 20  |..)l&..NO NAME  |
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
00000100  7d 00 66 b8 00 01 d0 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......|
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


=============================== StdErr Messages: ===============================

mdadm: No arrays found in config file or automatically

```
Can any one help me?

---

### Post by fabricator4 on 2011-01-22
> **gadikas said:**
> Same trouble as this one...
[gave up waiting for root device ubuntu 10.10](http://ubuntuforums.org/showthread.php?t=1634203)

Have installed Ubuntu server 10.10 on a A-Data CF card and added a 2tb disk for storage. 
And this is the result from boot_info_script055.sh

Can any one help me?

It's not seeing the OS on sdb1 at all. When you configured the partition did you set it to mount as root?  Depending on how you did the install/config you should have got an error saying there was no root.

Chris

---

### Post by gadikas on 2011-01-23
> **fabricator4 said:**
> It's not seeing the OS on sdb1 at all. When  you configured the partition did you set it to mount as root?  Depending  on how you did the install/config you should have got an error saying  there was no root.

Chris
Thanks for the help.
No i did not get an error. First time reboot every thing worked then i apt-get update and upgrade. I installed webmin and enabled ipv4 forwarding. Then rebooted and got that problem. 
Going to try to swap the sda cables from the two hard drives when i get home from work. If that dos not work i am going to wipe and reinstall the system :popcorn:

---

### Post by fabricator4 on 2011-01-23
> **gadikas said:**
> Thanks for the help.
No i did not get an error. First time reboot every thing worked then i apt-get update and upgrade. I installed webmin and enabled ipv4 forwarding. Then rebooted and got that problem. 
Going to try to swap the sda cables from the two hard drives when i get home from work. If that dos not work i am going to wipe and reinstall the system :popcorn:

I just managed to replicate this problem with 10.10.  Another installation I did on a USB drive worked fine, but I used Gparted to do the setup o the partitions.  I've got interested enough that I want to find out what's going on, but there's other variables as well.  The install that worked was a USB pen drive on sdb1, the one that failed was an internal card reader in the EeePC which was sdc1, plus I made a second partition for /home.

I might try following the same instructions I used for the first install and see if I can get it to work on sdc1

Chris.

---

### Post by fabricator4 on 2011-01-23
OK, cracked it, I think.  Do you get the grub boot loader menu when you start?  When the menu comes up, instead of pressing enter to boot the OS on the CF card, press 'e' to edit the boot commands instead. When it comes up with the seven lines you'll see the second one from the bottom will something like:

```
linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sdc1 ro quiet spla/sh
```

It seems that the boot device gets hard coded at the time of installation, in my example the card reader was read as sdc at the time I booted off the live USB because the live USB was itself sdb1.  Now, with the live USB removed the internal card reader is actually mounting as sdb, but the grub boot loader is still trying to boot the kernal off a non-existent sdc1.

If I change the sdc1 to sdb1, I find the system boots as expected.  The reason my last installation booted OK was I think because it was on a USB that must have been recognised as sdb1 purely by good luck.

Note that this method will get the system to boot off the card, but it doesn't remember it for next time.  With grub V1 to make a permanent change you just edited this line in /boot/grub/menu.lst but grub 2 works differently.  Very differently.

I found the way to get this to work is to run the grub updater after booting of the card, and found that it reconfigures itself correctly:

```
sudo update-grub
```

I did this and found the machine will now boot correctly off the card in the card reader.  I suspect that the reason you had it boot OK before updates and not afterwards is that the kernal was updated, and the system incorrectly set the wrong boot device for the new kernal for some reason (maybe you had another device mounted at the time)

Hope this works as well for you as it did for me.

Chris.

---

### Post by gadikas on 2011-01-23
nop it did not work :(
By the way this is my exact start error message.. 
```
/init: Line 241 wait-for-root: not found
Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
- Check rootdelay= (did the system wait long enough?)
- Check root= (did the system wait for right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/mapper/MediaHubbb-root does not exist. Dropping to a shell!


BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty: Job control turned off.
(initramfs) _
```Then i tryed this. 
```

(initramfs) df -h
Filesystem        Size            Used          Available    Used%   Mounted on
None             485.7            148.0K        485.5       0%       /dev

(initramfs) ls /dev/mapper/
MediaHubb-root        MediaHubb-swapp1         control 


```Hmm funny. I can find and mount MediaHubb-root but not the  grub

---

### Post by gadikas on 2011-01-24
Did a complete reinstall of the server and now every thing works :)
I think  the problem was that I  happened to choose to install Ubuntu with  lvm...

Thanks for the help Chris.

---

