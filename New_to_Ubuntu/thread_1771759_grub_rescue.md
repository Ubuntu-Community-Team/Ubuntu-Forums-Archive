---
title: "grub rescue"
date: 2011-05-30
forum: New to Ubuntu
---

### Post by lcflwt on 2011-05-30
After looking through the forums for "just my situation," I find I have to start a new thread.

The history: Been using Acer Aspire One netbook for 6 months with Grub 1.97-1.98 loading UNE after a failed attempt using Mint (no network card support). Today for the first time I attempted to run Vista to try to get the driver for a new Lexmark S305 printer/scanner. NO partition removals/upgrades/reloads.

The problem: Vista never loaded, then error messages ended with grub rescue prompt.

What I have done so far: Boot info script - I see that I have no partition 7, but I also see that I have no Ubuntu labeled partition and that concerns me. The mint I would like to get rid of anyway. And why does windows need 3 partitions?

```
 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 7 for (,msdos7)/boot/grub.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /BOOT/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 9 Isadora
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 3.86 2010-04-01
    Boot sector info:   Syslinux looks at sector 15234896 of /dev/sdb1 for 
                       its second stage. No errors found in the Boot 
                       Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    27,265,023    27,262,976  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     27,265,024    27,469,823       204,800   7 NTFS / exFAT / HPFS
/dev/sda3          27,469,824   116,579,824    89,110,001   7 NTFS / exFAT / HPFS
/dev/sda4         116,580,350   312,580,095   195,999,746   5 Extended
/dev/sda5         182,044,672   307,165,183   125,120,512  83 Linux
/dev/sda6         307,167,232   312,580,095     5,412,864  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 8019 MB, 8019509248 bytes
247 heads, 62 sectors/track, 1022 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             62    15,650,907    15,650,846   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        FA024C4D024C1155                       ntfs       PQSERVICE
/dev/sda2        0A324CA9324C9B97                       ntfs       SYSTEM RESERVED
/dev/sda3        1C4C4E3A4C4E0EC8                       ntfs       Acer
/dev/sda5        f6b9894a-6b2e-494c-be13-2f3083b4f4af   ext4       
/dev/sda6        0eade7cd-11c7-4569-a2fd-48ee270d309b   swap       
/dev/sdb1        80C3-F877                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
search --no-floppy --fs-uuid --set f6b9894a-6b2e-494c-be13-2f3083b4f4af
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
search --no-floppy --fs-uuid --set f6b9894a-6b2e-494c-be13-2f3083b4f4af
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
search --no-floppy --fs-uuid --set f6b9894a-6b2e-494c-be13-2f3083b4f4af
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
    search --no-floppy --fs-uuid --set f6b9894a-6b2e-494c-be13-2f3083b4f4af
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=f6b9894a-6b2e-494c-be13-2f3083b4f4af ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda5) -- recovery mode" --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set f6b9894a-6b2e-494c-be13-2f3083b4f4af
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=f6b9894a-6b2e-494c-be13-2f3083b4f4af ro single 
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
    search --no-floppy --fs-uuid --set f6b9894a-6b2e-494c-be13-2f3083b4f4af
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set f6b9894a-6b2e-494c-be13-2f3083b4f4af
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set fa024c4d024c1155
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 0a324ca9324c9b97
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=f6b9894a-6b2e-494c-be13-2f3083b4f4af /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=0eade7cd-11c7-4569-a2fd-48ee270d309b none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 106.933986664 = 114.819493888  boot/grub/core.img                             1
  90.980461121 = 97.689526272   boot/grub/grub.cfg                             1
 107.068435669 = 114.963857408  boot/initrd.img-2.6.32-21-generic              1
 106.961761475 = 114.849316864  boot/vmlinuz-2.6.32-21-generic                 1
 107.068435669 = 114.963857408  initrd.img                                     1
 106.961761475 = 114.849316864  vmlinuz                                        1

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/vesamenu.c32              :  COM32R module (v3.xx)

```Desired outcome A: have only Vista/7 and UNE available as Grub options.
Desired outcome B: scrap Grub and just have a UNE machine, after all I went 6 months Windows-free. Oh, and have someone tell me how to get the Lexmark driver to load :)

I have a USB allowing me to function on this machine as well as a windows machine next door for continuing communication. My experience status is novice.

thanks

---

### Post by Quackers on 2011-05-30
Is there more than one entry in the grub menu for Vista?
If so, try booting the one that ends with /dev/sda2 (even if it refers to the Recovery Environment.
You also appear to have chopped off most of the contents of the Results.txt file.

---

### Post by lcflwt on 2011-05-30
Sorry about the incomplete bootinfoscript, I have edited it in the initial post.

I can no longer get to the grub menu to see pressently how many Vista options were offered. If memory serves, I had a Vista option, and a Windows 7 option. About once a month, grub would add a duplicate ubuntu option, I had five.

---

### Post by Quackers on 2011-05-30
Grub is looking in partition sda7 for its boot files. There is no sda7. Have you deleted a partition? It seems you have deleted UNE as the only system besides Windows 7 is Linux Mint 9, which is in sda5.
I suggest you boot from the Linux Mint live cd (or the Ubuntu cd) and select the live desktop (try ubuntu or try Linux Mint) and open up a terminal and run these commands.
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
``` and if that reports no errors you can reboot - hopefully to a grub menu.

---

### Post by lcflwt on 2011-05-30
Quackers,

Thankyou, performing those commands took me to the grub menu as promised. Based on the results file, are you able to tell this newbie where my files may be located? In Ubuntu live (from USB stick) I was unable to locate them using the file manager. Will I be able to retrieve them by reloading UNE?

Crossing my fingers,

lcflwt

---

### Post by drs305 on 2011-05-30
Were the files you are looking for on the Mint partition?

If you still can't boot Mint or other OS from the grub prompt, from the LiveCD/USB you can mount sda5 and then use a file browser to inspect, copy or move any files you are interested in.
```

sudo mount /dev/sda5 /mnt
gksu nautilus /mnt
```

---

### Post by lcflwt on 2011-05-30
Linux Mint boots. Unfortunately I see no files. All were built in Ubuntu and were located in /home/myname.

In using Mint, shouldn't I be able to see them if they exist? 

And researching the cause...I did not attempt to reload or update anything. I restarted the system and selected Vista from grub, which did not load but gave me the grub rescue prompt. Any opinions on what happened?

Speaking of oddity, on reboot this time, I chose Vista from grub. Mint came up.

lsof? 
**DOWNLOAD & BUY Linux Data Recovery Software Tool - anyone have any opinions on these?**

---

### Post by lcflwt on 2011-05-31
The fix ended up being testdisk to recover the partition and

[https://help.ubuntu.com/community/Grub2#METHOD%203%20-%20CHROOT](https://help.ubuntu.com/community/Grub2#METHOD%203%20-%20CHROOT)

to repair the GRUB.

Now to figure out WHY it happened in the first place....

Thanks for all your help, this forum is great!

---

