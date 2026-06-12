---
title: "Partition question"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by Clever_Username on 2010-05-04
First off I'd like to say the extrordinary level of support for Ubuntu is one of the main reasons I decided to go with it and why I recommend it to others.
But alas, I think I did something stupid and I was hoping for some direction in fixing it.
I was running Win2K Pro when I downloaded Partition Magic and chopped the hard drive in half. I used Wubi (I don't have a cd burner) to install Ubuntu 9.1 on the other half of the hard disk. I ordered the live cd and when it arrived I installed. When I was running a backup yesterday, I noticed only 10 gigs of total disk space on the new install of Ubuntu.
When I reboot, Grub loads the dual boot screen. When I choose Windows, it takes me to another dual boot screen. So I'm pretty sure I have 3 operating systems on 1 hard disk here. Windows has 20 gigs, the first version of Ubuntu has 10 and then the second has 10. It's not an issue at this point, but I would like to know how to fix it.
How do I tell which version of Ubuntu is which? Some kind of time stamp maybe?
Secondly, how do I get rid of the Wubi version of Ubuntu without damage to the live cd version?
Thanks in advance for any help

---

### Post by psusi on 2010-05-04
Wubi installs to a file inside the windows partition, not to its own partition.  Sounds like you then installed a normal system on its own partition.  To remove wubi just uninstall it from the add/remove programs control panel in windows.

---

### Post by spydeyrch on 2010-05-04
I would agree with psusi. It looks like this is what happened:

Installed windows

Via Wubi installed ubuntu. When ubuntu is installed via wubi, it adds an OS line to the windows bootloader menu.

Installed ubuntu to it's own partition via live cd, this would be the "traditional" dual boot setup. By installing ubuntu to it's own partition, you also installed the GRUB boot menu. In the grub boot menu it show ubuntu (the second one that you installed via the live cd) and windows 7 (along with a few other options such as safe mode, etc). If you select the windows seven option from the GRUB boot menu, it takes you to the windows 7 boot menu, not directly to windows 7. Due to having installed ubuntu via wubi from within windows 7, you will still see that ubuntu is still an option in the windows 7 boot menu.

The only way to get rid of that boot option located in/on the windows 7 boot menu is to uninstall ubuntu/wubi via the add/remove programs from within windows 7. This will not affect the ubuntu install that you did via the live cd as it is on it's own partition and not seen as merely another program by windows. Wubi is treated as a program from within windows.

Hopefully that makes sense. So just uninstall WUBI/ubuntu from within windows 7 add/remove programs and you should be good.

-Spydey :D

---

### Post by ranch hand on 2010-05-04
I would pull up gparted on your Live CD and take a look at your partitions.  This should tell you what is going on there.

If you are having trouble booting to either the new install of Ubuntu or MS please run this either from your Ubuntu install or your live CD;

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

and post the results text that will be on your desktop here.

---

### Post by garvinrick4 on 2010-05-04
I have had this happen to me before by removing WUBI from add and remove programs in windows instead of from uninstall from inside of its folder in C: drive. It left (wublder) or something close to that in the Windows boot manager. So it chainloaded from one to the other and had 2 grubs. You can look in Windows.
Code:

bcdedit

If you see the wublder still there.
code:

bcdedit delete { identifier number}

and it will be gone from the Windows boot manager.

*Sometimes removing from add and remove programs works and sometimes it leaves itself in Windows boot manager but why take the chance use
the Uninstall in the Wubi folder right next to Users in C: drive.

---

### Post by Clever_Username on 2010-05-05
When I recieved the cd, I loaded Windows and formated the logical drive thru Windows. I then loaded the cd. Right now, when I load Ubunutu, I see a 10 G and an 8.2 G filesystem. The 10 G is the Windows file system ( shrank the partition from 20 gigs). The 8.2 is Ubuntu. My issue is, I have a 40 gig hd. And I don't understand why Ubunutu isn't see the other 20 gigs or so. I can understand it not seeing 10 gigs because I haven't increased the partition size of Ubuntu to include the 10 gigs I took away from Windows. I'm just a little nervous about doing that because I still don't have the first problem figured out. 
A guy at work is telling me to just wipe everything out and reinstall, but then a person doesn't learn anything by just sticking in a disk. There has to be a better way. 
Still working on getting the output for that command Ranch Hand.

I did manage to get the output of an fdisk -l. I hope this helps.

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd939d939

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1276    10249438+   7  HPFS/NTFS
/dev/sda2            2551        4865    18595237+   f  W95 Ext'd (LBA)
/dev/sda5            2551        3547     8008371    c  W95 FAT32 (LBA)
/dev/sda6            3548        4803    10088788+  83  Linux
/dev/sda7            4804        4865      497983+  82  Linux swap / Solaris

---

### Post by Clever_Username on 2010-05-05
Here is the output from boot_info_script.sh:

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/menu.lst /boot.ini /ntldr /NTDETECT.COM 
                       /wubildr.mbr /wubildr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd939d939

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    20,498,939    20,498,877   7 HPFS/NTFS
/dev/sda2          40,965,750    78,156,224    37,190,475   f W95 Ext d (LBA)
/dev/sda5          40,965,813    56,982,554    16,016,742   c W95 FAT32 (LBA)
/dev/sda6          56,982,618    77,160,194    20,177,577  83 Linux
/dev/sda7          77,160,258    78,156,224       995,967  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        ACE8C49AE8C463E4                       ntfs                                     
/dev/sda5        44D4-7A64                              vfat                                     
/dev/sda6        262fd3b0-d584-44a7-a6a2-3d3b9fcaffff   ext4                                     
/dev/sda7        315488de-da04-4598-8b18-b44f54562f81   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)
/dev/sda5        /media/44D4-7A64         vfat       (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,sh
ortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda1        /media/ACE8C49AE8C463E4  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blk
size=4096)


