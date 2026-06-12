---
title: "XP has killed my Ubuntu"
date: 2011-03-09
forum: New to Ubuntu
---

### Post by cobaltinfinity on 2011-03-09
Ok, so last week I installed 64 bit Ubuntu 10.10 onto a new SSD.

Then I moved my /home folder onto a separate Hard Disk with some great help from you guys. Everything was working fantastic, loved it. Then my brother starts telling me I should install Windows too to play some games. I wasn't particularly interested but thought I would give it a go. 

So I disconnected all the other drives, connected a clean HDD to put Windows XP on - it was IDE, btw, the other drives were SATA - and installed Windows, worked OK.

I connected back up the other drives, booted up back into the SSD 10.10 install, then I found this guide about Grub and how to configure it to give me a list of boot options. Well, I don't think I did this very well, and then after installing grub and trying to make it work, I found out I was meant to be using Grub 2. By this stage I was really wishing I hadn't bothered with the whole Windows thing. 

So I eventually found out how to install Grub 2, and I set it to install on the / (i.e. root) partition on my SSD. Then, the next time I tried to boot my computer, it just goes to a black screen that says 

```
GRUB Loading stage 1.5
GRUB Loading, please wait...

Error 15
```

I can't seem to get past it. So I suppose I killed my Ubuntu really but stupid XP is at least indirectly culpable. Is this at all fixable or do I need to do something really drastic like reformat the drive? I just want everything to be exactly the same as it was before I started with the Windows fiasco. 

Really grateful for any help guys.

---

### Post by coffeecat on 2011-03-09
When you install Windows it replaces grub in the mbr with Windows code, but this:

> **cobaltinfinity said:**
> ```
GRUB Loading stage 1.5
GRUB Loading, please wait...

Error 15
```

Tells us you have legacy grub in the mbr, not grub 2, so I can't quite follow what you mean when you say you installed grub 2.

Boot up from a live Ubuntu CD and choose 'try Ubuntu'. Go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script and post the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags. You can use the # icon on the message toolbar for this.

The RESULTS.txt file will tell us what is going on and someone will be able to tell you how to reinstall grub properly.

---

### Post by astrobob.tk on 2011-03-09
Hello cobaltinfinity; you might want to check out this [thread]("http://ubuntuforums.org/showthread.php?t=1470597"), it might be helpful.

Besides that, you should do a search online specially on the forums here as there must be other threads of similar questions.

I personally can't help any further as am not competent enough in this; maybe others can help ?

good luck

---

### Post by cobaltinfinity on 2011-03-09
> **coffeecat said:**
> Boot up from a live Ubuntu CD and choose 'try Ubuntu'. Go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script and post the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags. You can use the # icon on the message toolbar for this.

The RESULTS.txt file will tell us what is going on and someone will be able to tell you how to reinstall grub properly.


