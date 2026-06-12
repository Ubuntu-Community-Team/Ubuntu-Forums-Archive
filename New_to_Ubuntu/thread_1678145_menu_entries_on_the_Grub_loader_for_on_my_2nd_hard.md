---
title: "menu entries on the Grub loader for on my 2nd hard-disk cannot boot"
date: 2011-01-29
forum: New to Ubuntu
---

### Post by wstay on 2011-01-29
After installing Ubuntu 10.04 and booting the system, I find that there are menu entries on the Grub loader for my other operating systems on my 2nd hard-disk which the installed Grub loader cannot boot. When I boot the windows os on my 2nd hard-disk, it boots my windows os on my 1st hard-disk instead. How or what to put on the /etc/grub.d/40_custom file to get the Grub loader to boot my windows os on the 2nd hard-disk?
Can someone please help.

---

### Post by wilee-nilee on 2011-01-29
> **wstay said:**
> After installing Ubuntu 10.04 and booting the system, I find that there are menu entries on the Grub loader for my other operating systems on my 2nd hard-disk which the installed Grub loader cannot boot. When I boot the windows os on my 2nd hard-disk, it boots my windows os on my 1st hard-disk instead. How or what to put on the /etc/grub.d/40_custom file to get the Grub loader to boot my windows os on the 2nd hard-disk?
Can someone please help.

So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

---

