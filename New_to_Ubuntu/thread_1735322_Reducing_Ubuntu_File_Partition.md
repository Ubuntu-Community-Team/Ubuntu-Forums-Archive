---
title: "Reducing Ubuntu File Partition"
date: 2011-04-21
forum: New to Ubuntu
---

### Post by RMckelvie89 on 2011-04-21
Hey there. 

Very recently, I have needed most of my hard drive space to download games using Windows Vista and I am not really sure how to reduce the file partition.

To help things, I have a Live CD at hand, however, I am too used to .exe files and I do not know how to boot up CDs the ubuntu way.

Hope this helps

Ross

---

### Post by Locke_99GS on 2011-04-21
Make sure the computer's BIOS is configured to boot from CD. Put the LiveCD in, reboot the computer. When the LiveCD loads to a desktop, open *System -> Administration -> GParted*.

Reduce the size of your largest Linux partition. (usually will be formatted to ext3 or ext4) If needed, move any partitions between the linux partition you adjusted and the largest NTFS partition to the right, putting the free space adjacent to the NTFS partition. Exxpand the size of your largest NTFS partition into the free space you created. Apply. Reboot.


Very very, very, very careful in making sure that the partitions you are adjusting are the correct partitions.

---

### Post by seawolf167 on 2011-04-21
Couple additions to the previous post I'd suggest

[LIST]
[*]create a disk image with [Clonezilla ]("http://www.clonezilla.org")if you have any concerns or worries about what you are doing (besides, its always a good idea to have a backup)
[*]use the built-in Windows partition editor to resize the NTFS (i.e. Windows) partition, still use GParted to resize your Ubuntu partitions though
[/LIST]

---

### Post by Mark Phelps on 2011-04-21
> **seawolf167 said:**
> [*]use the built-in Windows partition editor to resize the NTFS (i.e. Windows) partition, still use GParted to resize your Ubuntu partitions though
[/LIST]

+1 -- Can't emphasize this enough ... Use the Win7 Disk Management feature to resize Win7 OS partitions.  Using GParted or other Linux utilities risks corrupting the Win7 filesystem.

---

### Post by RMckelvie89 on 2011-04-25
Thanks very much for all of your input. I have managed to use gparted to reduce the size from ~20GB to ~5GB, however,  I have a problem with trying to run Windows Disk Mangager. 

I do not know how to get the main Vista partition to claim the free space. I have tried formatting the volume to NTFS with an unassigned drive letter and when I try to extend the volume in the vista partition, the option has been greyed out.