=========================== sda1/boot/grub/menu.lst: ===========================

# This is a sample menu.lst file. You should make some changes to it.
# Added items for installing GRUB [ which is on your DOS drive C: ] to MBR

color black/cyan yellow/cyan
timeout 60
default 0

title Install Linux
kernel (hd0,0)/boot/vmlinuz   
initrd (hd0,0)/boot/initrd.lz    

title DOS/Win9x/Me/NT/2K/XP on (hd0,0)
chainloader (hd0,0)+1
rootnoverify (hd0)

title Mandrake Linux on (hd0,7)
kernel (hd0,7)/boot/vmlinuz root=/dev/hda8 quiet devfs=mount acpi=ht vga=788
initrd (hd0,7)/boot/initrd.img

title Red Hat Linux on (hd0,8)
kernel (hd0,8)/boot/vmlinuz root=/dev/hda9

title floppy on (fd0)
chainloader (fd0)+1
rootnoverify (fd0)

title memdrive duplicated from floppy image file (hd0,0)/sbm.bin
map --mem (hd0,0)/sbm.bin (fd0)
map --hook
chainloader (fd0)+1
rootnoverify (fd0)

title memdrive based on win98 partition (hd0,6)
map --mem (hd0,6)+1 (hd0)
# map --mem (hd0,0)/win98.gz (hd0)
map --hook
chainloader (hd0)+1
rootnoverify (hd0)

title DOS/Win9x on (hd1,0) -- Do not use this to start WinNT/2K/XP
pause Warning: drive map used. Press any key to start DOS/Win9x on (hd1,0)...
map (hd1) (hd0)
map (hd0) (hd1)
root (hd1,0)
makeactive
chainloader (hd1,0)+1
rootnoverify (hd0)

title install GRUB on (hd0,0) to MBR (hd0) and reboot. Password: danger
pause You requested to install GRUB onto MBR. We highly recommend you NOT to do so, basically for two rea
sons: 1. For some non-MS-compatible boot loaders(in case you might be using), the install is INDEED dange
rous and may cause your whole disk(and all your operating systems on it) unaccessible. 2. Even if you are
 using(in MBR)an MS-compatible boot loader such as LILO and GRUB, you may encounter problems like hard-di
