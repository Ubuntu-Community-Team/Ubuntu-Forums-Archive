---
title: "winload is missing or corrupt after installing Ubuntu side-by-side with Windows7"
date: 2011-04-04
forum: New to Ubuntu
---

### Post by fadimoh on 2011-04-04
i am a new user of ubunta 10.10 and i have installed it beside win7 but no in the boot screen when i choose win7 it says that winload is missing or currupt,i need help, what shoud i do??

---

### Post by s.fox on 2011-04-04
Post moved to own thread in [Absolute Beginner Talk]("http://ubuntuforums.org/forumdisplay.php?f=326")

---

### Post by Quackers on 2011-04-04
Please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by fadimoh on 2011-04-04
i did the instructions but it keep giving me 

fadi@fadi-VGN-NW21MF-S:~$ sudo bash ~/desktop/boot_info_script*.sh
bash: /home/fadi/desktop/boot_info_script*.sh: No such file or directory

i dont know why

---

### Post by Quackers on 2011-04-04
If the script is on your desktop the command is ```
sudo bash ~/Desktop/boot_info_script*.sh
```
That's a capital D for Desktop, not desktop :-)

It's usually a good idea to copy/paste commands into the terminal as it stops any typos.

---

### Post by fadimoh on 2011-04-04
#============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/grub.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63         2,047         1,985  42 SFS
/dev/sda2    *          2,048       206,847       204,800  42 SFS
/dev/sda3             206,848   614,402,047   614,195,200  42 SFS
/dev/sda4         614,404,094   976,771,071   362,366,978   5 Extended
/dev/sda5         614,404,096   615,378,943       974,848  83 Linux
/dev/sda6         615,380,992   617,332,735     1,951,744  82 Linux swap / Solaris
/dev/sda7         617,334,784   976,771,071   359,436,288  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mmcblk0p1   5DFF-0C07                              vfat       Memory card                   
/dev/sda2        1AE66B98E66B7345                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        5506723a-ab33-4aee-bc2a-50302cf276f9   ext4                                     
/dev/sda6        74fc4a8d-c724-43a2-a40a-d775887aae9e   swap                                     
/dev/sda7        643cd2f7-3d35-468b-9a3f-008f9f1fcced   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda5        /boot                    ext4       (rw,commit=0)


============================= sda5/grub/grub.cfg: =============================

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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 643cd2f7-3d35-468b-9a3f-008f9f1fcced
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 5506723a-ab33-4aee-bc2a-50302cf276f9
set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 5506723a-ab33-4aee-bc2a-50302cf276f9
	linux	/vmlinuz-2.6.35-28-generic-pae root=UUID=643cd2f7-3d35-468b-9a3f-008f9f1fcced ro   quiet splash
	initrd	/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 5506723a-ab33-4aee-bc2a-50302cf276f9
	echo	'Loading Linux 2.6.35-28-generic-pae ...'
	linux	/vmlinuz-2.6.35-28-generic-pae root=UUID=643cd2f7-3d35-468b-9a3f-008f9f1fcced ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-28-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 5506723a-ab33-4aee-bc2a-50302cf276f9
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 5506723a-ab33-4aee-bc2a-50302cf276f9
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 1ae66b98e66b7345
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

=================== sda5: Location of files loaded by Grub: ===================


 314.7GB: grub/core.img
 314.7GB: grub/grub.cfg
 314.6GB: initrd.img-2.6.35-28-generic-pae
 314.6GB: vmlinuz-2.6.35-28-generic-pae

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=643cd2f7-3d35-468b-9a3f-008f9f1fcced /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda5 during installation
UUID=5506723a-ab33-4aee-bc2a-50302cf276f9 /boot           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=74fc4a8d-c724-43a2-a40a-d775887aae9e none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 316.1GB: initrd.img
 316.1GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  08 1b 82 83 ad 97 08 52  e6 a6 fd 2d 35 cf f3 c1  |.......R...-5...|
