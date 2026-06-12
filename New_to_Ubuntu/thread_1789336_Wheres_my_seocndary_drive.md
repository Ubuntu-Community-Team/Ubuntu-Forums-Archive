---
title: "Wheres my seocndary drive?"
date: 2011-06-23
forum: New to Ubuntu
---

### Post by pete1606 on 2011-06-23
Hello Everyone

I hope I am posting in the proper section of this site. I am running mythbuntu version 10.10. I have to SATA hard drives. during installation I tried to format both drives. The installer recognized both drives, but I couldn't figure out the advanced settings. [I]I ended up not formatting the second drive.


I installed 10.10 and I later on booted into gparted and formated the secondary drive using ext2 file system. I cant see to see the drive in ubuntu or I am looking in the wrong place.

BTW: I purposely did not update to 11.04 I heard dvd ripping was disabled in the version. Is that true? 

Please help

Peter[/I]

---

### Post by TeoBigusGeekus on 2011-06-23
Is it not in the Places menu?

> BTW: I purposely did not update to 11.04 I heard dvd ripping was disabled in the version. Is that true?
No, although you did well not upgrading to natty: it's too buggy.

---

### Post by pete1606 on 2011-06-23
Where is the places menu located?

---

### Post by TeoBigusGeekus on 2011-06-23
Oops: Mythbuntu...
I have no idea mate, sorry.

---

### Post by jtarin on 2011-06-23
Your second drive is possibly not mounted. Is this an internal or external drive? Download and run the BootInfo Script in my signature so we can get a better look at what we are dealing with.

---

### Post by pete1606 on 2011-06-23
How do I unzip files. What program do you recommend?

---

### Post by jtarin on 2011-06-23
> **pete1606 said:**
> How do I unzip files. What program do you recommend?
I would recommend the program........**a right-click with the mouse and select "extract here"** program.:p

---

### Post by pete1606 on 2011-06-23
I found out how to unzip files here  [http://ubuntuforums.org/showthread.php?t=921219](http://ubuntuforums.org/showthread.php?t=921219)

---

### Post by chkneater on 2011-06-23
It is quite possible that it's not recognizing the drive because it's formatted as ext2.  If there is nothing on that drive (I'm assuming there's not) then try reformatting with at least ext3 but be aware that eventually ext4 will be the new "norm" at some point.

---

### Post by jtarin on 2011-06-23
> **pete1606 said:**
> I found out how to unzip files here  [http://ubuntuforums.org/showthread.php?t=921219](http://ubuntuforums.org/showthread.php?t=921219)That's the terminal command that the right-click menu represents.

---

### Post by pete1606 on 2011-06-24
Here is the output from Boot info script. It appears that my secondary hdd is SDF. It shows up in disk utility but not in but not in file manager.What do I do with the results?

Peter


       Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdf.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdf1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   306,440,191   306,438,144  83 Linux
/dev/sda2         306,442,238   312,580,095     6,137,858   5 Extended
/dev/sda5         306,442,240   312,580,095     6,137,856  82 Linux swap / Solaris


Drive: sdf _____________________________________________________________________

Disk /dev/sdf: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdf1                  63   488,392,064   488,392,002  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        9c7bc1f3-ff74-4814-b99a-9ea1f5c51c27   ext4       
/dev/sda5        d59b6023-afbf-4873-9913-596b81c8d5a1   swap       
/dev/sdf1        2ccb42f7-1dba-4f9e-afc9-c53f58d906a6   ext4       New Volume

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdf1        /media/New Volume        ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 9c7bc1f3-ff74-4814-b99a-9ea1f5c51c27
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 9c7bc1f3-ff74-4814-b99a-9ea1f5c51c27
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 9c7bc1f3-ff74-4814-b99a-9ea1f5c51c27
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=9c7bc1f3-ff74-4814-b99a-9ea1f5c51c27 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 9c7bc1f3-ff74-4814-b99a-9ea1f5c51c27
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=9c7bc1f3-ff74-4814-b99a-9ea1f5c51c27 ro single 
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 9c7bc1f3-ff74-4814-b99a-9ea1f5c51c27
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 9c7bc1f3-ff74-4814-b99a-9ea1f5c51c27
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sdf1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 4ffa5fb2-7659-4de2-b899-56e13601ef17
    linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sdf1 ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sdf1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 4ffa5fb2-7659-4de2-b899-56e13601ef17
    linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sdf1 ro single
    initrd /boot/initrd.img-2.6.35-22-generic
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

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=d59b6023-afbf-4873-9913-596b81c8d5a1 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 100.134296417 = 107.518382080  boot/grub/core.img                             1
  92.134330750 = 98.928484352   boot/grub/grub.cfg                             2
  55.063476562 = 59.123957760   boot/initrd.img-2.6.35-22-generic              2
 100.132854462 = 107.516833792  boot/vmlinuz-2.6.35-22-generic                 1
  55.063476562 = 59.123957760   initrd.img                                     2
 100.132854462 = 107.516833792  vmlinuz                                        1

========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde

---

### Post by pete1606 on 2011-06-24
take a look at the screenshot from disk utility

---

### Post by jtarin on 2011-06-24
Unix does not like spaces in filenames. Edit the filesystem label of "New Volume" using disk utility. 
After you do that......Issue the command: 
```
sudo grub-install /dev/sda
```
reboot.Then lets see where we're at then.

---

### Post by pete1606 on 2011-06-24
I made those changes. I still don't see it in the file manager.

---

### Post by jtarin on 2011-06-24
> **pete1606 said:**
> I made those changes. I still don't see it in the file manager.
Where exactly are you looking in the File Manager? Can you post a screenshot or give an accurate description?

---

### Post by pete1606 on 2011-06-24
here you go. I am looking on the left hand side of this window. I opened this window from the application- accessories menu.

---

### Post by jtarin on 2011-06-24
Click Filesystem>Media>New Volume

---

### Post by pete1606 on 2011-06-24
Thank you. I am writing files to it as we speak.

---

### Post by jtarin on 2011-06-24
Your welcome.:p

---