### Post by wstay on 2011-01-29
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #9 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /grldr /ntldr 
                       /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda7 and 
                       looks at sector 901166239 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #7 for 
                       /boot/grub/stage2.
    Operating System:  Welcome to openSUSE 11.2 
                       "Emerald" - Kernel ().
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /grldr /ntldr 
                       /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdb7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb9: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Mandriva Linux release 2010.0 
                       (Official) for i586 Kernel 2.6.31.14-desktop-1mnb on a 
                       Dual-processor i686 /
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   102,398,309   102,398,247   7 HPFS/NTFS
/dev/sda2         102,398,310   204,796,619   102,398,310   7 HPFS/NTFS
/dev/sda3         204,796,620   307,210,994   102,414,375   7 HPFS/NTFS
/dev/sda4    *    307,211,056   976,768,064   669,557,009   f W95 Ext d (LBA)
/dev/sda5         307,211,058   819,234,674   512,023,617   7 HPFS/NTFS
/dev/sda6         819,234,738   901,166,174    81,931,437  83 Linux
/dev/sda7         901,166,238   972,671,489    71,505,252  83 Linux
/dev/sda8         972,671,553   976,768,064     4,096,512  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 164.7 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    20,482,874    20,482,812   7 HPFS/NTFS
/dev/sdb2          20,482,875    81,947,564    61,464,690   7 HPFS/NTFS
/dev/sdb3          81,947,565   122,897,249    40,949,685   7 HPFS/NTFS
/dev/sdb4         122,897,311   321,669,494   198,772,184   f W95 Ext d (LBA)
/dev/sdb5         122,897,313   225,311,624   102,414,312   7 HPFS/NTFS
/dev/sdb6         225,311,688   266,357,699    41,046,012   7 HPFS/NTFS
/dev/sdb7         266,357,763   286,840,574    20,482,812   7 HPFS/NTFS
/dev/sdb8         286,840,638   290,937,149     4,096,512  82 Linux swap / Solaris
/dev/sdb9         290,937,213   321,669,494    30,732,282  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        568C83D18C83AA57                       ntfs       500GbXpSp3BlackEd2009Feb      
/dev/sda2        30E0F166E0F13328                       ntfs       500GbVistaUltimate10in1Sp2Activa
/dev/sda3        00542DCA542DC2F0                       ntfs       500GbW7ExtremeUltimate        
/dev/sda4: PTTYPE="dos" 
/dev/sda5        164098F47285DD01                       ntfs       500GbBackup250G               
/dev/sda6        f4cc8f0c-f6e2-4643-a547-4010530906e3   ext3                                     
/dev/sda7        20860e87-4cd7-480a-8a5d-b5bd1e7b8d63   reiserfs   OPENSUSE-11.                  
/dev/sda8        87aa8e19-ab9b-4883-a8ae-83b1bbd03efd   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        90C02598C0258596                       ntfs       150GB-XP-Sp2-VistaTheme       
/dev/sdb2        15FF1A9BCC935841                       ntfs       150GB-VISTA-SP1-EXTREME       
/dev/sdb3        06D6879AD687891F                       ntfs       150GB-Wins7Ultimate2009R1     
/dev/sdb4: PTTYPE="dos" 
/dev/sdb5        1254145F5414483D                       ntfs       150GB-BACKUP-1-Spare          
/dev/sdb6        9C5488EA5488C88A                       ntfs       150GB-BACKUP-2-ForUse         
/dev/sdb7        3E100FB3100F7167                       ntfs       150GB-BACKUP-3-Mei            
/dev/sdb8        c3daeed8-a79c-4603-a732-28f5ea90ff12   swap                                     
/dev/sdb9        ead12f68-b917-435a-a548-9d3be39d1f14   ext3       Mandriva_Dvd2010              
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext3       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="XP-Prof-BlackEd" /NOEXECUTE=OPTIN /FASTDETECT


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set f4cc8f0c-f6e2-4643-a547-4010530906e3
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set f4cc8f0c-f6e2-4643-a547-4010530906e3
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
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set f4cc8f0c-f6e2-4643-a547-4010530906e3
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=f4cc8f0c-f6e2-4643-a547-4010530906e3 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set f4cc8f0c-f6e2-4643-a547-4010530906e3
	echo	'Loading Linux 2.6.32-28-generic ...'
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=f4cc8f0c-f6e2-4643-a547-4010530906e3 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set f4cc8f0c-f6e2-4643-a547-4010530906e3
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=f4cc8f0c-f6e2-4643-a547-4010530906e3 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set f4cc8f0c-f6e2-4643-a547-4010530906e3
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=f4cc8f0c-f6e2-4643-a547-4010530906e3 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set f4cc8f0c-f6e2-4643-a547-4010530906e3
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set f4cc8f0c-f6e2-4643-a547-4010530906e3
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 568c83d18c83aa57
	chainloader +1
}
menuentry "Desktop -- openSUSE 11.2 - 2.6.31.14-0.4 (on /dev/sda7)" {
	insmod reiserfs
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 20860e87-4cd7-480a-8a5d-b5bd1e7b8d63
	linux /boot/vmlinuz-2.6.31.14-0.4-desktop root=/dev/disk/by-id/ata-SAMSUNG_HD502HJ_S20BJA0Z115107-part7 resume=/dev/disk/by-id/ata-WDC_WD800JB-00FMA0_WD-WMAJ97059404-part8 splash=silent quiet showopts vga=0x314
	initrd /boot/initrd-2.6.31.14-0.4-desktop
}
menuentry "Desktop -- openSUSE 11.2 - 2.6.31.14-0.4 For Boot From Mandriva2010 (on /dev/sda7)" {
	insmod reiserfs
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 20860e87-4cd7-480a-8a5d-b5bd1e7b8d63
	linux /boot/vmlinuz-2.6.31.14-0.4-desktop root=/dev/disk/by-id/ata-SAMSUNG_HD502HJ_S20BJA0Z115107-part7 resume=/dev/disk/by-id/ata-WDC_WD800JB-00FMA0_WD-WMAJ97059404-part8 splash=silent quiet showopts vga=0x314
	initrd /boot/initrd-2.6.31.14-0.4-desktop
}
menuentry "Failsafe -- openSUSE 11.2 - 2.6.31.14-0.4 (on /dev/sda7)" {
	insmod reiserfs
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 20860e87-4cd7-480a-8a5d-b5bd1e7b8d63
	linux /boot/vmlinuz-2.6.31.14-0.4-desktop root=/dev/disk/by-id/ata-SAMSUNG_HD502HJ_S20BJA0Z115107-part7 showopts apm=off noresume nosmp maxcpus=0 edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x314
	initrd /boot/initrd-2.6.31.14-0.4-desktop
}
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
	insmod ntfs
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 90c02598c0258596
	chainloader +1
}
menuentry "linux (on /dev/sdb9)" {
	insmod ext2
	set root='(hd1,9)'
	search --no-floppy --fs-uuid --set ead12f68-b917-435a-a548-9d3be39d1f14
	linux /boot/vmlinuz BOOT_IMAGE=linux root=UUID=ead12f68-b917-435a-a548-9d3be39d1f14 splash=silent resume=UUID=87aa8e19-ab9b-4883-a8ae-83b1bbd03efd vga=788
	initrd (hd0,8)/boot/initrd.img
}
menuentry "desktop 2.6.31.5-1mnb (on /dev/sdb9)" {
	insmod ext2
	set root='(hd1,9)'
	search --no-floppy --fs-uuid --set ead12f68-b917-435a-a548-9d3be39d1f14
	linux /boot/vmlinuz-2.6.31.5-desktop-1mnb BOOT_IMAGE=desktop_2.6.31.5-1mnb root=UUID=ead12f68-b917-435a-a548-9d3be39d1f14 splash=silent resume=UUID=87aa8e19-ab9b-4883-a8ae-83b1bbd03efd vga=788
	initrd (hd0,8)/boot/initrd-2.6.31.5-desktop-1mnb.img
}
menuentry "desktop 2.6.31.13-1mnb (on /dev/sdb9)" {
	insmod ext2
	set root='(hd1,9)'
	search --no-floppy --fs-uuid --set ead12f68-b917-435a-a548-9d3be39d1f14
	linux /boot/vmlinuz-2.6.31.13-desktop-1mnb BOOT_IMAGE=desktop_2.6.31.13-1mnb root=UUID=ead12f68-b917-435a-a548-9d3be39d1f14 splash=silent resume=UUID=87aa8e19-ab9b-4883-a8ae-83b1bbd03efd vga=788
	initrd (hd0,8)/boot/initrd-2.6.31.13-desktop-1mnb.img
}
menuentry "desktop 2.6.31.14-1mnb (on /dev/sdb9)" {
	insmod ext2
	set root='(hd1,9)'
	search --no-floppy --fs-uuid --set ead12f68-b917-435a-a548-9d3be39d1f14
	linux /boot/vmlinuz-2.6.31.14-desktop-1mnb BOOT_IMAGE=desktop_2.6.31.14-1mnb root=UUID=ead12f68-b917-435a-a548-9d3be39d1f14 splash=silent resume=UUID=87aa8e19-ab9b-4883-a8ae-83b1bbd03efd vga=788
	initrd (hd0,8)/boot/initrd-2.6.31.14-desktop-1mnb.img
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
05_otheros
}
menuentry "windows 7 (loader) (on /dev/sdb1)" {
        insmod ntfs
        set root='(hd1,1)'
        search --no-floppy --fs-uuid --set 90c02598c0258596
        chainloader +1
}


### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=f4cc8f0c-f6e2-4643-a547-4010530906e3 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=87aa8e19-ab9b-4883-a8ae-83b1bbd03efd none            swap    sw              0       0
# swap was on /dev/sdb8 during installation
UUID=c3daeed8-a79c-4603-a732-28f5ea90ff12 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 425.3GB: boot/grub/core.img
 425.3GB: boot/grub/grub.cfg
 425.4GB: boot/initrd.img-2.6.32-21-generic
 425.4GB: boot/initrd.img-2.6.32-28-generic
 425.3GB: boot/vmlinuz-2.6.32-21-generic
 425.4GB: boot/vmlinuz-2.6.32-28-generic
 425.4GB: initrd.img
 425.4GB: initrd.img.old
 425.4GB: vmlinuz
 425.3GB: vmlinuz.old

=========================== sda7/boot/grub/menu.lst: ===========================

# Modified by YaST2. Last modification on Sun Jan  9 13:42:00 MYT 2011
# THIS FILE WILL BE PARTIALLY OVERWRITTEN by perl-Bootloader
# Configure custom boot parameters for updated kernels in /etc/sysconfig/bootloader

default 0
timeout 60
##YaST - generic_mbr
gfxmenu (hd0,6)/boot/message

###Don't change this comment - YaST2 identifier: Original name: linux###
title Desktop -- openSUSE 11.2 - 2.6.31.14-0.4
    root (hd0,6)
    kernel /boot/vmlinuz-2.6.31.14-0.4-desktop root=/dev/disk/by-id/ata-SAMSUNG_HD502HJ_S20BJA0Z115107-part7 resume=/dev/disk/by-id/ata-WDC_WD800JB-00FMA0_WD-WMAJ97059404-part8 splash=silent quiet showopts vga=0x314
    initrd /boot/initrd-2.6.31.14-0.4-desktop

title Desktop -- openSUSE 11.2 - 2.6.31.14-0.4 For Boot From Mandriva2010
    root (hd1,6)
    kernel /boot/vmlinuz-2.6.31.14-0.4-desktop root=/dev/disk/by-id/ata-SAMSUNG_HD502HJ_S20BJA0Z115107-part7 resume=/dev/disk/by-id/ata-WDC_WD800JB-00FMA0_WD-WMAJ97059404-part8 splash=silent quiet showopts vga=0x314
    initrd /boot/initrd-2.6.31.14-0.4-desktop

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 11.2 - 2.6.31.14-0.4
    root (hd0,6)
    kernel /boot/vmlinuz-2.6.31.14-0.4-desktop root=/dev/disk/by-id/ata-SAMSUNG_HD502HJ_S20BJA0Z115107-part7 showopts apm=off noresume nosmp maxcpus=0 edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x314
    initrd /boot/initrd-2.6.31.14-0.4-desktop

###Don't change this comment - YaST2 identifier: Original name: windows 5###
title 150GB
    map (hd1) (hd0)
    map (hd0) (hd1)
    rootnoverify (hd1,0)
    makeactive
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: windows 2###
title 500GB
    rootnoverify (hd0,0)
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: linux###
title HT150GbMandriva2010
    root (hd1,8)
    kernel /boot/vmlinuz-2.6.31.14-desktop-1mnb root=/dev/sdb9 vga=0x305
    initrd /boot/initrd-2.6.31.14-desktop-1mnb.img

=============================== sda7/etc/fstab: ===============================

/dev/disk/by-id/ata-SAMSUNG_HD502HJ_S20BJA0Z115107-part7 /                    reiserfs   acl,user_xattr        1 1
/dev/disk/by-id/ata-WDC_WD800JB-00FMA0_WD-WMAJ97059404-part8 swap                 swap       defaults              0 0
/dev/disk/by-id/ata-SAMSUNG_HD502HJ_S20BJA0Z115107-part8 swap                 swap       defaults              0 0
/dev/disk/by-id/ata-HDT722516DLA380_VDS91DTGC6HYUZ-part9 swap                 swap       defaults              0 0
proc                 /proc                proc       defaults              0 0
sysfs                /sys                 sysfs      noauto                0 0
debugfs              /sys/kernel/debug    debugfs    noauto                0 0
usbfs                /proc/bus/usb        usbfs      noauto                0 0
devpts               /dev/pts             devpts     mode=0620,gid=5       0 0

=================== sda7: Location of files loaded by Grub: ===================


    ??GB: boot/grub/menu.lst
    ??GB: boot/grub/stage2
    ??GB: boot/initrd
    ??GB: boot/initrd-2.6.31.14-0.4-desktop
    ??GB: boot/vmlinuz
    ??GB: boot/vmlinuz-2.6.31.14-0.4-desktop

================================ sdb1/boot.ini: ================================

;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT


=========================== sdb9/boot/grub/menu.lst: ===========================

timeout 60e
color black/cyan yellow/cyan
gfxmenu (hd0,8)/boot/gfxmenu
default 5

