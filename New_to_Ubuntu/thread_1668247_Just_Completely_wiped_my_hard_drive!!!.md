---
title: "Just Completely wiped my hard drive!!!"
date: 2011-01-16
forum: New to Ubuntu
---

### Post by wiggy25 on 2011-01-16
First things first!!!!!!
 
Don't ever play about with Gparted when you're tired!!! 
 
Not slept well, so was up very early, thought what a good idea to try and recover a USB stick that hadn't been working.
Everything was going so well, then I came to create and remove some partitions that I had been playing about with on it, you know just to get an idea of how things worked.
Was going great, then went away came back and started playing a bit more.....
Problem is I forgot to DOUBLE CHECK I was actually working on the USB and not the PC hard drive!!!
 
So every partition has now been wiped from my hard drive, and this is running from a live CD. 
Can't even re-install Vista because that was on the hidden recovery partition!!
 
I don't want to turn the PC off.....time for a cup of tea and a weep.....everything gone, the wife will be impressed that all of her spreadsheets have departed.
I only made a back-up of my important documents.......I take it that there is no way to recover anything?
 
Not turned the PC off since doing any of this, also only running from Crunch Bang Live CD was trying it out, so it's the only disc in the drive.
 
Very sad looking at the GUI of GPARTED and seeing 250GB of Unallocated space where my O.S. once used to be!
 
Cheers
 
Ian

---

### Post by phredbull on 2011-01-16
Your data is still there. You can try a program called "testdisk" to recover your partitions. Even if it doesn't totally restore your disk, it should allow you to retrieve the data and save it on another disk.

---

### Post by lisati on 2011-01-16
Lesson #2: Make sure you have a set of recovery & repair disks ASAP after getting a new machine.
Lesson #3: BACKUP!

---

### Post by coffeecat on 2011-01-16
> **phredbull said:**
> Your data is still there. You can try a program called "testdisk" to recover your partitions.

+1 . Use testdisk. It will recover your partitions.

Step 1 - do not try to use anything apart from testdisk. Do not do anything that may write to the disc.

Step 2 - boot up with the live Ubuntu CD (if not already), make sure you are connected to the internet and install testdisk using Synaptic or Software Centre. Testdisk wiki here:

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Good luck!

---

### Post by wiggy25 on 2011-01-16
I'm actually running a live CD of crunch bang can I just shut down put in the Ubuntu live CD and go from there?

It is actually saying in Crunchbang that Testdisk is installed, I just don't know how to run it.

Any advice would great.

I'm not too bothered about Vista, mainly photos and docs, there actually isn't that much on the hard drive so not overly worried.

Would be nice though to get some photos back if I could work out how to use Test disk!

Cheers

Ian

---

### Post by davidmohammed on 2011-01-16
there are a few guides around - here is [one I found]("http://ubuntuforums.org/showthread.php?t=387922") - just read past the installation part and read how to restore your partitions.

---

### Post by coffeecat on 2011-01-16
> **wiggy25 said:**
> It is actually saying in Crunchbang that Testdisk is installed, I just don't know how to run it.

Any advice would great.

If Crunchbang has testdisk in the box, then run it from Crunchbang. You need to run it as root. In Ubuntu this would be 'sudo testdisk', but I don't know whether Crunchbang uses sudo or if you have to su to root. If you go to the link I provided and then down the page a bit, you come to a link to here:

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

It's not as bad as it looks.

---

### Post by Paul820 on 2011-01-16
> Lesson #2: Make sure you have a set of recovery & repair disks ASAP after getting a new machine.

That's my lesson #1

I hope you manage to retrieve your data wiggy25.

---

### Post by wiggy25 on 2011-01-16
Thanks everyone!

Got Testdisk to work and it found all of the partitions, so following the step by step tutorial used the write function to write the partition table back to the disc.
It then says reboot.
Problem now is when I try and reboot, Grub doesn't work, goes into grub recovery> then waits for me to do something.

If I run from Live CD and fire up GPARTED it still shows the whole HDD as unallocated so I'm assuming I need to reboot from HDD to get it all to work.

Does this mean I need to re-install GRUB?

At least I can see all my files with Testdisk, so I think I can copy them over to a spare USB at least I will have my documents back if nothing else.

As for getting a re-install CD the PC is about two years old, and thought I saw the disk in the pack that came with it!
WRONG.
reading through the paper work if I want a re-install disc I have to pay extra for it!!!!!
Funny I thought I had paid for a PC with O.S. so why should I pay extra for a disc...that should come with it???
Drives me mad when these places can sell PC's with no back-up discs, what happens if the HDD fails??
Shocking!

[IMG]http://i106.photobucket.com/albums/m280/wiggy25/Screenshot-3.png[/IMG]



Just thought I'd add this might make things a little easier.

Cheers

Ian

---

### Post by coffeecat on 2011-01-16
The things you describe are a few niggles. We **may** be able to get the system completely restored.

> **wiggy25 said:**
> Problem now is when I try and reboot, Grub doesn't work, goes into grub recovery> then waits for me to do something.

