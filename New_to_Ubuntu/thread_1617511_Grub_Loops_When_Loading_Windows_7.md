---
title: "Grub Loops When Loading Windows 7"
date: 2010-11-09
forum: New to Ubuntu
---

### Post by haximalion89 on 2010-11-09
I was using Linux Mint for a while. Basically more user-friendly version of Ubuntu with a Windows-like interface. A friend of mine couldn't install Windows (ancient computer) so I gave her the new Ubuntu (simpler than Mint). I was actually really impressed, and wanted to try it for myself. However, when I installed 10.10 the Grub broke, and I couldn't figure out how to fix it....

Then I had an idea! I installed Mint to a small partition, which set up a Grub of its own. Bingo. I can log in to Mint and the Ubuntu distros, no problem.

Windows 7 is another story, however. It takes me to another loader, black and white, and when I select Windows 7 it loops back to the same window. I've included a screenshot.

This is very frustrating. I do all of my work/classwork/writing in Linux but play by games from my Windows partition.

[IMG]http://oi51.tinypic.com/4j9f9l.jpg[/IMG]

Ideas? : (

---

### Post by Quackers on 2010-11-09
Installation of grub often breaks Windows bootloader. You will need to repair it with the Windows repair cd, by running the startup repair (possibly 3 times).

---

### Post by haximalion89 on 2010-11-09
All right, then. Guess I'll have to dig till I find that damn CD....

But wait, won't that override the Linux bootloader?

---

### Post by Quackers on 2010-11-09
It's a good question, but the answer is "not usually" :-)
There is another option, in that you can install Lilo from the Ubuntu Live CD, so don't despair!

---

### Post by AngusH on 2010-11-09
I would recommend that you post the results of the boot info script (I'll find a link in a min) before trying to repair windows bootloader. If it's looping back to GRUB that's normally an error with GRUB not windows.
Angus

EDIT Instructions here [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) The results from that will make it a lot easier for us to try and help you.

---

### Post by wilee-nilee on 2010-11-09
> **AngusH said:**
> I would recommend that you post the results of the boot info script (I'll find a link in a min) before trying to repair windows bootloader. If it's looping back to GRUB that's normally an error with GRUB not windows.
Angus

EDIT Instructions here [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) The results from that will make it a lot easier for us to try and help you.

+1 on the script

---

### Post by haximalion89 on 2010-11-09
This is what I've got. So lost...

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/burg.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 663027765 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 9 Isadora
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   353,279,897   353,279,835   7 HPFS/NTFS
/dev/sda2         971,530,875   972,044,954       514,080  82 Linux swap / Solaris
/dev/sda3         503,364,645   740,014,007   236,649,363  83 Linux
/dev/sda4         353,279,998   503,363,583   150,083,586   5 Extended
/dev/sda5         353,280,000   503,363,583   150,083,584  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   488,392,064   488,392,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        36F08AAEF08A73C1                       ntfs                                     
/dev/sda2        6d9c5f4b-5e90-4576-830f-4e1f3ce2943a   swap                                     
/dev/sda3        841b4cc8-b729-4d6c-a432-208646e1c3af   ext4                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        5df7f10c-77ef-4138-8c2e-ff4f84ec6056   ext3                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        D80CF09C0CF076BA                       ntfs       Media/Etc.                    
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext3       (rw,errors=remount-ro)
/dev/sdb1        /media/Media_Etc.        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 841b4cc8-b729-4d6c-a432-208646e1c3af
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 841b4cc8-b729-4d6c-a432-208646e1c3af
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
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 841b4cc8-b729-4d6c-a432-208646e1c3af
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=841b4cc8-b729-4d6c-a432-208646e1c3af ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 841b4cc8-b729-4d6c-a432-208646e1c3af
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=841b4cc8-b729-4d6c-a432-208646e1c3af ro single 
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
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 841b4cc8-b729-4d6c-a432-208646e1c3af
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 841b4cc8-b729-4d6c-a432-208646e1c3af
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 36f08aaef08a73c1
    chainloader +1
}
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda5) (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 5df7f10c-77ef-4138-8c2e-ff4f84ec6056
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=5df7f10c-77ef-4138-8c2e-ff4f84ec6056 ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda5) -- recovery mode (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 5df7f10c-77ef-4138-8c2e-ff4f84ec6056
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=5df7f10c-77ef-4138-8c2e-ff4f84ec6056 ro single
    initrd /boot/initrd.img-2.6.32-21-generic
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

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda3       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=6d9c5f4b-5e90-4576-830f-4e1f3ce2943a none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


 339.4GB: boot/grub/core.img
 363.2GB: boot/grub/grub.cfg
 258.3GB: boot/initrd.img-2.6.35-22-generic
 339.4GB: boot/vmlinuz-2.6.35-22-generic
 258.3GB: initrd.img
 339.4GB: vmlinuz

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 5df7f10c-77ef-4138-8c2e-ff4f84ec6056
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 5df7f10c-77ef-4138-8c2e-ff4f84ec6056
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

### BEGIN /etc/grub.d/06_mint_theme ###
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 5df7f10c-77ef-4138-8c2e-ff4f84ec6056
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
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda5)" --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 5df7f10c-77ef-4138-8c2e-ff4f84ec6056
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=5df7f10c-77ef-4138-8c2e-ff4f84ec6056 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda5) -- recovery mode" --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 5df7f10c-77ef-4138-8c2e-ff4f84ec6056
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=5df7f10c-77ef-4138-8c2e-ff4f84ec6056 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 5df7f10c-77ef-4138-8c2e-ff4f84ec6056
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 5df7f10c-77ef-4138-8c2e-ff4f84ec6056
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 36f08aaef08a73c1
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda3)" {
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 841b4cc8-b729-4d6c-a432-208646e1c3af
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=841b4cc8-b729-4d6c-a432-208646e1c3af ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda3)" {
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 841b4cc8-b729-4d6c-a432-208646e1c3af
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=841b4cc8-b729-4d6c-a432-208646e1c3af ro single
    initrd /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda5       /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=6d9c5f4b-5e90-4576-830f-4e1f3ce2943a none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 254.8GB: boot/grub/core.img
 254.9GB: boot/grub/grub.cfg
 254.9GB: boot/initrd.img-2.6.32-21-generic
 254.9GB: boot/vmlinuz-2.6.32-21-generic
 254.9GB: initrd.img
 254.9GB: vmlinuz
