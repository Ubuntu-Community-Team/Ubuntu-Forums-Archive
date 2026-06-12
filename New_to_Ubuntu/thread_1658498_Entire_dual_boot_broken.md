---
title: "Entire dual boot broken"
date: 2011-01-02
forum: New to Ubuntu
---

### Post by damien750 on 2011-01-02
I had xp and ubuntu installed to dual boot. Ubuntu worked fine but xp got "ctrl+alt+del" error on boot.  To fix it, I tried windows recovery console and ran "fixboot" and "fixmbr". Now no grub menu appears on boot, and windows still has "disc read error ctrl+alt+del to reboot" error. What can I do to get either of the os's working again?

I write this desperate plea for help from my iphone. 
Thanks for your helpin advance.

---

### Post by TeoBigusGeekus on 2011-01-02
You need to [reinstall grub2]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows").

---

### Post by damien750 on 2011-01-02
Thanks for the reply, TeoBigusGeekus.

Thought I was making progress, but I'm hitting snags...

```
ubuntu@ubuntu:~$ mount | tail -1
/dev/sda5 on /media/25b06a21-7a19-4482-97b7-08af3943c593 type ext4 (rw,nosuid,nodev,uhelper=udisks)
ubuntu@ubuntu:~$ ls /media/25b06a21-7a19-4482-97b7-08af3943c593
bin    dev   initrd.img      lost+found  opt   sbin     sys  var
boot   etc   initrd.img.old  media       proc  selinux  tmp  vmlinuz
cdrom  home  lib             mnt         root  srv      usr  vmlinuz.old
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/25b06a21-7a19-4482-97b7-08af3943c593 /dev/sda5
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.
ubuntu@ubuntu:~$ 

```

What am I doing wrong? I know I mounted the right partition.

---

### Post by TeoBigusGeekus on 2011-01-02
Instead of installing it on /dev/sda5, install it on /dev/sda.

---

### Post by damien750 on 2011-01-02
...Don't I feel dumb. ](*,)

```
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/25b06a21-7a19-4482-97b7-08af3943c593 /dev/sda
/usr/sbin/grub-setup: warn: Sector 32 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track..
Installation finished. No error reported.

```

---

### Post by damien750 on 2011-01-02
Grub menu is back up, allowing me to access ubuntu 10.10 again. However, windows boot still has "Disc Read Error, press Ctrl+Alt+Del to reboot" message.