Boot up with the live CD, and go to:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot script and post the RESULTS.txt file in code tags. (You can use the # icon on the forum message toolbar.) That should give us all the information we need to decide how to proceed.

> **wiggy25 said:**
>  If I run from Live CD and fire up GPARTED it still shows the whole HDD as unallocated so I'm assuming I need to reboot from HDD to get it all to work.

Don't worry about that for now. It's a glitch in Gparted. Testdisk has probably marked the end of one of the partitions as being beyond the end of the physical drive and this confuses Gparted. If so, that's fairly easily fixed and we can come to that. The RESULTS.txt information shold tell us whether that is so.

> **wiggy25 said:**
> As for getting a re-install CD the PC is about two years old, and thought I saw the disk in the pack that came with it!
WRONG.
reading through the paper work if I want a re-install disc I have to pay extra for it!!!!!
Funny I thought I had paid for a PC with O.S. so why should I pay extra for a disc...that should come with it???
Drives me mad when these places can sell PC's with no back-up discs, what happens if the HDD fails??
Shocking!

What make is it? If it's any good, it should have a utility for making recovery DVDs from the HD. But I agree; nothing excuses the cheese-paring, penny-pinching failure of the manufacturers to provide a set of discs.

---

### Post by wiggy25 on 2011-01-16
Hi Thanks for the help so far!

Heres the output of boot info script, very strange that there is sda4 extended partition unknown:-

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/burg.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 10 Julia
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    10,487,807    10,485,760   7 HPFS/NTFS
/dev/sda2          10,487,808   344,887,272   334,399,465   7 HPFS/NTFS
/dev/sda3         344,887,296   365,432,831    20,545,536  83 Linux
/dev/sda4         365,432,886   488,408,129   122,975,244   f W95 Ext d (LBA)
/dev/sda5         365,434,880   482,457,599   117,022,720  83 Linux
/dev/sda6         482,459,648   488,396,783     5,937,136  82 Linux swap / Solaris

/dev/sda4 ends after the last sector of /dev/sda

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        32C49991C49957C5                       ntfs       WINRE                         
/dev/sda2        043E98713E985E0C                       ntfs       SYSTEM                        
/dev/sda3        65b3cc11-b78a-44b9-a8d8-572fab9352b3   ext4                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        b7ba1c5a-b1a6-451a-b6b1-cdbb584a2791   ext4                                     
/dev/sda6        54c1f5e1-3ff6-4d35-b8ac-a11e9dd51a4c   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda3/boot/grub/grub.cfg: ===========================

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
set default="custom Menu"
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
search --no-floppy --fs-uuid --set 65b3cc11-b78a-44b9-a8d8-572fab9352b3
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 65b3cc11-b78a-44b9-a8d8-572fab9352b3
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=300
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
search --no-floppy --fs-uuid --set 65b3cc11-b78a-44b9-a8d8-572fab9352b3
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
menuentry 'Linux Mint 10, 2.6.35-24-generic (/dev/sda5)' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 65b3cc11-b78a-44b9-a8d8-572fab9352b3
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=65b3cc11-b78a-44b9-a8d8-572fab9352b3 ro  vga=792  quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Linux Mint 10, 2.6.35-24-generic (/dev/sda5) -- recovery mode' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 65b3cc11-b78a-44b9-a8d8-572fab9352b3
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=65b3cc11-b78a-44b9-a8d8-572fab9352b3 ro single  vga=792
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Linux Mint 10, 2.6.35-22-generic (/dev/sda5)' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 65b3cc11-b78a-44b9-a8d8-572fab9352b3
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=65b3cc11-b78a-44b9-a8d8-572fab9352b3 ro  vga=792  quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Linux Mint 10, 2.6.35-22-generic (/dev/sda5) -- recovery mode' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 65b3cc11-b78a-44b9-a8d8-572fab9352b3
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=65b3cc11-b78a-44b9-a8d8-572fab9352b3 ro single  vga=792
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
    search --no-floppy --fs-uuid --set 65b3cc11-b78a-44b9-a8d8-572fab9352b3
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 65b3cc11-b78a-44b9-a8d8-572fab9352b3
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 043e98713e985e0c
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.


menuentry "Custom Menu"{set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 65b3cc11-b78a-44b9-a8d8-572fab9352b3configfile /boot/grub/custom_menu.cfg
        }
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=65b3cc11-b78a-44b9-a8d8-572fab9352b3 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=b7ba1c5a-b1a6-451a-b6b1-cdbb584a2791 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=54c1f5e1-3ff6-4d35-b8ac-a11e9dd51a4c none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


 179.7GB: boot/grub/core.img
 180.0GB: boot/grub/grub.cfg
 177.8GB: boot/initrd.img-2.6.35-22-generic
 177.8GB: boot/initrd.img-2.6.35-24-generic
 179.9GB: boot/vmlinuz-2.6.35-22-generic
 180.0GB: boot/vmlinuz-2.6.35-24-generic
 177.8GB: initrd.img
 177.8GB: initrd.img.old
 180.0GB: vmlinuz
 179.9GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  86 d3 5b fd 6b f1 59 ba  8e bd 5c b3 e5 92 a7 01  |..[.k.Y...\.....|
00000010  fe 18 a9 7f 2f ec 8f 14  bf 87 48 73 2c b4 e8 fa  |..../.....Hs,...|
00000020  b6 d6 f9 40 b8 b5 aa 4f  60 0c 20 a0 d2 50 7d a9  |...@...O`. ..P}.|
00000030  67 74 08 20 f7 41 82 e9  00 b6 80 dc 69 c4 3c ee  |gt. .A......i.<.|
00000040  62 62 ea 6a ea c1 6d 66  c9 c1 6e 41 55 99 4f c0  |bb.j..mf..nAU.O.|
00000050  f5 c0 5f 26 f7 ef a9 71  88 83 c5 53 3a 6f f5 93  |.._&...q...S:o..|
00000060  42 8a a0 2b 61 b3 e7 a5  c4 64 70 64 30 64 f6 55  |B..+a....dpd0d.U|
00000070  6e 22 56 e4 45 7b 09 ab  10 e7 3b 38 af eb 23 58  |n"V.E{....;8..#X|
00000080  09 6c 64 64 e4 1b 8f 6d  e6 c0 73 b7 ff 46 4a 79  |.ldd...m..s..FJy|
00000090  5c 9f 01 94 3a 37 65 13  65 5b 74 4c cb cb ca 22  |\...:7e.e[tL..."|
000000a0  ef 76 b4 14 ff 70 6f 50  d3 2c 04 18 ec 24 18 e2  |.v...poP.,...$..|
000000b0  2d 7c 92 eb 29 c0 31 77  7c 90 11 fb d4 db ec 3a  |-|..).1w|......:|
000000c0  65 72 1b 63 dc b3 12 dd  0c 39 19 aa b5 66 63 66  |er.c.....9...fcf|
000000d0  87 6a 7d 13 73 f3 6c d1  40 c8 ca f6 3e 6a 28 a5  |.j}.s.l.@...>j(.|
000000e0  ef d3 03 a6 4e bd 13 7c  83 6f fd dd a1 ee 1d 6f  |....N..|.o.....o|
000000f0  b1 35 01 34 92 5d 6c f4  83 91 c0 3e 3d 3d 9d ad  |.5.4.]l....>==..|
00000100  b7 ae b5 13 d6 ae e5 82  3c 1b be 18 d1 04 5f f1  |........<....._.|
00000110  c5 fa ef c4 57 23 a9 65  a8 f5 e7 d1 c7 d2 f2 66  |....W#.e.......f|
00000120  44 80 b7 5c 4f 64 01 ba  49 32 cc d6 3e 93 52 9f  |D..\Od..I2..>.R.|
00000130  09 c9 91 97 f1 99 56 76  77 33 89 cd 3e a7 87 ed  |......Vvw3..>...|
00000140  c8 b1 d1 32 33 83 f2 ed  82 8b b5 6e 31 96 9e 4e  |...23......n1..N|
00000150  a8 2e 7c 73 58 cc 46 3c  c8 a2 af 3c 3a 57 bc 65  |..|sX.F<...<:W.e|
00000160  fe 37 19 09 b3 29 cf a2  f5 52 d4 ef 33 a5 94 4e  |.7...)...R..3..N|
00000170  bd 9c 36 cb 4d 38 f0 b7  41 d4 db cd bf e3 02 5a  |..6.M8..A......Z|
00000180  15 52 a5 c5 bc 29 d7 e4  53 e8 90 eb cd 6e 20 b7  |.R...)..S....n .|
00000190  99 5e d7 76 bd 43 cd 21  34 64 e4 70 19 ef aa 85  |.^.v.C.!4d.p....|
000001a0  f9 4c 58 ff 7a 0a 7e eb  49 73 7f 9d 5c 6b d3 15  |.LX.z.~.Is..\k..|
000001b0  88 89 f0 fb 3f 79 12 a3  be f1 cd 1d 11 07 00 fe  |....?y..........|
000001c0  ff ff 83 fe ff ff ca 07  00 00 00 a0 f9 06 00 fe  |................|
000001d0  ff ff 05 fe ff ff 62 af  f9 06 58 98 5a 00 00 00  |......b...X.Z...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

Hope it provides some answers!

Cheers

Ian

---

### Post by gradinaruvasile on 2011-01-16
Can you see the contents of the partitions by mounting them with the live cd (just click on the drive icons from nautilus)?

---

### Post by wiggy25 on 2011-01-16
Hi, yes I can.

In fact it shows every single partition!
I can click on all of them and the files/folders are all shown, even the WINREC partition, I believe this was a hidden partition before I did all this to it!

This problem is what's know as a P.I.C.N.I.C.
Problem In Chair Not In Computer :-)

Cheers

Ian

---

### Post by davidmohammed on 2011-01-16
From your report it looks like grub2 needs to be reinstalled - first line of the report says it should reside on /dev/sda5

**_suggest after you have fully backed up everything that you need_**...

follow the instructions [here]("https://help.ubuntu.com/community/Grub2") (search for reinstalling grub 2) and install grub2 back onto /dev/sda5

---

### Post by coffeecat on 2011-01-16
> **wiggy25 said:**
> Hope it provides some answers!

Yes. Several. :)

First, you seem to have burg in the mbr, but your main Linux install is Mint Julia which uses grub. It's easy enough to re-install grub to the mbr, but there is a complication. The numbering of the logical partitions sda5 upwards has shifted around a bit. Your Mint root partition was originally sda5, but it's now sda3. This bit in your Mint grub.cfg **in theory** should cause a problem:

```
menuentry 'Linux Mint 10, 2.6.35-24-generic (/dev/sda5)' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
[COLOR=Red]    set root='(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set 65b3cc11-b78a-44b9-a8d8-572fab9352b3
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=65b3cc11-b78a-44b9-a8d8-572fab9352b3 ro  vga=792  quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
```... but since the UUID in the following lines is correct, we may get away with what I suggest next.

Boot up an Ubuntu or Mint live CD. Open a terminal and:

```
sudo mount /dev/sda3 /mnt
```Now:

```
sudo grub-install --root-directory=/mnt/ /dev/sda
```Now reboot. If you can boot into Mint, open a terminal again and, to tidy up grub.cfg, run:

```
sudo update-grub
```The next problem is Gparted not showing anything. This is why:

> **wiggy25 said:**
> ```

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total [COLOR=Red]488397168[/COLOR] sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    10,487,807    10,485,760   7 HPFS/NTFS
/dev/sda2          10,487,808   344,887,272   334,399,465   7 HPFS/NTFS
/dev/sda3         344,887,296   365,432,831    20,545,536  83 Linux
/dev/sda4         365,432,886   [COLOR=Red]488,408,129[/COLOR]   122,975,244   f W95 Ext d (LBA)
/dev/sda5         365,434,880   482,457,599   117,022,720  83 Linux
/dev/sda6         482,459,648   488,396,783     5,937,136  82 Linux swap / Solaris

[COLOR=Red]/dev/sda4 ends after the last sector of /dev/sda[/COLOR]
```

It's as I suspected. Here's the explanation and fix:

[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

That's a webpage written by forum member srs5694, by the way. If you need help with that, post back, but I suggest you backup all data before proceeding with that. Indeed, see if you can prepare a set of Windows restore DVDs as well. Editing the partition table runs the risk of something going wrong.

---

### Post by coffeecat on 2011-01-16
> **davidmohammed said:**
> install grub2 back onto /dev/sda5

No. Have a look at the bootscript output again, particularly the UUIDs. What was sda5 is now sda3, and what was sda7 is now sda5. The root partition is now sda3.

---

### Post by coffeecat on 2011-01-16
@wiggy25, a rather large penny has just dropped although it doesn't make any practical difference. Your Mint root partition was originally sda5 - meaning it was a logical partition - but testdisk has recreated it as sda3, which means it is now a primary partition. This sometimes happens. It doesn't matter too much and the output of fdisk in your results file doesn't show any other problem (that I've noticed) so let's see if the repair of grub as I describe does the trick.

---

### Post by wiggy25 on 2011-01-16
Thanks for the info coffeecat!

Carried out the two commands but when use the:-

```
sudo grub-install --root-directory=/mnt/ /dev/sda
```It comes up with this, is it ok?:-

```
 ~ $ sudo mount /dev/sda3 /mnt
mint@mint ~ $ sudo grub-install --root-directory=/mnt/ /dev/sda
grub-probe: error: cannot find a device for /boot (is /dev mounted?).
Installation finished. No error reported.
mint@mint ~ $ 

```
Cheers

Ian

---

### Post by gradinaruvasile on 2011-01-16
Watch out for the windows restore - it might mess up your hdd for good!

As far as i know the recovery process is to put back a set of predefined partitions (or use the existing ones but as far as Windows is concerned, the Linux partitions are unknown and posiibly they wont be preserved). Search around and you will see accounts that Linux (probably because they are non-NTFS) partitions were messed up in the process. And the MBR will be rewritten aswell and you will have to reinstall grub anyway.

Better go with the grub reinstall procedure.

Usually grub goes in the mbr and it will manage all bootable partitions found on the drive, including Windows ones. So if you install grub for Ubuntu, it should detect all Linux and Windows bootable partitions.

The basic idea is to boot from a live-cd, mount the Ubuntu partition, and chroot to it and then install grub. But some more actions may be required (such as creating the proc, sys mounts).

---

### Post by gradinaruvasile on 2011-01-16
> **wiggy25 said:**
> Thanks for the info coffeecat!

Carried out the two commands but when use the:-

```
sudo grub-install --root-directory=/mnt/ /dev/sda
```It comes up with this, is it ok?:-

```
 ~ $ sudo mount /dev/sda3 /mnt
mint@mint ~ $ sudo grub-install --root-directory=/mnt/ /dev/sda
grub-probe: error: cannot find a device for /boot (is /dev mounted?).
Installation finished. No error reported.
mint@mint ~ $ 

```
Cheers

Ian

No it is not ok. You have to do this:

```

Mine was a slightly different story. I couldn't get grub to find the stage1 file or even recognize my drive. So I borrowed some knowledge I picked up while using Gentoo:

You have to mount your root partition using the livecd:
Code:

$ 
Code:
sudo mkdir /mnt/root
$ 
Code:
sudo mount -t ext3 /dev/sda6 /mnt/root
Then you have to mount the proc subsystem and udev inside /mnt/root also:
Code:

$ 
Code:
sudo mount -t proc none /mnt/root/proc
$ 
Code:
sudo mount -o bind /dev /mnt/root/dev
Doing this allows grub to discover your drives. Next you have to chroot:
Code:

$ 
Code:
sudo chroot /mnt/root /bin/bash
Now that you're chrooted into your drive as root everything should work.
Code:

# 
Code:
sudo grub
I edited in the sudo, just to be safe. When I enter grub and not sudo grub, grub cannot find the file. I do not know if the chroot changes this because I did not try it that way. In the end I figured it was better to err on the side of caution. Tosk I hope you don't mind my editing of your reply.
grub> 
Code:
find /boot/grub/stage1
It found mine on (hd0,5)
Code:

grub> 
Code:
root (hd0,5)
It successfully scanned the partition and recognized the filesystem-type
Code:

grub> 
Code:
setup (hd0)
That was it. It installed and on reboot I was thrown back into Ubuntu.

This might help some people who are having issues so I thought I would post it.

PLEASE NOTE: My Ubuntu was installed to /dev/sda6. This may not be the same for everyone. /dev/sdaX means it's SCSI/SATA/USB/FireWire drive. And it's partition 6 because I have a weird partitioning scheme in place.


```

Source: my personal experience and:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by coffeecat on 2011-01-16
I'm puzzled. This...

> **wiggy25 said:**
> ```
 ~ $ sudo mount /dev/sda3 /mnt
mint@mint ~ $ sudo grub-install --root-directory=/mnt/ /dev/sda
[COLOR=Red]grub-probe: error: cannot find a device for /boot (is /dev mounted?).[/COLOR]
Installation finished. No error reported.
mint@mint ~ $ 

```

... shouldn't have happened; your bootscript output shows boot files in sda3.

Two thoughts. I should have asked you more about that mention of burg in the mbr in your bootscript output. Did you ever replace grub with burg? If so, using grub to repair may not work.

Second thought. Despite the grub-probe error, it says "installation finished". Have you tried rebooting from the hard drive?

---

### Post by gradinaruvasile on 2011-01-16
> **coffeecat said:**
> I'm puzzled. This...



... shouldn't have happened; your bootscript output shows boot files in sda3.

Two thoughts. I should have asked you more about that mention of burg in the mbr in your bootscript output. Did you ever replace grub with burg? If so, using grub to repair may not work.

Second thought. Despite the grub-probe error, it says "installation finished". Have you tried rebooting from the hard drive?

He has to mount /proc and /dev in order to work. I did once like that and worked. Maybe it is a grub2 specific issue.

Look at my previous post.

---

### Post by wiggy25 on 2011-01-16
Hi,

I have installed Burg, which could be the issue.
I don't know if that automatically replaces Grub2 though, too much of newbie to know that, although I did ask on Mint forum if I installed Burg would it be possible to take it out at a later date which would still leave me with Grub.

I was told that would be OK.


[COLOR=Black][Gradinaruvasile]("http://ubuntuforums.org/member.php?u=589640")[/COLOR] I have tried your suggestions for mounting  /proc and /dev, these don't work says it's not there or something along those lines.

None of the above is working, I've done another boot script info and it has changed to say where Windows is now located:-

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Windows is installed in the MBR of /dev/sdf

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 10 Julia
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdf1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Boot/BCD /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    10,487,807    10,485,760   7 HPFS/NTFS
/dev/sda2          10,487,808   344,887,272   334,399,465   7 HPFS/NTFS
/dev/sda3         344,887,296   365,432,831    20,545,536  83 Linux
/dev/sda4         365,432,886   488,408,129   122,975,244   f W95 Ext d (LBA)
/dev/sda5         365,434,880   482,457,599   117,022,720  83 Linux
/dev/sda6         482,459,648   488,396,783     5,937,136  82 Linux swap / Solaris

/dev/sda4 ends after the last sector of /dev/sda

Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdf1    *             63   312,576,704   312,576,642   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        32C49991C49957C5                       ntfs       WINRE                         
/dev/sda2        043E98713E985E0C                       ntfs       SYSTEM                        
/dev/sda3        65b3cc11-b78a-44b9-a8d8-572fab9352b3   ext4                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        b7ba1c5a-b1a6-451a-b6b1-cdbb584a2791   ext4                                     
/dev/sda6        54c1f5e1-3ff6-4d35-b8ac-a11e9dd51a4c   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdf1        0ADC798CDC7972B5                       ntfs       TREKSTOR                      
/dev/sdf: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdf1        /media/TREKSTOR          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /media/b7ba1c5a-b1a6-451a-b6b1-cdbb584a2791 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda3        /media/65b3cc11-b78a-44b9-a8d8-572fab9352b3 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda2        /media/SYSTEM            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda3        /mnt                     ext4       (rw)
/dev/sda5        /media/sda5              ext4       (rw)
/dev/sda3        /media/sda3              ext4       (rw)


=========================== sda3/boot/grub/grub.cfg: ===========================

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
set default="custom Menu"
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
search --no-floppy --fs-uuid --set 65b3cc11-b78a-44b9-a8d8-572fab9352b3
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 65b3cc11-b78a-44b9-a8d8-572fab9352b3
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=300
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
search --no-floppy --fs-uuid --set 65b3cc11-b78a-44b9-a8d8-572fab9352b3
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
menuentry 'Linux Mint 10, 2.6.35-24-generic (/dev/sda5)' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 65b3cc11-b78a-44b9-a8d8-572fab9352b3
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=65b3cc11-b78a-44b9-a8d8-572fab9352b3 ro  vga=792  quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Linux Mint 10, 2.6.35-24-generic (/dev/sda5) -- recovery mode' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 65b3cc11-b78a-44b9-a8d8-572fab9352b3
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=65b3cc11-b78a-44b9-a8d8-572fab9352b3 ro single  vga=792
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Linux Mint 10, 2.6.35-22-generic (/dev/sda5)' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 65b3cc11-b78a-44b9-a8d8-572fab9352b3
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=65b3cc11-b78a-44b9-a8d8-572fab9352b3 ro  vga=792  quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Linux Mint 10, 2.6.35-22-generic (/dev/sda5) -- recovery mode' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 65b3cc11-b78a-44b9-a8d8-572fab9352b3
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=65b3cc11-b78a-44b9-a8d8-572fab9352b3 ro single  vga=792
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
    search --no-floppy --fs-uuid --set 65b3cc11-b78a-44b9-a8d8-572fab9352b3
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 65b3cc11-b78a-44b9-a8d8-572fab9352b3
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 043e98713e985e0c
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.


menuentry "Custom Menu"{set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 65b3cc11-b78a-44b9-a8d8-572fab9352b3configfile /boot/grub/custom_menu.cfg
        }
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=65b3cc11-b78a-44b9-a8d8-572fab9352b3 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=b7ba1c5a-b1a6-451a-b6b1-cdbb584a2791 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=54c1f5e1-3ff6-4d35-b8ac-a11e9dd51a4c none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


 179.0GB: boot/grub/core.img
 180.0GB: boot/grub/grub.cfg
 177.8GB: boot/initrd.img-2.6.35-22-generic
 177.8GB: boot/initrd.img-2.6.35-24-generic
 179.9GB: boot/vmlinuz-2.6.35-22-generic
 180.0GB: boot/vmlinuz-2.6.35-24-generic
 177.8GB: initrd.img
 177.8GB: initrd.img.old
 180.0GB: vmlinuz
 179.9GB: vmlinuz.old

=================== sda5: Location of files loaded by Grub: ===================


 217.3GB: boot/grub/core.img
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  86 d3 5b fd 6b f1 59 ba  8e bd 5c b3 e5 92 a7 01  |..[.k.Y...\.....|
00000010  fe 18 a9 7f 2f ec 8f 14  bf 87 48 73 2c b4 e8 fa  |..../.....Hs,...|
00000020  b6 d6 f9 40 b8 b5 aa 4f  60 0c 20 a0 d2 50 7d a9  |...@...O`. ..P}.|
00000030  67 74 08 20 f7 41 82 e9  00 b6 80 dc 69 c4 3c ee  |gt. .A......i.<.|
00000040  62 62 ea 6a ea c1 6d 66  c9 c1 6e 41 55 99 4f c0  |bb.j..mf..nAU.O.|
00000050  f5 c0 5f 26 f7 ef a9 71  88 83 c5 53 3a 6f f5 93  |.._&...q...S:o..|
00000060  42 8a a0 2b 61 b3 e7 a5  c4 64 70 64 30 64 f6 55  |B..+a....dpd0d.U|
00000070  6e 22 56 e4 45 7b 09 ab  10 e7 3b 38 af eb 23 58  |n"V.E{....;8..#X|
00000080  09 6c 64 64 e4 1b 8f 6d  e6 c0 73 b7 ff 46 4a 79  |.ldd...m..s..FJy|
00000090  5c 9f 01 94 3a 37 65 13  65 5b 74 4c cb cb ca 22  |\...:7e.e[tL..."|
000000a0  ef 76 b4 14 ff 70 6f 50  d3 2c 04 18 ec 24 18 e2  |.v...poP.,...$..|
000000b0  2d 7c 92 eb 29 c0 31 77  7c 90 11 fb d4 db ec 3a  |-|..).1w|......:|
000000c0  65 72 1b 63 dc b3 12 dd  0c 39 19 aa b5 66 63 66  |er.c.....9...fcf|
000000d0  87 6a 7d 13 73 f3 6c d1  40 c8 ca f6 3e 6a 28 a5  |.j}.s.l.@...>j(.|
000000e0  ef d3 03 a6 4e bd 13 7c  83 6f fd dd a1 ee 1d 6f  |....N..|.o.....o|
000000f0  b1 35 01 34 92 5d 6c f4  83 91 c0 3e 3d 3d 9d ad  |.5.4.]l....>==..|
00000100  b7 ae b5 13 d6 ae e5 82  3c 1b be 18 d1 04 5f f1  |........<....._.|
00000110  c5 fa ef c4 57 23 a9 65  a8 f5 e7 d1 c7 d2 f2 66  |....W#.e.......f|
00000120  44 80 b7 5c 4f 64 01 ba  49 32 cc d6 3e 93 52 9f  |D..\Od..I2..>.R.|
00000130  09 c9 91 97 f1 99 56 76  77 33 89 cd 3e a7 87 ed  |......Vvw3..>...|
00000140  c8 b1 d1 32 33 83 f2 ed  82 8b b5 6e 31 96 9e 4e  |...23......n1..N|
00000150  a8 2e 7c 73 58 cc 46 3c  c8 a2 af 3c 3a 57 bc 65  |..|sX.F<...<:W.e|
00000160  fe 37 19 09 b3 29 cf a2  f5 52 d4 ef 33 a5 94 4e  |.7...)...R..3..N|
00000170  bd 9c 36 cb 4d 38 f0 b7  41 d4 db cd bf e3 02 5a  |..6.M8..A......Z|
00000180  15 52 a5 c5 bc 29 d7 e4  53 e8 90 eb cd 6e 20 b7  |.R...)..S....n .|
00000190  99 5e d7 76 bd 43 cd 21  34 64 e4 70 19 ef aa 85  |.^.v.C.!4d.p....|
000001a0  f9 4c 58 ff 7a 0a 7e eb  49 73 7f 9d 5c 6b d3 15  |.LX.z.~.Is..\k..|
000001b0  88 89 f0 fb 3f 79 12 a3  be f1 cd 1d 11 07 00 fe  |....?y..........|
000001c0  ff ff 83 fe ff ff ca 07  00 00 00 a0 f9 06 00 fe  |................|
000001d0  ff ff 05 fe ff ff 62 af  f9 06 58 98 5a 00 00 00  |......b...X.Z...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```Something is happening but I don't know what!

Cheers

Ian

---

### Post by coffeecat on 2011-01-16
> **gradinaruvasile said:**
> He has to mount /proc and /dev in order to work. I did once like that and worked. Maybe it is a grub2 specific issue.

The OP should not have to chroot into the hard drive install the way you describe in order to re-install grub2 stage 1 to the mbr. See:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Although I agree we may need to use a chroot as a last resort.

> **wiggy25 said:**
> I have installed Burg, which could be the issue.

It may indeed. In which case we may need to chroot after all to completely reinstall grub2, or somehow reinstall burg to the mbr, but how you do that I don't know. But this doesn't look right.

> **wiggy25 said:**
> ```
 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive [COLOR=Red]in 
    partition #5[/COLOR] for (,msdos5)/boot/grub.
