---
title: "ububtu can't booting!!!"
date: 2011-01-22
forum: New to Ubuntu
---

### Post by Its_Rishi on 2011-01-22
i have dual boot ububtu and windows 7 after upgrading windows 7 no boot options were appearing windows is starting automatically
how can i replace ubuntu boot loader and start my linux?

---

### Post by Rubi1200 on 2011-01-22
I apologize, but your post is not clear.

Are you using a third-party bootloader on Windows?

How did you install Ubuntu?

Do you have a LiveCD or LiveUSB?

If yes, follow these instructions:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Its_Rishi on 2011-01-22
> **Rubi1200 said:**
> I apologize, but your post is not clear.

Are you using a third-party bootloader on Windows?

How did you install Ubuntu?

Do you have a LiveCD or LiveUSB?

If yes, follow these instructions:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

i downloaded the file but i didn't understand wat to do!!!

---

### Post by Quackers on 2011-01-22
You need to boot from the live cd/usb and select "try ubuntu" then, when the desktop loads, download the boot script to the desktop (not Downloads folder).
Then open up a terminal and run the command given by Rubi1200. The script will run then produce a results.txt file on your desktop.
Open that file and copy all of the contents and paste them into your next reply in between code tags.

---

### Post by Its_Rishi on 2011-01-22
> **Quackers said:**
> You need to boot from the live cd/usb and select "try ubuntu" then, when the desktop loads, download the boot script to the desktop (not Downloads folder).
Then open up a terminal and run the command given by Rubi1200. The script will run then produce a results.txt file on your desktop.
Open that file and copy all of the contents and paste them into your next reply in between code tags.

I have already did wat u have said and after download and done the terminal process it has created result.txt file on desktop
but i can't understand wat to copy,wat to paste and where to...!!!
Can u tell me more clearly...?

---

### Post by Rubi1200 on 2011-01-22
Open the RESULTS.txt file. Copy the entire contents and then paste it into a new post here.

---

### Post by Quackers on 2011-01-22
No problem.
Open the results.txt file and highlight all its contents by dragging the pointer from top to bottom (making sure the scroller goes all the way to the bottom), then right-click on the highlighted area and select "copy".
Then in the forum click on New Reply on the left (not quick reply).
Then click on the # symbol in the toolbar of the new window. Two code tags will appear, with the cursor in between them. Right-click on that cursor and select "paste" and all your text will appear. Move to the end of the last [/code] tag and click the mouse there, then click on "submit reply"

---

### Post by Its_Rishi on 2011-01-23
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    78,140,159    78,140,097   7 HPFS/NTFS
/dev/sda2          78,140,160   312,560,639   234,420,480   f W95 Ext d (LBA)
/dev/sda5          78,140,223   156,280,319    78,140,097   7 HPFS/NTFS
/dev/sda6         156,280,383   234,420,479    78,140,097   7 HPFS/NTFS
/dev/sda7         234,420,543   312,560,639    78,140,097   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048    39,069,695    39,067,648  83 Linux
/dev/sdb2          39,070,141   156,300,457   117,230,317   5 Extended
/dev/sdb5          39,070,143    78,140,159    39,070,017   7 HPFS/NTFS
/dev/sdb6          78,140,223   117,210,239    39,070,017   7 HPFS/NTFS
/dev/sdb7         117,210,303   156,280,319    39,070,017   7 HPFS/NTFS
/dev/sdb8         156,282,880   156,300,457        17,578  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3CD89D2BD89CE484                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        EC94F6D494F6A06E                       ntfs       Random                        
/dev/sda6        A4C8F053C8F02568                       ntfs       Williams                      
/dev/sda7        EA5473DE5473ABC7                       ntfs       Hemanth                       
/dev/sda: PTTYPE="dos" 
/dev/sdb1        8cdc429f-cde6-495b-8abe-20943dc647cd   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        28FA7773FA773C5E                       ntfs                                     
/dev/sdb6        E24C99464C9915FF                       ntfs                                     
/dev/sdb7        C2FCA870FCA86101                       ntfs                                     
/dev/sdb8        ef7d1ce5-8ae9-416a-a634-9be1f7752388   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/8cdc429f-cde6-495b-8abe-20943dc647cd ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb5        /media/28FA7773FA773C5E  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 8cdc429f-cde6-495b-8abe-20943dc647cd
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 8cdc429f-cde6-495b-8abe-20943dc647cd
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 8cdc429f-cde6-495b-8abe-20943dc647cd
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=8cdc429f-cde6-495b-8abe-20943dc647cd ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 8cdc429f-cde6-495b-8abe-20943dc647cd
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=8cdc429f-cde6-495b-8abe-20943dc647cd ro single 
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
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 8cdc429f-cde6-495b-8abe-20943dc647cd
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 8cdc429f-cde6-495b-8abe-20943dc647cd
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a0723b84723b5dea
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=8cdc429f-cde6-495b-8abe-20943dc647cd /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb8 during installation
UUID=ef7d1ce5-8ae9-416a-a634-9be1f7752388 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


  15.3GB: boot/grub/core.img
   4.4GB: boot/grub/grub.cfg
   4.6GB: boot/initrd.img-2.6.35-22-generic
  15.3GB: boot/vmlinuz-2.6.35-22-generic
   4.6GB: initrd.img
  15.3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  da da da da da da da da  da da da da da da da da  |................|
