---
title: "Cannot boot into Windows 7 after install 10.04"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by RobGThai on 2010-05-05
To be specific, install from LiveCD.

I have Windows 7 installed and working on my laptop. I also have beta version of Ubuntu 10 installed as well.

Then I boot into Ubuntu 10.04 from Live CD with option to try without changing anything. There I choose to install Ubuntu on the laptop.
After that Windows menu was removed from the Dualboot menu, the only "Windows-related" option present get me into the Windows screen with a single command Window open with "X:". If I close this cmd window, my laptop would reboot.

I'm completely new to all this, please help.

---

### Post by halitech on 2010-05-05
boot into Ubuntu and post the output of
```
sudo fdisk -l
```

---

### Post by wilee-nilee on 2010-05-05
Your post is rather confusing, is this a wubi install? yeah follow the post above.

---

### Post by RobGThai on 2010-05-05
Please excuse my English. I install Ubuntu from Live CD after booting into the "Try Ubuntu" option.

Here is the result.

```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3ffc3ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3825    30724281    c  W95 FAT32 (LBA)
/dev/sda2            3826       20399   133129216    7  HPFS/NTFS
/dev/sda3           20400       60660   323395585    f  W95 Ext'd (LBA)
/dev/sda4           60660       60802     1135448   12  Compaq diagnostics
/dev/sda5           20400       42083   174171766    7  HPFS/NTFS
/dev/sda6           52270       60660    67394560    7  HPFS/NTFS
/dev/sda7           42083       51849    78445568   83  Linux
/dev/sda8           51849       52269     3376128   82  Linux swap / Solaris

Partition table entries are not in disk order


```By the way, only Window-relate boot option says "Windows Vista (Loader) sda4".
I'm running Windows 7, not Vista. I also did not upgrade from Vista to 7, so I have no idea why Vista option is there at all.


I did also run the Boot info Script as well, and the result is here.
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda6/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda4 has 
                       2050047 sectors, but according to the info from fdisk, 
                       it has 2270895 sectors.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    61,448,624    61,448,562   c W95 FAT32 (LBA)
/dev/sda2          61,450,240   327,708,671   266,258,432   7 HPFS/NTFS
/dev/sda3         327,710,718   974,501,887   646,791,170   f W95 Ext d (LBA)
/dev/sda5         327,710,720   676,054,251   348,343,532   7 HPFS/NTFS
/dev/sda6         839,712,768   974,501,887   134,789,120   7 HPFS/NTFS
/dev/sda7         676,055,040   832,946,175   156,891,136  83 Linux
/dev/sda8         832,948,224   839,700,479     6,752,256  82 Linux swap / Solaris
/dev/sda4         974,502,272   976,773,167     2,270,896  12 Compaq diagnostics


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0       eff4aa17-20a2-4817-8964-14c760b12aa2   ext4                                     
/dev/sda1        443B-14EF                              vfat       FREEDOS                       
/dev/sda2        6A4A0B744A0B3BF7                       ntfs       System                        
/dev/sda3: PTTYPE="dos" 
/dev/sda4        E8567002566FCFBC                       ntfs       LENOVO_PART                   
/dev/sda5        80DED7C3DED7B020                       ntfs       Data                          
/dev/sda6        D244923944921FF1                       ntfs       New Volume                    
/dev/sda7        989765a5-f100-4292-af67-d83a695a06be   ext4                                     
/dev/sda8        b4d0e633-4cb5-4ea2-b585-1783a310a479   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro)
/dev/sda2        /media/System            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


======================== sda6/Wubi/boot/grub/grub.cfg: ========================

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
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set d244923944921ff1
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda6 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, Linux 2.6.32-21-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set d244923944921ff1
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda6 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "FreeDOS (on /dev/sda1)" {
    insmod fat
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 443b-14ef
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda4)" {
    insmod ntfs
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set e8567002566fcfbc
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda6/Wubi/etc/fstab: =============================

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

================= sda6/Wubi: Location of files loaded by Grub: =================


   2.4GB: boot/grub/grub.cfg
   4.9GB: boot/initrd.img-2.6.32-21-generic
   5.4GB: boot/vmlinuz-2.6.32-21-generic
   4.9GB: initrd.img
   5.4GB: vmlinuz

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 989765a5-f100-4292-af67-d83a695a06be
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
insmod ext2
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 989765a5-f100-4292-af67-d83a695a06be
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

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 989765a5-f100-4292-af67-d83a695a06be
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=989765a5-f100-4292-af67-d83a695a06be ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 989765a5-f100-4292-af67-d83a695a06be
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=989765a5-f100-4292-af67-d83a695a06be ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 989765a5-f100-4292-af67-d83a695a06be
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 989765a5-f100-4292-af67-d83a695a06be
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "FreeDOS (on /dev/sda1)" {
    insmod fat
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 443b-14ef
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda4)" {
    insmod ntfs
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set e8567002566fcfbc
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=989765a5-f100-4292-af67-d83a695a06be /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=b4d0e633-4cb5-4ea2-b585-1783a310a479 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 376.3GB: boot/grub/core.img
 376.3GB: boot/grub/grub.cfg
 376.4GB: boot/initrd.img-2.6.32-21-generic
 376.3GB: boot/vmlinuz-2.6.32-21-generic
 376.4GB: initrd.img
 376.3GB: vmlinuz
=============================== StdErr Messages: ===============================

ls: reading directory /media/System/: Input/output error

