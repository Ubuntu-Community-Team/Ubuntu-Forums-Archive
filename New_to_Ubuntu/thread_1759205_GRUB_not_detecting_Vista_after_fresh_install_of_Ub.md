---
title: "GRUB not detecting Vista after fresh install of Ubuntu 10.10"
date: 2011-05-15
forum: New to Ubuntu
---

### Post by dkc.com on 2011-05-15
Hi friends,

I was using my Dell Inspiron 1520 with Vista and Ubuntu 10.10 happily. But, unfortunately I upgraded to ubuntu 11.04 and it didn't work out for me so Using GParted I deleted Ubuntu partition (booted to Vista just to check) and did a fresh install of Ubuntu 10.10. Now there is no Windows Vista in my GRUB menu. How can I solve it.

Thanks.

---

### Post by SoFl W on 2011-05-15
Go here and follow the instructions, post the results.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by gandaran on 2011-05-15
> **dkc.com said:**
> Hi friends,

I was using my Dell Inspiron 1520 with Vista and Ubuntu 10.10 happily. But, unfortunately I upgraded to ubuntu 11.04 and it didn't work out for me so Using GParted I deleted Ubuntu partition (booted to Vista just to check) and did a fresh install of Ubuntu 10.10. Now there is no Windows Vista in my GRUB menu. How can I solve it.

Thanks.
install gparted and have a look if the vista partition is still there, if it is try the grub update command
```
sudo update-grub
```

---

### Post by dkc.com on 2011-05-15
> **SoFl W said:**
> Go here and follow the instructions, post the results.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