[[IMG]http://img860.imageshack.us/img860/6522/parions.jpg[/IMG]](http://img860.imageshack.us/i/parions.jpg/)

---

### Post by seawolf167 on 2011-04-25
What happens if you left click to select the C: partition then attempt to resize that one with a right-click?

---

### Post by RMckelvie89 on 2011-04-25
> **seawolf167 said:**
> What happens if you left click to select the C: partition then attempt to resize that one with a right-click?

I really don't know. As far as I know, I right click on the C: drive and I come up with that menu.

I am getting really sick and tired of having Linux on my computer as I have stumbled into another problem involving a crappy command at computer start up saying that I have the following:

error: unknown filesystem

grub rescue>

In short, I have screwed my entire system. *shakes fist*

Update: it seems that I cannot run my PC without the Live CD. Please make the pain go away. :(

---

### Post by K_45 on 2011-04-25
Run this boot info script off the live CD:

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

```
sudo bash ~/Downloads/boot_info_script*.sh
```

and upload the Results.txt file

---

### Post by RMckelvie89 on 2011-04-25
>                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

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

/dev/sda1               2,048    16,779,263    16,777,216  27 Hidden HPFS/NTFS
/dev/sda2    *     16,779,264   445,642,407   428,863,144   7 HPFS/NTFS
/dev/sda3         445,642,750   488,396,799    42,754,050   5 Extended
/dev/sda5         445,642,752   445,644,799         2,048   6 FAT16
/dev/sda6         476,141,568   486,526,975    10,385,408  83 Linux
/dev/sda7         486,529,024   488,396,799     1,867,776  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        184A4A004A49DAE0                       ntfs       _OEMBP                        
/dev/sda2        DEF88564F8853C31                       ntfs       HDD                           
/dev/sda3: PTTYPE="dos" 
/dev/sda6        24373205-e3ab-406d-94c7-a6feeb9321f5   ext4                                     
/dev/sda7        49978de0-d101-4ef9-a420-b624055f951e   swap                                     
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
/dev/sda6        /media/24373205-e3ab-406d-94c7-a6feeb9321f5 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda2        /media/HDD               fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set 24373205-e3ab-406d-94c7-a6feeb9321f5
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 24373205-e3ab-406d-94c7-a6feeb9321f5
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
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 24373205-e3ab-406d-94c7-a6feeb9321f5
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=24373205-e3ab-406d-94c7-a6feeb9321f5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 24373205-e3ab-406d-94c7-a6feeb9321f5
    echo    'Loading Linux 2.6.35-27-generic ...'
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=24373205-e3ab-406d-94c7-a6feeb9321f5 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 24373205-e3ab-406d-94c7-a6feeb9321f5
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=24373205-e3ab-406d-94c7-a6feeb9321f5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 24373205-e3ab-406d-94c7-a6feeb9321f5
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=24373205-e3ab-406d-94c7-a6feeb9321f5 ro single 
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
    search --no-floppy --fs-uuid --set 24373205-e3ab-406d-94c7-a6feeb9321f5
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 24373205-e3ab-406d-94c7-a6feeb9321f5
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 184a4a004a49dae0
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set def88564f8853c31
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=24373205-e3ab-406d-94c7-a6feeb9321f5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=49978de0-d101-4ef9-a420-b624055f951e none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 248.8GB: boot/grub/core.img
 246.5GB: boot/grub/grub.cfg
 245.6GB: boot/initrd.img-2.6.35-22-generic
 245.6GB: boot/initrd.img-2.6.35-27-generic
 243.8GB: boot/vmlinuz-2.6.35-22-generic
 243.9GB: boot/vmlinuz-2.6.35-27-generic
 245.6GB: initrd.img
 245.6GB: initrd.img.old
 243.9GB: vmlinuz
 243.8GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  06 00 65 03 ff ff ff ff  00 ff ff ff 20 ee 13 00  |..e......... ...|
00000010  5d dd 2b 47 f0 ff ff ff  2c 00 00 00 03 00 00 00  |].+G....,.......|
00000020  03 00 00 00 72 0c 00 00  00 00 00 00 00 00 00 00  |....r...........|
00000030  ba 03 00 01 51 74 00 00  05 00 d8 02 ff ff ff ff  |....Qt..........|
00000040  00 ff ff ff 24 ef 13 00  ad 15 29 47 0d 00 00 00  |....$.....)G....|
00000050  35 00 00 00 03 00 00 00  02 00 00 00 71 0c 00 00  |5...........q...|
00000060  00 00 00 00 00 00 00 00  b8 03 00 01 5a 74 00 00  |............Zt..|
00000070  06 00 5a 02 ff ff ff ff  00 ff ff ff e8 ef 13 00  |..Z.............|
00000080  0b 2c 37 47 f0 ff ff ff  35 00 00 00 03 00 00 00  |.,7G....5.......|
00000090  02 00 00 00 73 0c 00 00  00 00 00 00 00 00 00 00  |....s...........|
000000a0  6b 05 01 01 64 74 00 00  04 00 1f 00 ff ff ff ff  |k...dt..........|
000000b0  00 ff ff ff ac f0 13 00  00 00 d0 43 9b 00 00 00  |...........C....|
000000c0  de 00 00 00 01 00 00 00  04 00 00 00 74 0c 00 00  |............t...|
000000d0  00 00 00 00 00 00 00 00  cf 00 01 01 6c 74 00 00  |............lt..|
000000e0  05 00 3c 14 ff ff ff ff  00 ff ff ff 50 f1 13 00  |..<.........P...|
000000f0  00 00 f0 46 26 00 00 00  36 00 00 00 04 00 00 00  |...F&...6.......|
00000100  02 00 00 00 75 0c 00 00  00 00 00 00 00 00 00 00  |....u...........|
00000110  cf 00 01 01 75 74 00 00  04 00 8c 01 ff ff ff ff  |....ut..........|
00000120  00 ff ff ff 90 f1 13 00  00 00 f0 45 2a 00 00 00  |...........E*...|
00000130  36 00 00 00 01 00 00 00  02 00 00 00 76 0c 00 00  |6...........v...|
00000140  00 00 00 00 00 00 00 00  ce 00 00 01 7d 74 00 00  |............}t..|
00000150  04 00 71 14 ff ff ff ff  00 ff ff ff ac f1 13 00  |..q.............|
00000160  00 00 80 42 f7 00 00 00  b0 01 00 00 02 00 00 00  |...B............|
00000170  01 00 00 00 77 0c 00 00  00 00 00 00 00 00 00 00  |....w...........|
00000180  93 00 01 01 85 74 00 00  05 00 46 13 ff ff ff ff  |.....t....F.....|
00000190  00 ff ff ff 10 f2 13 00  00 00 40 45 f2 ff ff ff  |..........@E....|
000001a0  36 00 00 00 06 00 00 00  01 00 00 00 78 0c 00 00  |6...........x...|
000001b0  00 00 00 00 00 00 00 00  93 00 01 01 8a 74 00 fe  |.............t..|
000001c0  ff ff 06 fe ff ff 02 00  00 00 00 08 00 00 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 50  d1 01 00 88 9e 00 00 00  |.......P........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 

