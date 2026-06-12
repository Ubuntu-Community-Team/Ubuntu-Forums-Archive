---
title: "need to clean up partitions"
date: 2011-03-25
forum: New to Ubuntu
---

### Post by calfee1 on 2011-03-25
Here is the result of terminal run:
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *           8       17414   139819247+   7  HPFS/NTFS
/dev/sda3           17414       60801   348507681+   5  Extended
/dev/sda5           32007       47606   125301522   83  Linux
/dev/sda6           60687       60801      923706   82  Linux swap / Solaris
/dev/sda7           17414       31408   112404480   83  Linux
/dev/sda8           31408       32006     4805632   82  Linux swap / Solaris
/dev/sda9           47606       60149   100753408   83  Linux
/dev/sda10          60149       60686     4315136   82  Linux swap / Solaris

I want to keep my widows XP which is sda2 i think. I know there is 2 versions of lubuntu and all I want is the newest version. How do I tell??
and what is the rest of this stuff????:confused:

thanks

---

### Post by mikewhatever on 2011-03-25
You seem to have three Ubuntu installations and three swap partitions. To find out where the newest installation is, boot is and post the output of the **df -h** command.

---

### Post by calfee1 on 2011-03-25
jim@jim:~$ df -h 
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda9              95G   25G   66G  28% /
none                  1.5G  284K  1.5G   1% /dev
none                  1.5G  116K  1.5G   1% /dev/shm
none                  1.5G   96K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
none                   95G   25G   66G  28% /var/lib/ureadahead/debugfs
jim@jim:~$

---

### Post by Dutch70 on 2011-03-25
You can also open Gparted and take a screenshot. Attach it to your next post using the paper clip in the toolbar.

tip: try to get a good sized pic by ticking "select area to grab" when taking the screenshot.

---

### Post by mikewhatever on 2011-03-25
The output shows that /dev/sda9 is the root partition of the latest installation, /dev/sda10 is likely the swap, which means the following partitions can be removed:
```

/dev/sda5 32007 47606 125301522 83 Linux
/dev/sda6 60687 60801 923706 82 Linux swap / Solaris
/dev/sda7 17414 31408 112404480 83 Linux
/dev/sda8 31408 32006 4805632 82 Linux swap / Solaris

```

---

### Post by calfee1 on 2011-03-28
> **mikewhatever said:**
> The output shows that /dev/sda9 is the root partition of the latest installation, /dev/sda10 is likely the swap, which means the following partitions can be removed:
```

/dev/sda5 32007 47606 125301522 83 Linux
/dev/sda6 60687 60801 923706 82 Linux swap / Solaris
/dev/sda7 17414 31408 112404480 83 Linux
/dev/sda8 31408 32006 4805632 82 Linux swap / Solaris

```
and this will ssave my newest ubunu and windows XP??

---

### Post by calfee1 on 2011-03-28
screenshot

---

### Post by Dutch70 on 2011-03-28
> **calfee1 said:**
> and this will ssave my newest ubunu and windows XP??

Yes
After you delete them, run "sudo update-grub" in a terminal without the quotes.
If you have anything in those partitions you want to keep, better back it up. You can probably just copy/paste it into a folder in sda9.
Likely showing up in nautilus as "96 GB filesystem I believe.

Just so you don't freak out...lol. 
When you delete sda5-6-7-8, sda9 & 10 will probably become sda5 & 6. :P

Also, you're going to end up with a bunch of unallocated space & you will need to move some stuff around.

---

### Post by calfee1 on 2011-03-28
I am stuck. I know I have done this before but???

Go delete partition 5 and i get this message....Please unmount any logical partitions having a number higher than 5

have no idea what this means.

---

### Post by Dutch70 on 2011-03-28
Mounted means it's in use. You'll have to do it from the live cd.

Also I noticed a little yellow triangle next to sda8 I think, right click it and select information to see what that is. 
I doubt it's important though.

---

### Post by calfee1 on 2011-03-28
> **Dutch70 said:**
> Mounted means it's in use. You'll have to do it from the live cd.

Also I noticed a little yellow triangle next to sda8 I think, right click it and select information to see what that is. 
I doubt it's important though.

Thanks, got to find my live cd version of gparted
screen shot of sda8 triangle

---