```

That should be sda3, not sda5. Which is odd, because the code you posted earlier showed you mounting sda3 to /mnt in the live CD. Did you copy and paste your actual live CD commands into your post? Are you sure you mounted sda3 and not sda5?

---

### Post by wiggy25 on 2011-01-16
Everything I've done is by copy and paste.

I can't do anything else but run from Live CD, so everything I'm posting is from the terminal from the Live CD

Cheers

Ian

---

### Post by wiggy25 on 2011-01-16
I've got screen captures from Testdisk that I've just run:-

[IMG]http://i106.photobucket.com/albums/m280/wiggy25/Screenshot-4.png[/IMG]

[IMG]http://i106.photobucket.com/albums/m280/wiggy25/Screenshot-1-2.png[/IMG]



[IMG]http://i106.photobucket.com/albums/m280/wiggy25/Screenshot-2-1.png[/IMG]
I don't know if it will help or not, I thought the more info the better.

Cheers

Ian

---

### Post by coffeecat on 2011-01-16
I've done a bit of googling. It seems that the error message:

```
grub-probe: error: cannot find a device for /boot (is /dev mounted?).
```

... can be associated with a BIOS issue. Which means that between the BIOS and the kernel there could be some confusion over partition numbering. Which makes things complicated. So - you may have to chroot after all. Try following gradinaruvasile's chroot method but remember that your Mint root partition is sda3. You'll have to do a bit of substitution. That's if chrooting can get around partition number confusion. :?

If that doesn't work, I'll dig out my chroot method - and do a bit of thinking.

---

### Post by gradinaruvasile on 2011-01-16
> 
Although I agree we may need to use a chroot as a last resort.



It may indeed. In which case we may need to chroot after all to completely reinstall grub2, or somehow reinstall burg to the mbr, but how you do that I don't know. But this doesn't look right.


The idea was to first mount the Ubuntu partition somewhere, then do the /dev and /proc mount commands (careful with the paths, they have to be checked to be correct).

I did this on a Debian Squeeze machine that uses grub2 too and it worked for me by mounting the /dev and /proc from my hdd partition then chrooting to it  (i dd-ed my boot partition from my old hdd to a new one).

---

### Post by wiggy25 on 2011-01-16
I tried  the commands Gradinaruvasile posted but they don't work.

First command says directory exists then the others just come up with errors or bad commands or directory not found.

I do believe I may have killed it!

Thanks for all the help so far.

Cheers

Ian

---

### Post by gradinaruvasile on 2011-01-16
> **wiggy25 said:**
> I tried  the commands Gradinaruvasile posted but they don't work.

First command says directory exists then the others just come up with errors or bad commands or directory not found.

I do believe I may have killed it!

Thanks for all the help so far.

Cheers

Ian

First:
unmount your partition if you looked at it in nautilus (click on th eject button).

mount your partition to /mnt as instructed in that how-to.

Second:

cd /mnt

ls -al

And from this on, do the commands as described.

Post every command you issued (including the output of the "ls -al" above) and their output (if any).


PS.
In my case i first sudoed myself (from the live cd) with 

sudo su -

Then i issued every command (no need to put sudo in front in this case).

---

### Post by coffeecat on 2011-01-16
I'm beginning to wonder if the change of number (and type) of your Mint root partition from sda5 to sda3 is causing that problem with grub-install. How else would it designate partition #5 when you stipulated #3? What do you think, gradinaruvasile?

I can see two options. Perhaps others may be able to suggest something else. The first is to use testdisk to change your Mint partition from primary back to logical. That might help, but might just dig a deeper hole. The second has several steps, namely:

1 - Backup your personal data from your Mint partitions using the live CD.

2 - Repair the Windows mbr so that you can boot into Windows. You need either a Windows 7 repair disc [(available here)]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") or you can do this from the Mint live CD using lilo. I can tell you how.

3 - Delete all the Linux partitions. (That would also neatly sidestep the extended partition boundary problem which we haven't dealt with yet.)

4 - Re-install Mint or Ubuntu.

What do you think?

---

### Post by wiggy25 on 2011-01-16
I quite like the idea of number 2 and 3 as this will then sort the linux partitions as well.
Not really had any luck using the other method.

Also I don't have any documents in Mint so it's not like I need to keep anything there!

If you can tell me how to repair windows so that I can boot back into it using lilo, then we can delete all of the linux partitions.
will be easier than trying to shift things about.

Thanks for this!

Ian

---

### Post by gradinaruvasile on 2011-01-16
If you repair Windows it will overwrite the mbr and you will only be able to boot into Windows and may lose the Linux partitions.

The idea is to install grub in order to be able to boot from any partition (Linux or Windows).

---

### Post by srs5694 on 2011-01-16
This is closing the barn door after the cows have gone, but there was a safer and more reliable (but more tedious) way to fix the problem that would have avoided these issues. This will *only* work if you've trashed the disk *but not yet rebooted*. Once you reboot, the data are gone. In case anybody reads this in the future, I'll document the procedure here:

Linux keeps track of all the partitions on all its disks in pseudo-files in the /sys filesystem. Unfortunately, the exact path varies from one system to another and is rather ungainly. To find it, type this:

```

