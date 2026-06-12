---
title: "Grub rescue no such partition"
date: 2011-08-11
forum: New to Ubuntu
---

### Post by nikademo on 2011-08-11
Hi all

I'm totally beginner in lunix or ubuntu so sorry if the question is silly

I've tried to install Ubuntu (latest version) on external usb HD. All is ok, installation completed, linux partition created (on the hd there's also a windows ntsc partition).

If I try to boot the computer by usb I get the grub rescue terminal interface with this error

***Grub rescue no such partition***

and the grub prompt but I cannot use any command.

I've cheched the external HD and in boot folder I've grub. I'm clueless, how can I fix the installation ? thanks!!!

---

### Post by coffeecat on 2011-08-11
> **nikademo said:**
> Hi all

Hi there, and welcome to the forum.

> **nikademo said:**
> I'm totally beginner in lunix or ubuntu so sorry if the question is silly

There are no silly questions, only silly answers! :wink:

> **nikademo said:**
> I've tried to install Ubuntu (latest version) on external usb HD.

Did you use a live CD or live USB pendrive to do the installation? Because I need you to boot up with whichever you used. Also I need you to boot up with the external USB drive you've installed Ubuntu to, and which is giving you trouble, plugged in and switched on. If you used a live USB, you need to make sure the BIOS tries to boot from your USB pendrive, not the hard drive.

Boot up with the live CD/USB and select "try Ubuntu" so that you get the live desktop. You do not want the installer. Make sure you are connected to the Internet and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script and follow the directions there to get a RESULTS.txt file. Post the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags for readability. You can use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the message toolbar for this.

---

### Post by nikademo on 2011-08-11
this one :)

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.
 => Windows is installed in the MBR of /dev/sdd.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /BOOT/BCD

sdd2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sdd3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdd4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disco /dev/sda: 500.1 GB, 500105740288 byte
255 testine, 63 settori/tracce, 60801 cilindri, totale 976769024 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   780,307,731   780,305,684   7 NTFS / exFAT / HPFS
/dev/sda2         780,308,478   976,766,975   196,458,498   5 Extended
/dev/sda5         780,308,480   964,188,159   183,879,680  83 Linux
/dev/sda6         964,190,208   976,766,975    12,576,768  82 Linux swap / Solaris


Drive: sdd _____________________________________________________________________

Disco /dev/sdd: 1000.2 GB, 1000204886016 byte
255 testine, 63 settori/tracce, 121601 cilindri, totale 1953525168 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1               2,048    28,674,047    28,672,000  27 Hidden NTFS (Recovery Environment)
/dev/sdd2    *     28,674,048    28,878,847       204,800   7 NTFS / exFAT / HPFS
/dev/sdd3          28,878,848   991,196,228   962,317,381   7 NTFS / exFAT / HPFS
/dev/sdd4         991,199,232 1,953,520,613   962,321,382   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        0EBE1831BE181435                       ntfs       SIM_BIA
/dev/sda5        046186f6-4812-4e08-a756-e2442f814a51   ext4       
/dev/sda6        c3ef0577-c694-4caf-953a-53b780e57a18   swap       
/dev/sdd1        0454A30C54A30012                       ntfs       PQSERVICE
/dev/sdd2        CCA811C2A811AC48                       ntfs       SYSTEM RESERVED
/dev/sdd3        0CE82CA7E82C914E                       ntfs       Acer
/dev/sdd4        D21CF8EB1CF8CB8B                       ntfs       DATA

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/SIM_BIA           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /media/046186f6-4812-4e08-a756-e2442f814a51 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 046186f6-4812-4e08-a756-e2442f814a51
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 046186f6-4812-4e08-a756-e2442f814a51
set locale_dir=($root)/boot/grub/locale
set lang=it_IT
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
menuentry 'Ubuntu, con Linux 2.6.38-10-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 046186f6-4812-4e08-a756-e2442f814a51
    linux    /boot/vmlinuz-2.6.38-10-generic-pae root=UUID=046186f6-4812-4e08-a756-e2442f814a51 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-10-generic-pae
}
menuentry 'Ubuntu, con Linux 2.6.38-10-generic-pae (modalità ripristino)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 046186f6-4812-4e08-a756-e2442f814a51
    echo    'Loading Linux 2.6.38-10-generic-pae ...'
    linux    /boot/vmlinuz-2.6.38-10-generic-pae root=UUID=046186f6-4812-4e08-a756-e2442f814a51 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 046186f6-4812-4e08-a756-e2442f814a51
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 046186f6-4812-4e08-a756-e2442f814a51
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sdd1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdd,msdos1)'
    search --no-floppy --fs-uuid --set=root 0454A30C54A30012
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdd2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdd,msdos2)'
    search --no-floppy --fs-uuid --set=root CCA811C2A811AC48
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
UUID=046186f6-4812-4e08-a756-e2442f814a51 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=c3ef0577-c694-4caf-953a-53b780e57a18 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 428.208526611 = 459.785404416  boot/grub/core.img                             1
 418.245391846 = 449.087569920  boot/grub/grub.cfg                             1
 374.129192352 = 401.718161408  boot/initrd.img-2.6.38-10-generic-pae          2
 373.357852936 = 400.889942016  boot/vmlinuz-2.6.38-10-generic-pae             2
 374.129192352 = 401.718161408  initrd.img                                     2
 373.357852936 = 400.889942016  vmlinuz                                        2