### Post by Dutch70 on 2011-03-28
Gparted is on the live cd with Ubuntu on it. If you don't have one, a usb stick would be better.

That's about what I thought on that partition, don't worry about that.

---

### Post by calfee1 on 2011-03-28
I am using live CD of gparted and I get that same message...what am i doing wrong????

---

### Post by Dutch70 on 2011-03-28
Please post a screenshot of gparted from the live cd

---

### Post by calfee1 on 2011-03-28
> **Dutch70 said:**
> Please post a screenshot of gparted from the live cd

I go to delete partition 5...i get this...using live cd too

---

### Post by Dutch70 on 2011-03-28
Ok...right click both of your swap partitions and select "swapoff", then right click sda3 and select unmount if it's still mounted. 

Then try to delete the partitions.

---

### Post by newbuntuxx on 2011-03-28
Also, if you have multiple linux/ubuntu installations, you do not need to create a swap partition for each. You can use one swap partition for all.

---

### Post by calfee1 on 2011-03-29
I messed something up. I was able to delete the partitions as directed but now my computer wont boot. Here is a pic of gparted using live cd......what the heck did i do???

---

### Post by Dutch70 on 2011-03-29
Please post your boot info script

To post your boot info script, boot up to your live cd/usb,  download the boot info script from the following link & save it to your desktop. 
[COLOR="RoyalBlue"][[COLOR="RoyalBlue"]http://bootinfoscript.sourceforge.net/[/COLOR]]("http://bootinfoscript.sourceforge.net/")[/COLOR]
Then open a terminal (Cntrl+Alt+T) and run the following command...

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a results.txt file on your desktop. Open that file and copy/paste the info  **between code tags** using the "#" symbol in the toolbar of your next post.

To put it between code tags, just highlight the info and click the # symbol in the toolbar.

---

### Post by calfee1 on 2011-03-29
i posted wrong and changed in another post...sorry

---

### Post by calfee1 on 2011-03-29
> **Dutch70 said:**
> Please post your boot info script

To post your boot info script, boot up to your live cd/usb,  download the boot info script from the following link & save it to your desktop. 
[COLOR=RoyalBlue][[COLOR=RoyalBlue]http://bootinfoscript.sourceforge.net/[/COLOR]]("http://bootinfoscript.sourceforge.net/")[/COLOR]
Then open a terminal (Cntrl+Alt+T) and run the following command...

```
sudo bash ~/Desktop/boot_info_script*.sh
```This will create a results.txt file on your desktop. Open that file and copy/paste the info  **between code tags** using the "#" symbol in the toolbar of your next post.

To put it between code tags, just highlight the info and click the # symbol in the toolbar.
I hope the above post was what you were looking for......:)

---

### Post by calfee1 on 2011-03-29
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #9 for (,msdos9)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

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

/dev/sda1                  63       112,454       112,392  de Dell Utility
/dev/sda2    *        112,455   279,750,949   279,638,495   7 HPFS/NTFS
/dev/sda3         279,752,702   976,768,064   697,015,363   5 Extended
/dev/sda5         764,780,544   966,287,359   201,506,816  83 Linux
/dev/sda6         966,289,408   974,919,679     8,630,272  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        07D8-0B07                              vfat       DellUtility                   
/dev/sda2        7654199C54195FE3                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        39979148-29d5-441f-99ed-7f59688ce586   ext4                                     
/dev/sda6        ace89351-a106-4ca6-bba7-f6713704f88e   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

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
set root='(hd0,msdos9)'
search --no-floppy --fs-uuid --set 39979148-29d5-441f-99ed-7f59688ce586
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos9)'
search --no-floppy --fs-uuid --set 39979148-29d5-441f-99ed-7f59688ce586
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 39979148-29d5-441f-99ed-7f59688ce586
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=39979148-29d5-441f-99ed-7f59688ce586 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 39979148-29d5-441f-99ed-7f59688ce586
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=39979148-29d5-441f-99ed-7f59688ce586 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 39979148-29d5-441f-99ed-7f59688ce586
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=39979148-29d5-441f-99ed-7f59688ce586 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 39979148-29d5-441f-99ed-7f59688ce586
    echo    'Loading Linux 2.6.35-27-generic ...'
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=39979148-29d5-441f-99ed-7f59688ce586 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 39979148-29d5-441f-99ed-7f59688ce586
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=39979148-29d5-441f-99ed-7f59688ce586 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 39979148-29d5-441f-99ed-7f59688ce586
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=39979148-29d5-441f-99ed-7f59688ce586 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 39979148-29d5-441f-99ed-7f59688ce586
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=39979148-29d5-441f-99ed-7f59688ce586 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 39979148-29d5-441f-99ed-7f59688ce586
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=39979148-29d5-441f-99ed-7f59688ce586 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 39979148-29d5-441f-99ed-7f59688ce586
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=39979148-29d5-441f-99ed-7f59688ce586 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 39979148-29d5-441f-99ed-7f59688ce586
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=39979148-29d5-441f-99ed-7f59688ce586 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 39979148-29d5-441f-99ed-7f59688ce586
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=39979148-29d5-441f-99ed-7f59688ce586 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 39979148-29d5-441f-99ed-7f59688ce586
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=39979148-29d5-441f-99ed-7f59688ce586 ro single 
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
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 39979148-29d5-441f-99ed-7f59688ce586
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 39979148-29d5-441f-99ed-7f59688ce586
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 7654199c54195fe3
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu 9.04, kernel 2.6.28-19-generic (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 59c7e91d-9955-471a-ae7d-90f357ab42a0
    linux /boot/vmlinuz-2.6.28-19-generic root=UUID=59c7e91d-9955-471a-ae7d-90f357ab42a0 ro quiet splash
    initrd /boot/initrd.img-2.6.28-19-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-19-generic (recovery mode) (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 59c7e91d-9955-471a-ae7d-90f357ab42a0
    linux /boot/vmlinuz-2.6.28-19-generic root=UUID=59c7e91d-9955-471a-ae7d-90f357ab42a0 ro single
    initrd /boot/initrd.img-2.6.28-19-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-18-generic (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 59c7e91d-9955-471a-ae7d-90f357ab42a0
    linux /boot/vmlinuz-2.6.28-18-generic root=UUID=59c7e91d-9955-471a-ae7d-90f357ab42a0 ro quiet splash
    initrd /boot/initrd.img-2.6.28-18-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-18-generic (recovery mode) (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 59c7e91d-9955-471a-ae7d-90f357ab42a0
    linux /boot/vmlinuz-2.6.28-18-generic root=UUID=59c7e91d-9955-471a-ae7d-90f357ab42a0 ro single
    initrd /boot/initrd.img-2.6.28-18-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-17-generic (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 59c7e91d-9955-471a-ae7d-90f357ab42a0
    linux /boot/vmlinuz-2.6.28-17-generic root=UUID=59c7e91d-9955-471a-ae7d-90f357ab42a0 ro quiet splash
    initrd /boot/initrd.img-2.6.28-17-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode) (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 59c7e91d-9955-471a-ae7d-90f357ab42a0
    linux /boot/vmlinuz-2.6.28-17-generic root=UUID=59c7e91d-9955-471a-ae7d-90f357ab42a0 ro single
    initrd /boot/initrd.img-2.6.28-17-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-16-generic (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 59c7e91d-9955-471a-ae7d-90f357ab42a0
    linux /boot/vmlinuz-2.6.28-16-generic root=UUID=59c7e91d-9955-471a-ae7d-90f357ab42a0 ro quiet splash
    initrd /boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode) (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 59c7e91d-9955-471a-ae7d-90f357ab42a0
    linux /boot/vmlinuz-2.6.28-16-generic root=UUID=59c7e91d-9955-471a-ae7d-90f357ab42a0 ro single
    initrd /boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 59c7e91d-9955-471a-ae7d-90f357ab42a0
    linux /boot/vmlinuz-2.6.28-11-generic root=UUID=59c7e91d-9955-471a-ae7d-90f357ab42a0 ro quiet splash
    initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 59c7e91d-9955-471a-ae7d-90f357ab42a0
    linux /boot/vmlinuz-2.6.28-11-generic root=UUID=59c7e91d-9955-471a-ae7d-90f357ab42a0 ro single
    initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu 9.04, memtest86+ (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 59c7e91d-9955-471a-ae7d-90f357ab42a0
    linux /boot/memtest86+.bin 
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
# / was on /dev/sda9 during installation
UUID=39979148-29d5-441f-99ed-7f59688ce586 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda10 during installation
UUID=ace89351-a106-4ca6-bba7-f6713704f88e none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 436.8GB: boot/grub/core.img
 400.7GB: boot/grub/grub.cfg
 396.8GB: boot/initrd.img-2.6.35-22-generic
 414.1GB: boot/initrd.img-2.6.35-23-generic
 416.3GB: boot/initrd.img-2.6.35-24-generic
 391.9GB: boot/initrd.img-2.6.35-25-generic
 392.2GB: boot/initrd.img-2.6.35-27-generic
 392.1GB: boot/initrd.img-2.6.35-28-generic
 436.8GB: boot/vmlinuz-2.6.35-22-generic
 436.8GB: boot/vmlinuz-2.6.35-23-generic
 436.8GB: boot/vmlinuz-2.6.35-24-generic
 436.8GB: boot/vmlinuz-2.6.35-25-generic
 436.8GB: boot/vmlinuz-2.6.35-27-generic
 436.9GB: boot/vmlinuz-2.6.35-28-generic
 392.1GB: initrd.img
 392.2GB: initrd.img.old
 436.9GB: vmlinuz
 436.8GB: vmlinuz.old
```

---

### Post by Dutch70 on 2011-03-29
Ok, it looks like Grub2 was installed on sda9. You just need to reinstall Grub. 

Once again boot up the live cd/usb, open a terminal & run the following commands.

```
sudo mount /dev/sda5 /mnt
```

and then...

```
sudo grub-install --root-directory=/mnt /dev/sda
```

Then reboot and once logged in to Ubuntu run this command...

```
sudo update-grub
```

---

### Post by calfee1 on 2011-03-30
> **Dutch70 said:**
> Ok, it looks like Grub2 was installed on sda9. You just need to reinstall Grub. 

Once again boot up the live cd/usb, open a terminal & run the following commands.

```
sudo mount /dev/sda5 /mnt
```and then...

```
sudo grub-install --root-directory=/mnt /dev/sda
```Then reboot and once logged in to Ubuntu run this command...

```
sudo update-grub
```

Thanks...got my computer booting again. My last task is to take those unallocated partitions and put them into either the ubuntu or windows partitions......how do you do this....been trying to figure out but cannot seem to do????

---

### Post by Dutch70 on 2011-03-30
Great! glad to hear it's working for you. 

Next you'll want to do the following before moving on to the next steps I need to get some info from you. 

Click on sda5 & select resize/move. When the box pops up, click & drag sda5 all the way to the left (make sure the top box that says "free space preceding doesn't have a "1" in it, change it to a zero, look at the pic below) and apply. 

That will take a while, but it will allow you to increase the size of sda5 to regain your hdd space.

---

### Post by calfee1 on 2011-03-30
> **Dutch70 said:**
> Great! glad to hear it's working for you. 

Next you'll want to do the following before moving on to the next steps I need to get some info from you. 

Click on sda5 & select resize/move. When the box pops up, click & drag sda5 all the way to the left (make sure the top box that says "free space preceding doesn't have a "1" in it, change it to a zero, look at the pic below) and apply. 

That will take a while, but it will allow you to increase the size of sda5 to regain your hdd space.

OK did that. here screenshot of after completion....

---

### Post by Dutch70 on 2011-03-30
Nice! I see you went ahead and grew it also. 

How much physical RAM do you have? You've got almost 1GB where your old second swap partition was. You can grow your swap partition to take up that space if you need it, which I doubt, or you can delete and recreate your swap partition. Which you now know how easy that really is.

The 2.49MB on the end is not in your extended partition, so I wouldn't worry about that.

---

### Post by calfee1 on 2011-03-31
> **Dutch70 said:**
> Nice! I see you went ahead and grew it also. 

How much physical RAM do you have? You've got almost 1GB where your old second swap partition was. You can grow your swap partition to take up that space if you need it, which I doubt, or you can delete and recreate your swap partition. Which you now know how easy that really is.

The 2.49MB on the end is not in your extended partition, so I wouldn't worry about that.
Thanks for the help...all is working well. I will keeps as is

---

### Post by Dutch70 on 2011-03-31
You're quite welcome calfee, glad you've got it working to your satisfaction.

Best regards

---

