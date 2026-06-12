---
title: "Windows dont boot"
date: 2010-06-13
forum: New to Ubuntu
---

### Post by danics on 2010-06-13
HI everybody i install ubuntu 10.04 and i have windows 7 ,but now i cant boot windows ,i install another time ubuntu but my problem dont solve,i i can mount windows drive, please guide me thanks alot.

---

### Post by danics on 2010-06-13
i m use boot info script and get this result.txt

> 
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  According to the info in the boot sector, sda1 has 
                       80259 sectors.. But according to the info from the 
                       partition table , it has 1984 sectors.
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
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63         2,047         1,985  42 SFS
/dev/sda2    *          2,048       206,847       204,800  42 SFS
/dev/sda3             206,848   204,802,047   204,595,200  42 SFS
/dev/sda4         204,804,094   625,141,759   420,337,666   5 Extended
/dev/sda5         400,115,712   497,770,495    97,654,784  83 Linux
/dev/sda6         497,772,544   509,489,151    11,716,608  82 Linux swap / Solaris
/dev/sda7         204,804,096   400,113,663   195,309,568   b W95 FAT32
/dev/sda8         509,491,200   625,141,759   115,650,560   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4016 MB, 4016046080 bytes
90 heads, 25 sectors/track, 3486 cylinders, total 7843840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               8,192     7,843,839     7,835,648   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        AADC28CCDC28949B                       ntfs       System Reserved               
/dev/sda3        F61439E01439A491                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        623f7526-1002-4523-8cd2-7d98498a7db7   ext4                                     
/dev/sda6        3ed31f31-161d-4a16-8f33-82558d0a8ab4   swap                                     
/dev/sda7        563B-28D7                              vfat                                     
/dev/sda8        6AAE-6BDB                              vfat                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        3531-F492                              vfat       Transcend                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sda7        /windows                 vfat       (rw,utf8,umask=007,gid=46)
/dev/sr0         /media/Ubuntu 10.04 LTS i386 iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)
/dev/sdb1        /media/Transcend         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 623f7526-1002-4523-8cd2-7d98498a7db7
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 623f7526-1002-4523-8cd2-7d98498a7db7
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 623f7526-1002-4523-8cd2-7d98498a7db7
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=623f7526-1002-4523-8cd2-7d98498a7db7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 623f7526-1002-4523-8cd2-7d98498a7db7
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=623f7526-1002-4523-8cd2-7d98498a7db7 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 623f7526-1002-4523-8cd2-7d98498a7db7
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=623f7526-1002-4523-8cd2-7d98498a7db7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 623f7526-1002-4523-8cd2-7d98498a7db7
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=623f7526-1002-4523-8cd2-7d98498a7db7 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 623f7526-1002-4523-8cd2-7d98498a7db7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 623f7526-1002-4523-8cd2-7d98498a7db7
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set aadc28ccdc28949b
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=623f7526-1002-4523-8cd2-7d98498a7db7 /               ext4    errors=remount-ro 0       1
# /windows was on /dev/sda7 during installation
UUID=563B-28D7  /windows        vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sda6 during installation
UUID=3ed31f31-161d-4a16-8f33-82558d0a8ab4 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 252.3GB: boot/grub/core.img
 239.9GB: boot/grub/grub.cfg
 252.7GB: boot/initrd.img-2.6.32-21-generic
 252.7GB: boot/initrd.img-2.6.32-22-generic
 252.6GB: boot/vmlinuz-2.6.32-21-generic
 252.2GB: boot/vmlinuz-2.6.32-22-generic
 252.7GB: initrd.img
 252.7GB: initrd.img.old
 252.2GB: vmlinuz
 252.6GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  30 33 33 64 00 30 66 63  61 00 38 30 30 37 00 32  |033d.0fca.8007.2|
