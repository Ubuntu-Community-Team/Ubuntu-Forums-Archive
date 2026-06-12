---
title: "Partitioning a 500 GiB HDD for Ubuntu and Win7"
date: 2010-11-17
forum: New to Ubuntu
---

### Post by manuganji on 2010-11-17
I have a new 500 GiB internal HDD.I want to use it to run both Ubuntu 10.10 and Win 7. I don't have a win7 DVD with me but I have the back up media (2 DVDs) which I made at factory state. When I use them to install, they make three partitions to install Win7 and leave me with 400 GB unallocated space to install Ubuntu.The partition style is MBR so I can't make that 400 GB data available in Win7 if I install Ubuntu in the whole of that space. Please help me on how to install Win7 in a 30 GB drive, Ubuntu in a 10 GB drive through a GPT style partition and way to split the 400 GB space into at least 3 different drives. 

Thanks a lot in advance.

---

### Post by bodhi.zazen on 2010-11-17
I can not tell from your pose exactly what you are wanting to do.

You can partition your disk with Windows or with almost any live CD. Linux uses gparted.

See:

[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

[http://gparted.sourceforge.net/display-doc.php?name=help-manual&lang=C](http://gparted.sourceforge.net/display-doc.php?name=help-manual&lang=C)

---

### Post by oldfred on 2010-11-17
win7 will only boot from gpt partitons if you have an efi BIOS. 

But with MBR you can create an extended partition and add many additional partitions. Linux will boot from the logical partitions and Windows will read a NTFS partition in a logical if you want.

---

### Post by tad1073 on 2010-11-17
format 100gb as ntfs for W7, 50gb as ext4 for linux and the rest partition as ntfs so you can access if from both W7 and Ubuntu

---

### Post by oldfred on 2010-11-17
Everyone has there own suggestions on partitions and no one is really wrong. It depends on how you are going to use system. And as drives fill up you needs change.

My standard recommendation:
Ubuntu's standard install is just / & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up. Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM.

But if creating a larger NTFS partition for shared data /home does not have to be large or even separate a separate partition (becomes part of /root). I understand 30GB is about the minimum for win7, you should make it 50GB or more.

The advantage of a separate partition for /home is if you plan on reinstalling Ubuntu rather than upgrading all your user settings are in /home and not overwritten if you so specify. If all your data is elsewhere /home is small and easily backed up and restored. My home is only about 1GB but I aggressively move data & some normally hidden data folders to my /data (ext3) partition.

---

### Post by manuganji on 2010-11-18
Thanks a LOT for all the replies! 

First, on an empty hard disk, I tried to install Windows with the back up media. It made a MBR style partition table. It had a 125 Mb partition called OEM healthy, then an unallocated 5.6 Gb space, then Windows in 100 Gb, then a 400 Gb unallocated space. I tried to make a partition for Ubuntu which it refused saying 'the disk already has maximum no. of partitions allowed'. 
When I checked the disk in Ubuntu, it had a 1 KB partition between the Windows and the unallocated space of 400 Gb. It had some name I dont remember, but I couldn't delete it.
So I read a little about GPT partition scheme, I logged in with Ubuntu live CD, made a new GPT partition table which means I lost the last Windows installation. I made the following allocations starting from left.
15 Gb - ext4 labelled Ubuntu,
30 Gb - NTFS labelled OS,
10 Gb - NTFS labelled RECOVERY,
180 Gb - NTFS labelled Dump1,
100 Gb - NTFS labelled Dump2,
159 Gb - NTFS labelled Dump3,
6.1 Gb - Swap partition.

After this, I could mount the drives Dump1,2,3 and OS in the media. Then I installed Ubuntu into the first ext4 partition. Then, I tried installing Windows again with the back up media which failed saying there was no space. Now I 'GUESSED' ( pardon the sin :) ) that if I make the flags for Ubuntu partition and OS partition as 'boot' then that'll direct the backup media to install Windows in OS. But it installed Windows in the 180 Gb Dump1 partition! 


> **oldfred said:**
> win7 will only boot from gpt partitons if you have an efi BIOS. 

But with MBR you can create an extended partition and add many additional partitions. Linux will boot from the logical partitions and Windows will read a NTFS partition in a logical if you want.

Now how do we know if I have efi BIOS? 

I see most of you here suggest I go for an extended partition. I'll try to do that. Some thing is bothering me, what's that OEM partition? Is it required?

I'm sry I'm giving such a big reply.

---

### Post by cascade9 on 2010-11-18
I dont see why you've made 5 NTFS partitions. I'd just use 2 (OS + data).

BTW, GiB is wrong. Thats the stupid 'new' way to measure memory sizes, as its binary (1 GiB = 1073741824bytes). HDDs have always been sold in 'fake', non-binary GB (1'fake' GB = 1000000000bytes). 

Stipid GiB/GB, they should have just kept GB and made the HDD manufacturers sell them by 'real' GB, not the fake 'we make our HDDs look bigger'  GB.

---

### Post by Quackers on 2010-11-18
The oem partition is likely to have the first 2 Windows 7 boot files in it. If you delete that partition W7 will not boot up unless you then repair the installation - but that would require an installation/repair disc (not a recovery disc). However repair discs are available for download - have no link for one though.

---

### Post by manuganji on 2010-11-18
Ok people, I have erased the whole hard disk and installed Win7 with the back up media. The current state is as it's in this [screenshot]("http://bayimg.com/fAanlaaDk").

That 131 MB partition looks as OEM partition in Win7. The OS is the new Windows installation I made. Please help how to partition now so that I can limit Windows files to 30 GB and Ubuntu to 15 GB and keep the rest of the space available in both the partitions.

---

### Post by oldfred on 2010-11-18
Post this so we can see what system files are in what partition. Does windows boot ok with your reinstall?

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

You have efi with apple, windows servers and some new motherboards. I wanted to buy an efi board a couple of years ago and only one or two very high priced ones were available. When you go into BIOS/EFI it should tell you whether you also have an efi mode. You can use gpt with BIOS but cannot boot windows. I have windows on one drive and gpt on another just to learn about it. (Not much difference on small drive).

---

### Post by Mark Phelps on 2010-11-18
To shrink the Win7 OS partition, just run the Win7 Disk Management utility, click on that partition, select Shrink Volume, and tell it how many bytes to remove.  It's VERY FAST!

I did that recently an a new install for a client and shrunk a 1TB partition to 30GB in less than a minute.  Really!

---

### Post by manuganji on 2010-11-19
ok, I some how managed to make an extended partition. Then I installed Ubuntu in it first. Flagged one of the primary NTFS partitions as 'boot' and ran the back up media I had with me. It successfully got installed into the primary NTFS partition. But it's not booting now and saying BOOTMGR not available. First I reinstalled the grub by logging in with live CD. It showed an entry for Windows7. After I did the 'grub-update' and went back to grub screen, there was no Win7 entry! Now, I tried grub-update again. It still shows no entry for Win7. Can someone plz help? This is my boot_info_script result if it's needed. I tried adding the grub entry manually by doing what I found [here]("http://ubuntuguide.net/manually-addingremoving-entries-to-grub-2-menu") but it doesn't seem to work.


> 
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Boot/BCD

sda4: _________________________________________________________________________

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

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048       258,047       256,000  de Dell Utility
/dev/sda2             272,384    21,247,999    20,975,616   7 HPFS/NTFS
/dev/sda3    *     21,248,000    81,139,711    59,891,712   7 HPFS/NTFS
/dev/sda4          81,141,758   976,773,119   895,631,362   5 Extended
/dev/sda5          81,141,760   102,277,119    21,135,360  83 Linux
/dev/sda6         102,279,168   471,316,479   369,037,312   7 HPFS/NTFS
/dev/sda7         471,318,528   731,013,119   259,694,592   7 HPFS/NTFS
/dev/sda8         731,015,168   962,396,159   231,380,992   7 HPFS/NTFS
/dev/sda9         962,398,208   976,773,119    14,374,912  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        F87A-5EFF                              vfat                                     
/dev/sda2        7AB1841074230D10                       ntfs       RECOVERY                      
/dev/sda3        06809E60809E55D1                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        3fe03c60-f23d-40d3-b81e-3e39c7019cda   ext4                                     
/dev/sda6        6EDF29794386B51B                       ntfs       Entertainment                 
/dev/sda7        539CB1AF4B5CBC80                       ntfs       Acads                         
/dev/sda8        4B17C4961EAADC51                       ntfs       Dump                          
/dev/sda9        fd2f7120-f2e5-4cac-8f73-3b56ea83d8b1   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


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
search --no-floppy --fs-uuid --set 3fe03c60-f23d-40d3-b81e-3e39c7019cda
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 3fe03c60-f23d-40d3-b81e-3e39c7019cda
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 3fe03c60-f23d-40d3-b81e-3e39c7019cda
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=3fe03c60-f23d-40d3-b81e-3e39c7019cda ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 3fe03c60-f23d-40d3-b81e-3e39c7019cda
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=3fe03c60-f23d-40d3-b81e-3e39c7019cda ro single 
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
    search --no-floppy --fs-uuid --set 3fe03c60-f23d-40d3-b81e-3e39c7019cda
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 3fe03c60-f23d-40d3-b81e-3e39c7019cda
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/35_Win7 ###
Windows 7 Home Premium found
menuentry "Windows7 Home Premium" {
set root=(hd0,3)
chainloader (hd0,3)+1
}
### END /etc/grub.d/35_Win7 ###

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
UUID=3fe03c60-f23d-40d3-b81e-3e39c7019cda /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=fd2f7120-f2e5-4cac-8f73-3b56ea83d8b1 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  46.1GB: boot/grub/core.img
  42.3GB: boot/grub/grub.cfg
  42.2GB: boot/initrd.img-2.6.35-22-generic
  46.3GB: boot/vmlinuz-2.6.35-22-generic
  42.2GB: initrd.img
  46.3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 80 42 01 00 fe  |............B...|
000001d0  ff ff 05 fe ff ff 02 80  42 01 00 18 ff 15 00 00  |........B.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb 


---

### Post by Quackers on 2010-11-19
bootmgr is missing from your Windows partition (sda3). If you run the Startup Repair from the Windows installation disc it should fix that. It may need to run 3 times!

---

### Post by manuganji on 2010-11-20
Yeah, I think my laptop will get ok pretty soon. All thanks to the kind support I get here.

Quackers, i tried your solution with a win7 repair disk. It added an entry into grub menu and I could log into windows. I tried rebooting from windows. It shows this error msg instead of grub menu. 
> no module name found
Aborted. Press any key to exit.
When I press any key, it shows this msg
> Intel UNDI, PXE....
.
.
.
Realtek PCIe FE Family Controller Series
PXE-E61:Media test failure, check cable
PXE-MOF:Exiting PXE ROM.
Reboot & select proper boot device
or insert Boot media in selected boot media & press a key.

Here I tried booting with Live CD and restored the grub. But again, when I log into Windows and reboot the grub screen disappears. 

I even tried the repair disc after I get this error msg. But after doing 'Startup Repair' and rebooting I still see the same error msg.

This is the current output of boot_info_script

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD

sda4: _________________________________________________________________________

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

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048       258,047       256,000  de Dell Utility
/dev/sda2             272,384    21,247,999    20,975,616   7 HPFS/NTFS
/dev/sda3    *     21,248,000    81,139,711    59,891,712   7 HPFS/NTFS
/dev/sda4          81,141,758   976,773,119   895,631,362   5 Extended
/dev/sda5          81,141,760   102,277,119    21,135,360  83 Linux
/dev/sda6         102,279,168   471,316,479   369,037,312   7 HPFS/NTFS
/dev/sda7         471,318,528   731,013,119   259,694,592   7 HPFS/NTFS
/dev/sda8         731,015,168   962,396,159   231,380,992   7 HPFS/NTFS
/dev/sda9         962,398,208   976,773,119    14,374,912  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        F87A-5EFF                              vfat                                     
/dev/sda2        7AB1841074230D10                       ntfs       RECOVERY                      
/dev/sda3        06809E60809E55D1                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        3fe03c60-f23d-40d3-b81e-3e39c7019cda   ext4                                     
/dev/sda6        6EDF29794386B51B                       ntfs       Entertainment                 
/dev/sda7        539CB1AF4B5CBC80                       ntfs       Acads                         
/dev/sda8        4B17C4961EAADC51                       ntfs       Dump                          
/dev/sda9        fd2f7120-f2e5-4cac-8f73-3b56ea83d8b1   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=600)
/dev/sda6        /media/Entertainment     fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda7        /media/Acads             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda8        /media/Dump              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda3        /media/06809E60809E55D1  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
search --no-floppy --fs-uuid --set 3fe03c60-f23d-40d3-b81e-3e39c7019cda
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 3fe03c60-f23d-40d3-b81e-3e39c7019cda
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 3fe03c60-f23d-40d3-b81e-3e39c7019cda
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=3fe03c60-f23d-40d3-b81e-3e39c7019cda ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 3fe03c60-f23d-40d3-b81e-3e39c7019cda
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=3fe03c60-f23d-40d3-b81e-3e39c7019cda ro single 
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
    search --no-floppy --fs-uuid --set 3fe03c60-f23d-40d3-b81e-3e39c7019cda
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 3fe03c60-f23d-40d3-b81e-3e39c7019cda
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda3)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 06809e60809e55d1
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
UUID=3fe03c60-f23d-40d3-b81e-3e39c7019cda /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=fd2f7120-f2e5-4cac-8f73-3b56ea83d8b1 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  46.1GB: boot/grub/core.img
  42.3GB: boot/grub/grub.cfg
  42.2GB: boot/initrd.img-2.6.35-22-generic
  46.3GB: boot/vmlinuz-2.6.35-22-generic
  42.2GB: initrd.img
  46.3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 80 42 01 00 fe  |............B...|