sk-boot-failure when you move or delete the /boot/grub/stage2 file, or even when disk defragmentation ope
rations are made. Press any key to continue...
pause A password prompt will confirm that you want the operation anyway. Press any key to continue...
password danger
pause This will install GRUB in (hd0,0)/boot/grub/ to MBR. Press any key to begin...
root (hd0,0)
setup (hd0)
pause GRUB install OK! Press any key to reboot your machine...
reboot

title install GRUB on (hd0,1) to MBR (hd0) and reboot. Password: danger
pause You requested to install GRUB onto MBR. We highly recommend you NOT to do so, basically for two rea
sons: 1. For some non-MS-compatible boot loaders(in case you might be using), the install is INDEED dange
rous and may cause your whole disk(and all your operating systems on it) unaccessible. 2. Even if you are
 using(in MBR)an MS-compatible boot loader such as LILO and GRUB, you may encounter problems like hard-di
sk-boot-failure when you move or delete the /boot/grub/stage2 file, or even when disk defragmentation ope
rations are made. Press any key to continue...
pause A password prompt will confirm that you want the operation anyway. Press any key to continue...
password danger
pause This will install GRUB in (hd0,1)/boot/grub/ to MBR. Press any key to begin...
root (hd0,1)
setup (hd0)
pause GRUB install OK! Press any key to reboot your machine...
reboot

title mandrake ISO install (using vmlinuz and all.rdz)
pause Installing an OS is dangerous because it may overwrite all your disks(and partitions)! A password p
rompt will confirm that you want the operation anyway. Press any key to continue...
password danger
pause This will install Mandrake using iso files. Press any key to continue...
kernel (hd0,0)/vmlinuz ramdisk_size=128000 acpi=ht vga=788 splash=silent automatic=method:disk
initrd (hd0,0)/all.rdz


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINNT
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows 2000 Professional" /fastdetect
C:\wubildr.mbr = "Ubuntu"

=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/menu.lst
    ??GB: boot/grub/stage2
    ??GB: boot/initrd.lz
    ??GB: boot/vmlinuz

=========================== sda6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,6)
search --no-floppy --fs-uuid --set 262fd3b0-d584-44a7-a6a2-3d3b9fcaffff
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 262fd3b0-d584-44a7-a6a2-3d3b9fcaffff
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=262fd3b0-d584-44a7-a6a2-3d3b9fcaffff ro   quiet
 splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 262fd3b0-d584-44a7-a6a2-3d3b9fcaffff
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=262fd3b0-d584-44a7-a6a2-3d3b9fcaffff ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows 2000 Professional (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set ace8c49ae8c463e4
    drivemap -s (hd0) ${root}
    chainloader +1
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=262fd3b0-d584-44a7-a6a2-3d3b9fcaffff /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=315488de-da04-4598-8b18-b44f54562f81 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


  31.8GB: boot/grub/core.img
  31.8GB: boot/grub/grub.cfg
  30.0GB: boot/initrd.img-2.6.31-14-generic
  31.5GB: boot/vmlinuz-2.6.31-14-generic
  30.0GB: initrd.img
  31.5GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb

---

### Post by oldfred on 2010-05-05
You still have wubi in sda1 and somehow a menu.lst in the windows partition that looks like it has other info in it??

Boot files/dirs: [COLOR=DarkRed]  /boot/grub/menu.lst[/COLOR] /boot.ini /ntldr /NTDETECT.COM 
                       /wubildr.mbr /wubildr

And you have a install in sda6 root and sda7 swap. 

If you have info in your wubi that you want to copy to your install you can mount the root.disk file and copy the data from Ubuntu. Then you should uninstall wubi from windows. Since it is XP you cannot use bcdedit (Vista/7) and may have to edit boot.ini directly to remove the wubi boot entry.

---

### Post by Clever_Username on 2010-05-08
Well, I tried uninstalling WUBI from Windows and it said it was already gone. I ended up just wiping out everything (Windows included) and reinstalling Ubunu. Everything is running great now. Thanks so much

---