```

---

### Post by Sealbhach on 2010-05-05
> By the way, only Window-relate boot option says "Windows Vista (Loader)  sda4".


What happens when you select that option?

.

---

### Post by RobGThai on 2010-05-05
It boots into some Windows environment with nothing but a single DOS window.

I can perform some command in that window. However, as soon as I close that window, the computer reboots. I tried to wait but nothing happen at all.

Now I can get into Windows by choosing FreeDOS option, it will then provide me with two choices:
- Windows 7
- Ubuntu

These two options is always there since I install the beta version.
When I choose Windows 7, it said the device is inaccessible and I have to use Windows cd to fix the bootloader.

Now, I'm in my Windows 7 environment, but everything is messed up. All shortcut doesn't work including those in the Start menu. This really is bothersome.

Hope there is a way to fix it.

---

### Post by wilee-nilee on 2010-05-05
> **RobGThai said:**
> It boots into some Windows environment with nothing but a single DOS window.

I can perform some command in that window. However, as soon as I close that window, the computer reboots. I tried to wait but nothing happen at all.

Now I can get into Windows by choosing FreeDOS option, it will then provide me with two choices:
- Windows 7
- Ubuntu

These two options is always there since I install the beta version.
When I choose Windows 7, it said the device is inaccessible and I have to use Windows cd to fix the bootloader.

Now, I'm in my Windows 7 environment, but everything is messed up. All shortcut doesn't work including those in the Start menu. This really is bothersome.

Hope there is a way to fix it.

If it were me I would make sure that your windows isn't corrupted by, malware, trojans, viri,....etc to start with. Is this a certified MS install?

---

### Post by RobGThai on 2010-05-05
Yes, it is. I'm pretty sure it's not corrupt by any mean. I've been using it for only a month with Kaspersky antivirus running and up to date. I also scan it weekly so it's definitely not corrupted. All these happen after the installation of 10.04 which I dont know why.

---

### Post by wilee-nilee on 2010-05-05
> **RobGThai said:**
> Yes, it is. I'm pretty sure it's not corrupt by any mean. I've been using it for only a month with Kaspersky antivirus running and up to date. I also scan it weekly so it's definitely not corrupted. All these happen after the installation of 10.04 which I dont know why.

I wouldn't trust just kapersky, it is a good AV, but not any single one will get everything. Kapersky is well known and is a easy target for the crackers. Here are two other free AV scanners these are very good, and don't run live like kapersky and should install if you have no problems.
[http://www.malwarebytes.org/](http://www.malwarebytes.org/)
[http://www.superantispyware.com/](http://www.superantispyware.com/)
You may be correct that you have no nasty-ware, but if you do it may have kapersky in it's control.

---

### Post by twright on 2010-05-05
Ok, it does not sound like a virus. Could you just try right clicking on your main hard drive in Windows Explorer and selecting the check (or fix errors, etc) option.

---

### Post by oldfred on 2010-05-05
You must have installed wubi beta into a windows partition. Now you have a full Ubuntu install.

The label says sda2 is the system partition but it is missing all the boot files you normally see in a system partition. Boot flag is on sda1  and may be the win7 boot partition as it has /bootmgr /boot/bcd which are normally in the 100mb windows boot partition, but command.com is not?? as that is for old dos booting.

Script did not find this file in sda2 - please check to see if it really is there or not.
/Windows/System32/winload.exe 

I think you will have to do windows repairs.
How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands: 
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk /r 
BootRec.exe /FixBoot  #updates PBR partition boot 
BootRec.exe /ScanOs 
BootRec.exe /RebuildBcd

Some advanced BCD rebuild, Vista:
[http://ubuntuforums.org/showthread.php?t=1426103](http://ubuntuforums.org/showthread.php?t=1426103)

---

### Post by RobGThai on 2010-05-05
I'll try that when I get home tonight, thank you :)
Also I did chkDisk last night no problem found.

To summarise the whole thing right now.

#1 Dualboot menu
```

Ubuntu
Ubuntu(Recovery)
****cant remember*****
FreeDOS
Windows Vista (Launcher)

```

If I choose FreeDOS I get another dualboot screen(#2)
```

Windows 7
Ubuntu
```

I should point out that selecting Ubuntu in Dualboot menu #1 and #2 will take me into the different Ubuntu I have (I'm sure of this, because the one in #2 doesn't have Wireless adapter driver available).

My Windows 7 seems to be running okay after I delete the system shortcut and replace them with new one.

Tonight I'll try to do BootRec as oldfred posted. I also think that I dont need two Ubuntu install so is there anyway for me to remove the one in #2 and have the default dualboot selection to FreeDOS in #1 (Since I have to use Windows at work).

---

### Post by anothernewuser on 2010-05-05
Ummmm ... I'm really not all that good with Ubuntu but I've seen similar  screens before on my system ...

In my case, the first screen of boot options was from a regular install of Ubuntu that had been on my machine for years alongside Windows .. the second was from a "WUBI" install of another (more recent) copy of Ubuntu that I had added to test out a newer version.

Removing the WUBI installed Ubuntu also automatically removed the second boot screen ... as the OS wasn't there anymore there was no need for the boot options.  I was able to do this very easily ... there were loads of ways to remove the WUBI install ... it had a "uninstall WUBI" option or you could try Add/Remove Programs through the Control Panel.

Sooooooooooooo ....

If I were to generalize from my case to yours I suppose I'd say .. remove whatever is creating the need for a second boot menu.  This would simplify your system a bit but I'm not sure if that would solve your problems.  Best I can offer I'm afraid ... Good luck.

---

### Post by RobGThai on 2010-05-05
Thank you for sharing that anothernewuser.
I'll try to remove the one in Control Panel and see if that help. Thanks a lot :).

---

