---
title: "no bootable device found"
date: 2011-08-07
forum: New to Ubuntu
---

### Post by HLS69 on 2011-08-07
Dear folks

I know that Ubuntu runs on my laptop because I have already had installed the OS on my Laptop

A Acer Aspire 3810T. Yesterday I received my new Samsung Spinpoint M8 1TB drive.

I first wanted to install MAC OS onto it and everything worked fine - the I noticed that my hardware isn t fully supported by MAC OS and I ditched it! Durhin the installation process I changed the hard drive to GUID partition table!

Now everytime I install ubuntu installation runs fine but after the installation (when ubuntu should start) it shows

"No bootable device found"

Do you think that this is the problem and if yes: how can I fix it?

btw win7 installs just fine but I think that doesnt help.
There is no needed data on the hdd - everythin can be wiped completely.

---

### Post by oldfred on 2011-08-07
If you are only going to have Ubuntu on the 1TB drive ever, you should leave it as gpt. But you have to create a bios_grub partition if booting from BIOS or an efi partition if using UEFI.

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

GPT Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

However, in the GPT setup, there is no space following the 512-byte MBR for embedding the "second stage" core.img. Thus, you must make a separate "BIOS boot partition" to hold core.img. You can set bios_grub flag in gparted or with command line: In GPT fdisk (gdisk), give it a type code of EF02.
BIOS Boot Partition of about 100 KiB to 1 MiB.

sudo parted /dev/sda set <partition_number> bios_grub on

It only needs to be about 32 KiB in size, although in most cases make it 1 MiB because of partition alignment issues

---

### Post by HLS69 on 2011-08-07
I want to only install Ubuntu and nothign more and currently I want to keep it as simple to only know if it works.

Before I read your post I changed the partition table to MBR already. Unfortunately this doesn t change much.. instead of the error message

"no bootable device found" I now only see a blinking coursor...

please give me some advices

---

### Post by oldfred on 2011-08-07
No bootable device is often a BIOS error, but I thought it was only with Intel motherboards/BIOS. Some BIOS check to make sure there is a boot flag on a primary partition. Grub does not use nor need a boot flag, windows has to have one on a primary partition. It seems some BIOS check for boot flag and do not let grub work without one or assume windows.

Try putting a boot flag on any primary partition. (We even have to do that with some gpt systems even though gpt also does not use a boot flag normally.)

---

### Post by srs5694 on 2011-08-07
If you changed from GPT to MBR in a way that left the OS intact, you'll need to re-install GRUB, since GPT and MBR use different boot loader code.

At this point, if you can't get it working, it's probably best to do one of two things:


[list]
[*]Re-install from scratch, either to an MBR disk or to a GPT disk that contains a BIOS Boot Partition, as oldfred suggested; or
[*]Boot using an emergency system, run the [Boot Info Script,](http://sourceforge.net/projects/bootinfoscript/) and post the RESULTS.txt file that it produces here. Be sure to post it between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags for legibility.
[/list]

---

### Post by HLS69 on 2011-08-07
I tried boot info script but it gave me an error -.-

this is what I tiped into the terminal:

ubuntu@ubuntu:/media/System-reserviert$ sh boot_info_script.sh

and this is what I got

```

boot_info_script version: 0.60        [17 May 2011]


"gawk" could not be found, using "busybox awk" instead.
This may lead to unreliable results.

[: 326: busybox awk: unexpected operator
boot_info_script.sh: 353: Syntax error: "(" unexpected (expecting "fi")
ubuntu@ubuntu:/media/System-reserviert$ sh boot_info_script.sh

boot_info_script version: 0.60        [17 May 2011]


"gawk" could not be found, using "busybox awk" instead.
This may lead to unreliable results.

[: 326: busybox awk: unexpected operator
boot_info_script.sh: 353: Syntax error: "(" unexpected (expecting "fi")
ubuntu@ubuntu:/media/System-reserviert$ 

```

is it because "gawk" is missing?
I think I have to set the boot partition you two mentioned manually.

Because I have never done setting up the boot partition before I thought it is a good idea to first install Windows7 (which sets up the boot partition automatically as you told) and then install ubuntu to see if this will lead to success. Afterwards I could then do the whole thing manually and get rid of win7.

 This didn t work for me because the Ubuntu setup doesn t see the installed windows at all and just gives me the option to install Ubuntu or to partition manually - normaly there should be the option "Install Ubuntu besides Windows7"?!

---

### Post by oldfred on 2011-08-07
Had exactly the same error in another thread. You need to use sudo.

Command posted here:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

  sudo bash ~/Desktop/boot_info_script.sh

or if you have cd into folder

sudo bash boo{tab}  #if you hit tab it will complete line automatically.

---

### Post by HLS69 on 2011-08-07
worked like a charm with sudo :)