00000010  ea da da da da da da da  da da da da da da da da  |................|
00000020  fa da da da da da da da  da da da da da da da da  |................|
00000030  0a da da da da da da da  da da da da da da da da  |................|
00000040  1a da da da da da da da  da da da da da da da da  |................|
00000050  2a da da da da da da da  da da da da da da da da  |*...............|
00000060  3a da da da da da da da  da da da da da da da da  |:...............|
00000070  4a da da da da da da da  da da da da da da da da  |J...............|
00000080  5a da da da da da da da  da da da da da da da da  |Z...............|
00000090  6a da da da da da da da  da da da da da da da da  |j...............|
000000a0  7a da da da da da da da  da da da da da da da da  |z...............|
000000b0  8a da da da da da da da  da da da da da da da da  |................|
000000c0  9a da da da da da da da  da da da da da da da da  |................|
000000d0  aa da da da da da da da  da da da da da da da da  |................|
000000e0  ba da da da da da da da  da da da da da da da da  |................|
000000f0  ca da da da da da da da  da da da da da da da da  |................|
00000100  da da da da da da da da  da da da da da da da da  |................|
00000110  ea da da da da da da da  da da da da da da da da  |................|
00000120  fa da da da da da da da  da da da da da da da da  |................|
00000130  0a da da da da da da da  da da da da da da da da  |................|
00000140  1a da da da da da da da  da da da da da da da da  |................|
00000150  2a da da da da da da da  da da da da da da da da  |*...............|
00000160  3a da da da da da da da  da da da da da da da da  |:...............|
00000170  4a da da da da da da da  da da da da da da da da  |J...............|
00000180  5a da da da da da da da  da da da da da da da da  |Z...............|
00000190  6a da da da da da da da  da da da da da da da da  |j...............|
000001a0  7a da da da da da da da  da da da da da da da da  |z...............|
000001b0  8a da da da da da da da  da da da da da da 00 01  |................|
000001c0  c1 ff 07 fe ff ff 02 00  00 00 41 29 54 02 00 fe  |..........A)T...|
000001d0  ff ff 05 fe ff ff 43 29  54 02 80 29 54 02 00 00  |......C)T..)T...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by Quackers on 2011-01-23
Try setting the bios to boot from the 80GB drive first. Then after choosing Ubuntu run ```
sudo update-grub
``` in the terminal. I think that should fix you up.

---

### Post by Its_Rishi on 2011-01-23
> **Quackers said:**
> Try setting the bios to boot from the 80GB drive first. Then after choosing Ubuntu run ```
sudo update-grub
``` in the terminal. I think that should fix you up.

As u said i set 80GB hard disk as default boot device but no use after saving and restarting the windows is starting even i set the other hard disk as default.

---

### Post by Quackers on 2011-01-23
Windows isn't installed on that drive. You have Windows type partitions but no system. Something went wrong, I suspect.

---

### Post by Its_Rishi on 2011-01-26
> **Quackers said:**
> Windows isn't installed on that drive. You have Windows type partitions but no system. Something went wrong, I suspect.
nopezzz i have a windows 7 on that drive!!!

---

