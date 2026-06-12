---
title: "GRUB not detecting all OS"
date: 2010-10-18
forum: New to Ubuntu
---

### Post by siraitares on 2010-10-18
Hey, I'm new to this and was hoping you could help me out. The thing is I had a dual-boot system with Windows 7 and Fedora 13 and it worked perfectly. Now, after having installer Ubuntu 10.10, grub only detects Windows and Ubuntu, but not Fedora! Any ideas on what could be the problem?

---

### Post by Hippytaff on 2010-10-18
How did you install ubuntu - wubi or a real partition? silly question, but did you install over fedora?
 
Also you might try going to Advanced system setting and choose to have a option to show all OS that boot

---

### Post by Quackers on 2010-10-18
Please go to the link below and download the boot script to your desktop then run the script with the command given on that site. This will produce a Results.txt file on your desktop. Please copy the contents of that file and paste it between CODE tags in your next post. (For CODE tags click on New Reply then on the # symbol in the top bar).

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by siraitares on 2010-10-18
I installed using the Live CD on a partition I made using Windows 7. I'm pretty sure I didn't install over Fedora... I really hope I did not haha.
I'll do what Quackers said and be right back with the results

---

### Post by siraitares on 2010-10-18
So here's what I got. At least it seems like the Fedora GRUB is still there :p

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for (,msdos7)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst /grub/grub.conf

sda6: _________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         81,920    30,801,919    30,720,000   7 HPFS/NTFS
/dev/sda3          30,801,920   493,834,656   463,032,737   7 HPFS/NTFS
/dev/sda4         493,836,286   625,141,759   131,305,474   5 Extended
/dev/sda5         540,942,336   541,966,335     1,024,000  83 Linux
/dev/sda6         541,968,384   625,141,759    83,173,376  8e Linux LVM
/dev/sda7         493,836,288   540,942,335    47,106,048  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        78EECB41EECAF702                       ntfs       RECOVERY                      
/dev/sda3        945E5C395E5C1678                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        1d8ea411-427f-4b36-a638-bb050467be34   ext4                                     
/dev/sda6        L3STFP-3XUW-ImTm-JZCR-a4iZ-SLZ6-noORzf LVM2_member                               
/dev/sda7        8e649d32-5750-4de4-90f4-87542f92a2b9   ext4                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro,commit=600)


============================= sda5/grub/grub.conf: =============================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,4)
#          kernel /vmlinuz-version ro root=/dev/mapper/vg_pablo-lv_root
#          initrd /initrd-[generic-]version.img
#boot=/dev/sda
default=2
timeout=10
splashimage=(hd0,4)/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.33.8-149.fc13.i686)
    root (hd0,4)
    kernel /vmlinuz-2.6.33.8-149.fc13.i686 ro root=/dev/mapper/vg_pablo-lv_root rd_LVM_LV=vg_pablo/lv_root rd_LVM_LV=vg_pablo/lv_swap rd_NO_LUKS rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=la-latin1 rhgb quiet
    initrd /initramfs-2.6.33.8-149.fc13.i686.img
title Fedora (2.6.33.3-85.fc13.i686.PAE)
    root (hd0,4)
    kernel /vmlinuz-2.6.33.3-85.fc13.i686.PAE ro root=/dev/mapper/vg_pablo-lv_root rd_LVM_LV=vg_pablo/lv_root rd_LVM_LV=vg_pablo/lv_swap rd_NO_LUKS rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=la-latin1 rhgb quiet
    initrd /initramfs-2.6.33.3-85.fc13.i686.PAE.img
title Windows 7
    rootnoverify (hd0,1)
    chainloader +1

=================== sda5: Location of files loaded by Grub: ===================


 277.2GB: grub/grub.conf
 277.2GB: grub/menu.lst
 277.2GB: grub/stage2
 276.9GB: initramfs-2.6.33.3-85.fc13.i686.PAE.img
 277.0GB: initramfs-2.6.33.8-149.fc13.i686.img
 276.9GB: vmlinuz-2.6.33.3-85.fc13.i686.PAE
 276.9GB: vmlinuz-2.6.33.8-149.fc13.i686

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 8e649d32-5750-4de4-90f4-87542f92a2b9
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 8e649d32-5750-4de4-90f4-87542f92a2b9
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
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 8e649d32-5750-4de4-90f4-87542f92a2b9
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=8e649d32-5750-4de4-90f4-87542f92a2b9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 8e649d32-5750-4de4-90f4-87542f92a2b9
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=8e649d32-5750-4de4-90f4-87542f92a2b9 ro single 
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
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 8e649d32-5750-4de4-90f4-87542f92a2b9
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 8e649d32-5750-4de4-90f4-87542f92a2b9
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 78eecb41eecaf702
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
UUID=8e649d32-5750-4de4-90f4-87542f92a2b9 /               ext4    errors=remount-ro 0       1