00000010  32 30 66 00 39 31 33 64  00 38 30 30 33 00 30 34  |20f.913d.8003.04|
00000020  65 38 00 36 37 32 37 00  36 37 35 32 00 65 32 30  |e8.6727.6752.e20|
00000030  63 00 30 34 61 34 00 36  37 33 34 00 36 37 36 33  |c.04a4.6734.6763|
00000040  00 36 37 30 39 00 35 30  32 65 00 35 30 31 64 00  |.6709.502e.501d.|
00000050  35 30 32 32 00 35 30 32  66 00 35 30 32 34 00 35  |5022.502f.5024.5|
00000060  61 30 66 00 35 30 33 33  00 30 34 30 39 00 35 30  |a0f.5033.0409.50|
00000070  35 37 00 35 30 38 31 00  35 30 35 61 00 35 31 31  |57.5081.505a.511|
00000080  38 00 35 30 38 33 00 35  31 31 61 00 35 31 31 64  |8.5083.511a.511d|
00000090  00 35 31 32 35 00 35 30  39 31 00 35 30 38 62 00  |.5125.5091.508b.|
000000a0  35 30 38 61 00 35 30 34  37 00 35 30 37 66 00 35  |508a.5047.507f.5|
000000b0  30 35 34 00 35 30 37 64  00 35 30 39 33 00 35 31  |054.507d.5093.51|
000000c0  32 31 00 35 30 33 63 00  30 37 38 31 00 37 34 31  |21.503c.0781.741|
000000d0  30 00 37 34 35 30 00 37  34 35 32 00 37 34 33 32  |0.7450.7452.7432|
000000e0  00 37 34 33 34 00 37 34  64 30 00 37 34 38 30 00  |.7434.74d0.7480.|
000000f0  37 34 32 30 00 37 34 32  32 00 37 34 36 30 00 37  |7420.7422.7460.7|
00000100  34 63 30 00 37 34 63 32  00 37 34 30 31 00 37 34  |4c0.74c2.7401.74|
00000110  30 30 00 37 34 33 30 00  37 34 62 30 00 30 34 37  |00.7430.74b0.047|
00000120  34 00 30 32 33 30 00 38  39 30 31 00 38 39 30 39  |4.0230.8901.8909|
00000130  00 38 39 31 31 00 31 30  30 31 00 30 33 35 33 00  |.8911.1001.0353.|
00000140  32 32 30 65 00 30 33 32  37 00 30 63 37 37 00 31  |220e.0327.0c77.1|
00000150  30 31 31 00 31 30 31 35  00 31 30 31 30 00 31 38  |011.1015.1010.18|
00000160  66 36 00 31 62 64 63 00  66 61 62 66 00 30 65 63  |f6.1bdc.fabf.0ec|
00000170  37 00 30 35 34 63 00 30  30 34 65 00 30 33 34 33  |7.054c.004e.0343|
00000180  00 30 32 66 38 00 30 33  35 63 00 30 33 35 62 00  |.02f8.035c.035b.|
00000190  30 33 36 65 00 30 33 64  38 00 30 33 38 35 00 30  |036e.03d8.0385.0|
000001a0  33 32 36 00 30 33 66 65  00 30 33 38 65 00 30 33  |326.03fe.038e.03|
000001b0  35 61 00 30 33 38 63 00  30 33 38 38 00 30 00 fe  |5a.038c.0388.0..|
000001c0  ff ff 83 fe ff ff 02 38  a4 0b 00 18 d2 05 00 fe  |.......8........|
000001d0  ff ff 05 fe ff ff 02 50  76 11 00 d0 b2 00 00 00  |.......Pv.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

hexdump: sda1/AUTOEXEC.UP: Input/output error
hexdump: sda1/AUTOEXEC.UP: Input/output error
hexdump: sda1/AUTOEXEC.UP: Input/output error
hexdump: sda1/DELLDIAG.INI: Input/output error
hexdump: sda1/SEAL.EXE: Input/output error
hexdump: sda1/SEAL.EXE: Input/output error
hexdump: sda1/SEAL.EXE: Input/output error



please help me how can i fix my boot

---

### Post by oldfred on 2010-06-13
I do not see anything in the script that shows a problem. Maybe someone else will.

You have the windows install that boots thru a 100MB boot/windows recovery partition into the full install in sda3. The windows files and boot sectors look normal.

Did windows boot ok before you installed. Did you use windows to shrink the windows partition?