### Post by Quackers on 2011-01-26
According to the boot script output, you have Windows 7 installed in sda1, which is the first partition of your 160BG hard drive.
You appear to have Windows partitions on sdb (your 80GB hard drive) but no Windows operating system.
Curiously the Windows partitions on sdb are almost exactly half the size of the Windows partitions on sda (sda6, sda6 and sda7). Have you copied them over to the other drive?

---

### Post by Its_Rishi on 2011-01-26
> **Quackers said:**
> According to the boot script output, you have Windows 7 installed in sda1, which is the first partition of your 160BG hard drive.
You appear to have Windows partitions on sdb (your 80GB hard drive) but no Windows operating system.
Curiously the Windows partitions on sdb are almost exactly half the size of the Windows partitions on sda (sda6, sda6 and sda7). Have you copied them over to the other drive?
No i don't have any other free space device to copy them!!!

---

### Post by Hindol on 2011-01-26
> **Its_Rishi said:**
> i have dual boot ububtu and windows 7 after upgrading windows 7 no boot options were appearing windows is starting automatically
how can i replace ubuntu boot loader and start my linux?

You just need to re-install grub (the Ubuntu bootloader). Can you specify what version of Ubuntu are you using? I need to know whether you are using grub or grub2. In grub I think I used 'setup-grub' command. And for grub2 it's 'grub-install'.

Just tell me your Ubuntu version and I will help you out.

---

### Post by rocthrttle on 2011-01-26
or you can get the alternative-installation cd and it will have repair menu tools to reinstall the grub through an simple menu. just get the matching ubuntu version to what you have installed to be safe. but i do recommend that you do it in terminal. if you need further instructions i can do it and write a procedure for you. just letting you know that it is possible. make sure you install the grub to sda1 where the BIOS is pointing.

---

### Post by Its_Rishi on 2011-01-27
> **Hindol said:**
> You just need to re-install grub (the Ubuntu bootloader). Can you specify what version of Ubuntu are you using? I need to know whether you are using grub or grub2. In grub I think I used 'setup-grub' command. And for grub2 it's 'grub-install'.
 
Just tell me your Ubuntu version and I will help you out.
 
Ubuntu 10.10

---

### Post by Its_Rishi on 2011-01-27
> **rocthrttle said:**
> or you can get the alternative-installation cd and it will have repair menu tools to reinstall the grub through an simple menu. just get the matching ubuntu version to what you have installed to be safe. but i do recommend that you do it in terminal. if you need further instructions i can do it and write a procedure for you. just letting you know that it is possible. make sure you install the grub to sda1 where the BIOS is pointing.
 
I do have ubuntu live cd i also tried with that but i can't find any repair option on live cd!!!

---

### Post by Quackers on 2011-01-27
> **Its_Rishi said:**
> No i don't have any other free space device to copy them!!!

Nevermind! You miss my point!

Do you see below, where it says operating sytem?
```
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    [COLOR="Red"]Operating System:  Windows 7[/COLOR]
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

```

It says Windows 7, yes?
(Actually, in the Boot files/dirs: field it also says /grldr, which shouldn't be there).

Well, in your other hard drive (sdb) all of those fields are empty in the Windows type partitions.[COLOR="Black"]This detail, and the lack of Windows boot files, would seem to indicate that Windows is not installed in any of those partitions.[/COLOR]

Which hard drive is set to boot first, in your bios?

---

### Post by rocthrttle on 2011-01-27
> **Its_Rishi said:**
> I do have ubuntu live cd i also tried with that but i can't find any repair option on live cd!!!

[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download)

[http://releases.ubuntu.com/maverick/ubuntu-10.10-alternate-i386.iso.torrent](http://releases.ubuntu.com/maverick/ubuntu-10.10-alternate-i386.iso.torrent)

there is an alternate cd for each version. those cd's have the install grub option i spoke of. please read entire post and relax. your in good shape and in good hands. this is a simple fix. with my method or another's. your almost there.

---

### Post by Hindol on 2011-01-29
> **Its_Rishi said:**
> Ubuntu 10.10

This tutorial will solve your problem - [http://aroundtheweb.info/2010/10/restorerecover-grub-2-ubuntu-10-10-maverick-meerkat-reinstalling-windows-xpvistawin7/](http://aroundtheweb.info/2010/10/restorerecover-grub-2-ubuntu-10-10-maverick-meerkat-reinstalling-windows-xpvistawin7/)

---