Hi thanks so much for the response. I did what you said, here are the results. Sorry if it's large I don't know which part is relevant:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 8654288 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   112,351,231   112,349,184  83 Linux
/dev/sda2         112,353,278   117,229,567     4,876,290   5 Extended
/dev/sda5         112,353,280   117,229,567     4,876,288  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,465,144,064 1,465,144,002  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
16 heads, 63 sectors/track, 484521 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   471,040,415   471,040,353   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        b7f5139f-42a7-4d0d-a7ed-e8634bcd16ba   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        beb63290-d3af-453f-b552-313ed664f2cb   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        cc8ac091-95a6-4583-81ff-1e1663e94a48   ext4       HDD                           
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        AE0C1F9E0C1F609F                       ntfs                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set b7f5139f-42a7-4d0d-a7ed-e8634bcd16ba
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set b7f5139f-42a7-4d0d-a7ed-e8634bcd16ba
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
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set b7f5139f-42a7-4d0d-a7ed-e8634bcd16ba
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=b7f5139f-42a7-4d0d-a7ed-e8634bcd16ba ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set b7f5139f-42a7-4d0d-a7ed-e8634bcd16ba
    echo    'Loading Linux 2.6.35-27-generic ...'
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=b7f5139f-42a7-4d0d-a7ed-e8634bcd16ba ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set b7f5139f-42a7-4d0d-a7ed-e8634bcd16ba
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=b7f5139f-42a7-4d0d-a7ed-e8634bcd16ba ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set b7f5139f-42a7-4d0d-a7ed-e8634bcd16ba
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=b7f5139f-42a7-4d0d-a7ed-e8634bcd16ba ro single 
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
    search --no-floppy --fs-uuid --set b7f5139f-42a7-4d0d-a7ed-e8634bcd16ba
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set b7f5139f-42a7-4d0d-a7ed-e8634bcd16ba
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sdc1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set ae0c1f9e0c1f609f
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=b7f5139f-42a7-4d0d-a7ed-e8634bcd16ba /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=beb63290-d3af-453f-b552-313ed664f2cb none            swap    sw              0       0
# (identifier)  (location, eg sda5)   (format, eg ext3 or ext4)      (some settings) 
UUID=cc8ac091-95a6-4583-81ff-1e1663e94a48   /home    ext4          nodev,nosuid       0       2

=================== sda1: Location of files loaded by Grub: ===================


   4.4GB: boot/grub/core.img
  49.9GB: boot/grub/grub.cfg
   1.2GB: boot/initrd.img-2.6.35-22-generic
    .3GB: boot/initrd.img-2.6.35-27-generic
   4.4GB: boot/vmlinuz-2.6.35-22-generic
   4.4GB: boot/vmlinuz-2.6.35-27-generic
    .3GB: initrd.img
   1.2GB: initrd.img.old
   4.4GB: vmlinuz
   4.4GB: vmlinuz.old

================================ sdc1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect
```

---

### Post by coffeecat on 2011-03-09
Curious. Legacy grub (0.97) is indeed installed in the mbr of sda, but there's not a hint or whiff of legacy grub elsewhere. Grub 2 files are in your Ubuntu 10.10 root partition, sda1.

Rather than solve the mystery of how legacy grub came to be in your mbr, here's how you rescue the situation.

Boot up with the live 10.10 Ubuntu CD. Make sure it's the 10.10 release and not an earlier one. Choose 'try Ubuntu', and when you get to the desktop, open a terminal and:

```
sudo mount /dev/sda1 /mnt
```Then:

```
sudo grub-install --root-directory=/mnt /dev/sda
```That's it. Now reboot and you should see your grub dual-boot menu, because grub.cfg shows a Windows entry in the correct place. If you do see any problem with the grub menu, boot into Ubuntu and run:

```
sudo update-grub
```But there shouldn't be. The entries for Ubuntu and Windows look OK to me.

Here's one for your bookmarks for the next time your brother persuades you to install Windows. :wink:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")

**EDIT**: there is one oddity, possibly as a result of your earlier attempt to repair grub. Grub 2 stage 1 is also in the boot sector of sda1. It doesn't do any good there, but won't do any harm. If the above fix doesn't work, for whatever reason, post back and we'll take it from there. I'm logging off in a moment - late here - but I'll check this thread in the morning.

---

### Post by cobaltinfinity on 2011-03-09
Oh my God, Thank you so much, it appears to have totally fixed it!!! Don't know how you did that in two commands! You legend! Seriously I can't thank you enough for taking the time to answer. I thought this was going to be a catastrophe. 

:D:D:D:D:D:D:D:D

---

### Post by coffeecat on 2011-03-10
You're welcome. I'm glad it's fixed.

If you are still following this thread, I am still curious about the legacy grub in the mbr. When you tried to repair grub before you started this thread by following a guide you found, did you by chance use a live CD of a release of Ubuntu prior to 9.10? Say Jaunty/9.04 or Hardy/8.04?

---