00000010  3b 8f eb d7 7e 95 ef 08  ee a1 54 dd dd c5 cf d2  |;...~.....T.....|
00000020  c3 55 09 f2 67 d0 df 3d  ad 1e 0d 87 ce 69 2d b0  |.U..g..=.....i-.|
00000030  a9 12 67 2f 9f aa ac f6  ba a7 d4 9e be d6 f6 21  |..g/...........!|
00000040  08 5a df 3f 54 f6 02 55  50 f8 13 88 73 ad d1 14  |.Z.?T..UP...s...|
00000050  c2 80 fd 25 c7 43 5c c0  41 5e b4 02 90 dc d2 b9  |...%.C\.A^......|
00000060  36 84 b6 d7 ab 7d 09 f4  84 c9 9c 60 7c aa 01 ca  |6....}.....`|...|
00000070  5b e4 43 4a f9 32 97 cf  61 aa 7e 45 5a aa b5 e1  |[.CJ.2..a.~EZ...|
00000080  43 55 49 fa a7 cf ab 52  a6 f6 94 37 cf ab 57 dd  |CUI....R...7..W.|
00000090  2e 05 6f de eb 7d 6d 5a  9c b5 e3 d3 4a fa b4 35  |..o..}mZ....J..5|
000000a0  5c 1f 52 6b 0a 78 c8 54  d5 4d 85 11 53 e5 d0 ab  |\.Rk.x.T.M..S...|
000000b0  be 7d 4d 33 a9 cf d2 d6  85 4a ba a5 50 b9 93 df  |.}M3.....J..P...|
000000c0  2d e7 74 e9 d3 a7 4e 9d  20 1c d9 02 1c 00 e5 e1  |-.t...N. .......|
000000d0  f4 a8 06 89 9a e9 18 03  63 2c 47 0e ef d0 98 bd  |........c,G.....|
000000e0  bc 49 b4 11 bb aa 1c 47  11 b3 ce 95 2a 24 86 9e  |.I.....G....*$..|
000000f0  4d 24 0f 6b 25 46 6b 6e  16 c6 cc 00 b3 e4 5f 1f  |M$.k%Fkn......_.|
00000100  a1 97 c3 f8 c0 c6 8f b8  08 63 7f 7e 60 e7 49 db  |.........c.~`.I.|
00000110  71 24 89 ba bd b8 46 53  9a 38 6b 20 5c d2 c5 b6  |q$....FS.8k \...|
00000120  c6 44 4c 7d dc 58 ef 5f  8b 14 14 63 3a f5 c8 e4  |.DL}.X._...c:...|
00000130  46 44 e3 4d 49 bb 36 96  26 e6 66 de 72 d4 53 be  |FD.MI.6.&.f.r.S.|
00000140  bb 4a 4a 22 53 ef 2f 88  40 b8 fd a7 4f 75 7b aa  |.JJ"S./.@...Ou{.|
00000150  cd 8c 61 e8 ee ba 32 74  5a 15 b3 11 62 16 5c 1a  |..a...2tZ...b.\.|
00000160  8a 36 da f6 1b 4b 34 b5  f3 eb 41 f0 5f 35 88 07  |.6...K4...A._5..|
00000170  44 72 6f 20 ca 7d 6d ef  0c 41 61 07 b8 cf 48 d6  |Dro .}m..Aa...H.|
00000180  39 c8 49 68 0b 6f 22 0f  06 23 83 32 a7 33 53 7b  |9.Ih.o"..#.2.3S{|
00000190  2a d3 5c 48 59 d8 64 91  e1 13 30 70 cc 13 23 c5  |*.\HY.d...0p..#.|
000001a0  fd ea dc c4 1a cc af 43  4a 57 0e a2 a3 67 69 64  |.......CJW...gid|
000001b0  41 93 6a f9 c3 71 45 89  24 63 7a 49 d5 72 a3 26  |A.j..qE.$czI.r.&|
000001c0  0f 80 10 03 a5 b8 c1 3a  5b 4f d5 be 7d 06 1d 6a  |.......:[O..}..j|
000001d0  ea de 57 b0 99 f2 a7 e4  5c d7 69 ad 53 e7 69 5f  |..W.....\.i.S.i_|
000001e0  2b 73 60 3f 15 4f 61 2a  55 06 3d 25 ea 5f a6 79  |+s`?.Oa*U.=%._.y|
000001f0  c5 2e 0b ef 3f 7e 72 48  1f 60 e6 ed f2 4c 1f 9d  |....?~rH.`...L..|
00000200

