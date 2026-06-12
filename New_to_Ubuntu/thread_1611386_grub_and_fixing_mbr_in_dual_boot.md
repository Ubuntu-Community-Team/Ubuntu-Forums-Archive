---
title: "grub and fixing mbr in dual boot"
date: 2010-11-01
forum: New to Ubuntu
---

### Post by tadcan on 2010-11-01
A friend called. he has a dual boot windows 7 and ubuntu 10.04 installation. Now when windows is chosen an mbr error is given. 

If I use a windows disk to fix the mbr will this remove grub. If so can I fix through grub.

---

### Post by papibe on 2010-11-01
Been there, done that... it's scary but not deadly! ;)

You can repair the mbr block with the original Window Disk. This will kill grub (just grub, not your Linux partitions), but you have no choice here, just do it. Fortunately, you can restore grub.

Check my post [here]("http://ubuntuforums.org/showpost.php?p=9498158&postcount=1155").

Good Luck!

---

### Post by tadcan on 2010-11-01
ouch that does look scary. Did you use the reinstalling from live cd method.

When the time comes I'll probably be asking specific questions, since this is beyond what I normally do.

---

### Post by papibe on 2010-11-01
> **tadcan said:**
> Did you use the reinstalling from live cd method.
Yes. At the moment I did it, only method 3 was available (under "Reinstalling from LiveCD"). Maybe now using methods 1 or 2 could be easier.

Regards.

---

### Post by garvinrick4 on 2010-11-01
Do you have a live CD (install cd for Ubuntu) if you do use Try Ubuntu  and open a terminal and and Download this script to DESKTOP and then run  the code I give you below. Will put a text file on Desktop after  running code. Copy and Paste to this Thread, will then be able to tell  you code to replace grub2 in mbr.