000001d0  ff ff 05 fe ff ff 02 80  42 01 00 18 ff 15 00 00  |........B.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

---

### Post by oldfred on 2010-11-20
Please post boot script results.txt in code tags. You highlight entire thing after pasting and click on # in edit panel above. Or click on # in edit panel and paste between code and /code tags.

You only posted part of the updated boot script. Please post the entire thing as it may make a difference. Do you have a boot flag on sda3? Grub does not use it. Windows does, but some BIOS require a boot flag.

---

### Post by cmcanulty on 2010-11-20
Is there a reason /Home should be logical rather than primary? I have 20GB /, 300GB /home both primary and 2GB swap

---

### Post by Quackers on 2010-11-20
> **cmcanulty said:**
> Is there a reason /Home should be logical rather than primary? I have 20GB /, 300GB /home both primary and 2GB swap

Not really, though Linux will run quite happily from logical partitions within an extended partition.
The problem some people face is the limit of 4 primary partitions available in the mbr system. Sometimes it can be necessary to delete a 4th primary partition and replace it with an extended partition which can have oodles of logical partitions within it.

---

### Post by manuganji on 2010-11-21
fred, i made those changes.plz, take a look at them.

---

### Post by oldfred on 2010-11-21
Your sdc3 has the boot flag and the first two of the windows boot files.

Vista and win7 boot files
  Boot files/dirs:   /bootmgr /Boot/BCD

Sometimes a partition just has the above files and is a boot only partition, usually 100MB, but yours is larger. But then a larger partition  also includes this file from the main windows install. Please review your NTFS partitions and see if you have /window/system32 folders anywhere as that is the main system partition.

 /Windows/System32/winload.exe

---

### Post by manuganji on 2010-11-23
fred, the same sda3 has /bootmgr, /Boot/BCD and also the said system32 folders with winload.exe. So, what should we do now? I have just Win7 on my computer and on this partition alone.

---

### Post by oldfred on 2010-11-23
Does windows boot from the grub entry? What messages do you get?

If it does not boot but starts to then grub has transfered control to windows and it is a windows issue. You could try the windows repairs agian but sometimes the command line windows repairs work better.

oldfred's Windows Vista/Win7 repair links:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)

[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://www.bleepingcomputer.com/tutorials/tutorial148.html](http://www.bleepingcomputer.com/tutorials/tutorial148.html)

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by manuganji on 2010-11-26
fred, atlast I used EasyBCD in Windows7 and and then made the GRUB_TIMEOUT to be zero, that worked. Now everything works.

---