I would just try the windows repairs from the windows CD. If you run fixMBR you will have to reinstall grub so be prepared for that.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
kansasnoob on grub or grub2 reinstall
[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r /f (may have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

---

### Post by Sylchat on 2010-06-15
I have a similar problem, when selecting the windows 7 partition, I only get a black screen with a blinking underscore. I'm about to try the testdisk solution ([http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)).

See thread [http://ubuntuforums.org/showthread.php?p=9345043](http://ubuntuforums.org/showthread.php?p=9345043)

---

### Post by wilee-nilee on 2010-06-15
> **Sylchat said:**
> I have a similar problem, when selecting the windows 7 partition, I only get a black screen with a blinking underscore. I'm about to try the testdisk solution ([http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)).

See thread [http://ubuntuforums.org/showthread.php?p=9345043](http://ubuntuforums.org/showthread.php?p=9345043)

I wouldn't just run testdisk without starting a thread and posting the script in my sig with the code tags as described

---

### Post by Sylchat on 2010-06-15
> **wilee-nilee said:**
> I wouldn't just run testdisk without starting a thread and posting the script in my sig with the code tags as described

Thanks for the advice, but I've already read all the info I needed, and gathered information (fdisk -l, bootscript, backed up MBR and GRUB).
I just wanted to mention that testdisk seemed to repair better than the windows fixmbr tool, from what I've seen. 

The only thing strange, is that the script reports sda1 as boot (*) which is the windows recovery partition (Seven is actually on sda2). So I'll may post in a new thread anyway.

---

### Post by wilee-nilee on 2010-06-15
> **Sylchat said:**
> Thanks for the advice, but I've already read all the info I needed, and gathered information (fdisk -l, bootscript, backed up MBR and GRUB).
I just wanted to mention that testdisk seemed to repair better than the windows fixmbr tool, from what I've seen. 

The only thing strange, is that the script reports sda1 as boot (*) which is the windows recovery partition (Seven is actually on sda2). So I'll may post in a new thread anyway.

Yeah if you know how to read the script thats great, my main concern was that sometimes people try fixes without knowing whats up, and with a boot problem that can be disastrous at worse and fixable at best. If you start a thread feel free to PM me I may not have the answer, but I wont give you advice that will bork your setup.

Most of the time the recovery is the boot partition it is part of the recovery process in some computers, especially with a OEM setup.

---

### Post by Sylchat on 2010-06-15
> **wilee-nilee said:**
> Yeah if you know how to read the script thats great, my main concern was that sometimes people try fixes without knowing whats up, and with a boot problem that can be disastrous at worse and fixable at best. If you start a thread feel free to PM me I may not have the answer, but I wont give you advice that will bork your setup.

Most of the time the recovery is the boot partition it is part of the recovery process in some computers, especially with a OEM setup.

The script is great, it gives all the info I needed (and some I already got). But I really don't want to mess up with my ubuntu machine, and I need to clarify to myself a few things before (I have 1 MBR per disk, got 2 disks, what MBR is chosen, and what testdisk does, is something I will investigate/ask).

But now, back from holidays, got zillions things to do at work :/

---

### Post by wilee-nilee on 2010-06-15
> **Sylchat said:**
> The script is great, it gives all the info I needed (and some I already got). But I really don't want to messed up with my ubuntu machine, and I need to clarify to myself a few things before (I have 1 MBR per disk, got 2 disks, what MBR is chosen, and what testdisk does, is something I will investigate/ask).

But now, back from holidays, got zillions things to do at work :/

Once you know where grub goes to the mbr you can install in what ever order you want and just reload the mbr if needed. If you in the future do a W7 install after Ubuntu you just want to prebuild the ntfs partition with gparted or any one that will build it independent of the W7 install disc. I have had my Ubuntu installs go unallocated with doing a custom W7 install and letting it build the partition.

---

### Post by Sylchat on 2010-06-15
> **wilee-nilee said:**
> Once you know where grub goes to the mbr you can install in what ever order you want and just reload the mbr if needed. If you in the future do a W7 install after Ubuntu you just want to prebuild the ntfs partition with gparted or any one that will build it independent of the W7 install disc. I have had my Ubuntu installs go unallocated with doing a custom W7 install and letting it build the partition.

Yes, this is why I had a few questions regarding MBR... I posted a new thread here: [http://ubuntuforums.org/showthread.php?t=1510195](http://ubuntuforums.org/showthread.php?t=1510195)

---