Is the Windows boot beyond repair? :-(

---

### Post by TeoBigusGeekus on 2011-01-02
A quick googling of your error message gave [this]("http://forums.cnet.com/7723-6142_102-227333.html").

---

### Post by wilee-nilee on 2011-01-02
Do this, so from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags paste all the text in between.

---

### Post by damien750 on 2011-01-02
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   294,649,578   294,649,516   7 HPFS/NTFS
/dev/sda2         372,148,560   390,715,919    18,567,360   c W95 FAT32 (LBA)
/dev/sda3         294,649,854   372,148,223    77,498,370   5 Extended
/dev/sda5         294,649,856   368,873,471    74,223,616  83 Linux
/dev/sda6         368,875,520   372,148,223     3,272,704  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        EC28D52A28D4F514                       ntfs       HP_PAVILION                   
/dev/sda2        4B6E-6BC0                              vfat       HP_RECOVERY                   
/dev/sda3: PTTYPE="dos" 
/dev/sda5        25b06a21-7a19-4482-97b7-08af3943c593   ext4                                     
/dev/sda6        5a3786e9-1e9c-4a7f-9318-5e7d51ea561e   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=3 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 

================================ sda2/boot.ini: ================================

[boot loader] 
timeout=0 
default=C:\CMDCONS\BOOTSECT.DAT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 

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
search --no-floppy --fs-uuid --set 25b06a21-7a19-4482-97b7-08af3943c593
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 25b06a21-7a19-4482-97b7-08af3943c593
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
    search --no-floppy --fs-uuid --set 25b06a21-7a19-4482-97b7-08af3943c593
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=25b06a21-7a19-4482-97b7-08af3943c593 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 25b06a21-7a19-4482-97b7-08af3943c593
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=25b06a21-7a19-4482-97b7-08af3943c593 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 25b06a21-7a19-4482-97b7-08af3943c593
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=25b06a21-7a19-4482-97b7-08af3943c593 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 25b06a21-7a19-4482-97b7-08af3943c593
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=25b06a21-7a19-4482-97b7-08af3943c593 ro single 
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
    search --no-floppy --fs-uuid --set 25b06a21-7a19-4482-97b7-08af3943c593
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 25b06a21-7a19-4482-97b7-08af3943c593
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows XP Media Center Edition (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set ec28d52a28d4f514
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sda2)" {
    insmod part_msdos
    insmod fat
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 4b6e-6bc0
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
UUID=25b06a21-7a19-4482-97b7-08af3943c593 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=5a3786e9-1e9c-4a7f-9318-5e7d51ea561e none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 153.2GB: boot/grub/core.img
 151.0GB: boot/grub/grub.cfg
 151.8GB: boot/initrd.img-2.6.35-22-generic
 151.9GB: boot/initrd.img-2.6.35-24-generic
 153.2GB: boot/vmlinuz-2.6.35-22-generic
 153.2GB: boot/vmlinuz-2.6.35-24-generic
 151.9GB: initrd.img
 151.8GB: initrd.img.old
 153.2GB: vmlinuz
 153.2GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  41 01 10 01 f0 4b 6b 11  01 d1 0e cf 14 01 de 12  |A....Kk.........|
00000010  01 b1 0e bd 05 14 01 cc  10 01 6a 03 e9 3b 03 61  |..........j..;.a|
00000020  b4 14 ec 0f 8d 78 40 12  b1 05 9a 01 20 02 83 f0  |.....x@..... ...|
00000030  fb a8 fc 0f 85 de 65 20  01 f4 0f 40 01 b3 14 51  |......e ...@...Q|
00000040  32 01 d1 05 5a 71 36 01  3d 32 01 f1 05 5d 36 01  |2...Zq6.=2...]6.|
00000050  29 d5 32 01 ec f0 15 49  36 01 15 30 01 21 06 82  |).2....I6..0.!..|
00000060  37 10 01 3c f8 0f 85 9d  f6 15 62 25 11 01 80 0f  |7..<......b%....|
00000070  85 13 17 d1 05 13 77 12  01 11 17 71 05 05 d0 00  |......w....q....|
00000080  16 17 41 05 f4 62 41 10  67 c3 a8 c0 11 17 01 02  |..A..bA.g.......|
00000090  e4 d1 f0 00 ff 75 ec 18  17 d2 10 01 1d 17 92 d0  |.....u..........|
000000a0  11 17 ed 17 14 17 0c 53  11 17 b2 d0 11 17 c6 cd  |.......S........|
000000b0  19 17 c0 30 e4 11 17 aa  5c 12 17 5b 21 0b 84 d0  |...0....\..[!...|
000000c0  04 8b 13 17 b6 90 c0 6e  53 11 6f 41 01 10 17 7e  |.......nS.oA...~|
000000d0  12 01 b5 51 0b 5d 14 01  6c 12 01 81 09 4b 14 01  |...Q.]..l....K..|
000000e0  56 5a 12 01 a1 0b 39 14  01 48 10 01 6a 18 04 e9  |VZ....9..H..j...|
000000f0  b7 40 11 f2 2c e8 0f 8d  50 f0 40 ed ff d1 06 16  |.@..,...P.@.....|
00000100  20 02 83 80 f0 fd a8 fe  0f 85 dd 20 01 6d d3 06  | .......... .m..|
00000110  01 40 01 33 18 c9 32 01  f1 06 ed 5b 90 00 33 01  |.@.3..2....[..3.|
00000120  b5 32 01 11 07 d9 36 01  a1 ab 32 01 31 07 c5 36  |.2....6...2.1..6|
00000130  01 8d 32 01 e8 70 19 5a  b1 36 01 79 90 00 61 07  |..2..p.Z.6.y..a.|
00000140  9f 70 00 3c ed 70 1f af  76 19 d1 02 3c 70 19 93  |.p.<.p..v...<p..|
00000150  1a 11 07 ee 7b 31 02 96  1a f1 06 69 12 01 91 1a  |....{1.....i....|
00000160  91 06 ee 5b d0 00 96 1a  61 06 4a 00 01 21 0a 91  |...[....a.J..!..|
00000170  1a dd 01 02 3a f0 00 60  6c 98 1a 28 10 01 9d 1a  |....:..`l..(....|
00000180  92 cc 91 1a 43 16 94 1a  62 51 91 1a 52 cc 91 1a  |....C...bQ..R...|
00000190  1c cc 99 1a 7b b4 31 6e  65 92 1a 6d 41 0c da 3f  |....{.1ne..mA..?|
000001a0  b0 02 93 1a e6 db d0 96  b3 13 c5 41 01 90 1a d4  |...........A....|
000001b0  12 01 71 0c 5a b3 14 01  c2 12 01 71 0c a1 00 fe  |..q.Z......q....|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 90 6c 04 00 fe  |............l...|
000001d0  ff ff 05 fe ff ff 02 90  6c 04 00 f8 31 00 00 00  |........l...1...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

---

### Post by wilee-nilee on 2011-01-02
Are  you seeing two XP lines on the grub menu the recovery sda2 shows in the list as well as sda1 the main OS=C?

---

### Post by damien750 on 2011-01-02
The grub menu lists a couple versions of Ubuntu 10.10 (regular and compatibility/recovery versions), memtests, and these two windows boots:

Windows XP Media Center Edition (on sda1)
and
Windows NT/2000/XP (on sda2)

at the bottom.

Choosing XP boots to the disc read error.
Choosing NT/2000/XP leads to an HP Pavilion Recovery software.

---

### Post by wilee-nilee on 2011-01-02
I miss read your first post you have not had xp since it went down.

The link that the other poster is all I saw basically with a quick look on Google myself.

If it was me and the recovery works I would pull out what you need from XP with a live cd onto a HD and run the recovery, then make sure what you pulled out is scanned with several av's to make sure that was not the cause.

---

### Post by damien750 on 2011-01-02
No, XP did not boot after fixboot and fixmbr. Instead, it only deleted the grub menu, causing the computer to automatically attempt to boot to windows, which still had the disc read error.

I did not run chkdsk /r.

I forgot the update to grub2. I just updated it and rebooted, the problem remains.

---

### Post by CoreyB. on 2011-01-02
If you can, copy all of your important data from XP onto your Ubuntu partition.

I had an XP error this summer, not sure if it is the same as yours, but I too was unable to boot into Windows.

I fixed it by installing ntfsprogs in Ubuntu then running

sudo ntfsfix /dev/drive_name

where drive_name is wherever you have XP installed like sda1 or something.

But most importantly, copy all of your important info on your XP partition to Ubuntu or an external hard drive or something.

---

### Post by damien750 on 2011-01-02
Alright, I think that's what I'll have to do: copy over the info and repair or reinstall it.

Thanks everyone for your help.

---