[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/") 
 	Code:
 	```
 sudo bash ~/Desktop/boot_info_script*.sh
```

---

### Post by wilee-nilee on 2010-11-01
> **garvinrick4 said:**
> do you have a live cd (install cd for ubuntu) if you do use try ubuntu  and open a terminal and and download this script to desktop and then run  the code i give you below. Will put a text file on desktop after  running code. Copy and paste to this thread, will then be able to tell  you code to replace grub2 in mbr.

[sourceforge.net: Boot info script - project web hosting - open source software]("http://bootinfoscript.sourceforge.net/") 
 	code:
 	```
 sudo bash ~/desktop/boot_info_script*.sh
```

+1

---

### Post by tadcan on 2010-11-01
> **papibe said:**
> Yes. At the moment I did it, only method 3 was available (under "Reinstalling from LiveCD"). Maybe now using methods 1 or 2 could be easier.

Regards.

Thanks. I presumed method 2 was not an option since the installed partition will have been over written with the windows mbr. So I planned to try method one first and as a last resort try chroot.

---

### Post by tadcan on 2010-11-01
> **garvinrick4 said:**
> Do you have a live CD (install cd for Ubuntu) if you do use Try Ubuntu  and open a terminal and and Download this script to DESKTOP and then run  the code I give you below. Will put a text file on Desktop after  running code. Copy and Paste to this Thread, will then be able to tell  you code to replace grub2 in mbr.

[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/") 
 	Code:
 	```
 sudo bash ~/Desktop/boot_info_script*.sh
```

When I am at my friends place on wednesday I'll do that. Doing some research first before I arrive.

---

### Post by garvinrick4 on 2010-11-01
this will put windows to boot but not ubuntu:
Put in ubuntu install cd and choose Try Ubuntu open a terminal and copy and paste:
```
sudo apt-get install lilo
``````
sudo lilo -M /dev/sda mbr
``` Will say error but ignore we only want mbr.
To put grub2 back to boot both: Use the live cd and in terminal:
I am using sda5 use your own sda# by running
```
sudo fdisk -l
``` (small L) 
then using your own Ubuntu install #
```
sudo mkdir /media/root
``````
sudo mount /dev/sda5 /media/root
``````
sudo grub-install --recheck --root-directory=/media/root /dev/sda
``````
sudo umount /media/root
```not a typo umount
Reboot into harddrive Ubuntu and.
```
sudo update-grub
```done both will boot if nothing unusual in bootscript, running blind without it. This is normal fix above. Here is link for using Windows 7 disk to install windows boot loader.
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by tadcan on 2010-11-03
I'm starting to fix tye problem now. The mbr has bee reset for windows. Now have to fix grub.

```

Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2. But according to the info from fdisk, 
                       sda5 starts at sector 2048.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,046    71,696,383    71,694,338   5 Extended
/dev/sda5               2,048    30,738,431    30,736,384   7 HPFS/NTFS
/dev/sda6          30,740,480    69,900,287    39,159,808  83 Linux
/dev/sda7          69,902,336    71,696,383     1,794,048  82 Linux swap / Solaris
/dev/sda2    *     71,698,095   488,392,064   416,693,970   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1: PTTYPE="dos" 
/dev/sda2        129C50839C506371                       ntfs       MyDocs                        
/dev/sda5        D87037FE7037E244                       ntfs                                     
/dev/sda6        5986b5f7-298f-4670-bde6-6f6d4d144bff   ext4                                     
/dev/sda7        7b8b8768-89f7-4f3d-9673-8f673122dc46   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 5986b5f7-298f-4670-bde6-6f6d4d144bff
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 5986b5f7-298f-4670-bde6-6f6d4d144bff
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
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 5986b5f7-298f-4670-bde6-6f6d4d144bff
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=5986b5f7-298f-4670-bde6-6f6d4d144bff ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 5986b5f7-298f-4670-bde6-6f6d4d144bff
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=5986b5f7-298f-4670-bde6-6f6d4d144bff ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 5986b5f7-298f-4670-bde6-6f6d4d144bff
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=5986b5f7-298f-4670-bde6-6f6d4d144bff ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 5986b5f7-298f-4670-bde6-6f6d4d144bff
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=5986b5f7-298f-4670-bde6-6f6d4d144bff ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 5986b5f7-298f-4670-bde6-6f6d4d144bff
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=5986b5f7-298f-4670-bde6-6f6d4d144bff ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 5986b5f7-298f-4670-bde6-6f6d4d144bff
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=5986b5f7-298f-4670-bde6-6f6d4d144bff ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 5986b5f7-298f-4670-bde6-6f6d4d144bff
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=5986b5f7-298f-4670-bde6-6f6d4d144bff ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 5986b5f7-298f-4670-bde6-6f6d4d144bff
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=5986b5f7-298f-4670-bde6-6f6d4d144bff ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 5986b5f7-298f-4670-bde6-6f6d4d144bff
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=5986b5f7-298f-4670-bde6-6f6d4d144bff ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 5986b5f7-298f-4670-bde6-6f6d4d144bff
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=5986b5f7-298f-4670-bde6-6f6d4d144bff ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 5986b5f7-298f-4670-bde6-6f6d4d144bff
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 5986b5f7-298f-4670-bde6-6f6d4d144bff
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 129c50839c506371
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=5986b5f7-298f-4670-bde6-6f6d4d144bff /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=7b8b8768-89f7-4f3d-9673-8f673122dc46 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


  24.6GB: boot/grub/core.img
  18.2GB: boot/grub/grub.cfg
  24.7GB: boot/initrd.img-2.6.32-21-generic
  22.7GB: boot/initrd.img-2.6.32-22-generic
  20.1GB: boot/initrd.img-2.6.32-23-generic
  24.8GB: boot/initrd.img-2.6.32-24-generic
  25.1GB: boot/initrd.img-2.6.32-25-generic
  24.6GB: boot/vmlinuz-2.6.32-21-generic
  31.3GB: boot/vmlinuz-2.6.32-22-generic
  26.8GB: boot/vmlinuz-2.6.32-23-generic
  25.2GB: boot/vmlinuz-2.6.32-24-generic
  33.5GB: boot/vmlinuz-2.6.32-25-generic
  25.1GB: initrd.img
  24.8GB: initrd.img.old
  33.5GB: vmlinuz
  25.2GB: vmlinuz.old
```

---

### Post by tadcan on 2010-11-03
I tried garvinrick4 steps. Now I get a message saying grub error file not found.

For sudo fdisk -l there is a * at sda2 which means this is the active partition. So I changed sda5 with sda2. Can someone confirm this is correct.

---

### Post by papibe on 2010-11-03
Is Windows booting ok?

If so, try restoring grub using th live CD. If not, I'd go with my original suggestion (Windows CD to restore mbr, and then live CD to restore Grub).

Good Luck.

---

### Post by oldfred on 2010-11-03
Boot flag has to be on a primary partition and is only used by windows. But some BIOS will not let you boot unless you have a boot flag on a primary partition.

Your windows boots from sda2 which has the initial windows boot files. The main install is in sda5 which is a logical partition. Windows will not directly boot an install in logical partitions but only boot thru a primary partition.

You boot flag has to be on sda2 to use windows boot loader. But once you reinstall grub2 it will not matter as grub will not use it.

---

### Post by tadcan on 2010-11-03
> **papibe said:**
> Is Windows booting ok?

If so, try restoring grub using th live CD. If not, I'd go with my original suggestion (Windows CD to restore mbr, and then live CD to restore Grub).

Good Luck.

The windows partition was fixed, but the attempt to fix grub failed. Now Grub is giving me an error when I boot.

> **oldfred said:**
> Boot flag has to be on a primary partition and is only used by windows. But some BIOS will not let you boot unless you have a boot flag on a primary partition.

Your windows boots from sda2 which has the initial windows boot files. The main install is in sda5 which is a logical partition. Windows will not directly boot an install in logical partitions but only boot thru a primary partition.

You boot flag has to be on sda2 to use windows boot loader. But once you reinstall grub2 it will not matter as grub will not use it.

If I understand correctly I can try the previous instructions but leave sd5 since grub is mainly for linux. If not I'll have look at he ubuntu grub page and follow that.

---

### Post by tadcan on 2010-11-03
I followed the instructions and have the grub command line. How do I boot into ubuntu from there.

---

### Post by tadcan on 2010-11-03
Am following the command line instructions from the ubuntu website. for the 
```
linux /vmlinuz root=/dev/sdXY ro
``` command it gives me a file not found. When I use tab to find possible answers it just gives me windows file option. 

I may just take the lazy way out. Back up the files and reinstall ubuntu.

---

### Post by tadcan on 2010-11-03
had another look, opps I should have put in hd0,6 not hd0,5.
Was able to boot into the kernel but was then dropped into the busybox shell
Which is kind of ironic because the first time I tried to install ubuntu it didn't work because of busybox.

---

### Post by oldfred on 2010-11-03
Did you just put in the one line?

set root=(hd0,6)
linux /vmlinuz root=/dev/sda6 ro
initrd /initrd.img
boot

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
chroot & grub uninstall & reinstall
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by tadcan on 2010-11-03
[edit] no i did it in separate lines, pressing enter after each one[edit]

However have re-installed ubuntu and it didn't recognize windows, ie no grub at all. Not sure what I did.

---

### Post by oldfred on 2010-11-03
Hopefully you did not overwrite either sda2 or sda5.

You can post the boot script again, so we can see what has changed.

---

### Post by tadcan on 2010-11-04
No I did not overwrite the sd2 or sd5. They are both mountable. 

[Grip]The new installer doesn't have the install on continuous free that 10.04 has. It doesn't have a write over this OS, just a install beside.[/Grip]

I didn't use the chroot option either, i got annoyed and tried to use the method I presumed would just work.

Talking to my friend, he just uses win7 for itunes syncing. So I'm learning about virtualbox since otherwise its a waste HD space. While part of me wants to figure it out, my friend just wants a functioning computer. Will be back on friday and will post then.

---