title linux
kernel (hd0,8)/boot/vmlinuz BOOT_IMAGE=linux root=UUID=ead12f68-b917-435a-a548-9d3be39d1f14 splash=silent resume=UUID=87aa8e19-ab9b-4883-a8ae-83b1bbd03efd vga=788
initrd (hd0,8)/boot/initrd.img

title desktop 2.6.31.5-1mnb
kernel (hd0,8)/boot/vmlinuz-2.6.31.5-desktop-1mnb BOOT_IMAGE=desktop_2.6.31.5-1mnb root=UUID=ead12f68-b917-435a-a548-9d3be39d1f14 splash=silent resume=UUID=87aa8e19-ab9b-4883-a8ae-83b1bbd03efd vga=788
initrd (hd0,8)/boot/initrd-2.6.31.5-desktop-1mnb.img

title desktop 2.6.31.13-1mnb
kernel (hd0,8)/boot/vmlinuz-2.6.31.13-desktop-1mnb BOOT_IMAGE=desktop_2.6.31.13-1mnb root=UUID=ead12f68-b917-435a-a548-9d3be39d1f14 splash=silent resume=UUID=87aa8e19-ab9b-4883-a8ae-83b1bbd03efd vga=788
initrd (hd0,8)/boot/initrd-2.6.31.13-desktop-1mnb.img

title desktop 2.6.31.14-1mnb
kernel (hd0,8)/boot/vmlinuz-2.6.31.14-desktop-1mnb BOOT_IMAGE=desktop_2.6.31.14-1mnb root=UUID=ead12f68-b917-435a-a548-9d3be39d1f14 splash=silent resume=UUID=87aa8e19-ab9b-4883-a8ae-83b1bbd03efd vga=788
initrd (hd0,8)/boot/initrd-2.6.31.14-desktop-1mnb.img

title 500Gb
root (hd1,0)
map (0x81) (0x80)
map (0x80) (0x81)
makeactive
chainloader +1

title 150Gb
root (hd0,0)
makeactive
chainloader +1

title openSUSE 11.2 (i586)
root (hd1,6)
configfile /boot/grub/menu.lst






=============================== sdb9/etc/fstab: ===============================

# Entry for /dev/sdb9 :
UUID=ead12f68-b917-435a-a548-9d3be39d1f14 / ext3 relatime 1 1
/dev/cdrom /media/cdrom auto umask=0,users,iocharset=utf8,noauto,ro,exec 0 0
# Entry for /dev/sda1 :
UUID=568C83D18C83AA57 /media/win_c ntfs-3g defaults,umask=000 0 0
# Entry for /dev/sdb1 :
UUID=90C02598C0258596 /media/win_c2 ntfs-3g defaults,umask=000 0 0
# Entry for /dev/sda5 :
UUID=164098F47285DD01 /media/win_d ntfs-3g defaults,umask=000 0 0
# Entry for /dev/sdb5 :
UUID=1254145F5414483D /media/win_d2 ntfs-3g defaults,umask=000 0 0
# Entry for /dev/sda2 :
UUID=30E0F166E0F13328 /media/win_e ntfs-3g defaults,umask=000 0 0
# Entry for /dev/sdb6 :
UUID=9C5488EA5488C88A /media/win_e2 ntfs-3g defaults,umask=000 0 0
# Entry for /dev/sda3 :
UUID=00542DCA542DC2F0 /media/win_f ntfs-3g defaults,umask=000 0 0
# Entry for /dev/sdb7 :
UUID=3E100FB3100F7167 /media/win_f2 ntfs-3g defaults,umask=000 0 0
# Entry for /dev/sdb2 :
UUID=15FF1A9BCC935841 /media/win_g ntfs-3g defaults,umask=000 0 0
# Entry for /dev/sdb3 :
UUID=06D6879AD687891F /media/win_h ntfs-3g defaults,umask=000 0 0
none /proc proc defaults 0 0
# Entry for /dev/sda8 :
UUID=87aa8e19-ab9b-4883-a8ae-83b1bbd03efd swap swap defaults 0 0
/dev/sdb8 swap swap defaults 0 0

=================== sdb9: Location of files loaded by Grub: ===================


 163.4GB: boot/grub/menu.lst
 163.3GB: boot/grub/stage2
 162.1GB: boot/initrd-2.6.31.13-desktop-1mnb.img
 162.3GB: boot/initrd-2.6.31.14-desktop-1mnb.img
 162.2GB: boot/initrd-2.6.31.5-desktop-1mnb.img
 162.3GB: boot/initrd-desktop.img
 162.3GB: boot/initrd.img
 162.1GB: boot/vmlinuz
 162.1GB: boot/vmlinuz-2.6.31.13-desktop-1mnb
 162.1GB: boot/vmlinuz-2.6.31.14-desktop-1mnb
 162.2GB: boot/vmlinuz-2.6.31.5-desktop-1mnb
 162.1GB: boot/vmlinuz-desktop
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb4

