---
title: "Kernel Panic..."
date: 2011-05-25
forum: New to Ubuntu
---

### Post by tb75252 on 2011-05-25
Using Ubuntu 10.10, 32-bit.

This morning I went into the BIOS and did some tweaking to the cache settings for BIOS and DRAM.  Apparently, that did not go down well with Ubuntu 10.10 and now I am unable to launch the OS.

What I now get is GRUB which offers me to boot up using one of several kernels either in Generic or Recovery Mode.  Any of the choices selected result in a screen of what appears to be computer code and the only intelligible thing that I can make out is that there is a kernel panic.  (Before all this I was not getting the GRUB screen because Ubuntu is the only OS that I have on the HD.)

Resetting the BIOS to the original values unfortunately does not help.  I see that the installation DVD comes with a recovery option but it offers several choices and I am not quite sure which one to pick.  So I did not do anything for fear of making things worse.

Is there a recovery procedure that I can follow without having to re-install?

---

### Post by aphatak on 2011-05-25
Before you do anything, it is a good idea to boot the live CD and copy your data from the hard drive to another drive (such as a USB drive).

If grub shows you a number of OS's when you have only one, you might try re-installing grub from the live CD.  It is worth a try - installing grub from the live CD would not kill the Ubuntu installation.  I should give this a try - at least you'd be no worse off than now.

---

### Post by tb75252 on 2011-05-25
> **aphatak said:**
> Before you do anything, it is a good idea to boot the live CD and copy your data from the hard drive to another drive (such as a USB drive).
 
If grub shows you a number of OS's when you have only one, you might try re-installing grub from the live CD. It is worth a try - installing grub from the live CD would not kill the Ubuntu installation. I should give this a try - at least you'd be no worse off than now.
 
Thanks for the suggestion I will try it this evening and hope for the best.
 
One clarification, though:  GRUB does not show different OSs -- it shows different **kernels** for the same distribution.  It is my understanding that each Ubuntu distribution ships with several kernels.

---

### Post by Rubi1200 on 2011-05-25
You should definitely try and save your data as a first step.

However, before considering reinstalling, do this:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by tb75252 on 2011-05-25
> **Rubi1200 said:**
> You should definitely try and save your data as a first step.
 
However, before considering reinstalling, do this:
 
Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:
 
1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command
 
```
sudo bash ~/Desktop/boot_info_script.sh
```
 
This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.
 
Thanks for your suggestion.
 
I guess what you are saying is that I should boot up using the LiveCD method and then navigate to [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) and download file Boot Info Script. What I do not understand, and need more details about, is Step 2 of your task list. How do I copy Boot Info Script to the Desktop if I am using "Try Ubuntu without any changes"? Sorry, but I am a real newbie and I am probably misunderstanding what you are saying...

---

### Post by corncob on 2011-05-25
I think he means to download it to your desktop.  No permanent changes will be made as you're working with RAM and the swap file in this case.

---

### Post by Rubi1200 on 2011-05-25
If you download the script with Firefox it will default to put the file in Downloads. Just open that folder and simply drag and drop it to the Desktop on the LiveCD.

Then, right-click and Extract here to get the contents. Once that folder is on the desktop, open it and drag/drop the boot script again onto the desktop.

Finally, run the code and follow the rest of the instructions to post back here.

Thanks.

---

### Post by tb75252 on 2011-05-25
> **Rubi1200 said:**
> If you download the script with Firefox it will default to put the file in Downloads. Just open that folder and simply drag and drop it to the Desktop on the LiveCD.

Then, right-click and Extract here to get the contents. Once that folder is on the desktop, open it and drag/drop the boot script again onto the desktop.

Finally, run the code and follow the rest of the instructions to post back here.

Thanks.