=================== sda7: Location of files loaded by Grub: ===================


 255.1GB: boot/grub/core.img
 259.5GB: boot/grub/grub.cfg
 253.5GB: boot/initrd.img-2.6.35-22-generic
 255.1GB: boot/vmlinuz-2.6.35-22-generic
 253.5GB: initrd.img
 255.1GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb 

```

---

### Post by drs305 on 2010-10-18
siraitares,

Welcome to the Ubuntu forums.  :-)

I don't know why Grub 2 isn't picking up Fedora. Until you find a solution, you can paste this below the existing lines in */etc/grub.d/40 custom*. 

> 
menuentry 'title Fedora (2.6.33.8-149.fc13.i686)' {
	insmod ext2
	set root='(hd0,5)'
	linux  /vmlinuz-2.6.33.8-149.fc13.i686 ro root=/dev/mapper/vg_pablo-lv_root rd_LVM_LV=vg_pablo/lv_root rd_LVM_LV=vg_pablo/lv_swap rd_NO_LUKS rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=la-latin1 rhgb quiet
	    initrd /initramfs-2.6.33.8-149.fc13.i686.img
}


menuentry 'Fedora (2.6.33.3-85.fc13.i686.PAE' {
	insmod ext2
	set root='(hd0,5)'
	linux  /vmlinuz-2.6.33.3-85.fc13.i686.PAE ro root=/dev/mapper/vg_pablo-lv_root rd_LVM_LV=vg_pablo/lv_root rd_LVM_LV=vg_pablo/lv_swap rd_NO_LUKS rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=la-latin1 rhgb quiet
    initrd /initramfs-2.6.33.3-85.fc13.i686.PAE.img
}



You will have to edit the file as root. Paste the contents, save the file, and then update grub (*update-grub* run as root) to incorporate the changes into the Grub 2 menu.

Disclaimer: I don't use Fedora and constructed this from your Grub legacy entries. If they don't work, someone using Fedora can probably help spot the problem.

---

### Post by oldfred on 2010-10-18
Should not set root be sda5? hd0,4 was old grub numbering and its needs one more for grub2. (I know drs305 knows, so it is just a typo).

set root='(hd0,4)'

---

### Post by drs305 on 2010-10-18
> **oldfred said:**
> Should not set root be sda5? hd0,4 was old grub numbering and its needs one more for grub2. (I know drs305 knows, so it is just a typo).

set root='(hd0,4)'

You are correct, but also too kind. It's been long enough from my days with Grub that I didn't even consider it. I'll go back and change the original entry. Thanks.

(I'll claim I was just overwhelmed by all the kernel options.)

---

### Post by siraitares on 2010-10-18
> **drs305 said:**
> siraitares,

Welcome to the Ubuntu forums.  :-)

I don't know why Grub 2 isn't picking up Fedora. Until you find a solution, you can paste this below the existing lines in */etc/grub.d/40 custom*. 



You will have to edit the file as root. Paste the contents, save the file, and then update grub (*update-grub* run as root) to incorporate the changes into the Grub 2 menu.

Disclaimer: I don't use Fedora and constructed this from your Grub legacy entries. If they don't work, someone using Fedora can probably help spot the problem.
Hey, thanks for the help! I just tried that and it didn't work ):

---

### Post by drs305 on 2010-10-18
> **siraitares said:**
> Hey, thanks for the help! I just tried that and it didn't work ):

As I said, it was a guess. I tried 'translating' into Grub 2 but haven't used Fedora. Someone who has incorporated Fedora into Grub2 may come by the thread, or I'm sure you can find someone at wherever the Fedora users hang out.

They may also know how to get Grub 2 to pick up the OS, which of course would be the better option.

---

### Post by siraitares on 2010-10-18
Nevermind, it DID work. Stupid me forgot to update grub haha.
Thanks a lot, you've been really helpful! :)

---