here are the results:

```
Boot Info Script 0.60    from 17 May 2011
 
 
 ============================= Boot Info Summary: ===============================
 
  => Windows is installed in the MBR of /dev/sda.
  => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.
 
 sda1: __________________________________________________  ________________________
 
     File system:       ntfs
     Boot sector type:  Windows Vista/7
     Boot sector info:   No errors found in the Boot Parameter Block.
     Operating System:  
     Boot files:        /bootmgr /Boot/BCD
 
 sda2: __________________________________________________  ________________________
 
     File system:       ntfs
     Boot sector type:  Windows Vista/7
     Boot sector info:   No errors found in the Boot Parameter Block.
     Operating System:  Windows 7
     Boot files:        /Windows/System32/winload.exe
 
 sdb1: __________________________________________________  ________________________
 
     File system:       vfat
     Boot sector type:  SYSLINUX 4.04 2011-04-18
     Boot sector info:   Syslinux looks at sector 2185080 of /dev/sdb1 for its 
                        second stage. SYSLINUX is installed in the  directory. 
                        The integrity check of the ADV area failed. No errors 
                        found in the Boot Parameter Block.
     Operating System:  
     Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys
 
 ============================ Drive/Partition Info: =============================
 
 Drive: sda __________________________________________________  ___________________
 
 Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
 255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
 Units = sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 
 Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
 
 /dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
 /dev/sda2             206,848 1,953,521,663 1,953,314,816   7 NTFS / exFAT / HPFS
 
 
 GUID Partition Table detected, but does not seem to be used.
 
 Partition    Start Sector    End Sector  # of Sectors System
 
 Drive: sdb __________________________________________________  ___________________
 
 Disk /dev/sdb: 3984 MB, 3984588800 bytes
 128 heads, 10 sectors/track, 6080 cylinders, total 7782400 sectors
 Units = sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 
 Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
 
 /dev/sdb1    *             63     7,782,399     7,782,337   b W95 FAT32
 
 
 "blkid" output: __________________________________________________  ______________
 
 Device           UUID                                   TYPE       LABEL
 
 /dev/loop0                                              squashfs   
 /dev/sda1        5204169D041683DF                       ntfs       System-reserviert
 /dev/sda2        38541BA3541B6344                       ntfs       
 /dev/sdb1        725C-5E17                              vfat       
 
 ================================ Mount points: =================================
 
 Device           Mount_Point              Type       Options
 
 /dev/loop0       /rofs                    squashfs   (ro,noatime)
 /dev/sdb1        /cdrom                   vfat        (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,i   ocharset=iso8859-1,shortname=mixed,errors=remount-ro)
 
 
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
 
 # If you would like to use the new menu and be presented with the option  to install or run from USB at startup, remove # from the following  line. This line was commented out (by request of many) to allow the old  menu to be presented and to enable booting straight into the Live  Environment! 
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
 
 =============================== StdErr Messages: ===============================
 
 /home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected
```as mentioned before I insrtalled win7 in hope that it sets up the boot partition automatically but as final result I only want to have Ubuntu.

EDIT: The entrys of my USB stick with the Ubuntu setup are also in the RESULTS.txt but I think you already noticed that at first glance xD

---

### Post by oldfred on 2011-08-07
Windows will not work on gpt partitioning ( unless you use UEFI) and it looks like you have some bits of gpt left even though windows has converted to gpt.

I do not want to steal srs5694 thunder as this is his program, but not sure how soon he may post.

FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by srs5694 on 2011-08-07
If you intend to keep Windows, as it's installed in the MBR, your first step should be to get rid of the stray GPT data, as oldfred suggests. From there, you should be able to resize your Windows partitions (which is most safely done within Windows) to make room for Linux, add Linux partitions (which you should *not* do in Windows!), and install Linux. This should work *if* you installed Windows after installing Linux and if the Windows filesystems are intact.

If you installed Linux after you installed Windows, it could be that Linux is installed using GPT but that the MBR data reported by Boot Info Script is hiding the GPT partitions. If this is the case, the GPT and MBR partitions doubtless overlap, and there's no telling which is intact and which has been damaged. In this situation, it's best to delete everything and start from scratch:


[list=1]
[*]In the Ubuntu installer's "try it now" mode, launch a shell and type "sudo apt-get install gdisk".
[*]Type "sudo sgdisk -Z /dev/sda". (This assumes that /dev/sda is the disk you want to wipe clean and re-use. Verify this identity first if you have any doubts about it.) This command erases all the MBR and GPT data on the disk, making it safe to re-use it.
[*]Do one of two things:

[list]
[*]If you want to dual-boot with Windows, you should reboot and install Windows, giving it as much disk space as you want it to have. The Windows installer will create a fresh MBR partition table.
[*]If you *don't* want to dual-boot with Windows (if you want a Linux-only installation), you must decide whether to use MBR (old and well-understood by many people) or GPT (new and with some improvements over MBR, but less well-understood by most people) for your partitions. Launch GParted and select Device -> Create Partition Table. Click Advanced and select either "msdos" (for MBR) or "gpt" (for GPT). If you choose GPT, create a ~1 MiB partition with no filesystem and set the "bios_grub flag" on it. There's no need to create any special partition for MBR at this point (the Ubuntu installer will do that).
[/list]

[*]Reboot and install Linux, using its partitioner to create partitions.
[/list]

---

### Post by HLS69 on 2011-08-07
Oh no :(

As I can tell fixparts didn t solve the problem, too -.-

I am still getting the "No bootable device" message.

This is what I ve done:

Installed fixparts and started it in the terminal with:

```
sudo fixparts /dev/sda
```fixparts asked:

```
NOTICE: GPT signatures detected on the disk, but no 0xEE protective partition!
The GPT signatures are probably left over from a previous partition table.
Do you want to delete them (if you answer 'Y', this will happen
immediately)? (Y/N):
```and I pressed Y, then I exit the console.
The fixparts homepage states that you dont have to save the opearation and fixparts didn t ask me the question again when I enterede sudo fixparts /dev/sda again.

I ll put up a log of "boot_info_script" again.

EDIT:

okay this is what boot_info_script gave me

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /etc/fstab

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 2185080 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048   249,999,359   249,997,312  83 Linux
/dev/sda2         250,001,406 1,953,523,711 1,703,522,306   5 Extended
/dev/sda5         250,001,408 1,949,523,967 1,699,522,560  83 Linux
/dev/sda6       1,949,526,016 1,953,523,711     3,997,696  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 3984 MB, 3984588800 bytes
128 heads, 10 sectors/track, 6080 cylinders, total 7782400 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63     7,782,399     7,782,337   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        930eafb6-eaed-40e7-85dd-ef5d0ebea651   ext4       
/dev/sda5        8cdfa2c3-6653-4517-9288-040b8baedab0   ext4       
/dev/sda6        3d70ae1b-3f61-40cb-9713-85e908211f82   swap       
/dev/sdb1        725C-5E17                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


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
# /boot was on /dev/sda5 during installation
UUID=8cdfa2c3-6653-4517-9288-040b8baedab0 /boot           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=3d70ae1b-3f61-40cb-9713-85e908211f82 none            swap    sw              0       0
--------------------------------------------------------------------------------

============================= sda5/grub/grub.cfg: ==============================

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
  insmod efi_gop
  insmod efi_uga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 930eafb6-eaed-40e7-85dd-ef5d0ebea651
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 8cdfa2c3-6653-4517-9288-040b8baedab0
set locale_dir=($root)/grub/locale
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
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 8cdfa2c3-6653-4517-9288-040b8baedab0
    linux    /vmlinuz-2.6.38-8-generic root=UUID=930eafb6-eaed-40e7-85dd-ef5d0ebea651 ro   quiet splash vt.handoff=7
    initrd    /initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 8cdfa2c3-6653-4517-9288-040b8baedab0
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /vmlinuz-2.6.38-8-generic root=UUID=930eafb6-eaed-40e7-85dd-ef5d0ebea651 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 8cdfa2c3-6653-4517-9288-040b8baedab0
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 8cdfa2c3-6653-4517-9288-040b8baedab0
    linux16    /memtest86+.bin console=ttyS0,115200n8
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

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 135.337242126 = 145.317257216  grub/grub.cfg                                  1
 119.370632172 = 128.173240320  initrd.img-2.6.38-8-generic                    1
 119.354801178 = 128.156241920  vmlinuz-2.6.38-8-generic                       1

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

=============================== StdErr Messages: ===============================

/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```the Line "GUID Partition Table detected, but does not seem to be used" is gone - I asume thats a step forwared?!

Is it possible that the error is here:
"Windows is installed in the MBR of /dev/sda." ?

At the installation I created 3 partitions:

a 128GB sys logical partition, about 800GB extended partition and a 2GB swap drive.
Then I chose to install Ubuntu to the 128GB drive (set it to "/")...

Sorry, I am totaly lost and dont know what to do.. I ve never worked with such low level HDD formating tools.

---

### Post by oldfred on 2011-08-07
I would still put a boot flag on a primary partition.

But you have to reinstall grub to the MBR. You also have a separate /boot (which I do not recommend for standard desktops).

Many instructions do not mention the extra line to mount the /boot partition or have it has a footnote that most users miss.

#If separate /boot
$ sudo mount /dev/sda1 /mnt
$ sudo mount /dev/sda5 /mnt/boot
$ grub-install --boot-directory=/mnt /dev/sda

But you may just want to consider reinstalling. Your /boot is large and your / is small which is backwards.

We have also seen issues with very large / (root) partitions. It is better to keep root small and let /home be the larger partition.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3) With a 1TB drive you can even be a little larger but do not have to be a lot larger.
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by HLS69 on 2011-08-08
Putting a boot flag onto the primary partition means re installing grub? Which I can do with the Terminal commands you posted,right?

Ive got a question regarding partitioning:

What should my secondary drive be:
 /home or / ? I always choose /boot because it was right under / but I didnt knew what it meant.

I also need the sweap partition because I am hibernating a lot and I got 4GB of RAM.
4GB = 4000MiB right? But the Uhuntu setup routine states "MB" so should I choose 4000mb or 4096mb as sweap?

Will try reinstalling grub (which I think means puting a Boot flag onto the Drogen) when I get home in 2hours.

Thank you :)

---

### Post by hansolo4949 on 2011-08-08
I believe that /boot has to be in the primary drive, and /home/ has to be in the secondary if you want it to boot. Also, technically, 4 GB of ram SHOULD be 4096 MB, but manufacturers like to round, so it will only be around 4000 MB technically Which size you choose for swap will not crash you system, (I have the same amount of ram as you do, and I believe ubuntu formatted a 2 GB swap file) so I would google around and find the recommended size. When you have 4 GB of ram, you *should* not need a large swap file.

---

### Post by srs5694 on 2011-08-08
> **HLS69 said:**
> Putting a boot flag onto the primary partition means re installing grub? Which I can do with the Terminal commands you posted,right?

No, the "boot flag" is a bit in the partition table that identifies a partition as bootable. You can set it (or clear it) using fdisk, parted, GParted, or other partitioning tools. AFAIK, the GRUB installation scripts do not change the boot flag, nor do they use it themselves.

> What should my secondary drive be:
 /home or / ? I always choose /boot because it was right under / but I didnt knew what it meant.

The term "secondary drive" is not a standard term in partitioning, so it's unclear to me what you mean by this. I suspect you're confusing and extrapolating some other common disk terms:


[list]
[*]**Primary partition** -- This is one of the four partitions that can be defined in the primary Master Boot Record (MBR) partition table.
[*]**Extended partition** -- This is a special type of primary partition that holds logical partitions.
[*]**Logical partition** -- This is a type of partition that's contained within an extended partition. Logical partitions exist as a workaround for the shortsightedness of whoever designed the primary partition table to be only large enough to hold four primary partitions.
[*]**Master disk** -- This refers to a jumper setting for a PATA hard disk. It's meaningless for SATA disks.
[*]**Slave disk** -- This refers to a jumper setting for a PATA hard disk. It's meaningless for SATA disks.
[/list]


You could also be using "primary" in some generic and non-technical way.

> I also need the sweap partition because I am hibernating a lot and I got 4GB of RAM.
4GB = 4000MiB right? But the Uhuntu setup routine states "MB" so should I choose 4000mb or 4096mb as sweap?

First, I believe you mean "swap," not "sweap." Swap space is a partition or file that's used as a supplement to RAM.

Second, there's a lot of confusion over units in computers. Years ago, people in the computer industry began abusing [SI prefixes,](http://en.wikipedia.org/wiki/Si_prefix) which are commonly used in metric measurements to refer to power-of-10 multiples of a unit, as in "k" ("kilo") for 1000, "M" ("mega") for 1,000,000, and so on. In computers, many quantities are better measured by power-of-2 units, as in 1024 or 1,048,576. Since the SI units are close to those values, computer people began using them inappropriately.

There are several problems with this, though. For instance, it confuses those who are familiar with SI prefixes in normal contexts; and some programs and sub-industries (such as disk manufacturers and in measuring modem speeds) used the SI prefixes properly, leading to ambiguity.

Thus, a few years ago new prefixes were defined, [IEEE-1541 units,](http://en.wikipedia.org/wiki/IEEE_1541-2002) which precisely and unambiguously describe power-of-2 values, as in "KiB" ("kibibyte") for 1,024 and "MiB" (mebibyte) for 2,048,576.

To get more directly to your question, your computer's memory is almost certainly described by a power-of-2 unit, so it's probably 4 GiB even if the computer manufacturer incorrectly describes it as "4 GB". Thus, you'd need at least 4 GiB in swap space to hibernate successfully. Part of the problem, though, is that it might not be clear if the partitioning software you use is measuring in GiB or GB, particularly if the label is "GB". There might also be rounding going on, so you might set a slider at a value that reads "4 GiB" when in fact the program will produce a partition that's 3.98 GiB in size. For these reasons, I recommend going a bit over the required amount -- say, 4.5 GiB or 5 GiB for swap space. That way you can be sure you've got enough.

[quote=hansolo4949]I believe that /boot has to be in the primary drive, and /home/ has to be in the secondary if you want it to boot.[/quote]

Again, "secondary" isn't a normal term for disks or partitions. My suspicion is that you mean "logical partition." Interpreted that way, your statement is incorrect. Linux doesn't care about the primary vs. logical status of its partitions; you can boot a system with all primary partitions, all logical partitions, or any mix of primary and logical that you like. (Of course, you can't exceed the limits on the number of primary partitions in MBR.) Furthermore, the nature of the /home partition, if it's separate from others, is completely irrelevant to booting the OS. The partition that holds the kernel and initial RAM disk (either root (/) or /boot) sometimes has to be handled in a special way to get around BIOS or boot loader limitations -- it may need to be located below a particular point on the disk or kept outside of a RAID or LVM configuration, for instance. These limitations don't always apply, though (it depends on your BIOS's and boot loader's limits), and if they do, they don't affect the status of that partition as primary vs. logical.

---

### Post by HLS69 on 2011-08-08
you people are awesome :)

I never ever received updates so fast and qualified in a message board :) thanks for your patience!
I read carefully over all you comments so that I can write more understandable in the future!

I also took some steps:

I used "parted magic" to set the boot flag on the partition where I installed Ubuntu. I then received "No Operating System" when I tried to boot.

Then I installed GRUB useing these commands in the terminal:

```
$ sudo mount /dev/sda1 /mnt
$ grub-install --boot-directory=/mnt /dev/sda
```

now Grub starts when I power on my machine. What to do now?
I will use google on how to use grub but maybe you can give me a hint or two - thanks.

---

### Post by srs5694 on 2011-08-08
If GRUB is starting normally, it's very easy to use -- just select the kernel or OS you want to boot with the keyboard and press the Enter key to boot it.

If you're not seeing a full GRUB menu, but rather a "grub>" prompt or some other error message, you should post details and a a fresh Boot Info Script RESULTS.txt file (since the installation of GRUB will have changed some key information from your earlier RESULTS.txt file).

---

### Post by HLS69 on 2011-08-08
RESULTS.txt.

```

Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/grub on this drive.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 2185080 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048    58,593,279    58,591,232  83 Linux
/dev/sda2       1,943,758,846 1,953,523,711     9,764,866   5 Extended
/dev/sda5       1,943,758,848 1,953,523,711     9,764,864  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 3984 MB, 3984588800 bytes
128 heads, 10 sectors/track, 6080 cylinders, total 7782400 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63     7,782,399     7,782,337   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        aa40bd20-ca42-410f-81f0-eb9232c6e838   ext4       
/dev/sda5        8dd5690c-2203-475b-b129-f748b9922ef5   swap       
/dev/sdb1        725C-5E17                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


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
  insmod efi_gop
  insmod efi_uga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root aa40bd20-ca42-410f-81f0-eb9232c6e838
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root aa40bd20-ca42-410f-81f0-eb9232c6e838
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
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root aa40bd20-ca42-410f-81f0-eb9232c6e838
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=aa40bd20-ca42-410f-81f0-eb9232c6e838 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root aa40bd20-ca42-410f-81f0-eb9232c6e838
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=aa40bd20-ca42-410f-81f0-eb9232c6e838 ro single 
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
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root aa40bd20-ca42-410f-81f0-eb9232c6e838
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root aa40bd20-ca42-410f-81f0-eb9232c6e838
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
UUID=aa40bd20-ca42-410f-81f0-eb9232c6e838 /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  14.767974854 = 15.856992256   boot/grub/grub.cfg                             1
   0.511260986 = 0.548962304    boot/initrd.img-2.6.38-8-generic               2
  14.765762329 = 15.854616576   boot/vmlinuz-2.6.38-8-generic                  1
  10.131790161 = 10.878926848   grub/core.img                                  1
   0.511260986 = 0.548962304    initrd.img                                     2
  14.765762329 = 15.854616576   vmlinuz                                        1

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

=============================== StdErr Messages: ===============================

unlzma: Decoder error
/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

when GRUB starts it displays

 "GNU GRUB version 1.99~rc1-13ubuntu3

Minimal BASH-like line editing is supported. For the first word. TAB lists possible command completions.
Anywhere else TAB lists possible device or file completions

grub>" but the menu which should normally appear is nowhere.

---

### Post by oldfred on 2011-08-08
I am not sure what the issue is, but have seen the same issue on several posts with users having very large hard drives and a very large / (root) partition. 

At least one user did follow my suggestion to just try shrinking the / partition and it worked. My normal suggestion is to make a smaller system partition of 25GB and make the rest of the drive /home or possibly additional partitions for NTFS if sharing with windows or a backup partition etc.

Since you do not have a lot of data in / yet you should be able to use gparted from the liveCD to just shrink / to 25 or 100GB as a test. If it works you could move /home into the free space or reinstall with a separate /home.

---

### Post by HLS69 on 2011-08-08
just repartitioned my / partition with parted magic to a size of 15GB and still the same:

GRUB doesn t show me the installed Ubuntu but only a prompt where I can enter text.

---

### Post by oldfred on 2011-08-08
You can try manually booting.
Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt 
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

Your install is sda1
Adjust drive, partition to your install:
sh:grub>ls
#If on (hd0,1) or sda1
sh:grub>ls (hd0,1)/
#Should show the links vmlinuz & initrd.img
sh:grub>linux (hd0,1)/vmlinuz root=/dev/sda1
sh:grub>initrd (hd0,1)/initrd.img
sh:grub>boot

Or this may work:
configfile (hd0,1)/boot/grub/grub.cfg

Or you can download either of these:
Boot Repair as liveCD or install into Ubuntu liveCD:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Supergrub is a liveCD:
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

---

### Post by HLS69 on 2011-08-08
thank you for your suggestion - I will deffinitifely try that if nothing else works!

atm it seems like the solution may be more obvious:

I installed my old 320gb hard drive with and win7 and Ubuntu installation back into my laptop and because everything on that drive is backed up I decided to run the Ubuntu setup and see what happens -> no bootable device found!

So is something wrong with the installation file or the usb stick from where I am installing Ubuntu?
Will d/l Ubuntu again and then install it from an optical disc.

---

### Post by srs5694 on 2011-08-08
> **HLS69 said:**
> RESULTS.txt.

```

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/grub on this drive.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /grub/core.img

```

The problem is that GRUB's MBR and post-MBR code is looking for a directory called /grub on "(,msdos1)" (that is, /dev/sda1), but /dev/sda1 holds GRUB in its /boot/grub directory. In other words, GRUB is installed in the MBR as if you had a separate /boot partition, but you don't.

I'm sure there's a way to fix this by re-installing from the Ubuntu install disc, but the way I'd do it is as follows:


[list=1]
[*]Download and prepare [Super GRUB 2 Disk](http://www.supergrubdisk.org) -- note that's Super GRUB ***2*** Disk, not Super GRUB (no "2") Disk.
[*]Boot with Super GRUB 2 Disk. It will give you various options, and you may need to experiment with them before you find one that will get your system booted.
[*]With the computer booted into the installation on your hard disk, open a terminal window and type "sudo grub-install /dev/sda".
[/list]

---

### Post by HLS69 on 2011-08-08
I just used another pendrive to install Ubuntu and now everything works like a charm :)

thanks for your patience and all the advices you gave me :) at least I learnd a bit about partitioning, Linux and general and my lesson about no name pen drives ^^

---