following is my results.txt file:

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
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
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

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       224,909       224,847  de Dell Utility
/dev/sda2    *        225,280    21,196,799    20,971,520   7 HPFS/NTFS
/dev/sda3          21,205,800   105,097,229    83,891,430   7 HPFS/NTFS
/dev/sda4         105,097,291   234,436,544   129,339,254   5 Extended
/dev/sda5         105,097,293   168,007,768    62,910,476   7 HPFS/NTFS
/dev/sda6         230,918,373   234,436,544     3,518,172  82 Linux swap / Solaris
/dev/sda7         168,011,776   230,918,143    62,906,368  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07D7-0A0C                              vfat       DellUtility                   
/dev/sda2        E4248FAE248F81F2                       ntfs       AKC_2                         
/dev/sda3        1684D91A84D8FD65                       ntfs       AKC_1                         
/dev/sda4: PTTYPE="dos" 
/dev/sda5        3F2133785B2FE97D                       ntfs       AKC_3                         
/dev/sda6        67fa1866-2593-4402-92f1-f74984640207   swap                                     
/dev/sda7        320f1a16-aed9-4377-a945-77710ec954c6   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro,commit=0)


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
search --no-floppy --fs-uuid --set 320f1a16-aed9-4377-a945-77710ec954c6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 320f1a16-aed9-4377-a945-77710ec954c6
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 320f1a16-aed9-4377-a945-77710ec954c6
    linux    /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=320f1a16-aed9-4377-a945-77710ec954c6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 320f1a16-aed9-4377-a945-77710ec954c6
    echo    'Loading Linux 2.6.35-28-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=320f1a16-aed9-4377-a945-77710ec954c6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 320f1a16-aed9-4377-a945-77710ec954c6
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 320f1a16-aed9-4377-a945-77710ec954c6
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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
UUID=320f1a16-aed9-4377-a945-77710ec954c6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=67fa1866-2593-4402-92f1-f74984640207 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


  92.7GB: boot/grub/core.img
 103.3GB: boot/grub/grub.cfg
  87.4GB: boot/initrd.img-2.6.35-28-generic-pae
  92.6GB: boot/vmlinuz-2.6.35-28-generic-pae
  87.4GB: initrd.img
  92.6GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  80 00 00 00 01 00 04 80  50 00 00 00 60 00 00 00  |........P...`...|
00000010  00 00 00 00 14 00 00 00  02 00 3c 00 02 00 00 00  |..........<.....|
00000020  00 00 18 00 ff 01 1f 00  01 02 00 00 00 00 00 05  |................|
00000030  20 00 00 00 20 02 00 00  00 00 14 00 ff 01 1f 00  | ... ...........|
00000040  01 01 00 00 00 00 00 05  12 00 00 00 01 01 00 00  |................|
00000050  00 00 00 05 01 02 00 00  00 00 00 05 20 00 00 00  |............ ...|
00000060  20 02 00 00 01 01 00 00  00 00 00 05 12 00 00 00  | ...............|
00000070  a4 0d 34 81 8c 01 00 00  70 5a 00 00 00 00 00 00  |..4.....pZ......|
00000080  70 00 00 00 01 00 04 80  40 00 00 00 50 00 00 00  |p.......@...P...|
00000090  00 00 00 00 14 00 00 00  02 00 2c 00 01 00 00 00  |..........,.....|
000000a0  00 00 14 00 ff 01 1f 00  01 01 00 00 00 00 00 05  |................|
000000b0  12 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000c0  00 00 65 00 01 02 00 00  00 00 00 05 20 00 00 00  |..e......... ...|
000000d0  20 02 00 00 01 01 00 00  00 00 00 05 12 00 00 00  | ...............|
000000e0  33 da c9 01 8d 01 00 00  e0 5a 00 00 00 00 00 00  |3........Z......|
000000f0  70 00 00 00 01 00 04 80  40 00 00 00 50 00 00 00  |p.......@...P...|
00000100  00 00 00 00 14 00 00 00  02 00 2c 00 01 00 00 00  |..........,.....|
00000110  00 00 14 00 ff 01 1f 00  01 01 00 00 00 00 00 05  |................|
00000120  12 00 00 00 00 00 10 00  00 00 00 00 80 80 00 00  |................|
00000130  04 70 c5 8e 01 02 00 00  00 00 00 05 20 00 00 00  |.p.......... ...|
00000140  20 02 00 00 01 01 00 00  00 00 00 05 12 00 00 00  | ...............|
00000150  06 c4 44 33 8e 01 00 00  50 5b 00 00 00 00 00 00  |..D3....P[......|
00000160  70 00 00 00 01 00 04 80  40 00 00 00 50 00 00 00  |p.......@...P...|
00000170  00 00 00 00 14 00 00 00  02 00 2c 00 01 00 00 00  |..........,.....|
00000180  00 00 14 00 ff 01 1f 00  01 01 00 00 00 00 00 05  |................|
00000190  12 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  90 0d 18 86 01 02 00 00  00 00 00 05 20 00 00 00  |............ ...|
000001b0  20 02 00 00 01 01 00 00  00 00 00 05 12 00 00 fe  | ...............|
000001c0  ff ff 07 fe ff ff 02 00  00 00 0c f0 bf 03 00 fe  |................|
000001d0  ff ff 05 fe ff ff 5b e0  7f 07 1b af 35 00 00 00  |......[.....5...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by dkc.com on 2011-05-15
> **gandaran said:**
> install gparted and have a look if the vista partition is still there, if it is try the grub update command
```
sudo update-grub
```

Hi friend,

I just followed the script mentioned above your reply and pasted it's result. What do you think, should I still go with grub update?

Thanks.

---

### Post by gandaran on 2011-05-15
> **dkc.com said:**
> Hi friend,

I just followed the script mentioned above your reply and pasted it's result. What do you think, should I still go with grub update?

Thanks.
yes, boot ubuntu and run the command, it mite not work but wont do any damage either

---

### Post by dkc.com on 2011-05-15
> **gandaran said:**
> yes, boot ubuntu and run the command, it mite not work but wont do any damage either

Also ran "sudo update-grub" and it found a new image and updated it self. I restarted but did not help.

---

### Post by gandaran on 2011-05-15
> **dkc.com said:**
> Also ran "sudo update-grub" and it found a new image and updated it self. I restarted but did not help.
what was the output? did it show any error?

---

### Post by dkc.com on 2011-05-15
> **gandaran said:**
> what was the output? did it show any error?

Here is the output:

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-28-generic-pae
Found initrd image: /boot/initrd.img-2.6.35-28-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
done

---

### Post by dkc.com on 2011-05-15
Screenshot from GParted, if it helps:

[IMG]https://lh5.googleusercontent.com/_QDqgNwjwgCk/TdBDCYlPZaI/AAAAAAAACfY/4YJvJdaPhj0/s720/GParted.png[/IMG]

---

### Post by Quackers on 2011-05-15
Will you just check something please?
Open synaptic package manager and in the search box enter os-prober and when it appears in the main window it should have a green box to its left, to show that it is installed. If it doesn't please install it and try sudo update-grub again.

---

### Post by dkc.com on 2011-05-15
> **Quackers said:**
> Will you just check something please?
Open synaptic package manager and in the search box enter os-prober and when it appears in the main window it should have a green box to its left, to show that it is installed. If it doesn't please install it and try sudo update-grub again.

Bingo!!!!!!

os-prober installation worked for me. It wasn't there. After installing it, when I ran sudo update-grub, I got the following result:

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-28-generic-pae
Found initrd image: /boot/initrd.img-2.6.35-28-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Found Dell Utility Partition on /dev/sda1
Found Windows Vista (loader) on /dev/sda2
Found Windows Recovery Environment (loader) on /dev/sda3
done

After restart, it's now showing Vista in grub.

One of the most important reasons I love ubuntu is this community support.

Thanks to all of my friends who read and answer my query. A friend in need is friend indeed.

---

