---
title: "windows 7 will not load anymore please help"
date: 2011-05-17
forum: New to Ubuntu
---

### Post by skilgannon82 on 2011-05-17
after two days i finally was able to install ubuntu by deleting my recovery partition (after making backup disks of course) and ubuntu now works fine but today when i tried to load windows 7 my laptop says there was an error and some files are missing windows cannot load it says to use the recovery disks to repair windows but when i used the disks it came up with a menu and all that i could choose from the list is a factory reset repair wasnt even one of the choices i could choose 

somebody please help me i really need windows back hopefully without losing ubuntu

---

### Post by garvinrick4 on 2011-05-17
Here are directions for your Windows, Going to need Ubuntu's install CD using Try Ubuntu to
get Ubuntu and Windows both working after doing the Windows fix below. Let me know when
you are ready for UBuntu fix. Post results of:
sudo fdisk -l (lower case L) here.

[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by skilgannon82 on 2011-05-17
thank you for your help but i must also mention i am a total noob and i only have the ubuntu on usb that i installed it from is this still ok

---

### Post by NormanFLinux on 2011-05-17
A usb flash drive is OK. It looks like you will need to fix MBR = Master Boot Record in Windows to get it booting again to the desktop.

---

### Post by skilgannon82 on 2011-05-17
this is what i got from what you told me to do

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8b3e70a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           1         992+  42  SFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   *           1          26      203776   42  SFS
Partition 2 does not end on cylinder boundary.
/dev/sda3              26       52442   421028864   42  SFS
/dev/sda4           52442       60802    67151896   83  Linux
```

---

### Post by garvinrick4 on 2011-05-17
> thank you for your help but i must also mention i am a total noob and i  only have the ubuntu on usb that i installed it from is this still ok
Yes that is fine use the link provided to get windows booting then put in the flash drive
and get internet working on it and get to these forums and let me know you are ready for
next commands. Give me results I asked for then of sudo fdisk -l

---

### Post by skilgannon82 on 2011-05-17
ok its running from usb now

---

### Post by garvinrick4 on 2011-05-17
> **skilgannon82 said:**
> this is what i got from what you told me to do

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8b3e70a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           1         992+  42  SFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   *           1          26      203776   42  SFS
Partition 2 does not end on cylinder boundary.
/dev/sda3              26       52442   421028864   42  SFS
/dev/sda4           52442       60802    67151896   83  Linux
```
I have not worked with this format before SFS usually most are NTFS with a mbr (master boot record)  I will bump this up to front to see if anyone out there can work with this format. What does it say when you use the recovery CD? Does it boot into Windows OK now? Will give it a go if Windows boots.

---

### Post by skilgannon82 on 2011-05-17
the only option it lets me choose with the recovery disks is factory reset and i dont really want to do that if there is another way to fix this problem

---

### Post by garvinrick4 on 2011-05-17
while in the ubuntu flash drive do this for me.
Download this script to your DESKTOP
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Then run this code and will put a RESULTS file on your desktop.
copy and paste it to this thread will tell more about your system.
after you copy and paste to the Message box, highlight the whole thing
and hit the # in the upper right of Message box will put in a nice little box to read from.
```
 sudo bash ~/Desktop/boot_info_script*.sh 
```

Only takes a minute or so not a big thing.

---

### Post by skilgannon82 on 2011-05-17
oh it does let me open a command promt aswell if that is helpful

---

### Post by garvinrick4 on 2011-05-17
How did your machine get the SFS format?

---

### Post by skilgannon82 on 2011-05-17
ok

---

### Post by skilgannon82 on 2011-05-17
thats how my partitions were before i even touched them they are called simple drive or something

---

### Post by garvinrick4 on 2011-05-17
> thats how my partitions were before i even touched them they are called simple drive or something
I have only seen it a few times in last years I do not even believe it uses a master boot record to boot with. 
I got know idea and is out of my knowledge range. If a user that knows what is
going on with SFS does not chime in then I do not know what to tell you really. I do not even
no if it can be formatted back to NTFS and will have an mbr again. Been reading about it a bit
and just do not no why or how your machine got formatted SFS at all. Buy it used maybe do
not know. Good luck to you hope someone steps up and helps you out. Sorry partner.

---

### Post by skilgannon82 on 2011-05-17
ok thanks for trying to help anyway
i really hope someone can figure this out too because i am hopeless =(

---

### Post by skilgannon82 on 2011-05-17
ok this is what it came up with

```
  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos4)/boot/grub on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

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
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>.........V9...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:   Syslinux looks at sector 4263232 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63         2,047         1,985  42 SFS
/dev/sda2    *          2,048       409,599       407,552  42 SFS
/dev/sda3             409,600   842,467,327   842,057,728  42 SFS
/dev/sda4         842,467,328   976,771,119   134,303,792  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 8000 MB, 8000110592 bytes
160 heads, 19 sectors/track, 5139 cylinders, total 15625216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32    15,625,215    15,625,184   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda2        BE9015269014E6A5                       ntfs       SYSTEM
/dev/sda3        5E226C77226C5655                       ntfs       
/dev/sda4        fce8f74f-2c50-4940-ac3b-5eb1bfc2d2ee   ext4       
/dev/sdb1        C040-B193                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda4/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos4)'
search --no-floppy --fs-uuid --set=root fce8f74f-2c50-4940-ac3b-5eb1bfc2d2ee
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos4)'
search --no-floppy --fs-uuid --set=root fce8f74f-2c50-4940-ac3b-5eb1bfc2d2ee
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos4)'
    search --no-floppy --fs-uuid --set=root fce8f74f-2c50-4940-ac3b-5eb1bfc2d2ee
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=fce8f74f-2c50-4940-ac3b-5eb1bfc2d2ee ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos4)'
    search --no-floppy --fs-uuid --set=root fce8f74f-2c50-4940-ac3b-5eb1bfc2d2ee
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=fce8f74f-2c50-4940-ac3b-5eb1bfc2d2ee ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos4)'
    search --no-floppy --fs-uuid --set=root fce8f74f-2c50-4940-ac3b-5eb1bfc2d2ee
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos4)'
    search --no-floppy --fs-uuid --set=root fce8f74f-2c50-4940-ac3b-5eb1bfc2d2ee
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root BE9015269014E6A5
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root 5E226C77226C5655
    drivemap -s (hd0) ${root}
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
--------------------------------------------------------------------------------

=============================== sda4/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda4       /               ext4    errors=remount-ro 0       1
--------------------------------------------------------------------------------

=================== sda4: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 417.962711334 = 448.784044032  boot/grub/core.img                             1
 406.464202881 = 436.437614592  boot/grub/grub.cfg                             1
 403.422851562 = 433.171988480  boot/initrd.img-2.6.38-8-generic               2
 417.960983276 = 448.782188544  boot/vmlinuz-2.6.38-8-generic                  1
 403.422851562 = 433.171988480  initrd.img                                     2
 417.960983276 = 448.782188544  vmlinuz                                        1

=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

========= Devices which don't seem to have a corresponding hard drive: =========

sdc 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected
```

---

### Post by garvinrick4 on 2011-05-17
Ok, I will write a bit of code for you be right back. Give her a shot.

---

### Post by skilgannon82 on 2011-05-17
yeah i know what the problem is now i just dont know how to fix it

---

### Post by garvinrick4 on 2011-05-17
In the USB flash you have: copy and paste these one at a time in a terminal.
```
sudo mount /dev/sda4 /mnt
``````
sudo grub-install --root-directory=/mnt /dev/sda
``````
sudo umount /mnt
``````
sudo reboot
```boot into Ubuntu and 
```
sudo update-grub
```

---

### Post by skilgannon82 on 2011-05-17
ha ha i cant believe i am such a dumb *** you knew what was wrong as soon as you looked at it too =)

how do i copy them onto usb? do i type this in the terminal or put it in a note pad on usb ?
sorry but i really am a dumb *** im not sure how to do what you said

---

### Post by garvinrick4 on 2011-05-17
Open a terminal in the USB flash and copy and paste them one at a time.
We are not out of the water yet, SFS format remember but it says it has a mbr. So took a shot.

---

### Post by skilgannon82 on 2011-05-17
i dont know how to open a terminal in the usb flash :(

---

### Post by garvinrick4 on 2011-05-17
> **skilgannon82 said:**
> i dont know how to open a terminal in the usb flash :(
You boot the USB flash drive into your Linux on the flash and then:
ctrl/alt/t
Hit those 3 keys and a terminal will open.
then copy and paste the code I gave you one at a time and hit enter

You had to open a terminal to put the code in to make the boot script you posted.

---

### Post by garvinrick4 on 2011-05-17
Here is a link about your dynamic disk setup. SFS format
Copied this from website.
If you are going to dual-boot Ubuntu and Windows 7, make sure your drive  is a Basic disk and not a Dynamic one as Dynamic disk is Microsoft  proprietary thing. Linux doesn't support it and you may end up losing  some or all of your data. If you find that your disk is a Dynamic disk,  Windows 7 partitioning tool can convert it to Basic for you but make  sure to have strong backups of everything important on your drive.

[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
[Convert a Dynamic Disk to a Basic Disk - Windows 7 Forums]("http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html")

---

### Post by skilgannon82 on 2011-05-17
this is what came up i didnt even get to finish it

```
ubuntu@ubuntu:~$ sudo mount /dev/sda4 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=mnt /dev/sda
/usr/sbin/grub-probe: error: cannot find a device for mnt/boot/grub (is /dev mounted?).
```

---

### Post by skilgannon82 on 2011-05-17
i dont have a dynamic disk do i 
i created one then it wouldnt install ubuntu onto it so i got rid of it

---

### Post by garvinrick4 on 2011-05-17
> **skilgannon82 said:**
> this is what came up i didnt even get to finish it

```
ubuntu@ubuntu:~$ sudo mount /dev/sda4 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=mnt /dev/sda
/usr/sbin/grub-probe: error: cannot find a device for mnt/boot/grub (is /dev mounted?).
```
sudo grub-install --root-directory=/mnt /dev/sda

You have a typo notice =/mnt
forgot the / infront of mnt

---

### Post by garvinrick4 on 2011-05-17
> **skilgannon82 said:**
> i dont have a dynamic disk do i 
i created one then it wouldnt install ubuntu onto it so i got rid of it
Yes bootscript says dynamic but I saw one bit of NTFS in there so just for heck of
it I gave you the code.

---

### Post by skilgannon82 on 2011-05-17
all the code worked and as i had to load back into ubuntu on my hdd (is that what i am supposed to do?) to enter the last bit of code 
i restarted without the usb chose ubuntu to load and then just got a black screen
so now i am back on the usb 
what happens if i put that last bit of code in while on the usb?

---

### Post by garvinrick4 on 2011-05-17
lets look at another bootscript and make a decision about this. All indicators and everything
about dynamic drives go's against our having anything near success. I am hoping to get you
bootable but lets look at one more bootscript first.

---

### Post by skilgannon82 on 2011-05-17
ok this is the new one

```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos4)/boot/grub on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

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
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>.........V9...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:   Syslinux looks at sector 4263232 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63         2,047         1,985  42 SFS
/dev/sda2    *          2,048       409,599       407,552  42 SFS
/dev/sda3             409,600   842,467,327   842,057,728  42 SFS
/dev/sda4         842,467,328   976,771,119   134,303,792  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 8000 MB, 8000110592 bytes
160 heads, 19 sectors/track, 5139 cylinders, total 15625216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32    15,625,215    15,625,184   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda2        BE9015269014E6A5                       ntfs       SYSTEM
/dev/sda3        5E226C77226C5655                       ntfs       
/dev/sda4        fce8f74f-2c50-4940-ac3b-5eb1bfc2d2ee   ext4       
/dev/sdb1        C040-B193                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda4/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos4)'
search --no-floppy --fs-uuid --set=root fce8f74f-2c50-4940-ac3b-5eb1bfc2d2ee
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos4)'
search --no-floppy --fs-uuid --set=root fce8f74f-2c50-4940-ac3b-5eb1bfc2d2ee
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos4)'
    search --no-floppy --fs-uuid --set=root fce8f74f-2c50-4940-ac3b-5eb1bfc2d2ee
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=fce8f74f-2c50-4940-ac3b-5eb1bfc2d2ee ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos4)'
    search --no-floppy --fs-uuid --set=root fce8f74f-2c50-4940-ac3b-5eb1bfc2d2ee
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=fce8f74f-2c50-4940-ac3b-5eb1bfc2d2ee ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos4)'
    search --no-floppy --fs-uuid --set=root fce8f74f-2c50-4940-ac3b-5eb1bfc2d2ee
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos4)'
    search --no-floppy --fs-uuid --set=root fce8f74f-2c50-4940-ac3b-5eb1bfc2d2ee
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root BE9015269014E6A5
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root 5E226C77226C5655
    drivemap -s (hd0) ${root}
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
--------------------------------------------------------------------------------

=============================== sda4/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda4       /               ext4    errors=remount-ro 0       1
--------------------------------------------------------------------------------

=================== sda4: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 417.965461731 = 448.786997248  boot/grub/core.img                             1
 406.464202881 = 436.437614592  boot/grub/grub.cfg                             1
 403.422851562 = 433.171988480  boot/initrd.img-2.6.38-8-generic               2
 417.960983276 = 448.782188544  boot/vmlinuz-2.6.38-8-generic                  1
 403.422851562 = 433.171988480  initrd.img                                     2
 417.960983276 = 448.782188544  vmlinuz                                        1

=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

========= Devices which don't seem to have a corresponding hard drive: =========

sdc 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

---

### Post by garvinrick4 on 2011-05-17
It is suppose to look in to sda4 for the boot files to make it boot so the code I gave you was
telling it to do that. The boot script says it is still looking in sector 1 for
boot files. So I gave it a try for you but the dynamic disk is just not going to boot. I gave you
a link to change it back to basic so I am afraid that is what you will have to do. If it's not going
to boot now there is just nothing I know how to do for a dynamic disk.

---

### Post by skilgannon82 on 2011-05-17
i started ubuntu recovery and it let me choose update grub it didnt do it properly but it let me back into ubuntu from my hdd so updated grub in the terminal and it found windows 7 in the sda2 so i went back to the grub menu and the windows 7 loader did change to sda2 (what it is supposed to be) but it still wont load windows 7 it says it needs to be repaired with the recovery disks so i tried that but it still doesnt give me the option to repair so i went back to the grub menu and loaded ubuntu from my hdd and it gave me the black screen again f*******ck

---

