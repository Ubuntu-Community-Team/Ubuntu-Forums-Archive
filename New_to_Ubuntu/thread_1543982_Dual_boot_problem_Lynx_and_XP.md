---
title: "Dual boot problem Lynx and XP"
date: 2010-08-01
forum: New to Ubuntu
---

### Post by dexter74 on 2010-08-01
Hi, I am a relatively new Ubuntu user with an installed Lucid Lynx dual booted with Windows XP.  My current drive setup is at 320GB hard drive partitioned into 2 where C is a system drive for booting and D is a data drive to store .... well data.  I have installed Ubuntu in C drive also where ubuntu is located in a folder in the Windows filesystem.  Now my problem is that when my computer is booted up the error "Disk boot failure insert system disk and press enter" comes up.  I have experienced this error before and have tried to fix it with the following

a) Boot into the system using the Windows recovery CD and in the recovery console ran fixboot and/or fixmbr with no success.
b) Currently I am able to access Windows and Ubuntu with the recovery CD inside my drive as the first boot device and letting it go through to the point where I can select which OS I am booting into.

What I want to happen is to be able to boot without having the recovery CD in the drive.  I guess there may be a problem with the MBR with GRUB2, but what do I know right?  I have had this problem before and my only solution then was to reinstall Windows and Ubuntu and I lost some files because of that and I don't want to do that again.

I would really appreciate any help I can get from anyone here so I can fix the boot sequence of my PC.  Thanks in advance.

---

### Post by henry cow on 2010-08-01
You need to get a complete answer from someone better than I, but Linux and Windows each need its own partition for a dual boot. You should consider about 10GB for the Ubuntu system and at least that much more for Ubuntu storage.

If you want a pure data partition, you should make it NTFS and also create a Windows boot partition of 20GB or so.

Partitioning scared me to death at the beginning, but it is necessary and has worked well for me a couple of times. Make sure your disk is very clean and completely defragged.

---

### Post by Windwalker52 on 2010-08-01
Let me know how this turns out. I have a XP/Ubuntu10.04LTS dual boot installed which runs fine except for Windows which needs it's own partition. btw. Ubuntu can find the Windows formatted partition and then you should be able to recover the files you were looking for. You mentioned that there was a second partition (drive D) which seems the logical place to install Ubuntu. But if you don't mind losing the XP installation and you just want the data files then reinstall or rebuild Ubuntu. You must however as has been mentioned partition for Ubuntu separate from XP. I don't think you will be able to recover the files using XP as easily as if you were using Ubuntu and Linux. just my opinion and may be some advice that will help you, good luck and let me know.
:popcorn:

---

### Post by oldfred on 2010-08-02
dexter74 welcome to the forums.

You do not have a true dual boot but a wubi install if you installed Ubuntu inside the window NTFS partition. Wubi boots thru the windows boot loader and is a file root.disk on the NTFS patition. Grub in wubi does not actually boot the system but shows it in the same way as a true dual boot with separate partitions.


To see your install:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by dexter74 on 2010-08-02
Hi OldFred, I followed your instructions and got these results below.

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/mapper/nvidia_ajegaecb

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

nvidia_ajegaecb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

nvidia_ajegaecb1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

nvidia_ajegaecb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

nvidia_ajegaecb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, 
                       nvidia_ajegaecb5 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   245,762,369   245,762,307   7 HPFS/NTFS
/dev/sda2         245,762,370   625,121,279   379,358,910   f W95 Ext d (LBA)
/dev/sda5         245,762,433   625,121,279   379,358,847   7 HPFS/NTFS


Drive: nvidia_ajegaecb ___________________ _____________________________________________________

Disk /dev/mapper/nvidia_ajegaecb: 1320.3 GB, 1320277817344 bytes
255 heads, 63 sectors/track, 160514 cylinders, total 2578667612 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/nvidia_ajegaecb1   *             63   245,762,369   245,762,307   7 HPFS/NTFS
/dev/mapper/nvidia_ajegaecb2        245,762,370   625,121,279   379,358,910   f W95 Ext d (LBA)
/dev/mapper/nvidia_ajegaecb5        245,762,433   625,121,279   379,358,847   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0       2cd0af20-bd80-400d-bac5-93b8f2cc78bc   ext4                                     
/dev/mapper/nvidia_ajegaecb1 A2DCB2BDDCB28B55                       ntfs                                     
/dev/mapper/nvidia_ajegaecb5 8CC0E380C0E36EC0                       ntfs       Data                          
/dev/mapper/nvidia_ajegaecb: PTTYPE="dos" 
/dev/sda                                                nvidia_raid_member                               
/dev/sdb                                                nvidia_raid_member                               
error: /dev/mapper/nvidia_ajegaecb2: No such file or directory
error: /dev/sda1: No such file or directory
error: /dev/sda2: No such file or directory
error: /dev/sda5: No such file or directory

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
nvidia_ajegaecb
nvidia_ajegaecb1
nvidia_ajegaecb5

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext4       (rw,errors=remount-ro)
/dev/mapper/nvidia_ajegaecb1 /host                    fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)


