---
title: "problem with dual boot installation (it installed in the wrong disk and erased everyt"
date: 2010-08-31
forum: New to Ubuntu
---

### Post by fellowsh on 2010-08-31
Dear all,
I have 4 1T hard disks in my pc (C D E F).
I tried to install UBUNTU 10.04 (64 bit) alongside Windows 7 (64) in C
I tried the option to install then next to each other in the same drive so I split them 500G/500G each
When I rebooted, it did the scandisk of C but then I realised that it had installed Ubuntu in F and not in C and also all the content of F has been erased! I had numerous folders mainly with docs photos and videos
Any chance to recover it in any way? 
Thanx
r

---

### Post by arrange on 2010-08-31
You can try TestDisk or PhotoRec (part of TestDisk package). I think there is an option to mark a partition as NTFS though it has been formatted differently (ext? in your case).

BTW you seem to blame the error on the installer. Is that right?

---

### Post by Rubi1200 on 2010-08-31
See this:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

And, from the Ubuntu CD, boot the computer and post the results of the bootscript linked to at the bottom of my post.

---

### Post by howefield on 2010-08-31
It seems that incorrectly telling Ubuntu where to install wasn't your only mistake :-(

All that storage and no backup ? It was only a matter of time.

Chances of recovering files that have already been overwritten are fairly slim. There may be data that hasn't been overwritten so the above applications may help.

What file system had you on the disk ?

Depending on how valuable the data is, a specialist data recovery expert/company might be able to help, but could be expensive.

---

### Post by fellowsh on 2010-09-01
Dear all,
thank you very much for your kind answers. I appreciate that.
@arrange: it is my impression that Ubuntu was not installed where I told the installer. Nonetheless, I cannot rule out (a) mistake(s) on my part.

@Rubi: thanks for the links. I am trying to familiarize with the material and I will post the bootscript as soon as I get back home

@howe: I know! My bad. Do you have any recommendation in terms of companies/software to look at?

I found a link to recuva in lifehacker and managed to recuperate numerous videos yesterday nite. It did however seem to miss  files larger than 1G

---

### Post by Mark Phelps on 2010-09-01
For recovering data from MS Windows (NTFS) partitions, I highly recommend GetDataBack from Runtime Software.  I have used their products for years and they have never failed me.

You can download a free trial of GetDataBack for NTFS from their website.  It won't actually recovery any data but it will give you information on what it finds.  You can then decide whether or not to buy the commercial version from them.

Also, be sure to remove the drive that is having problems and plug it in as an external drive when you do the data scanning/recovery.  Continuing to use that drive virtually guarantees that you will not be able to recovery anything.

---

### Post by fellowsh on 2010-09-05
Dear Ruby, thank you for your kind suggestion
Please find attached the script you kindly suggested
Being a beginner I am not sure what's going on and I would be very grateful of any feedback you may have about this
I am a bit alarmed by the last bit of the script where is says BARCLAYS BANK a lot......


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd
 => No boot loader is installed in the MBR of /dev/sde
 => No boot loader is installed in the MBR of /dev/sdf
 => No boot loader is installed in the MBR of /dev/sdg

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdd6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sde1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdf1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdg1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 1,953,503,999 1,953,503,937   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1               2,048   974,240,015   974,237,968   7 HPFS/NTFS
/dev/sdd2         974,241,790 1,953,523,711   979,281,922   5 Extended
/dev/sdd5         974,241,792 1,913,815,039   939,573,248  83 Linux
/dev/sdd6       1,913,817,088 1,953,523,711    39,706,624  82 Linux swap / Solaris


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1                  63   312,576,704   312,576,642   7 HPFS/NTFS


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdf1                  63   625,137,344   625,137,282   7 HPFS/NTFS


Drive: sdg ___________________ _____________________________________________________

Disk /dev/sdg: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdg1                  63   312,576,704   312,576,642   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        AE70878070874E51                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        98F4DEAAF4DE89C0                       ntfs       Local Disk                    
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        3422BF3B1C09CB9C                       ntfs       Local Disk                    
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        630AB5E96D468077                       ntfs                                     
/dev/sdd2: PTTYPE="dos" 
/dev/sdd5        0bbd4081-afca-48a3-8353-997ebcd2d329   ext4                                     
/dev/sdd6        264e84e6-4df3-479e-b24c-7c96207c98e0   swap                                     
/dev/sdd: PTTYPE="dos" 
/dev/sde1        10E47CA4E47C8DAA                       ntfs       Lacie                         
/dev/sde: PTTYPE="dos" 
/dev/sdf1        CCB24448B24438EA                       ntfs       LaCie                         
/dev/sdf: PTTYPE="dos" 
/dev/sdg1        0ED85643D856296B                       ntfs       Lacie                         
/dev/sdg: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sde1        /media/Lacie             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=5

default=multi(0)disk(0)rdisk(2)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(2)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT


=========================== sdd5/boot/grub/grub.cfg: ===========================

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
set default="4"
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
set root='(hd3,5)'
search --no-floppy --fs-uuid --set 0bbd4081-afca-48a3-8353-997ebcd2d329
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
set root='(hd3,5)'
search --no-floppy --fs-uuid --set 0bbd4081-afca-48a3-8353-997ebcd2d329
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd3,5)'
	search --no-floppy --fs-uuid --set 0bbd4081-afca-48a3-8353-997ebcd2d329
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=0bbd4081-afca-48a3-8353-997ebcd2d329 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd3,5)'
	search --no-floppy --fs-uuid --set 0bbd4081-afca-48a3-8353-997ebcd2d329
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=0bbd4081-afca-48a3-8353-997ebcd2d329 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd3,5)'
	search --no-floppy --fs-uuid --set 0bbd4081-afca-48a3-8353-997ebcd2d329
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd3,5)'
	search --no-floppy --fs-uuid --set 0bbd4081-afca-48a3-8353-997ebcd2d329
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set ae70878070874e51
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdd5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdd5 during installation
UUID=0bbd4081-afca-48a3-8353-997ebcd2d329 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdd6 during installation
UUID=264e84e6-4df3-479e-b24c-7c96207c98e0 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdd5: Location of files loaded by Grub: ===================


 853.3GB: boot/grub/core.img
 509.7GB: boot/grub/grub.cfg
 853.4GB: boot/initrd.img-2.6.32-24-generic
 853.4GB: boot/vmlinuz-2.6.32-24-generic
 853.4GB: initrd.img
 853.4GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdd2

00000000  40 41 4e 32 30 39 33 35  31 30 7f 3a 00 00 dc 1e  |@AN2093510.:....|
00000010  00 00 42 41 52 43 4c 41  59 53 20 42 41 4e 4b 20  |..BARCLAYS BANK |
00000020  50 4c 43 00 20 20 20 20  20 20 20 20 20 20 20 20  |PLC.            |
00000030  04 00 00 fa 44 00 00 40  41 4e 32 32 37 31 37 31  |....D..@AN227171|
00000040  30 7f 3a 00 00 dc 1e 00  00 42 41 52 43 4c 41 59  |0.:......BARCLAY|
00000050  53 20 42 41 4e 4b 20 50  4c 43 00 20 20 20 20 20  |S BANK PLC.     |
00000060  20 20 20 20 20 20 20 04  00 00 fa 44 00 00 40 41  |       ....D..@A|
00000070  4e 37 32 34 38 32 31 30  7f 3a 00 00 dc 1e 00 00  |N7248210.:......|
00000080  42 41 52 43 4c 41 59 53  20 42 41 4e 4b 20 50 4c  |BARCLAYS BANK PL|
00000090  43 00 20 20 20 20 20 20  20 20 20 20 20 20 04 00  |C.            ..|
000000a0  00 fa 44 00 00 40 41 4e  39 32 35 31 32 31 31 7f  |..D..@AN9251211.|
000000b0  3a 00 00 dc 1e 00 00 42  41 52 43 4c 41 59 53 20  |:......BARCLAYS |
000000c0  42 41 4e 4b 20 50 4c 43  00 20 20 20 20 20 20 20  |BANK PLC.       |
000000d0  20 20 20 20 20 04 00 00  fa 44 00 00 40 41 50 30  |     ....D..@AP0|
000000e0  30 35 36 59 31 30 7f 3a  00 00 dc 1e 00 00 42 41  |056Y10.:......BA|
000000f0  52 43 4c 41 59 53 20 42  41 4e 4b 20 50 4c 43 00  |RCLAYS BANK PLC.|
00000100  20 20 20 20 20 20 20 20  20 20 20 20 04 00 00 fa  |            ....|
00000110  44 00 00 40 41 50 30 30  35 38 36 31 30 7f 3a 00  |D..@AP0058610.:.|
00000120  00 dc 1e 00 00 42 41 52  43 4c 41 59 53 20 42 41  |.....BARCLAYS BA|
00000130  4e 4b 20 50 4c 43 00 20  20 20 20 20 20 20 20 20  |NK PLC.         |
00000140  20 20 20 04 00 00 fa 44  00 00 40 41 50 33 30 35  |   ....D..@AP305|
00000150  35 37 31 30 7f 3a 00 00  dc 1e 00 00 42 41 52 43  |5710.:......BARC|
00000160  4c 41 59 53 20 42 41 4e  4b 20 50 4c 43 00 20 20  |LAYS BANK PLC.  |
00000170  20 20 20 20 20 20 20 20  20 20 04 00 00 fa 44 00  |          ....D.|
00000180  00 40 41 50 33 30 35 38  30 31 31 7f 3a 00 00 dc  |.@AP3058011.:...|
00000190  1e 00 00 42 41 52 43 4c  41 59 53 20 42 41 4e 4b  |...BARCLAYS BANK|
000001a0  20 50 4c 43 00 20 20 20  20 20 20 20 20 20 20 20  | PLC.           |
000001b0  20 04 00 00 fa 44 00 00  40 41 50 33 37 30 00 fe  | ....D..@AP370..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 c0 00 38 00 fe  |.............8..|
000001d0  ff ff 05 fe ff ff 02 c0  00 38 00 e8 5d 02 00 00  |.........8..]...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by fellowsh on 2010-09-05
Dear Mark, thank you for your kind suggestion
I ended up buying GetDataBack and managed to recover everything!!!
I am very grateful. Recuva only managed to recover some bit and pieces but GetDataBack worked wonders!!! Thank you so much!
I am still wondering what went wrong
In any case thank you all for your kind suggestions
Best
R

---

### Post by candtalan on 2010-09-05
In some cases when using the Ubuntu installer at the partitioner decision stage I have noticed that a radio button has been apparently checked when all I did was to move the mouse across it. It did not require me to actually click the mouse!

My guess is that the op's attention was focussed on the changes to partition size of the win7 partition, and at some stage, a change from the original selected marked radio button to another one, went un noticed. The new selection would have been the next option I think, 'take over complete drive'.

The particular drive then used and taken over would be that one showing at the time in the selected field.
hth

---

