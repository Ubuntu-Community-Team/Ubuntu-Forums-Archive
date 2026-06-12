---
title: "(quick reply needed)Can I install 10.4 onto a USB? (actually install)"
date: 2010-06-24
forum: New to Ubuntu
---

### Post by JamesParnell on 2010-06-24
My harddrive broke yesterday, just out of the blue died....now I cant afford another one, so I was wondering if I could install 10.4 using a live usb to another usb then boot from it (which i can do anyway)
 
Will the install work if i try to install it to a 4gb pen drive?

---

### Post by k3lt01 on 2010-06-24
4gb is probably to small I would have at least 10 apart from that I would say yes AS LONG as your BIOS allows booting to the USB.

---

### Post by Rubi1200 on 2010-06-24
I have successfully done it with an 8GB USB stick.

If you can, use UNetbootin to create the live USB; just be aware that it will not save settings and documents, but you will have an OS at your fingertips.

Ideally, see if you can install to the USB from a computer which has Ubuntu and use the USB Startup Disk Creator; this will allow you the option of a persistent part of the install where documents can be saved.

---

### Post by Paqman on 2010-06-24
Yes, you can. On a 4GB drive I would recommend using the minimal ISO (see my sig) and only installing the packages you actually need. With gnome-core the system only takes up about 1.2GB. Installing the full Ubuntu desktop will leave with you little or no room for files on a 4GB stick.

---

### Post by C.S.Cameron on 2010-06-24
You can do a Full install to a 4GB flash drive but a persistent install using usb-creator will allow you more space as the file system is compressed on the drive and expands into RAM in use.

---

### Post by JamesParnell on 2010-06-24
I use the Live usb i created on "USB A" and install to "USB B" using the "Install Ubuntu 10.04 LTS" thingy...and i watch it until it says something about unpacking grub and stuff...after in finishes I restart and try to boot from the full installation "USB B" and it says it cant find a Boot Record....

Also, in gparted when i first completed the installation, the BOOT flag wasnt there...

please help.

---

### Post by KdotJ on 2010-06-24
Maybe try this, don't actually install to a USB stick itself. Instead, make a Live USB stick that has persistent storage. This way you can choose your "Try Ubuntu..." option when the computer boots from the USB stick. It will run a live session but then you will be able to save files to the persistent storage section. It might be ok to deal with until you can get a new HDD.

---

### Post by C.S.Cameron on 2010-06-24
After partitioning you will notice an advanced tab, click this and tell it to install grub to the correct USB drive.

---

### Post by JamesParnell on 2010-06-24
On gparted or using the installation thingy?

---

### Post by C.S.Cameron on 2010-06-24
> **JamesParnell said:**
> On gparted or using the installation thingy?

I usually do it during the install process but I understand that you can use the Live CD (or Live USB) to install grub to the device.
Probably best to Google install grub as my memory is not too hot.

---

### Post by oldfred on 2010-06-24
Advanced button during install:
[http://members.iinet.net/~herman546/p28/032_install-now.png](http://members.iinet.net/~herman546/p28/032_install-now.png)

If you did not use it during the install it probably wrote grub from the USB install to sda and you cannot boot without the USB flash drive. You will have to reinstall grub to sda from the correct partition.

Standard full install to flash or SSD:
Ubuntu Karmic Koala Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)