find /sys/devices/ -name sda1

```Change "sda1" to any other partition you know exists (or did exist). This will produce a directory name; in my case, it's /sys/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda1. You can then view the files in that directory:

```

$ ls /sys/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda1
alignment_offset  holders    power  start  subsystem
dev               partition  size   stat   uevent

```The start and size pseudo-files hold the start point and size of the partition, in sectors. Copy-and-paste these values into a text editor. (Don't try writing them down by hand; most will be very long, and therefore prone to human copying errors.) Repeat this for all the partitions described in the directory in question. Note that any extended partition will have a ridiculously small size (2 on a test disk I just examined). You'll need to adjust that later.

With that information in hand, fire up fdisk using its -u option ("sudo fdisk -u /dev/sda") and use it to re-create the partitions. Using "-u" (or using the 'u' option once you've started it) is very important; without it, fdisk will interpret values in cylinders rather than sectors, but the values you've got are in sectors. Enter an absolute value for the partition start point, then use "+" to indicate a relative value for the size, but *subtract one from the size value obtained earlier!* I recommend doing any extended partition after all the other primaries; that way you can ignore the size value and just accept fdisk's default. You'll then do the logical partitions (those numbered 5 and up) after the primaries and extended. The interactions with fdisk look like this:

```

Command (m for help): **n**
Command action
   e   extended
   p   primary partition (1-4)
