---
title: "WinXP won't boot from menu in dual-boot, dual hard-drive WinXP/Ubuntu 10.10 system"
date: 2011-02-01
forum: New to Ubuntu
---

### Post by robstan68 on 2011-02-01
The system has two hard drives, one SATA (sdb) and one IDE (sda). WinXP has been installed on the SATA drive for quite sometime. Ubuntu 10.10 was recently installed on the IDE drive from a live CD. WinXP will boot successfully if its hard drive is listed first in the BIOS hard drive list. If the IDE drive is listed first in the BIOS hard drive list, the GRUB 2 menu comes up with the appropriate choices. If the Ubuntu choice is selected, Ubuntu boots successfully, but if the WinXP choice is selected, the following statement appears: A disk error occurred Press Ctrl+Alt+Del to restart.

From my admittedly inexperienced position as a newcomer to Linux, I'm unable to detect the problem. Any assistance would be much appreciated.

The Boot Info Script is shown below:

```
              Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

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

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       976,895       974,848  83 Linux
/dev/sda2             976,896    40,038,399    39,061,504  83 Linux
/dev/sda3          40,038,400    49,803,263     9,764,864  82 Linux swap / Solaris
/dev/sda4          49,805,310   234,440,703   184,635,394   5 Extended
/dev/sda5          49,805,312   234,440,703   184,635,392  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    40,965,749    40,965,687   7 HPFS/NTFS
/dev/sdb2          40,965,750   312,560,639   271,594,890   f W95 Ext d (LBA)
/dev/sdb5          40,965,813   176,763,194   135,797,382   7 HPFS/NTFS
/dev/sdb6         176,763,258   312,560,639   135,797,382   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        f66e6730-eac4-40a2-8e03-bdc9466443c3   ext4                                     
/dev/sda2        8a5dce92-1594-4f69-acb0-9f94eb656084   ext4                                     
/dev/sda3        0ce0f52f-cdc3-48d9-b1c0-4411ea6173f5   swap                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        f75a09ad-1850-474d-a7a7-f097c63d3403   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        FE48D4AC48D464C5                       ntfs       Windows XP                    
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        0AB004A5B00498F9                       ntfs                                     
/dev/sdb6        E230079A300774B7                       ntfs                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda1        /boot                    ext4       (rw,commit=0)
/dev/sda5        /home                    ext4       (rw,commit=0)


============================= sda1/grub/grub.cfg: =============================

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
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 8a5dce92-1594-4f69-acb0-9f94eb656084
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set f66e6730-eac4-40a2-8e03-bdc9466443c3
set locale_dir=($root)/grub/locale
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set f66e6730-eac4-40a2-8e03-bdc9466443c3
    linux    /vmlinuz-2.6.35-24-generic root=UUID=8a5dce92-1594-4f69-acb0-9f94eb656084 ro   quiet splash
    initrd    /initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set f66e6730-eac4-40a2-8e03-bdc9466443c3
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /vmlinuz-2.6.35-24-generic root=UUID=8a5dce92-1594-4f69-acb0-9f94eb656084 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set f66e6730-eac4-40a2-8e03-bdc9466443c3
    linux    /vmlinuz-2.6.35-22-generic root=UUID=8a5dce92-1594-4f69-acb0-9f94eb656084 ro   quiet splash
    initrd    /initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set f66e6730-eac4-40a2-8e03-bdc9466443c3
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /vmlinuz-2.6.35-22-generic root=UUID=8a5dce92-1594-4f69-acb0-9f94eb656084 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set f66e6730-eac4-40a2-8e03-bdc9466443c3
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set f66e6730-eac4-40a2-8e03-bdc9466443c3
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set fe48d4ac48d464c5
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

=================== sda1: Location of files loaded by Grub: ===================


    .2GB: grub/core.img
    .2GB: grub/grub.cfg
    .0GB: initrd.img-2.6.35-22-generic
    .0GB: initrd.img-2.6.35-24-generic
    .0GB: vmlinuz-2.6.35-22-generic
    .0GB: vmlinuz-2.6.35-24-generic

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=8a5dce92-1594-4f69-acb0-9f94eb656084 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=f66e6730-eac4-40a2-8e03-bdc9466443c3 /boot           ext4    defaults        0       2
# /home was on /dev/sda5 during installation
UUID=f75a09ad-1850-474d-a7a7-f097c63d3403 /home           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=0ce0f52f-cdc3-48d9-b1c0-4411ea6173f5 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


    .5GB: initrd.img
    .5GB: initrd.img.old
    .5GB: vmlinuz
    .5GB: vmlinuz.old

================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 50 01 0b 00 00  |...........P....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by Mark Phelps on 2011-02-02
Call it deja vu if you wish, but your post seems awfully familiar!

Anyway, since you can boot XP OK when booting from that drive, it's not an XP or drive problem per se.

You probably just need to update the GRUB entries.

To do that, boot into Ubuntu, open a terminal, and enter "sudo update-grub".  That will regenerate the GRUB menu.

When you then reboot, you should be able to launch XP OK.

---

### Post by robstan68 on 2011-02-02
Mark,
 
Thanks for the response. I tried your suggestion of using the command "sudo update-grub". Unfortunately, it didn't work. 
 
At the GRUB2 manual site: [http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/) I found the following and wonder if it has some bearing on the problem, particularly the caution emphasized in red.
 
[LEFT][FONT=CMBX12][SIZE=4][FONT=CMBX12][SIZE=1]4.2.3 DOS/Windows[/SIZE][/FONT][/SIZE][/FONT]
[FONT=CMR10][FONT=CMR10][SIZE=1]GRUB cannot boot DOS or Windows directly, so you must chain-load them (see section 4.1.2 [Chain-loading], page 13). However, their boot loaders have some critical deficiencies, so it may not work to just chain-load them. To overcome the problems, GRUB provides you wih two helper functions. If you have installed DOS (or Windows) on a non-first hard disk, you have to use the disk swapping technique, because that OS cannot boot from any disks but the first one. The workaround used in GRUB is the command drivemap (see Section 13.3.12 [drivemap], page 51), like this: drivemap -s (hd0) (hd1). This performs a virtual swap between your first and second hard drive. [/SIZE][/FONT][/FONT][FONT=CMB10][FONT=CMB10][SIZE=1][COLOR=red]Caution: [/COLOR][/SIZE][/FONT][/FONT][FONT=CMR10][FONT=CMR10][SIZE=1][COLOR=red]This is effective only if DOS (or Windows) uses BIOS to access the swapped [/COLOR][/SIZE][/FONT][/FONT][FONT=CMR10][FONT=CMR10][SIZE=1][COLOR=red]disks. If that OS uses a special driver for the disks, this probably won’t work.[/COLOR][/SIZE][/FONT][/FONT][/LEFT]

---

### Post by Mark Phelps on 2011-02-03
That is true because, in some situations, people have add-in cards with disk controllers in their PCs and GRUB (according to that article) then won't be able to boot their PC.

When you said it didn't work, you should provide some details of what happened.

Also, although you may have tried this, boot with just the Ubuntu drive attached and confirm that you can boot into Ubuntu.

---

### Post by robstan68 on 2011-02-03
> **Mark Phelps said:**
> That is true because, in some situations, people have add-in cards with disk controllers in their PCs and GRUB (according to that article) then won't be able to boot their PC.

When you said it didn't work, you should provide some details of what happened.

Also, although you may have tried this, boot with just the Ubuntu drive attached and confirm that you can boot into Ubuntu.

When I say it didn't work, I mean that the result is identical with the situation described in my initial post, i.e. when I choose the Winxp menu option, the result is the message "A disc read error has occurred Press Ctrl+Alt+Del to restart".

I can, indeed, boot into Ubuntu with just the Ubuntu drive attached.

Thanks for working with me on this.

---

### Post by quesadilla on 2011-02-03
if you still want to run windows, you can always use virtualzation software like virtualbox.

---

### Post by YesWeCan on 2011-02-03
I think the problem here *may* be that the XP HD is not the first boot disk. I know Vista gets upset, maybe XP does too. Windows 7 is fine.
It could be this is specific to putting Ubuntu on IDE. Ity may be if both XP and Ubuntu disks are SATA it will be ok. Just guessing here.
If so, this is a restriction of the MS bootloader. You will have to put up with selecting XP from the bios rather than from the Grub menu.

---

### Post by oldfred on 2011-02-03
Mixed PATA & SATA drives seem to have this issue more than all one or the other.

Your windows thinks it is on the first disk or drive 0.
multi(0)disk(0)[COLOR=Red]rdisk(0)[/COLOR]partition(1)\WINDOWS="Microsoft Windows

The drivemap command in grub is supposed to reverse the boot entry so windows thinks it is first.

Grub sees it as the second drive or hd1.

menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='([COLOR=Red]hd1[/COLOR],msdos1)'
    search --no-floppy --fs-uuid --set fe48d4ac48d464c5
    drivemap -s (hd0) ${root}
    chainloader +1
}

But the drivemap should reverse the root entry. Not sure why it is not working.
You could copy boot stanza to 40_custom and see if other versions work or install grub to the windows drive, run the sudo update grub  and boot that. The boot drive is also hd0 in grub and then it still should be drive 0.

---

### Post by robstan68 on 2011-02-03
> **YesWeCan said:**
> I think the problem here *may* be that the XP HD is not the first boot disk. I know Vista gets upset, maybe XP does too. Windows 7 is fine.
It could be this is specific to putting Ubuntu on IDE. Ity may be if both XP and Ubuntu disks are SATA it will be ok. Just guessing here.
If so, this is a restriction of the MS bootloader. You will have to put up with selecting XP from the bios rather than from the Grub menu.
 
I'm inclined to agree that the major difficulty may be not having WinXP on the first hard drive. It's obvious that the chainloading feature of Grub 2 doesn't work with this arrangement.
 
I'm in the process of deciding what to do. From my experience with Ubuntu 10.10 to this point, it looks to have all of the capabilities necessary for my purposes, so a total abandonment of WinXP is within the realm of possibility. For the short term, I can certainly use the BIOS for operating system selection even though it's a bit inconvenient.
 
I despise being defeated by a technical problem, however, so will continue to puzzle over this. 
 
All help is appreciated.

---

### Post by YesWeCan on 2011-02-03
[QUOTE=robstan68]I despise being defeated by a technical problem, however, so will continue to puzzle over this.[/QUOTE]
I know that feeling.  :p

---

### Post by robstan68 on 2011-02-03
> **oldfred said:**
> Mixed PATA & SATA drives seem to have this issue more than all one or the other.
 
Your windows thinks it is on the first disk or drive 0.
multi(0)disk(0)[COLOR=red]rdisk(0)[/COLOR]partition(1)\WINDOWS="Microsoft Windows
 
The drivemap command in grub is supposed to reverse the boot entry so windows thinks it is first.
 
Grub sees it as the second drive or hd1.
 
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
insmod part_msdos
insmod ntfs
set root='([COLOR=red]hd1[/COLOR],msdos1)'
search --no-floppy --fs-uuid --set fe48d4ac48d464c5
drivemap -s (hd0) ${root}
chainloader +1
}
 
But the drivemap should reverse the root entry. Not sure why it is not working.
You could copy boot stanza to 40_custom and see if other versions work or install grub to the windows drive, run the sudo update grub and boot that. The boot drive is also hd0 in grub and then it still should be drive 0.
 
oldfred,
 
Your astute observation highlighted in red coupled with your comment regarding SATA/PATA complications adds more intrigue to the mix.
 
Installing Grub to the WinXP drive should probably be considered. However my current level of Grub knowledge will have to be increased for me to attempt this as I am not at all proficient with either Grub or Linux and their commands. If possible, could you give me some information as to how this should be done in a safe manner? As I am still having to use the WinXP drive, I don't want to mess it up through my own incompetence.
 
Thanks for your insight.

---

### Post by oldfred on 2011-02-04
I consider this an experiment or a kluge to make it work with the mixed IDE/SATA configuration. I always prefer to have the boot loader of a system in that drive's MBR, so worst case each drive can be separately booted.

If you can boot into Ubuntu, you just install grub to the MBR, you do not have to use the liveCd install procedure. The only actual difference is you do not have to mnt the Ubuntu partition as you are in it so it uses your working install as the location of the rest of grub.

#reinstall from working (not liveCD) system - first find Ubuntu drive make sure IDE drive with windows is still sdb in Ubuntu:
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

Then in BIOS change to boot the IDE drive.

You can easily reinstall the windows boot loader with fixMBR from a windows CD or install lilo with the Ubuntu liveCD or from Ubuntu to the MBR only and it will boot windows.

---

### Post by robstan68 on 2011-02-04
> **oldfred said:**
> I consider this an experiment or a kluge to make it work with the mixed IDE/SATA configuration. I always prefer to have the boot loader of a system in that drive's MBR, so worst case each drive can be separately booted.

If you can boot into Ubuntu, you just install grub to the MBR, you do not have to use the liveCd install procedure. The only actual difference is you do not have to mnt the Ubuntu partition as you are in it so it uses your working install as the location of the rest of grub.

#reinstall from working (not liveCD) system - first find Ubuntu drive make sure IDE drive with windows is still sdb in Ubuntu:
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

Then in BIOS change to boot the IDE drive.

You can easily reinstall the windows boot loader with fixMBR from a windows CD or install lilo with the Ubuntu liveCD or from Ubuntu to the MBR only and it will boot windows.

Oldfred,

Your instructions worked flawlessly. The system is bootable into either Ubuntu or WinXP from the menu on the WinXP drive. 

This experience has had a multi-fold effect. It has demonstrated the validity of the Linux OS, the depth of knowledge of the Ubuntu community and the willingness to share the knowledge, and it has served as an inspiration to me to become more knowledgeable.

Thanks to everyone who contributed on this thread, especially oldfred!

---

### Post by Lt. Surge on 2011-02-04
Dammit! I was about to sugest the BIOS fix :lolflag:

---

### Post by oldfred on 2011-02-04
Glad it worked. :)

---