========================== nvidia_ajegaecb1/boot.ini: ==========================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\wubildr.mbr = "Ubuntu" 

================== nvidia_ajegaecb1/Wubi/boot/grub/grub.cfg: ==================

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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-21-generic" {
    insmod ntfs
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set a2dcb2bddcb28b55
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-21-generic root=/dev/mapper/nvidia_ajegaecb1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, Linux 2.6.32-21-generic (recovery mode)" {
    insmod ntfs
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set a2dcb2bddcb28b55
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-21-generic root=/dev/mapper/nvidia_ajegaecb1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/mapper/nvidia_ajegaecb1)" {
    insmod ntfs
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set a2dcb2bddcb28b55
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

======================= nvidia_ajegaecb1/Wubi/etc/fstab: =======================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=========== nvidia_ajegaecb1/Wubi: Location of files loaded by Grub: ===========


  11.8GB: boot/grub/grub.cfg
   8.8GB: boot/initrd.img-2.6.32-21-generic
   8.8GB: boot/vmlinuz-2.6.32-21-generic
   8.8GB: initrd.img
   8.8GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1


Unknown BootLoader  on sda2


Unknown BootLoader  on sda5


Unknown BootLoader  on nvidia_ajegaecb2



=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/mapper/nvidia_ajegaecb2: No such file or directory
hexdump: /dev/mapper/nvidia_ajegaecb2: No such file or directory

```

---

### Post by dexter74 on 2010-08-02
From what I've understood here in the posts is that my current setup is not a true dual boot install so would you be so kind enough to let me know how I can make it such that it is a true dual boot.  I wouldn't mind removing wubi and setting it up to be a true dual boot.  I haven't used wubi that much so there's no data there that I am concerned to lose yet.  My main concern right now is to make sure Windows does boot up without having to put in the recovery CD, once Windows can boot up by itself I can re-install Ubuntu in its' own partition.  My apologies for the newbie approach as I am a greenhorn to the disk/OS management side of PC.  Thanks in advance.

---

### Post by oldfred on 2010-08-02
You seem to have two drives but the second sdb 1320GB is set up as Nvidia RAID or logical volume? The device mapper changes how the drive is set up and your XP is also in that and makes it more complex. I am not familiar with the nvidia mapper setup.

Grub/Ubuntu used only work with the server install for that type of set up but now it think it is ok.  I do not know if gparted will see it as a standard drive that you can edit partitions or not.

What data do you have where will make a big difference. You will have to back up something and or shrink one of the NTFS partitions to make room for / (root), swap and perhaps /home. You can move data from the /home in wubi to the new partition if you have anything you want to save. It may be easier to install to your sda which does not have the nvidia mapper set up, but what is in those partititons?

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

HOWTO: migrate wubi install to partition by bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

Overview of manual conversion but see bcbc's instructions above:
Old conversion LVPM, see Alternative Instructions 
[http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591)
1. Create 3 new partitions with the Partition Manager : a 10-20 GB (ext3 format) partition to use as root (/), a ~2 GB (equal to RAM size) (swap format) partition to use as swap, and make the rest a (ext3 format) partition to use as /home.
2. Boot back into the Wubi-generated Ubuntu install, mount the new partition that will be used as /home in the dedicated-partition install to /media/disk, and copy the contents of the current /home recursively over to the new partition:
rsync -avx /home/ /media/disk
Additionally, if you want to avoid the hassle of manually reinstalling all the packages you currently have installed, run:
dpkg --get-selections > selections.dpkg
That'll generate a list of packages you have installed (back up that list to somewhere safe); after reinstalling the system, just open Synaptic, go file > read markings, select that file that was generated (selections.dpkg), press apply, and it'll reinstall all the software you have on your current system ).
Repair LVPM conversion:
[http://ubuntuforums.org/showthread.php?t=1501751](http://ubuntuforums.org/showthread.php?t=1501751)

---