=============================== StdErr Messages: ===============================

ls: reading directory sda1/: Input/output error

```

---

### Post by drs305 on 2010-11-09
Grub 2 was installed in the Windows boot sector.

Forum member *meierfra* wrote about how to fix it:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector")

---

### Post by haximalion89 on 2010-11-09
> **drs305 said:**
> Grub 2 was installed in the Windows boot sector.

Forum member *meierfra* wrote about how to fix it:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)


Follow the directions faithfully, but I don't get "boot BS" I get "rebuild BS" , which only has the options "Dump," "List" and "Quit." : (

---

### Post by drs305 on 2010-11-09
I don't have Windows on this machine but I'll take a look at TestDisk and see what I get.

Perhaps someone else with Windows can run it and see the options they get.

---

### Post by drs305 on 2010-11-09
The other option to teskdisk is also detailed in that thread:
> You can repair the boot sector of Windows system partition via "fixboot" from a Windows XP CD, or "bootrect /fixboot" from a Windows Vista/7 CD.

If you don't have the disk, here are some links where you can get what you need and *oldfred's* link will help you run them.

W7 Repair Disk:  [http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")
Vista Repair Disk:  [http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/ ]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/")
*oldfred's*  Windows repair links:  
[http://ubuntuforums.org/showthread.php?p=9826152]("http://ubuntuforums.org/showthread.php?p=9826152")

---

### Post by haximalion89 on 2010-11-10
Nothing seems to be working. I'm quite frustrated. I basically said to hell with it since the majority of my important data is on a separate "media" drive and tried to erase all the partitions (except Ubuntu, which I'm running now, obviously) and reinstall linux/windows/grub. 

But that damn black and white BURG bootloader! I supposedly removed it from my system (through Synaptic Package Manager) but every freaking time I boot up I get to it! WHY? Every time I try to load a Live CD (windows, ubuntu, mint, anything) it sends me back to this black and white crappy grub loader. It even has the same options! But obviously gives me an error when I choose one, since that partition got toasted.

A bit upset, here. I can't even load a live CD to fix the problem. I have no idea why it's looping.

---

### Post by Quackers on 2010-11-10
Your boot script states
=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/burg.
Have you installed BURG as well as GRUB?

Also I have bad news for you. From your boot script I can't see any Windows operating system installed!
As the boot flag is set to sda1, I suspect W7 was there. I wonder if it could be hidden by the fact that grub2 was installed in there and it is masking W7???
The only thing I can suggest is to run Startup Repair up to 3 times from the Windows repair disc.

---

### Post by toekneewood on 2010-11-10
One thing to watch out for is that I think that Windows 7 used dynamic disks and writes the boot information at the end of the partition.  If you then resize the partition it can cause problems.  One of the tech doods in the office just mentioned this as they have had problems with it in the past.  If you resize any windows partitions, do yourself a favour and run a chkdsk -f before you resize

---

### Post by haximalion89 on 2010-11-10
> **Quackers said:**
> Your boot script states
=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/burg.
Have you installed BURG as well as GRUB?

Also I have bad news for you. From your boot script I can't see any Windows operating system installed!
As the boot flag is set to sda1, I suspect W7 was there. I wonder if it could be hidden by the fact that grub2 was installed in there and it is masking W7???
The only thing I can suggest is to run Startup Repair up to 3 times from the Windows repair disc.

Like I said, I can't run CDs (install/repair/live/etc.). It just goes to Burg, in which Ubuntu is the only option that works. I just want to wipe everything clean, but if Burg keeps popping up and live CDs/install CDs won't load I can't even do that.

---

### Post by drs305 on 2010-11-10
> **haximalion89 said:**
> Like I said, I can't run CDs (install/repair/live/etc.). It just goes to Burg, in which Ubuntu is the only option that works. I just want to wipe everything clean, but if Burg keeps popping up and live CDs/install CDs won't load I can't even do that.

If you can boot into Ubuntu and want to wipe everything, you can install TestDisk and then let it write to the MBR. It will remove Grub/Burg and make the system unbootable until you add another bootloader. (If you are installing testdisk from a LiveCD make sure the *universe* repository is enabled.

```
sudo apt-get install testdisk
sudo testdisk
```
No Log > Select drive & Proceed > Intel > MBR Code > Y > Y > OK > Quit > Quit

---

### Post by haximalion89 on 2010-11-10
Well things seem to have taken a turn for the worst. Not only can I not boot Live CDs, I can't boot Ubuntu or anything else either. 

All I have is a black screen with that blinking underscore, whether I've put a live CD in or let it run on its own. Nothing else. 

The BIOS is set up to run CDs before the hard drive, so it's not that. It's plugged in securely and the PSU is fine. I have no idea why this is happening to me. I've tried everything. I feel like just throwing it out the window. 

Typing this from my laptop, btw.

---

### Post by oldfred on 2010-11-10
Your boot script showed two windows partitions but no windows files to boot???

It should have shown something like this:
    Boot files/dirs:    /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe 

Sometimes it is split into two partitions where one is boot with just the bootmgr & BCD and the other is the full system with the winload.exe file.

Did you have two windows installs and overwrite the system one?

If you installed the windows boot loader to the MBR and have no windows you will not boot at all. You need to reinstall grub to at least get Ubuntu.

If you have good CD it should boot if set first in BIOS. But if CD is not bootable for any reason it defaults back to HD and then will not boot. I would check that CD is bootable.

---

### Post by haximalion89 on 2010-11-10
I've tried dozens of CDs. Windows and Linux distros. Nothing works. It just gets to that hanging underscore and then nothing.

---

### Post by haximalion89 on 2010-11-10
Wait, no. Mint is working, for some reason. Strange.

---

### Post by aqb on 2010-12-06
@haximalion89 have you fixed the boot problems yet? or did you just do a straight wipe? i'm currently having the same problem where i can't boot into windows 7 after installing mint 10. when i select windows 7 from the grub menu it just goes to a blank screen and returns to the grub loader.

so at the moment i can only load mint 10, but i have altering fixing the grub configuration file but it hasn't made a difference. i've also tried repairing the boot from the windows 7 cd which also hasn't made a difference.

---

### Post by aqb on 2010-12-06
I fixed it by running "bootrec /fixboot" in command promo within the repair option of the windows 7 DVD.

---