Thanks for your help.  Here are the contents of file results.txt:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for (,msdos1)/boot/grub.

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

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   149,843,967   149,841,920  83 Linux
/dev/sda2         149,846,014   156,301,311     6,455,298   5 Extended
/dev/sda5         149,846,016   156,301,311     6,455,296  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        9e7ffb80-807a-48f1-b6c7-94d71a94ba16   ext4       
/dev/sda5        46e24cfc-2b14-4571-9e8e-8354bfd3d91e   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


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
search --no-floppy --fs-uuid --set 9e7ffb80-807a-48f1-b6c7-94d71a94ba16
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 9e7ffb80-807a-48f1-b6c7-94d71a94ba16
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 9e7ffb80-807a-48f1-b6c7-94d71a94ba16
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=9e7ffb80-807a-48f1-b6c7-94d71a94ba16 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 9e7ffb80-807a-48f1-b6c7-94d71a94ba16
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=9e7ffb80-807a-48f1-b6c7-94d71a94ba16 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 9e7ffb80-807a-48f1-b6c7-94d71a94ba16
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=9e7ffb80-807a-48f1-b6c7-94d71a94ba16 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 9e7ffb80-807a-48f1-b6c7-94d71a94ba16
    echo    'Loading Linux 2.6.35-27-generic ...'
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=9e7ffb80-807a-48f1-b6c7-94d71a94ba16 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 9e7ffb80-807a-48f1-b6c7-94d71a94ba16
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=9e7ffb80-807a-48f1-b6c7-94d71a94ba16 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 9e7ffb80-807a-48f1-b6c7-94d71a94ba16
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=9e7ffb80-807a-48f1-b6c7-94d71a94ba16 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 9e7ffb80-807a-48f1-b6c7-94d71a94ba16
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=9e7ffb80-807a-48f1-b6c7-94d71a94ba16 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 9e7ffb80-807a-48f1-b6c7-94d71a94ba16
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=9e7ffb80-807a-48f1-b6c7-94d71a94ba16 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 9e7ffb80-807a-48f1-b6c7-94d71a94ba16
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=9e7ffb80-807a-48f1-b6c7-94d71a94ba16 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 9e7ffb80-807a-48f1-b6c7-94d71a94ba16
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=9e7ffb80-807a-48f1-b6c7-94d71a94ba16 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 9e7ffb80-807a-48f1-b6c7-94d71a94ba16
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=9e7ffb80-807a-48f1-b6c7-94d71a94ba16 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 9e7ffb80-807a-48f1-b6c7-94d71a94ba16
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=9e7ffb80-807a-48f1-b6c7-94d71a94ba16 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 9e7ffb80-807a-48f1-b6c7-94d71a94ba16
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=9e7ffb80-807a-48f1-b6c7-94d71a94ba16 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 9e7ffb80-807a-48f1-b6c7-94d71a94ba16
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=9e7ffb80-807a-48f1-b6c7-94d71a94ba16 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 9e7ffb80-807a-48f1-b6c7-94d71a94ba16
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 9e7ffb80-807a-48f1-b6c7-94d71a94ba16
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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
# / was on /dev/sda1 during installation
UUID=9e7ffb80-807a-48f1-b6c7-94d71a94ba16 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=46e24cfc-2b14-4571-9e8e-8354bfd3d91e none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  32.148521423 = 34.519212032   boot/grub/core.img                             1
  37.419872284 = 40.179281920   boot/grub/grub.cfg                             1
   1.756065369 = 1.885560832    boot/initrd.img-2.6.32-25-generic              3
   0.485351562 = 0.521142272    boot/initrd.img-2.6.35-22-generic              2
   0.714122772 = 0.766783488    boot/initrd.img-2.6.35-23-generic              2
   3.015937805 = 3.238338560    boot/initrd.img-2.6.35-24-generic              2
   1.120372772 = 1.202991104    boot/initrd.img-2.6.35-25-generic              1
   1.269416809 = 1.363025920    boot/initrd.img-2.6.35-27-generic              2
  38.292255402 = 41.115996160   boot/initrd.img-2.6.35-28-generic              1
  32.640918732 = 35.047919616   boot/vmlinuz-2.6.32-25-generic                 1
  32.629974365 = 35.036168192   boot/vmlinuz-2.6.35-22-generic                 1
  32.644920349 = 35.052216320   boot/vmlinuz-2.6.35-23-generic                 1
  32.648921967 = 35.056513024   boot/vmlinuz-2.6.35-24-generic                 1
  32.633975983 = 35.040464896   boot/vmlinuz-2.6.35-25-generic                 1
  32.652923584 = 35.060809728   boot/vmlinuz-2.6.35-27-generic                 1
  32.692478180 = 35.103281152   boot/vmlinuz-2.6.35-28-generic                 1
  38.292255402 = 41.115996160   initrd.img                                     1
   1.269416809 = 1.363025920    initrd.img.old                                 2
  32.692478180 = 35.103281152   vmlinuz                                        1
  32.652923584 = 35.060809728   vmlinuz.old                                    1


```

---

### Post by jtarin on 2011-05-25
I don't see anything outstanding, but then I'm half-blind. Possibly a reinstall of Grub2. The reinstallation will tell you if Grub finds everything.Without knowing exactly what you did....it's a shot in the dark.

---

### Post by tb75252 on 2011-05-25
> **jtarin said:**
> I don't see anything outstanding, but then I'm half-blind. Possibly a reinstall of Grub2. The reinstallation will tell you if Grub finds everything.Without knowing exactly what you did....it's a shot in the dark.

Thanks for your reply.
I have re-installed GRUB --twice!-- but unfortunately no improvement...

You want to know exactly what I did:
I went into the BIOS, selected the **Chipset Features Setup** option and
*_ Enabled_ **System BIOS Cacheable** option.  (It was disabled before)
* _Enabled_ the **Video RAM Cacheable** option.  (It was disabled before.)

Why did I do that??  Because my computer is eleven years old and I was trying to wring out every possible drop of performance improvement.

PS:  Disabling again the above two options does not solve the problem!

---

### Post by jtarin on 2011-05-25
[Here's]("https://wiki.archlinux.org/index.php/Kernel_Panics") some basics for all Kernels regardless the distro. Read through and then come back and post if you have questions. Basically what you will be doing is uninstalling Kernel(s) and reinstalling a retro-kernel.There's Ubuntu documentation on CHROOT if you need.

---