---

### Post by Quackers on 2011-04-04
Oh dear!
sda1 and sda3 are unmountable. This is probably because they have a SFS file system. This means that at some time Windows has changed its partitions from primary to dynamic disks. This is often caused by attempting to create a 5th primary partition on a drive, which is "illegal" on a mbr partitioned disc - could this have happened? Ii is likely that there are other possible causes though.

This is very bad news for any operating system other than Windows (which may be the reason Windows does it!).
I know of no surefire way to go back to simple partitions and the only remedy I have seen is to re-install everything. See what others think first, though.

If you re-install Windows first, check to see how many primary partitions it has used - before installing any other operating system.

---

### Post by jvacek996 on 2011-04-04
I had the absolutely same problem just yesterrday. I have a thread on it. Ill post it within seconds

---

### Post by fadimoh on 2011-04-04
i tried to re-install windows 7 again but i cant see the drives and
is there a possibility to remove the kubunta and get windows back or to view the windows drives on kubunta?

---

### Post by jvacek996 on 2011-04-04
[http://ubuntuforums.org/showthread.php?t=1720377](http://ubuntuforums.org/showthread.php?t=1720377)

i guess youll have to make your way through the ********. maybe read the whole thing before doing anything, as it could save your computer

---

### Post by oldfred on 2011-04-04
If you attempt any of this be sure to have good backups. Windows' official policy is to backup, erase everything, repartition and restore from backups. Windows did tell you it was converting to dynamic partitions when you tried to make the new one.

[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You can use a third-party tool, such as Partition Wizard 4.2. to convert a convert a dynamic disk to a basic disk without having to delete or format them.
The Partition Wizard software for Windows is supposed to be able to convert dynamic disks to regular partitions without data loss, so it may be what you need to get around this problem; however, I've never used it and so I can't be sure it will work.

Since your three SFS partitions are all in order, it may be easier to convert back.

If not rebooted recover partition:
[http://ubuntuforums.org/showpost.php?p=10364557&postcount=34](http://ubuntuforums.org/showpost.php?p=10364557&postcount=34)
Used testdisk but see caveats in Post#7:
[http://ubuntuforums.org/showthread.php?t=1669418](http://ubuntuforums.org/showthread.php?t=1669418)
Used EASEUS Partition Master
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
Also used testdisk
[http://ubuntuforums.org/showthread.php?t=1675420](http://ubuntuforums.org/showthread.php?t=1675420)
Not sure if in "free" version, but older version had it & was free see 4.2:
[http://www.partitionwizard.com/help/convert-dynamic-disk-to-basic-disk.html](http://www.partitionwizard.com/help/convert-dynamic-disk-to-basic-disk.html)
[http://www.hdd-tool.com/partition-manager/change-partition-type-logical-to-primary-without-data-losing.htm](http://www.hdd-tool.com/partition-manager/change-partition-type-logical-to-primary-without-data-losing.htm)

---

### Post by fadimoh on 2011-04-04
thanks jvacek996 for your help i hope i get something ti fix it as i dont want to loose the work on the HDD

---

### Post by jvacek996 on 2011-04-04
make sure to at least give it a try with the windows cd if you still have it. there is this BootRec.exe which would've saved me but it was too late when someone posted it.
[B]
EDIT[/B] here it is

> Since the cd is now recognizing windows try this, I have highlighted the  two commands to run and have included the rest if needed.

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter>  at the language selection prompt then hit <R> for Repair to get to  the Repair section. 
2) Select the command prompt (console) and type in the following commands:
**BootRec.exe /fixmbr** (#updates MBR master boot record...do not run if you still want grub)
**chkdsk /r**
**BootRec.exe /FixBoot** (#updates PBR partition boot)
[B]BootRec.exe /ScanOs
BootRec.exe /RebuildBcd[/B]
[http://www.sevenforums.com/tutorials...ot-record.html]("http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html")

I would be running a chkdsk /r at some point as well.

---

### Post by Quackers on 2011-04-04
You may indeed be able to save Windows, but it will still be a SFS system. This means that no other operating system will install.

---