========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc 

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by coffeecat on 2011-08-11
This is a bit of a puzzle. The boot script output looks OK to me and I haven't yet worled out why you should be getting a grub error.

Let's clarify a few things first. The boot script identifies your 500GB drive as sda and your 1000GB drive as sdd. Ubuntu is installed to sda; Windows 7 in sdd. Is your 500GB drive the USB one and the 1000GB the internal drive? And when you booted the live CD was the BIOS set to give priority to the external drive over the internal one. I just need to check these points to explain why the external drive is showing as sda.

According the boot script output, if you disconnect the USB drive, the machine should boot from the 1000GB drive straight into Windows. Is this what happens?

But this is where I get puzzled. If you have the 500GB drive plugged in, the way the grub bootloader is installed and the contents of its configuration file (grub.cfg) tells me that it *should* boot into the grub menu and give you a choice between Ubuntu and Windows. But clearly not.

It's late here. I'll look at this again in the morning when I'm fresher to see if I've missed anything.

---

### Post by nikademo on 2011-08-12
Yes you guessed all right. W7 is on 1000GB, Ubuntu on partition 2 of 500GB. When I boot from USB I get the grub error, if I boot without the external hd I get W7 as usual.

> **coffeecat said:**
> This is a bit of a puzzle. The boot script output looks OK to me and I haven't yet worled out why you should be getting a grub error.

Let's clarify a few things first. The boot script identifies your 500GB drive as sda and your 1000GB drive as sdd. Ubuntu is installed to sda; Windows 7 in sdd. Is your 500GB drive the USB one and the 1000GB the internal drive? And when you booted the live CD was the BIOS set to give priority to the external drive over the internal one. I just need to check these points to explain why the external drive is showing as sda.

According the boot script output, if you disconnect the USB drive, the machine should boot from the 1000GB drive straight into Windows. Is this what happens?


---

### Post by YesWeCan on 2011-08-12
The grub rescue prompt appears when the Grub program in the MBR area is running ok but it cannot locate its files at the fixed location it has for the boot/grub directory. You can manually boot from here and once booted run grub install
[https://help.ubuntu.com/community/Grub2#Rescue%20Mode%20(''grub%20rescue%3E'')%20Booting](https://help.ubuntu.com/community/Grub2#Rescue%20Mode%20(''grub%20rescue%3E'')%20Booting)

---

