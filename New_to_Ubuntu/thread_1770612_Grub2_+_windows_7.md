---
title: "Grub2 + windows 7"
date: 2011-05-29
forum: New to Ubuntu
---

### Post by viniciuscarvalho on 2011-05-29
Hi, I've recently install a new HD fresh, and put win7 and ubuntu 11.04. First windows, and later ubuntu, as I was trying to avoid the annoying windows MBR overwriting.

Problem is, that windows for some reason creates a 100mb partition on sda1, and that is the partition that grub2 believes it's windows:
vinicius@cyberton:/etc/grub.d$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1eb5b968

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          206848   481279999   240536576    7  HPFS/NTFS
/dev/sda3       481280000   676591615    97655808   83  Linux
/dev/sda4       676593662   976771071   150088705    5  Extended
/dev/sda5       676593664   684404735     3905536   82  Linux swap / Solaris
/dev/sda6       684406784   976771071   146182144   83  Linux


My question is (I knew this on the great, good easy to use grub 1): How can I just change from sda1 to sda2 on grub2?

Regards

---

### Post by ram0042 on 2011-05-29
> **viniciuscarvalho said:**
> Hi, I've recently install a new HD fresh, and put win7 and ubuntu 11.04. First windows, and later ubuntu, as I was trying to avoid the annoying windows MBR overwriting.

Problem is, that windows for some reason creates a 100mb partition on sda1, and that is the partition that grub2 believes it's windows:
vinicius@cyberton:/etc/grub.d$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1eb5b968

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          206848   481279999   240536576    7  HPFS/NTFS
/dev/sda3       481280000   676591615    97655808   83  Linux
/dev/sda4       676593662   976771071   150088705    5  Extended
/dev/sda5       676593664   684404735     3905536   82  Linux swap / Solaris
/dev/sda6       684406784   976771071   146182144   83  Linux


My question is (I knew this on the great, good easy to use grub 1): How can I just change from sda1 to sda2 on grub2?