There are my Results

---

### Post by K_45 on 2011-04-25
GRUB has gotten lost, its not on sda5, more info here:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) (See rescue mode)

and here:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by RMckelvie89 on 2011-04-25
> **K_45 said:**
> GRUB has gotten lost, its not on sda5, more info here:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) (See rescue mode)

and here:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)


Are the following commands performed at the Terminal? Just wondering.

---

### Post by K_45 on 2011-04-25
Some are from the LIveCD, others on boot up. Yes, you will use the terminal.

---

### Post by Dutch70 on 2011-04-25
From the live cd/usb, run these 2 commands in a terminal and reboot. That should take care of it. 
Although I'm not sure what sda5 was or what you did with it. Was it a /boot partition? 

```
sudo mount /dev/sda6 /mnt
```

```
sudo grub-install --root-directory=/mnt /dev/sda
```

---

### Post by RMckelvie89 on 2011-04-25
I think the sda5 could be the "Free Space" I was trying to absorb into Vista. 

I'm not great when it comes to working with partitions, so the best I can do is guess/assume.

As soon as the disk gets up and running, I will try running those commands reboot and see if there is any joy. :)

---

### Post by RMckelvie89 on 2011-04-25
Dutch70: I tried those Terminal commands and nothing has happened. Would it be safe to experiment with other partitions using that command and see what turns up?

---

### Post by Dutch70 on 2011-04-25
No, post a new boot script, this time paste it between [CODE][ /CODE] tags by using the # symbol in the toolbar.

---

### Post by RMckelvie89 on 2011-04-25
I think it would be easier to throw my Hard Drive in the nearest lake. :D

Joking aside, I'll look into this matter later on. It's pretty late and I need some shut-eye.

Update: Okay. I don't know what I just done differently, but everything seems to be working fine for now. Thanks for your input and taking the time and effort into solving my problem(s).

---