00000000  b5 25 65 65 3a ab ad 56  9a 74 da a7 6a 97 38 c0  |.%ee:..V.t..j.8.|
00000010  d3 ae b3 59 be 0b 5d 9e  ce b4 d5 a6 d3 6a a8 c8  |...Y..]......j..|
00000020  db 3e db 6b 95 b6 da cc  7b 92 3a 49 cc 6d a2 48  |.>.k....{.:I.m.H|
00000030  be d7 6f 04 5f c7 9f d7  e4 7b b5 6e 02 5f 59 3d  |..o._....{.n._Y=|
00000040  85 eb 6e 2a 8a ac e9 8c  96 0e 68 24 ba e2 0d d8  |..n*......h$....|
00000050  8a 81 5c 36 1d 04 55 6b  c2 20 4c 63 71 9e a4 82  |..\6..Uk. Lcq...|
00000060  a9 bc e4 32 57 95 52 0f  00 4f 79 64 a0 c1 ab 5e  |...2W.R..Oyd...^|
00000070  df e4 7b 0d 3e a7 3a 26  00 3c 3f 0f a4 a9 e9 8a  |..{.>.:&.<?.....|
00000080  b4 f5 64 c0 1f 12 e0 90  26 07 46 88 01 6c d6 7e  |..d.....&.F..l.~|
00000090  3a e2 d8 12 c8 d7 da d1  2b c7 69 0d 1f c3 2e 17  |:.......+.i.....|
000000a0  dc 98 25 90 d4 cc 24 35  78 f5 8f c2 20 1f 7f 08  |..%...$5x... ...|
000000b0  89 61 84 38 98 79 9b af  b9 ea 32 5e 98 52 04 e0  |.a.8.y....2^.R..|
000000c0  27 80 63 bc e4 37 5b 0e  81 de 31 dc d4 3a 79 7d  |'.c..7[...1..:y}|
000000d0  1d 14 9d 14 0e cf aa 68  d1 18 79 0b 4e 42 95 fc  |.......h..y.NB..|
000000e0  82 c3 a9 41 03 f2 bc a6  0b 7f a6 5e 12 dc bf c2  |...A.......^....|
000000f0  e0 f7 9e 7f 12 89 c3 44  4e f7 64 22 be ca 00 27  |.......DN.d"...'|
00000100  42 02 77 c8 99 68 9c 8a  18 94 54 37 55 7d 74 e8  |B.w..h....T7U}t.|
00000110  8d e8 d5 a0 9a 69 8d ee  85 c2 f7 bd d0 50 12 8a  |.....i.......P..|
00000120  2f 50 05 08 28 14 0a 36  87 5d d3 e6 22 6a df 85  |/P..(..6.].."j..|
00000130  e8 74 4e b3 db 91 fc 61  1b 47 c9 18 e4 18 0e 8e  |.tN....a.G......|
00000140  a1 06 4a 21 04 43 47 57  b3 87 c2 f2 7a bf c6 9a  |..J!.CGW....z...|
00000150  2f 92 ed fd c8 40 d7 e7  e6 7e d9 1c ca f8 7c 77  |/....@...~....|w|
00000160  56 63 97 a7 fa f3 75 7b  8f c7 d7 75 db d2 53 13  |Vc....u{...u..S.|
00000170  bd f6 68 89 03 df 46 91  b9 63 ef 6a 2a 78 4a 6d  |..h...F..c.j*xJm|
00000180  b8 b5 ac ae 5f c0 f2 eb  48 32 79 cc 65 c1 50 5c  |...._...H2y.e.P\|
00000190  6b d3 20 05 dc 94 cc 18  62 94 19 df 01 ff 1d cf  |k. .....b.......|
000001a0  d3 fe ba aa 60 c8 a0 e8  e5 ac fd 48 de f3 5a b3  |....`......H..Z.|
000001b0  3f d4 e5 90 66 62 01 ee  39 49 f7 de f9 96 00 01  |?...fb..9I......|
000001c0  41 e2 07 fe bf c8 02 00  00 00 e8 b7 1a 06 00 fe  |A...............|
000001d0  ff ff 05 fe ff ff ea b7  1a 06 3b 50 72 02 00 00  |..........;Pr...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by wstay on 2011-01-30
> **wilee-nilee said:**
> So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

The Results.txt from the Boot_Info_Script.sh is in the above reply column.

---

### Post by oldfred on 2011-01-30
Windows combines the boot of different windows systems into one as that is the only way windows can boot. Windows uses the boot flag (active partition) to know what partition to boot. Grub does not use boot flag. You do have two boot flags in sda, you should remove one, but that would only help solve an issue if you revert to a windows boot loader.

The script does not parse BCD, so we cannot see how win7 is booting. But the boot.ini shown in both sda & sdb refers to drive0 or sda.

Not sure if your issue is win7 or XP. note this from script:
> ;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.


You can edit boot.ini from Ubuntu but have to be sure to save with windows line endings. nano works, gedit has a setting.

You have to use BCDEDIT in windows to edit the BCD.

Lots of info on how windows boots, review pictures if you just want a quick overview.
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by wstay on 2011-02-04
> **oldfred said:**
> Windows combines the boot of different windows systems into one as that is the only way windows can boot. Windows uses the boot flag (active partition) to know what partition to boot. Grub does not use boot flag. You do have two boot flags in sda, you should remove one, but that would only help solve an issue if you revert to a windows boot loader.

The script does not parse BCD, so we cannot see how win7 is booting. But the boot.ini shown in both sda & sdb refers to drive0 or sda.

Not sure if your issue is win7 or XP......

My problem is that though the grub boot menu offers to boot:

menuentry "Windows 7 (loader) (on /dev/sdb1)" {
	insmod ntfs
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 90c02598c0258596
	chainloader +1
}

which is an active/system partition on the second hard-disk with the W7 bootmgr boot file in the root of sdb1,the computer cannot boot the W7 bootmgr on the second hard-disk. Instead it boots the W7 bootmgr on the first hard-disk.
Maybe we should have something as in other distro like a 
Device Map: 
(hd0) /dev/sdb
(hd1) /dev/sda
or
Device Map:
(hd0.hd1)
(hd1,hd0)
in the /boot/grub directory or in /boot/grub/grub.cfg file.

What is your opinion and if it does work, how to write it into the /boot/grub/grub.cfg file or we can just put a Device Map file in the /boot/grub directory.
If there is already a Device Map, could you please point me to it.

---

### Post by oldfred on 2011-02-04
There is a mapdevice command for grub2. But that is not your problem. All grub does is the same thing a windows boot loader in the MBR does. It jumps to the partition boot sector to continue booting. So your issue is your windows and what the windows has set as the partitions to boot.

This has a lot of good explanation of how windows boots. It discusses Vista but also applies to 7. If you just want a quick understanding the pictures explain a lot.
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
[http://www.multibooters.co.uk/articles/windows_seven.html](http://www.multibooters.co.uk/articles/windows_seven.html)

With XP you can do all the repairs (except chkdsk) from Ubuntu to make a XP install bootable, but with 7 I think you have to use BCD edit. Windows will only repair a partition with the boot flag so you may have to move boot flags and then repair.

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
Use bootsect.exe to repair XP & older or Vista/7 bootsectors
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)


set boot flag on for sda1 (off for others)
sudo sfdisk -A1 /dev/sda

some have recommended this, I have never used it.
[http://neosmart.net/blog/2010/welcome-to-easybcd-2/](http://neosmart.net/blog/2010/welcome-to-easybcd-2/)

---

### Post by wstay on 2011-02-04
> **oldfred said:**
> 
set boot flag on for sda1 (off for others)
sudo sfdisk -A1 /dev/sda

From the RESULT.txt the sda4 which is a logical partition has a boot flag.
I tried to set the boot flag off for it but has got a problem as follow:

[wstay@localhost ~]$ su
Password:
[root@localhost wstay]# sfdisk -A1 /dev/sda4
Warning: start=307211056 - this looks like a partition rather than
the entire disk. Using fdisk on it is probably meaningless.
[Use the --force option if you really want this]
[root@localhost wstay]# sfdisk -A1 /dev/sda
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Done

[root@localhost wstay]#

sda4 is an extended partition for logical partitions.
When I installed Ubuntu, I installed Grub loader to the MBR of sda.
While doing partitioning to install windows before I installed Ubuntu, I did set the boot flag to only sda1. I don't know why and how the sda4 has a boot flag. Can this cause any problem?
From above Terminal posting there is a 'Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.'
How do I correct this?

---

### Post by oldfred on 2011-02-04
Drives are sda, sdb etc, partitions are sda1, sda2, sdb1 etc.

sudo sfdisk -A1 /dev/sda
sudo sfdisk -A1 /dev/sda4

You tried the wrong command. See also 
man sfdisk if confused.

in the A1 where the 1 is the partition and then /dev/sda is the drive.

So if you wanted the boot flag on a windows install in sda4
sudo sfdisk -A4 /dev/sda

---

### Post by wstay on 2011-02-05
> **oldfred said:**
> 
So if you wanted the boot flag on a windows install in sda4
sudo sfdisk -A4 /dev/sda

I have my sda4 as an Extended partition with a few logical partitions with no Windows installed except Linux and other ntfs partitions to store data.
Since I have sda1 as an active partition, I have set off the boot flag on sda4. I don't know how sda4 has its got boot flag when I see it in the RESULT.txt.

From the RESULTS.txt in the above reply, I don't understand why the sda1 which has Xp os installed (should have a Xp boots sector type) has a Vista/7 boot sector type whilst sda3 which is a W7 os installed (should have a W7 boot sector type) has a Xp boot sector type. Installing W7 after installing Xp could have replace the Xp boot sector type with a Vista/7 boot sector type on sda1 which is a Xp os partition. What about the Xp boot sector type on sda3 which is a W7 os partition. How did it get there?

Another question is why 
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 568c83d18c83aa57
	chainloader +1
}
can load the vista/7 boot sector from the Partition Boot Record (PBR) on sda1 and also show the w7 bootmgr boot menu (from the bcd installed). 

but
}
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
	insmod ntfs
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 90c02598c0258596
	chainloader +1
}
cannot load the vista/7 boot sector from the Partition Boot Record (PBR) on sdb1 and also therefore cannot show the w7 bootmgr boot menu from the bcd installed.
The point is the set root='(hd1,1)'is asking Ubuntu to boot sdb1 (that is from the first partition on the second hard-disk which has an active flag. Instead it boots sda1 although the set root='(hd1,1)' should tell it to boot sdb1.
The vista/7 boot sector on the PBR on sdb1 has a valid PBR because when I boot sdb (which has a Mandriva Grub loader installed on its mbr) directly on its own (not through the boot menu from Ubuntu on sda) it can boot and show the w7 bootmgr-menu for the windows on sda and also for windows on sdb and can boot normally whichever windows I choose to boot from the bootmgr-menu.
Editing the Xp boot.ini file now would not help because Ubuntu is not booting sdb from the Ubuntu Grub loader menu. As mentioned, the mbr on sdb has Mandriva Grub loader installed.
Is it possible to have Ubuntu Grub loader to boot the windows on sdb from the Mandriva Grub loader on sdb. So instead of set root='(hd1,1)', can we have set root='(hd1,0)'.

---

### Post by oldfred on 2011-02-05
Your set roots are identical. Grub2 has changed partition counting so it starts at 1 where old grub started at 0. 

Grub's chainload just jumps to the windows partition to continue booting. But grub2 has added some capability that if it does not work instead of crashing it will return.

You might try removing the extra lines and make it a 'pure' chainboot which may be more like Mandriva's old grub.

You can copy this into 40_custom and edit it (or copy several times to test).

# Entry N - Chainload another bootloader
menuentry "Chainload my OS" {
    set root=(hd1,1)
    chainloader +1
}

You may or may not need the 
drivemap -s (hd1) (hd0)

Part of the difference also is whichever drive you boot in BIOS that will be drive 0. So the mapping of drives changes, depending on which drive you boot from. I chainboot from sda, sdb, & sdc and had to change the entries depending on which drive I actually used to boot as that was 0 and then 1, & 2 became the next drives in order. Or if I boot sdb, it is drive 0 and sda is drive 1. If I boot sdc, it is drive 0 and sda is drive 1. But if I boot sda it is drive 0 and sdb is drive 1 & sdc is drive 2.

---

### Post by wstay on 2011-02-06
> **oldfred said:**
> 
You can copy this into 40_custom and edit it (or copy several times to test).
# Entry N - Chainload another bootloader
menuentry "Chainload my OS" {
    set root=(hd1,1)
    chainloader +1
}

I copy it into the 40_custom file and reboot but the menuentry "Chainload my OS" does not appear on the Grub menu.
What about the readme file in /etc/grud.d that says:
```
All executable files in this directory are processed in shell expansion order.
00_*: Reserved for 00_header.
10_*: Native boot entries.
20_*: Third party apps (e.g. memtest86+).

The number namespace in-between is configurable by system installer and/or
administrator.  For example, you can add an entry to boot another OS as
01_otheros, 11_otheros, etc, depending on the position you want it to occupy in the menu; and then adjust the default setting via .
```

Where should I put the 01_otheros or 11_otheros in  the menuentry "Chainload my OS" to position it in the Grub menu and after that, how or what to adjust in the /etc/default/grub file.

---

### Post by oldfred on 2011-02-06
I left off that you have to run this:

```
sudo update-grub
```

grub.cfg is rewritten on the above command or if system downloads new kernels or grub code (actually runs command as part of update). Changes then are only added if  command is run. Above command is actually just a script that runs other commands.

---

### Post by wstay on 2011-02-08
> **oldfred said:**
> Your set roots are identical. Grub2 has changed partition counting so it starts at 1 where old grub started at 0. 

Grub's chainload just jumps to the windows partition to continue booting. But grub2 has added some capability that if it does not work instead of crashing it will return.

You might try removing the extra lines and make it a 'pure' chainboot which may be more like Mandriva's old grub.

You can copy this into 40_custom and edit it (or copy several times to test).

# Entry N - Chainload another bootloader
menuentry "Chainload my OS" {
    set root=(hd1,1)
    chainloader +1
}

You may or may not need the 
drivemap -s (hd1) (hd0)

Part of the difference also is whichever drive you boot in BIOS that will be drive 0. So the mapping of drives changes, depending on which drive you boot from. I chainboot from sda, sdb, & sdc and had to change the entries depending on which drive I actually used to boot as that was 0 and then 1, & 2 became the next drives in order. Or if I boot sdb, it is drive 0 and sda is drive 1. If I boot sdc, it is drive 0 and sda is drive 1. But if I boot sda it is drive 0 and sdb is drive 1 & sdc is drive 2.

Making a 'pure' chainboot as suggested:

# Entry N - Chainload another bootloader
menuentry "Chainload my OS" {
    set root=(hd1,1)
    chainloader +1
}
 
also cannot boot the second hard-disk sdb. It boots the windows partition on sda instead.
I changed the set root=(hd1,1) to set root=(hd1,0) to get it to boot from the mbr of sdb where Mandriva Grub loader is installed. 
On reboot and selecting this entry from the Ubuntu Grub boot menu, it returns an error message saying 'No such partition'. 

I tried the repair option by booting the W7 installation dvd to add the windows partitions on sdb to sda W7 bootmenu.
The repair was successful and now when I select to boot from a windows partition on sdb from the Ubuntu Grub boot menu, though it boots from a sda windows partition, I am able to choose to boot the other windows partitions on sdb from it.

We can only change the chainboot setting of our hard-disks from the Bios.
Drive-mapping and chainboot setting in the grub.cfg do not seem to be able to boot the other hard-disks except sda or hd0.

What does the 'chainloader +1' in the grub.cfg refers to?
Can we have 'chainloader +0 or +2' and so on and what does that mean or what effect does it have?  

The readme file in /etc/grud.d that says:
```
Code:
All executable files in this directory are processed in shell expansion order.
00_*: Reserved for 00_header.
10_*: Native boot entries.
20_*: Third party apps (e.g. memtest86+).

The number namespace in-between is configurable by system installer and/or
administrator.  For example, you can add an entry to boot another OS as
01_otheros, 11_otheros, etc, depending on the position you want it to occupy in the menu; and then adjust the default setting via /etc/default/grub.
```

I put 01_otheros, 11_otheros in the 2 entries in the 40_custom file:

```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

#Entry 1 Boot Sdb1
01_otheros
menuentry "windows 7 (loader) (on /dev/sdb1)" {
set root=(hd1,1)
chainloader +2
}

# Entry 2 - Chainload another bootloader
11_otheros
menuentry "Chainload my OS" {
set root=(hd1,0)
chainloader +1
}
```

and it does not change anything when I boot the Ubuntu Grub boot menu. The two entries above just add to the last entry on the Ubuntu Grub boot menu when reboot. How then can we arrange the custom boot entry to boot in the position on the boot menu we want?

---

### Post by oldfred on 2011-02-08
The chainloader +1 is jump to the first sector to boot, you cannot use other sectors.

If you want to boot the MBR you have to leave off the partition. There is no partition 0 in grub2, so it is not (hd1,0) but (hd1). I chainboot grub2 from any of sda, sdb, & sdc, but the issue is that the boot drive is always hd0. Then the other drives appear in SATA port/BIOS order for me.

menuentry "Lucid Lynx on sda (When from sdc) Chainboot" {
set root=(hd1)
chainloader +1
}

---

### Post by wstay on 2011-02-09
> **oldfred said:**
> The chainloader +1 is jump to the first sector to boot, you cannot use other sectors.

If you want to boot the MBR you have to leave off the partition. There is no partition 0 in grub2, so it is not (hd1,0) but (hd1). I chainboot grub2 from any of sda, sdb, & sdc, but the issue is that the boot drive is always hd0. Then the other drives appear in SATA port/BIOS order for me.

menuentry "Lucid Lynx on sda (When from sdc) Chainboot" {
set root=(hd1)
chainloader +1
}

I put the entry into the 40_custom file:
```
#Entry 1
menuentry "To Boot hd1 mbr" {
set root=(hd1)
chainloader +1
}
```
hd1 should be sdb.
When I choose to boot menuentry "To Boot hd1 mbr" from the Ubuntu Grub menu, instead of booting the mbr of sdb, it boots with the error message - hd0,8/boot/gfxmenu: not found. It should be booting hd1,8/boot/gfxmenu which is the Mandriva partition on sdb9. On the Mandriva partition on sdb9 there is a directory /boot/gfxmenu. 
The problem is how to have boot/grub/grub.cfg on the Ubuntu partition on sda6 to read the hd1,8/boot/gfxmenu directory on the Mandriva partition on sdb9. Can the grub.cfg on Ubuntu be edited with vim editor to to include and boot the hd1,8/boot/gfxmenu directory and what stanza should be included.

---

### Post by oldfred on 2011-02-09
You are into the issues of grub legacy & grub2 counting partitions differently.

Your Mandriva is in sdb9 so old grub calls it (hd1,8) but grub2 it is (hd1,9).

Grub2's os-prober's line will work if you delete the partition number init entry that it copied from grub legacy. It does not know it should not copy that part and it is not on the init line in Ubuntu.

```
menuentry "linux (on /dev/sdb9)" {
    insmod ext2
    set root='(hd1,9)'
    search --no-floppy --fs-uuid --set ead12f68-b917-435a-a548-9d3be39d1f14
    linux /boot/vmlinuz BOOT_IMAGE=linux root=UUID=ead12f68-b917-435a-a548-9d3be39d1f14 splash=silent resume=UUID=87aa8e19-ab9b-4883-a8ae-83b1bbd03efd vga=788
    initrd [COLOR=Red](hd0,8)[/COLOR]/boot/initrd.img
}

```

Copy to 40_custom and edit out the red part an it will boot hd0,8.

Another way to boot old grub installs is to put the grub legacy into the partition and then chainload to the partition.

---

### Post by wstay on 2011-02-12
Thank you Oldfred.
After editing to (hd1,9), I got the Mandriva distro booting normally.
That means Grub2 is counting partition using hd starting from 1 and not from 0 as from legacy Grub.

According to the Readme file in the /etc/grub.d directory we can add an entry to boot another OS as 01_otheros, 11_otheros, etc, depending on the position we want it to occupy in the menu and then adjust the default setting via /etc/default/grub.

How can I get this custom entry:
> menuentry "linux (on /dev/sdb9)" {
    insmod ext2
    set root='(hd1,9)'
    search --no-floppy --fs-uuid --set ead12f68-b917-435a-a548-9d3be39d1f14
    linux /boot/vmlinuz BOOT_IMAGE=linux root=UUID=ead12f68-b917-435a-a548-9d3be39d1f14 splash=silent resume=UUID=87aa8e19-ab9b-4883-a8ae-83b1bbd03efd vga=788
    initrd (hd1,9)/boot/initrd.img
}
to boot say as the first or second entry on the boot menu.

---

### Post by oldfred on 2011-02-12
You can create 09_custom. It may be easier just to copy 40_custom to get the couple of lines that are the top and I think are required.
You then can copy your entry into 09_custom and have to make 09_custom executable.

If you put your menu entry in /etc/grub.d/40_custom it will not be over written and will be at the end of your menu. Or you can copy it to 09_custom and make it executable and it will be at the top of your menu.

or a new file that will be first in the menu
gksudo gedit /etc/grub.d/09_custom
sudo chmod 755 /etc/grub.d/09_custom

[http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html#Custom_Boot_Entries](http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html#Custom_Boot_Entries)

See #14
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