See post #19 C.S.Cameron ( But I do not unplug hard drive, just use advanced button to install to USB) 
[http://ubuntuforums.org/showthread.php?t=1509603](http://ubuntuforums.org/showthread.php?t=1509603)

---

### Post by JamesParnell on 2010-06-24
Ok thanks. I will try and figure it out.

Thanks for all your helpful guidance.

EDIT: I am really stupid, I didnt notice that button at all. DoH!..thanks

---

### Post by DJonsson2008 on 2010-06-24
I found it easiest to simply

* Use Gparted to delete any of the existing USB partions.

Then 

* Install to the USB just like installing onto a hard drive, using 
  mostly default settings.

To further simplify things I did this with all other drives disconnected except the CD drive and the drive being installed to.

This was on a 4gig USB stick using Xubuntu and works fine, seems like Ubuntu would work the same way.

---

### Post by C.S.Cameron on 2010-06-24
> If you did not use it during the install it probably wrote grub from the USB install to sda and you cannot boot without the USB flash drive. You will have to reinstall grub to sda from the correct partition.

He had already broke his hard drive, grub was probably written to the first USB drive.


> See post #19 C.S.Cameron ( But I do not unplug hard drive, just use advanced button to install to USB) 

Nowadays I an only suggesting disabling the internal drives if the poster has less than 5 beans. 
I do find that removing the hard drive gives a cleaner grub.cfg file though, without reference to the installer pen drive or Windows, etc.

---

### Post by JamesParnell on 2010-06-24
Right, the story is as follows: 

Ran through the installation setup which was running from my live USB (/dev/sda) and in the advanced section, i selected installation to to to /dev/sdb,  even though I've done this, the bios still doesnt find the boot record...

??

root@ubuntu:/home/ubuntu# grub-setup /dev/sdc
Segmentation fault (core dumped)

---

### Post by C.S.Cameron on 2010-06-24
I think OldFred is the master at updating Grub2.

---

### Post by oldfred on 2010-06-24
It looks like the installer and grub are numbering drives differently. You say your are installing grub to sda as it put the USB key first but the error message is on sdc? Error sounds like sdc does not exist, so it stops.

You should be able just to install grub2 from any working liveCD or install.

Find your install:
Install from LiveCD:
Find linux partition change sda5 if not correct or even sda if sdb wanted:
sudo fdisk -l
sudo mkdir /mnt/sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo grub-install --recheck --root-directory=/mnt /dev/sda

If you want specific commands leave USB plugged in and run the boot info script:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

That should tell us where everything is at.

---

### Post by JamesParnell on 2010-06-24
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 2000 MB, 2000682496 bytes
255 heads, 63 sectors/track, 243 cylinders, total 3907583 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     3,903,794     3,903,732   b W95 FAT32


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 4043 MB, 4043284480 bytes
125 heads, 62 sectors/track, 1018 cylinders, total 7897040 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  62     5,920,999     5,920,938  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        F449-5834                              vfat                                     
/dev/sda: PTTYPE="dos" 
/dev/sdd1        e1451ab3-ad05-4481-aff4-7d37260ad26b   ext4       Ubuntu                        
/dev/sdd: PTTYPE="dos" 
error: block: No such file or directory
error: devices: No such file or directory
error: /dev/mapper/no: No such file or directory
error: found: No such file or directory

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sda1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdd1        /mnt                     ext4       (rw)


=================== sdd1: Location of files loaded by Grub: ===================


    .1GB: boot/grub/core.img
=======Devices which don't seem to have a corresponding hard drive==============

hda no block devices found

---

### Post by oldfred on 2010-06-24
You do not install to a partition. Drives are sda, sdb, sdc, sdd, etc, Partitions have numbers at the end sda1, sda2, sdb1 etc.

You want to install to what ever drive the USB flash drive is mounted as.

I think we have seen a few flash drives that just do not work. What Brand it this one. I have always used noname from Microcenter or Kingston without any issue.

---

### Post by JamesParnell on 2010-06-24
not sure of model, but its a busbi stick

---

### Post by snip3r8 on 2010-06-24
> **JamesParnell said:**
> On gparted or using the installation thingy?

the installation thingy ie: system>Admin>USB startup disk creator

---

### Post by Ozitraveller on 2010-06-24
Create a Persistent Bootable Ubuntu USB Flash Drive
[http://www.howtogeek.com/howto/14912/create-a-persistent-bootable-](http://www.howtogeek.com/howto/14912/create-a-persistent-bootable-)
ubuntu-usb-flash-drive/

---

### Post by JamesParnell on 2010-06-24
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdd and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 2000 MB, 2000682496 bytes
255 heads, 63 sectors/track, 243 cylinders, total 3907583 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     3,903,794     3,903,732   b W95 FAT32


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 4043 MB, 4043284480 bytes
125 heads, 62 sectors/track, 1018 cylinders, total 7897040 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  62     6,874,249     6,874,188  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        F449-5834                              vfat                                     
/dev/sda: PTTYPE="dos" 
/dev/sdd1        0280892c-334f-4d7d-a5bb-8610ce1700db   ext4       ubuntu                        
/dev/sdd: PTTYPE="dos" 
error: block: No such file or directory
error: devices: No such file or directory
error: /dev/mapper/no: No such file or directory
error: found: No such file or directory

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sda1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdd1        /mnt                     ext4       (rw)


=================== sdd1: Location of files loaded by Grub: ===================


    .1GB: boot/grub/core.img
=======Devices which don't seem to have a corresponding hard drive==============

hda no block devices found

---

### Post by oldfred on 2010-06-24
There is no install just grub installed to sda & sdd. Is that what you wanted?

---

### Post by JamesParnell on 2010-06-24
sda is the Live USB, sdd is the one i wanted it on, but didnt install it first XD...so when it finishes in a few minutes im going to repeat the steps you provided just to make sure.

---

### Post by JamesParnell on 2010-06-24
Im not even joking, its still not working...


i got somewhere with your thing before, it found the boot record..it just did nothnig after that..it just stopped


unless it needed more than 5 minutes?


im going to try and do it again, and if it doesnt work..well, i cant afford a harddrive so I guess if it doesnt work...it doesnt work.

---

### Post by JamesParnell on 2010-06-25
Right, so I install ubuntu using the shortcut on the live disc, supposedly installing the bootloader...after running the script..it appears the Bootloader isnt there..so using the method you described on page 2, i make it..still nothing.

Screenshots of installation (drive installing to, and where grub is installed)

[http://i49.tinypic.com/35jkpas.png](http://i49.tinypic.com/35jkpas.png) - creating partition on sdb \\:D/
[http://i47.tinypic.com/ot3d07.png](http://i47.tinypic.com/ot3d07.png) - installing grub bootloader on sdb \\:D/

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 2000 MB, 2000682496 bytes
255 heads, 63 sectors/track, 243 cylinders, total 3907583 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     3,903,794     3,903,732   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4043 MB, 4043284480 bytes
123 heads, 26 sectors/track, 2469 cylinders, total 7897040 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *        610,470     7,895,626     7,285,157  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        F449-5834                              vfat                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        b20b1ceb-0957-42f8-9815-12a3aa5eaacf   ext4                                     
/dev/sdb: PTTYPE="dos" 
error: block: No such file or directory
error: devices: No such file or directory
error: /dev/mapper/no: No such file or directory
error: found: No such file or directory

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sda1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set b20b1ceb-0957-42f8-9815-12a3aa5eaacf
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set b20b1ceb-0957-42f8-9815-12a3aa5eaacf
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
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set b20b1ceb-0957-42f8-9815-12a3aa5eaacf
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=b20b1ceb-0957-42f8-9815-12a3aa5eaacf ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set b20b1ceb-0957-42f8-9815-12a3aa5eaacf
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=b20b1ceb-0957-42f8-9815-12a3aa5eaacf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set b20b1ceb-0957-42f8-9815-12a3aa5eaacf
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set b20b1ceb-0957-42f8-9815-12a3aa5eaacf
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=b20b1ceb-0957-42f8-9815-12a3aa5eaacf /               ext4    errors=remount-ro 0       1
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


   2.1GB: boot/grub/core.img
   2.1GB: boot/grub/grub.cfg
   2.3GB: boot/initrd.img-2.6.32-21-generic
   2.3GB: boot/vmlinuz-2.6.32-21-generic
   2.3GB: initrd.img
   2.3GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

no block devices found 
```

everything seems correct this time...so lets see, time for the reboot

---

### Post by JamesParnell on 2010-06-25
after ten minutes of waiting.....

[http://i46.tinypic.com/mhwu1.jpg](http://i46.tinypic.com/mhwu1.jpg)


whats wrong with it now -_-

---

### Post by k3lt01 on 2010-06-25
> **JamesParnell said:**
> after ten minutes of waiting.....

[http://i46.tinypic.com/mhwu1.jpg](http://i46.tinypic.com/mhwu1.jpg)


whats wrong with it now -_-By that picture nothing is wrong, it says it found the boot record on the usb-fdd.

---

### Post by JamesParnell on 2010-06-25
Yes, it would appear to be working...but that picture was taken after 5 minutes of showing that same picture.


I've just done it again, for 15 minutes, same problem. It doesnt hang, as the _ at the bottom still flashes.

---

### Post by C.S.Cameron on 2010-06-25
Is there any thing in the floppy slot?
Can you try booting with only the flash drive plugged in and selected as the first boot device in BIOS?

I have never seen anything like this.
If the persistent flash boots ok you would think the Full install one should boot also.

Is the flash drive used for the Full install good?

---