**p**
Partition number (1-4): **1**
First sector (63-15654911, default 63): **63**
Last sector, +sectors or +size{K,M,G} (63-15654911, default 15654911): **+2537**

Command (m for help): **p**

Disk /dev/sdb: 8015 MB, 8015314944 bytes
255 heads, 63 sectors/track, 974 cylinders, total 15654912 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000c9b9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63        2600        1269   83  Linux
Partition 1 does not end on cylinder boundary.

```I've bolded the user's input. This example creates a partition that starts at sector 63 and that's *2538* sectors long -- note that's 2538, not 2537, as entered. (This is because the "+" option to fdisk sets the end sector, not the partition size per se.)

If the disk is a GUID Partition Table (GPT) disk, you can use [gdisk]("http://www.rodsbooks.com/gdisk/") much like fdisk; however, gdisk interprets a "+" in the end sector field as a flag for size, so you should *not* subtract 1 from the size values, as you do with fdisk.

You'll now need to go through and set the partition type codes for those partitions that don't hold Linux filesystems. You can use the 't' option for this. You may need to do some guessing; however, the "blkid" utility can help by identifying what filesystems are on each partition.

When done, use fdisk's 'w' option to save the changes. Cross your fingers and reboot. If you did everything perfectly, your partitions will be saved.

This procedure is safer than using testdisk *if* you're meticulous about recording and copying the data. The problem with testdisk is that it can make mistakes and it can mix up partition numbers, as described in this thread. One common testdisk error, which is illustrated in this thread, is creating an extended partition that's too big. I've seen lots of reports of this problem.

Anyhow, best of luck to wiggy25 in recovering the partitions!

---

### Post by srs5694 on 2011-01-16
You can change /dev/sda3 to /dev/sda5 in at least a couple of ways that are safer than using testdisk again, but less destructive than wiping your Linux installation:


[list]
[*]Use sfdisk to change the start point and size of /dev/sda4 (the extended partition), then change the name of /dev/sda3 to /dev/sda5. This procedure is similar in principle to the one I describe on [this page of mine](http://www.rodsbooks.com/missing-parts/index.html) (which was referenced in an earlier post). If you haven't corrected it already, you'll be able to fix the problem with the mis-sized extended partition at the same time.
[*]Use my [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) to convert from MBR to GPT format and then back again. This is a bit of an ugly solution, but it should work. If you attempt this, be sure to use the latest version of gdisk from [the GPT fdisk downloads page;](http://sourceforge.net/projects/gptfdisk/files/) the version that's included in the Ubuntu repositories is badly out of date and will not work for this procedure. To use gdisk in this way, you'd launch it on the disk, type 'r' to get to the recovery & transformation menu, type 'g' to do the conversion, and fine-tune the partition type codes and primary/logical assignments from there. (See the "Converting from GPT to MBR" section of [this page](http://www.rodsbooks.com/gdisk/mbr2gpt.html) for details.) This procedure will also fix the problem with the mis-sized extended partition. You'll probably have to re-install your boot loader when you're done.
[/list]


Both procedures are a bit risky, but at this point, you've got very little to lose. That said, I recommend using an emergency disk to back up any important data right now, while you at least have access to your filesystems, even if the computer won't boot.

---

### Post by wiggy25 on 2011-01-16
Just rebooted and I'm now presented with the GNU GRUB version 1.98.........
 
It then says Minimal Bash-like line editing is supported. for the first word, TAB lists possible command completions. Anywhere else tab lists possible device or file completions.
 
grub>
 
 
Thats it, don't know what to do from this point on.
I still think an easier way is to just repair the Windows boot loader remove the Linux partitions and reinstall the Linux O.S.
 
Unless something can be done with the Grub command line?
 
Cheers
 
Ian

---

### Post by wiggy25 on 2011-01-16
Well, downloaded the Vista recovery disc as shown here:-

[http://ubuntuforums.org/showthread.php?t=1014708&highlight=reinstall+Vista+bootloader](http://ubuntuforums.org/showthread.php?t=1014708&highlight=reinstall+Vista+bootloader)

Followed the instructions and all I get is the Missing BootMNGER press ctrl+alt+del to restart.
then just follow the constant circle.

It has found Vista home premium on drive D but can't do anything else with it.

What fun.

---

### Post by coffeecat on 2011-01-16
> **wiggy25 said:**
> Followed the instructions and all I get is the Missing BootMNGER press ctrl+alt+del to restart.
then just follow the constant circle.

That sounds like something wrong with the boot files in the boot sector of the Windows partition. Which should be C:, not D:. Whatever.

Repairing the mbr won't help with that although you did need to restore the Windows mbr.

I can't remember the sequence with the Vista disc, but once you've ogt into the recovery options, there should be one to repair boot problems. Have you tried that? If that doesn't work there is a command you can run from the Windows command prompt which you should be able to access somewhere in the Windows disc. See here:

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

You've probably already done the equivalent of 'bootrec /FixMbr' but it won't hurt to do it again. Then you could try 'bootrec /FixBoot'.

---

### Post by wiggy25 on 2011-01-16
I've tried all of that.
Just won't repair the Vista boot.
Tried all of those bootrec/fixboot and bootrec/fixmbr still comes up with bootmanager missing.

It's looking very grim now!

Shame as when I put that downloaded Vista recovery disc in, it does show Windows Vista as being on D:
I just can't boot in to it.

Lost count now how many times I've put that recovery disc in and used the fixboot / fix mbr.

Not too sure what to do now.
If I could perhaps sort out the partitions so that Gparted could see them, I'm wondering if it would then be possible to install Mint again resetting the partitions but to give me a new GRUB loader, which may allow me to boot into Vista.

Clutching at straws somewhat now.

Cheers

Ian

> **coffeecat said:**
> That sounds like something wrong with the boot files in the boot sector of the Windows partition. Which should be C:, not D:. Whatever.

Repairing the mbr won't help with that although you did need to restore the Windows mbr.

I can't remember the sequence with the Vista disc, but once you've ogt into the recovery options, there should be one to repair boot problems. Have you tried that? If that doesn't work there is a command you can run from the Windows command prompt which you should be able to access somewhere in the Windows disc. See here:

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

You've probably already done the equivalent of 'bootrec /FixMbr' but it won't hurt to do it again. Then you could try 'bootrec /FixBoot'.

---

### Post by coffeecat on 2011-01-16
> **wiggy25 said:**
> 
Not too sure what to do now.
If I could perhaps sort out the partitions so that Gparted could see them, I'm wondering if it would then be possible to install Mint again resetting the partitions but to give me a new GRUB loader, which may allow me to boot into Vista.

If Vista is refusing to allow itself to be repaired, I'm not sure that grub will help, but I suppose it's worth trying.

Follow srs5694's advice and his link. There are two things to do: sorting out the end sector of the extended partition so that Gparted can see the partitions, and (if I'm following this correctly) changing the partition type of what's presently called sda3 so that you can reinstall grub.

Have you tried to rescue your personal files with the live CD yet?

---

### Post by wiggy25 on 2011-01-16
Yes, copied them all to discs.
Don't like the idea of changing those sector sizes and partitions, don't really understand any of it!
 
I wouldn't do it by choice, there again I wouldn't wipe out my har drive by choice either.....but I did!
 
Cheers
 
Ian

---

### Post by wiggy25 on 2011-01-16
Yes, copied them all to discs.
Don't like the idea of changing those sector sizes and partitions, don't really understand any of it!
 
I wouldn't do it by choice, there again I wouldn't wipe out my har drive by choice either.....but I did!
 
Cheers
 
Ian

---

### Post by wiggy25 on 2011-01-16
Yes, copied them all to discs.
Don't like the idea of changing those sector sizes and partitions, don't really understand any of it!
 
I wouldn't do it by choice, there again I wouldn't wipe out my har drive by choice either.....but I did!
 
Cheers
 
Ian

---

### Post by wiggy25 on 2011-01-16
Yes, copied them all to discs.
Don't like the idea of changing those sector sizes and partitions, don't really understand any of it!
 
I wouldn't do it by choice, there again I wouldn't wipe out my har drive by choice either.....but I did!
 
Cheers
 
Ian

---

### Post by coffeecat on 2011-01-16
> **wiggy25 said:**
> Don't like the idea of changing those sector sizes and partitions, don't really understand any of it!

It's not as bad as it might look. I followed those directions once for the same reason after using testdisk, and it worked OK.

Good luck!

---

### Post by srs5694 on 2011-01-16
> **wiggy25 said:**
> Don't like the idea of changing those sector sizes and partitions, don't really understand any of it!
 
I wouldn't do it by choice, there again I wouldn't wipe out my har drive by choice either.....but I did!

If you're not comfortable using sfdisk and manually editing the sizes, you could use a rather hacky method using [GPT fdisk (gdisk):](http://www.rodsbooks.com/gdisk/) Convert the disk to GPT form (in gdisk's memory only) and then back to MBR (using the 'g' option on the recovery & transformation menu). This minimizes the risk of doing something wrong because of an arithmetic error, but it's really not any easier than using sfdisk to do the job. You'll also have to adjust the Linux partitions' type codes during the conversion, since Linux and Windows share a type code in GPT but not in MBR. OTOH, if you want to convert /dev/sda3 into a logical partition, the gdisk-mediated conversion makes that just a little easier. (Basically, when converting back to MBR gdisk will create its own new extended partition to fit whatever logical partitions you tell it to create, so you needn't mess with the arithmetic of figuring out how to size it all. AFAIK, gdisk has no bugs that create improperly-sized extended partitions.)

I'm sorry you're in this mess, but given where things stand, I see four choices for you:


[list]
[*]Look for a point-and-click utility that's smart enough to figure out what's wrong and fix it. Such a tool might exist, but if so, I don't know what it is. You're more likely to find such a program in the Windows world than in the Linux world, for various reasons, so running it could be a problem if you can't get Windows to boot. Trying random utilities is likely to make matters worse, so I recommend running such a tool only if somebody can recommend a program that will fix your specific problems.
[*]Bite the bullet and deal with an sfdisk or gdisk solution to the problem.
[*]Back up what you can, delete all your partitions, and start over from scratch, re-installing your OSes and then restoring your user data afterwards.
[*]Pay big bucks for a data recovery specialist to fix your disk.
[/list]

---

### Post by ZoneSeek on 2011-01-17
I've skimmed through, will re-read the thread more closely in a bit, but I'm panicking. Was using the downloaded iso on my Seagate 320gig portable drive to install Ubuntu Maverick Meerkat on my girlfriend's messed-up netbook. I think the install wasn't detecting her netbook's hard drive anymore so Ubuntu started to install on my Seagate portable. Now I can't get to the Seagate's files, either on my own Ubuntu netbook or on another Win XP laptop. But Ubuntu Disk Utility sees the Seagate drive: Unknown 317gb; Extended Container for logical partitions 3.1gb; Linux Swap Space 3.1gb.

My house just burned down a few days ago, the Seagate portable drive is my only copy of about 15 years worth of files. I'm kicking myself vehemently for not making multiple backups first thing, but here I am. I think I just have to delete the Linux partition, but I'd like to be sure.

---

### Post by srs5694 on 2011-01-17
> **ZoneSeek said:**
> I've skimmed through, will re-read the thread more closely in a bit, but I'm panicking.

Please start a *new* thread. No matter how similar your problem seems to the one discussed here, it might be very different, and intertwining two peoples' problems will create nothing but confusion (and perhaps entirely new problems as a result).

Please include either a GParted screen shot of the problem drive or the output of "sudo fdisk -lu" (enclosed between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags).

---

### Post by wiggy25 on 2011-01-17
@ srs5694

Thanks for your tutorial, scared myself doing it but edited the partition that was too big!!

I now have a Gparted screen shot!

[IMG]http://i106.photobucket.com/albums/m280/wiggy25/Screenshot-5.png[/IMG]

Very different to when I first started all of this!!
I know the first partition was hidden, as it's the Vista recovery bit, then there was the Vista system, the next chunk was the extended partition.

Still can't boot into windows, tried the Vista recovery disc download and followed all of the instructions to fix boot and fix mbr also did the rebuild BCD still nothing.

I can't remember what I did but on booting up Mint Live CD late last night it did actually show windows vista to boot into, which I promptly did and all was well.......won't work now though.
Just can't get it to boot into windows at all.

Any thing else you guys can come up with would be very useful.
I can see me wiping the HDD and installing XP, I have a disc for that, will take hours to download all the service packs though!
I may even just install a Linux flavour of my choosing and become Linux only.

Thanks again everybody for all your help so far.
Like I say I've managed to copy all of my important documents, any downloaded programs will be gone, if I can't get back into Vista although, it's annoying me as I managed to get into it, but that was before I resized that too large a partition.

Cheers

Ian

---

### Post by srs5694 on 2011-01-17
As you've deleted your Linux partitions, what you've got now is a Windows-only system. If you want to get Windows booted, I recommend you go to a Windows forum, where people more knowledgeable in the Windows boot process and fixing Windows problems hang out.

---

### Post by coffeecat on 2011-01-17
> **wiggy25 said:**
> Any thing else you guys can come up with would be very useful.

Your partition #1 with the label WINRE has the boot flag. At only 5GB I guess it's a restore partition and that your Windows C: is on partition #2. Windows needs the boot flag to be able to boot. Use Gparted to set the boot flag to partition sda2 and then try booting from the hard drive.

---

### Post by wiggy25 on 2011-01-17
> **coffeecat said:**
> Your partition #1 with the label WINRE has the boot flag. At only 5GB I guess it's a restore partition and that your Windows C: is on partition #2. Windows needs the boot flag to be able to boot. Use Gparted to set the boot flag to partition sda2 and then try booting from the hard drive.
 
 
I was going to try that as I've nothing to lose.
Oh yes and it's back, now in Vista had to use the recovery disc, but did the Bootrec.exe /FixBoot and Bootrec.exe /FixMbr and just to make sure Bootrex /rebuildbcd
Took out the disks rebooted straight back into Windows!!
 
Thank you all, for all the help!!
I don't really deserve it for being a complete bloody idiot!
 
I know I shouldn't mess but the Vista recovery partition do I need to put it back to Hidden or just leave it as it is?
I don't even know how you're supposed to get into that if something goes wrong, hence should it stay as hidden?
Using Gparted reset the extended partition so it's ready to have Linux re-installed!
Just waiting for Vista to boot up and shut down is a joke, as I've not used it since using Ubuntu or Mint forgot just how bad it is!
 
Again thanks everyone for all the help and advice!
I do believe that is a SOLVED!!

---

### Post by coffeecat on 2011-01-17
> **wiggy25 said:**
> I don't even know how you're supposed to get into that if something goes wrong, hence should it stay as hidden?

With some manufacturers you press one of the function keys during the POST screen to get into the recovery partition. You'd have to check the manual for which one. When you've reinstalled a Linux distro, you'll probably have a grub entry for the recovery partition. As far as whether or not it should be hidden, I don't know. I think a recovery partition is only made hidden to prevent the average user from tampering with it.

Good luck!

---

### Post by wiggy25 on 2011-01-17
Well in that case it can stay as it is!!!
I took the boot flag off of it and just put it on to partition #2 as you suggested.
 
I've done enough damage for one lifetime..........until I do something just as stupid again!!!
 
Thanks again for all the helpsupport and advice, could never have done it without everyones help.
 
Cheers
 
Ian

---

### Post by srs5694 on 2011-01-17
Now that this is fixed, may I suggest you back up your Windows partition? That way, if you run into problems again, you'll at least be able to wipe the partition and restore Windows to a bootable state. I've successfully used [DriveImage XML](http://www.runtime.org/driveimage-xml.htm) for this purpose. To restore, you'll need a Windows boot disk; see [this page on their site](http://www.runtime.org/peb.htm) for a rough guide, including links to the tools needed to create the necessary boot CD.

---