Regards
Cannot find the **menu.lst** anymore. Whatever it has been replaced with, it has to be in that **/boot/grub/** directory. I was just going to say to switch the hdX,Y to hdX,Z: where **X** is the correct HDD and **Z** is the correct partition.

Maybe if you reinstall grub2 (which is risky) you can edit that configuration.

---

### Post by ajgreeny on 2011-05-29
There is no menu.lst file any more in grub2; it's been replaced by grub.cfg, but you can not edit that manually, as it is read-only, and even if you did, it would revert next time you run update-grub, or a new kernel appears in updates.

Have a look at the grub2 info at [Grub 2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275") for all the info.  I assume that the windows OS is in the list shown by grub, but it is just the wrong one of the two.  I think that is a known bug of grub, and was for Vista as well.

---

### Post by coffeecat on 2011-05-29
> **viniciuscarvalho said:**
> Problem is, that windows for some reason creates a 100mb partition on sda1, and that is the partition that grub2 believes it's windows:

That is normal. It is possible to install Windows 7 on a single partition but if you leave the installer to its own devices it will create a separate boot partition of about 100MB. Which also has some repair utilities, I believe. Grub 2 doesn't believe that Windows is on sda1, it simply boots Windows from sda1 - which is OK. 

> **viniciuscarvalho said:**
> 
My question is (I knew this on the great, good easy to use grub 1): How can I just change from sda1 to sda2 on grub2?

Why would you want to? Is Windows booting OK?

---

### Post by oldfred on 2011-05-29
You will not have grub legacy unless you have upgraded from versions 9.04 or before and not installed grub2. Most installs now are grub2.

Windows installs a (hidden in windows) 100MB boot/recovery partition. It has two essential boot files in that partition and the boot flag. Windows boots to the partition with the boot flag and the BCD then defines the main windows install. Windows also has essential boot code in the partition boot sector. Grub does not use boot flag but searches for the boot files and sets up to jump to the partition boot sector with the boot code.

While discussing Vista, Windows 7 is the same and all MBR/msdos computers work the same way. Grub just does not put code into the PBR like windows and lilo. If too much info review pictures for a general overview.
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by viniciuscarvalho on 2011-05-30
> **coffeecat said:**
> That is normal. It is possible to install Windows 7 on a single partition but if you leave the installer to its own devices it will create a separate boot partition of about 100MB. Which also has some repair utilities, I believe. Grub 2 doesn't believe that Windows is on sda1, it simply boots Windows from sda1 - which is OK. 



Why would you want to? Is Windows booting OK?

Windows is not booting anymore. As I said, it tries to boot from sda1, but the windows is installed on sda2.

All I want is a way to change this, make grub load the sda2 not sda1. Where do I change that?

---

### Post by coffeecat on 2011-05-30
> **viniciuscarvalho said:**
> Windows is not booting anymore. As I said, it tries to boot from sda1, but the windows is installed on sda2.

All I want is a way to change this, make grub load the sda2 not sda1. Where do I change that?

Since Windows 7 is designed to boot from its 100MB boot partition and is not doing so, I think we need to investigate that. You could add a sda2 stanza to your /etc/grub.d/40_custom file, and it may or may not work, but it would be better to see what has gone wrong with Windows.

Boot into Ubuntu and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Follow the instructions there to download and run the boot info script and post the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] for clarity. We'll be able to see from that what has gone wrong with the Windows boot files.

---

### Post by viniciuscarvalho on 2011-05-30
Thanks a lot guys, Results.txt below.

The funny part is that windows does not boot. it shows a bootloader with a windows 7 option, I select it and got an error 0xc000000c or something like that.

Regards

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos3)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   481,279,999   481,073,152   7 NTFS / exFAT / HPFS
/dev/sda3         481,280,000   676,591,615   195,311,616  83 Linux
/dev/sda4         676,593,662   976,771,071   300,177,410   5 Extended
/dev/sda5         676,593,664   684,404,735     7,811,072  82 Linux swap / Solaris
/dev/sda6         684,406,784   976,771,071   292,364,288  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        A6E6316EE6313FBB                       ntfs       System Reserved
/dev/sda2        4210414210413DE3                       ntfs       
/dev/sda3        db809e96-d974-44a0-a9f7-42d4a1802dc2   ext4       
/dev/sda5        1a998e9a-ab0b-409e-9a12-8a85eceedef4   swap       
/dev/sda6        dcbc3ede-f7d3-43ff-b9d3-66c0a99917a5   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda6        /home                    ext4       (rw,user_xattr,commit=0)


=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos3)'
search --no-floppy --fs-uuid --set=root db809e96-d974-44a0-a9f7-42d4a1802dc2
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos3)'
search --no-floppy --fs-uuid --set=root db809e96-d974-44a0-a9f7-42d4a1802dc2
set locale_dir=($root)/boot/grub/locale
set lang=en_IE
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root db809e96-d974-44a0-a9f7-42d4a1802dc2
	linux	/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=db809e96-d974-44a0-a9f7-42d4a1802dc2 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root db809e96-d974-44a0-a9f7-42d4a1802dc2
	echo	'Loading Linux 2.6.38-8-generic-pae ...'
	linux	/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=db809e96-d974-44a0-a9f7-42d4a1802dc2 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root db809e96-d974-44a0-a9f7-42d4a1802dc2
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root db809e96-d974-44a0-a9f7-42d4a1802dc2
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root A6E6316EE6313FBB
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

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=db809e96-d974-44a0-a9f7-42d4a1802dc2 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=dcbc3ede-f7d3-43ff-b9d3-66c0a99917a5 /home           ext4    defaults,user_xattr        0       2
# swap was on /dev/sda5 during installation
UUID=1a998e9a-ab0b-409e-9a12-8a85eceedef4 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 261.640377045 = 280.934215680  boot/grub/core.img                             1
 305.934020996 = 328.494153728  boot/grub/grub.cfg                             1
 231.668167114 = 248.751800320  boot/initrd.img-2.6.38-8-generic-pae           1
 230.184020996 = 247.158210560  boot/vmlinuz-2.6.38-8-generic-pae              1
 231.668167114 = 248.751800320  initrd.img                                     1
 230.184020996 = 247.158210560  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 30 77 00 00 fe  |...........0w...|
000001d0  ff ff 05 fe ff ff 02 30  77 00 00 28 6d 11 00 00  |.......0w..(m...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error


```

---

### Post by coffeecat on 2011-05-30
First thing - your sda2 partition does not contain the /bootmgr and /Boot/BCD files needed for booting so creating a grub sda2 stanza wouldn't work. Second thing is that the boot script has not shown any problems in the boot sectors of sda1 and sda2, therefore no reason why Windows is not booting. It wasn't a wasted exercise to run the boot script though. Sometimes grub code finds its way into the boot sector of a Windows partition and interferes with the Windows boot files. At least we have excluded that issue.

It would be helpful if you recorded the exact error that Windows throws out. "Something like that" doesn't help for googling the error message. :wink: If you google an exact error message you can often get very helpful hits.

Do you have a Microsoft installation DVD or repair CD for Windows 7? I know you installed Windows 7 but we need to know whether this was from a Microsoft DVD or an OEM manufacturer's restore disc. If you have an installation DVD, you could boot from it, go to the system recovery choice and try the startup repair. More details here:

[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)

Be careful not to let it "repair" the mbr. If it does this it overwrites the grub code with Windows code, and if it doesn't fix the Windows booting problem you won't be able to boot into Windows or Ubuntu. Not the end of the world because it's easy to re-install grub frm the Ubuntu live CD, but it's something you'll want to avoid.

You might want to wait until oldfred comments on this last suggestion. Running the startup repair from the Windows disc isn't going to do any harm, but oldfred knows a thing or three about this area, and it would be useful to see what he has to say.

---

### Post by darkomano on 2011-05-30
If Windows 7 does not boot it should be repaired first. 
Windows 7 installation creates a so called "System Reserved" partition, makes that partition active and places there the Windows 7 boot environment. Then installs on another primary partition the Windows 7 OS.
There are many problems with this System reserved:
- main problem is that it uses one primary entry in the partition table (only 4 entries in total)
- the space allocated by default - 100 MB - can generate problems later due to its small size.
 
You can delete this System reserved make the Windows 7 partition active (and primary) and then run the "Startup Repair" option from Windows 7 install/recovery DVD/CD up to three times to get the Windows 7 boot repaired.
 
I have on my notebook Windows 7 code in the MBR.
Windows 7 bootmgr can chain load grub2 (Kubuntu) and load Windows 7
When grub2 receives control it can either load Kubuntu or chain load Windows 7.
 
The setup of the dual-boot entry for Kubuntu(grub2) is fairly easy.
Create a so called "Boot sector loader entry" in the BCD (Boot Config Data) and give it as target the file "boot.img" (this file contains the grub first stage boot code an resides in directory /boot/grub). "boot.img" should be placed(copied) on the active partition in the root ("\" for Windows) or in a special folder so you always know where it is.
 
Please note that **partition addressing** in Windows and in Ubuntu/Grub2 **is** **absolute** so if you delete the "system reserved" partition than you have to repair the Windows boot environment and the grub2 boot environment ! (boot.img holds an absolute partition address too !)
 
And here a link for a BCD editor - [http://boyans.my3gb.com](http://boyans.my3gb.com) which can create the boot loader entry for Ubuntu in Windows 7 BCD on one click. You have to adjust the path to "boot.img" with actual drive and folder. The standard Windows 7 tool for manipulating the BCD - bcdedit.exe is a command line tool and has pretty complex commands.
 
With Super Grub disk the repair of Grub2 is pretty easy.

---

### Post by oldfred on 2011-05-30
darkomano is correct that you can in effect obsolete the 100MB boot/recovery partition that windows 7 creates. It is for two reasons. One is to let you encrypt the main partition as the boot files can not be encrypted. The other is to have the recovery partition separate, so if you have problems in the main install you may still be able to boot to a recovery on your hard drive with out having to have a recovery CD.

I do not like running the auto repair as it will also reinstall windows boot loader to the MBR. You can just run the command line versions of the same repairs and skip the one that is fixMBR or reinstalling windows boot loader to the MBR. Repairs only work on the partition with the boot flag as that is how windows knows which partition is the boot partition.

I copied the windows command line repairs in this post from several windows sites.
oldfred's Windows Vista/Win7 repair links posts #7 & #9:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)
Make sure boot flag is set for any partition you try to repair.

---

