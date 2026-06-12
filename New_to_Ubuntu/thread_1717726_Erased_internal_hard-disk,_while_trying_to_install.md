---
title: "Erased internal hard-disk, while trying to install ubuntu to usb! Any help please."
date: 2011-03-30
forum: New to Ubuntu
---

### Post by santhust on 2011-03-30
Help needed desperately :(. Let me detail what I did:

1. tried to install ubuntu 10.10 on external usb 8GB; have done it earlier successfully a number of times. But this time I found my internal hard-disk is completely erased! I think I took care while doing so; but one thing different: once I stopped the installation process forcefully, after following all the steps of installation[because i used ext2 partition] to have ext4 partition.[i suspect this could be the cause of error, however not sure.] But the installation in the external usb occurred fine. I m using this now to access my machine and Internet. 

2. my hard disk showed completely free space. After doing a lot of search to recover data over Internet, i installed grub-rescue-remix on my external usb. Using testdisk utility therein I recovered some of the partition. i am able to mount and open the windows vista partition [but booting windows shows error and i am unable to boot]; however the ubuntu/linux partition although shown is not mounting and showing errors.

3. here are some of the outputs of the tests i carried and the text, png file i collected illustrate my machines present state:
```

The output of
$ sudo fdisk -l 
is:
Disk /dev/sda: 250 GB, 250056737280 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *           1       10239    82244736    7  HPFS/NTFS
/dev/sda2           10240       29578   155332485    f  Extended LBA
/dev/sda5           10240       29578   155332485   83  Linux
Warning: Partition 5 does not end on cylinder boundary.

Disk /dev/sdb: 8 GB, 8011422720 bytes
255 heads, 63 sectors/track, 974 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1   *           1         876     7036438   83  Linux
Warning: Partition 1 does not end on cylinder boundary.
/dev/sdb2             876         975      795217    5  Extended
Warning: Partition 2 does not end on cylinder boundary.
/dev/sdb5             876         975      795217   82  Linux swap
Warning: Partition 5 does not end on cylinder boundary.
-------------------------------------------------------------------

The output of 
$ sudo LANG=C sfdisk -d /dev/sda >sfdisk_sda.txt
the contents of sfdisk_sda.txt:
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=164489472, Id= 7, bootable
/dev/sda2 : start=164489535, size=310681035, Id= f
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start=164489598, size=310680972, Id=83
---------------------------------------------------------------------

The output of
$ sudo parted -l
is:
Model: ATA WDC WD2500BEVS-7 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  84.2GB  84.2GB  primary   ntfs         boot
 2      84.2GB  243GB   159GB   extended               lba
 5      84.2GB  243GB   159GB   logical   ext4


Model: Kingston DataTraveler G2 (scsi)
Disk /dev/sdb: 8015MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  7200MB  7198MB  primary   ext4            boot
 2      7201MB  8014MB  814MB   extended
 5      7201MB  8014MB  814MB   logical   linux-swap(v1)
--------------------------------------------------------------------

The run of testdisk:
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0   1  1 10238 254 63  164489472
 2 E extended LBA         10239   0  1 29577 254 63  310681035
 5 L Linux                10239   1  1 29577 254 63  310680972



*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
[Quick Search]  [ Backup ]
                            Try to locate partition
----------------------------------------------------------------------

[after selecting quick search the next window:]

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63
     Partition               Start        End    Size in sectors
* HPFS - NTFS              0   1  1 10238 254 63  164489472
L Linux                10239   1  1 29577 254 63  310680972



Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
NTFS, 84 GB / 78 GiB
----------------------------------------------------------------------
[after selecting the line having: L Linux ....]

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63

     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0   1  1 10238 254 63  164489472
 2 E extended LBA         10239   0  1 29577 254 63  310681035
 5 L Linux                10239   1  1 29577 254 63  310680972



[  Quit  ]  [Deeper Search]  [ Write  ]  [Extd Part]
                          Try to find more partitions
---------------------------------------------------------------------

[Selection Deeper Search option the next window is:]

sk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63
     Partition               Start        End    Size in sectors
D HPFS - NTFS              0   1  1 10238 254 63  164489472
D HPFS - NTFS              0   1  8 10238 254 63  164489465
D Linux                10239   1  1 29577 254 63  310680972
D HPFS - NTFS          27805   1  1 29576 254 63   28467117 [New Volume]
D Linux                28842   2  1 30066 254 63   19679499

Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
EXT4 Large file Sparse superblock, 159 GB / 148 GiB
-------------------------------------------------------------------

[but i am unable to write this partition table.]
-------------------------------------------------------

output of $ dmesg|tail
[   26.242574] Skipping EDID probe due to cached edid
[   26.770057] Skipping EDID probe due to cached edid
[   36.256495] EXT4-fs (sdb1): re-mounted. Opts: errors=remount-ro,commit=0
[   44.340109] Skipping EDID probe due to cached edid
[   44.872578] Skipping EDID probe due to cached edid
[   45.402736] Skipping EDID probe due to cached edid
[   45.930257] Skipping EDID probe due to cached edid
[   48.262597] Skipping EDID probe due to cached edid
[   52.232603] Skipping EDID probe due to cached edid
[  577.138493] EXT4-fs (sda5): no journal found



```

4. some screen shots are attached.

5. I have done some recovery of some pdfs ,txt, doc files. however since their file names doesn't describe their contents and there sheer number in thousands, it is intimidating to open each file and see if this the file i actually want. 

please, any help,:oops:[-o<:cry: to be able to see/mount my 159GB linux partition [other than windows], so that i can pick up my data there locked there. It would be excellent if by some way my machine could be restored to previous state: dual boot with Ubuntu and Windows Vista.

[please note: the 8GB ext usb shown is the one i am using now to run my machine, internet, and posting this thread.]

---

### Post by Hedgehog1 on 2011-03-31
santhust,

You have not actually erase your hard disk.  The Ubuntu partition is damaged, and your Vista should be fine.

This situation is most likely recoverable. :P

I need to ask you to boot from your USB stick and do this:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Some of the info you have already posted is duplicated in the script output, but there is also some additional data that we need to help; the script captures that.

***The Hedge***

:KS

p.s. I will add a post to show you how to boot into vista again while we help you fix your Ubuntu partition.

---

### Post by Hedgehog1 on 2011-03-31
To get your PC to boot directly into Windows again:

You will need your windows 7 / Vista  emergency repair disk.

If you don't have one, you can download the ISO for   [VISTA]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") or [WINDOWS7]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/") recovery disks.

Boot from the windows 7 / Vista  emergency repair disk, do the following:
[IMG]http://img10.imageshack.us/img10/5826/small51runningrecoveryd.png[/IMG]
[IMG]http://img856.imageshack.us/img856/3690/small52selectingwindows.png[/IMG]
[IMG]http://img826.imageshack.us/img826/3484/small53commandprompt.png[/IMG]
[IMG]http://img215.imageshack.us/img215/9547/small54bootrec.png[/IMG]

You will now be able to boot directly into Vista again.

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-03-31
Burying you with info - sorry -

Once you have posted your script results and have your PC booting vista, the next step is to try to rescue the Ubuntu partition as-is.

To do this, the first step to boot from your Ubuntu USB, and then run this command:

```
sudo fsck -fC /dev/sda5
```

After this command, **_If we all luck-out you can mount and you can use the partition OK from the USB_**, these two commands will get you dual-booting again:

```
sudo mount /dev/sda5 /mnt
```

```
sudo grub-install --root-directory=/mnt /dev/sd**a**
```

If the partition is not yet accessible (or you get an error message from fsck), we will begin phase 2.

***The Hedge***

:KS

---

### Post by santhust on 2011-04-01
_Thanks Hedgehog1_. I had almost lost hopes of any reply. But this morning I received a notification of your reply over my mail :).

Before receiving your reply, I had already tried some things. I shall detail them, in the temporal order, I followed:

1. I ran the command: **$ sudo e2fsck -f -y -v /dev/sda5**. Its output is[there many lines of output(similar to first line "Free inodes...") . I captured the last few lines. It may be informative.]:
```
..........................
..........................
Free inodes count wrong (9307598, counted=9687230).
Fix? yes


/dev/sda5: ***** FILE SYSTEM WAS MODIFIED *****

   28482 inodes used (0.29%)
     257 non-contiguous files (0.9%)
      18 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 15862/15869/15867
         Extent depth histogram: 24653/4
 1070354 blocks used (2.76%)
       0 bad blocks
       2 large files

   23465 regular files
     698 directories
     623 character device files
     617 block device files
     648 fifos
4294965901 links
    2341 symbolic links (1837 fast symbolic links)
     579 sockets
--------
4294966599 files

```

1.a. I am able to mount my 159GB ubuntu partition now. :)
1.b. The command generated a directory **lost+found** in my 159GB partition[partition for ubuntu/linux]. But I couldn't follow this directory, and the other directories present inside this. [Their names were not informative.]
1.c. **I don't know if by running the above mentioned command if I have done some wrong to my partition[some overwriting etc?]**

2. To boot into my Vista, I had followed similar steps as outlined by you. And now I am able to boot into Windows Vista :).

3. I have checked man pages for command **fsck** and **e2fsck**; and understood that e2fsck is used to check the ext2/ext3/ext4 family of file systems, while fsck  is  used  to check and optionally repair one or more Linux file systems.

4. Question: I am able to mount the 159GB partition. Should I use
```
sudo fsck -fC /dev/sda5
``` **and** follow other command as advised by you? **Or** straight away go using the mounting of partition and restoring the grub[as you have advised; **since I had already issued e2fsck**]?

5. I am attaching the output of **boot_info_script_055.sh**, as asked by you:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________
GNU Fdisk 1.2.4
Copyright (C) 1998 - 2006 Free Software Foundation, Inc.
This program is free software, covered by the GNU General Public License.

This program is distributed in the hope that it will be useful,

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   164,489,534   164,489,472   7 HPFS/NTFS
/dev/sda2         164,489,535   475,170,569   310,681,035   f W95 Ext d (LBA)
/dev/sda5         164,489,598   475,170,569   310,680,972  83 Linux


Drive: sdb ___________________ _____________________________________________________
GNU Fdisk 1.2.4
Copyright (C) 1998 - 2006 Free Software Foundation, Inc.
This program is free software, covered by the GNU General Public License.

This program is distributed in the hope that it will be useful,

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048    14,061,567    14,059,520  83 Linux
/dev/sdb2          14,063,614    15,652,863     1,589,250   5 Extended
/dev/sdb5          14,063,616    15,652,863     1,589,248  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        D4A81E30A81E119A                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        9f74b502-7c7d-477a-9997-ed1b82d4a043   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        4c39f71b-e27b-4509-86de-0ac6aef95e27   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        6040cb74-5288-4944-ad7a-0b7aabeb01bb   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 4c39f71b-e27b-4509-86de-0ac6aef95e27
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 4c39f71b-e27b-4509-86de-0ac6aef95e27
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
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 4c39f71b-e27b-4509-86de-0ac6aef95e27
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=4c39f71b-e27b-4509-86de-0ac6aef95e27 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 4c39f71b-e27b-4509-86de-0ac6aef95e27
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=4c39f71b-e27b-4509-86de-0ac6aef95e27 ro single 
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
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 4c39f71b-e27b-4509-86de-0ac6aef95e27
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 4c39f71b-e27b-4509-86de-0ac6aef95e27
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set d4a81e30a81e119a
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdc1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=6040cb74-5288-4944-ad7a-0b7aabeb01bb none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


   2.7GB: boot/grub/core.img
   5.2GB: boot/grub/grub.cfg
   5.3GB: boot/initrd.img-2.6.35-22-generic
   2.7GB: boot/vmlinuz-2.6.35-22-generic
   5.3GB: initrd.img
   2.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  7d 20 ea b9 da 7e 17 42  dc 4a 36 1c fa db e1 df  |} ...~.B.J6.....|
00000010  44 fe 24 67 49 b2 a2 a4  ae 01 49 bd 2a 15 ef e2  |D.$gI.....I.*...|
00000020  d2 c3 41 72 90 dc 40 ef  2c 47 27 be 4e 6c b1 3f  |..Ar..@.,G'.Nl.?|
00000030  1a fd 22 d3 7a fd e9 fb  85 74 16 3d a3 ad 9b c0  |..".z....t.=....|
00000040  f4 24 81 f5 ca ee a4 dc  55 64 3f 2d 3f 97 6a 2b  |.$......Ud?-?.j+|
00000050  64 cc 8b c2 6a e3 c8 83  c2 33 48 2b 67 3a db cc  |d...j....3H+g:..|
00000060  83 a2 20 7a 50 89 1a 53  be 64 c9 9b 8a b9 ae a4  |.. zP..S.d......|
00000070  00 52 29 7f 54 71 58 4f  2d 3f d2 cc 8b 12 8a 3f  |.R).TqXO-?.....?|
00000080  60 d2 65 2d b6 d9 56 c6  4c c9 67 9e a9 7f 56 41  |`.e-..V.L.g...VA|
00000090  81 21 f5 40 92 9e b7 41  2f a5 a0 9b ba ac 88 4e  |.!.@...A/......N|
000000a0  8a 75 54 54 8a 8b 5e a2  a4 93 32 8f 89 56 42 41  |.uTT..^...2..VBA|
000000b0  37 5d 58 a6 93 9a 74 54  ec f1 40 2f 35 d1 41 c1  |7]X...tT..@/5.A.|
000000c0  b1 1a f1 b6 45 2f a5 1f  13 bd 64 a1 93 5a d3 94  |....E/....d..Z..|
000000d0  60 a1 ad d3 40 2d fe ff  50 ec ea ea 5a e0 a8 a2  |`...@-..P...Z...|
000000e0  e4 e5 26 f8 26 b8 34 27  36 d1 c3 62 74 0b 31 ab  |..&.&.4'6..bt.1.|
000000f0  39 0c 16 41 2c 8d a0 fb  4f 4c f3 51 dc 09 85 4a  |9..A,...OL.Q...J|
00000100  00 51 fd 36 50 14 11 0c  5d 69 47 0e 09 11 83 c1  |.Q.6P...]iG.....|
00000110  90 5a 85 18 00 db 6d 2a  05 ad b8 c9 da 54 be d0  |.Z....m*.....T..|
00000120  a7 2a 58 28 60 74 b3 34  f2 d9 5a 8e ac 58 b8 ce  |.*X(`t.4..Z..X..|
00000130  fd cc fd 64 67 ca 86 40  f9 6e 86 4f df dc c8 cd  |...dg..@.n.O....|
00000140  f9 30 4b be e6 39 9f fb  ec 87 43 98 ce c9 2f e5  |.0K..9....C.../.|
00000150  e4 bf 5c 7e 93 94 3f 27  0b e6 e6 9f 20 bb 31 01  |..\~..?'.... .1.|
00000160  aa ea 66 e6 40 d8 8f 45  25 e6 40 fc 34 27 df b4  |..f.@..E%.@.4'..|
00000170  6c 98 97 92 f6 c9 49 4f  71 d1 5a 5a 15 86 90 a5  |l.....IOq.ZZ....|
00000180  eb fa 72 d1 4e 8e 97 92  9e 3c 56 38 21 a5 16 46  |..r.N....<V8!..F|
00000190  e4 48 93 91 bc 2b a3 1e  a1 d0 36 21 ea 9b 13 5b  |.H...+....6!...[|
000001a0  52 63 57 72 9b b1 25 c1  9b 13 7b e6 c6 a6 d4 da  |RcWr..%...{.....|
000001b0  8c b8 c3 b4 66 f8 8a 65  07 ad 1d 0a b3 25 00 6b  |....f..e.....%.k|
000001c0  c1 6b 82 58 ca ce 02 00  00 00 00 40 18 00 00 00  |.k.X.......@....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

[FONT="Courier New"][B]
Thanks again. I eagerly wait for your relpy :).[/B][/FONT]

---

### Post by picman1 on 2011-04-01
I'd like to offer one small but significant bit of advice...

Consider either a RAID setup which automatically backs up your entire system
or perhaps Time Machine if you have your different operating systems set up on a Mac as I do.

I have never understood how anyone could rely on a computer as much as most of us do and yet not have some kind of backup in place for this or any other tragic loss of data. 

Good Luck

](*,)

---

### Post by santhust on 2011-04-01
> **picman1 said:**
> I'd like to offer one small but significant bit of advice...

Consider either a RAID setup which automatically backs up your entire system
or perhaps Time Machine if you have your different operating systems set up on a Mac as I do.

I have never understood how anyone could rely on a computer as much as most of us do and yet not have some kind of backup in place for this or any other tragic loss of data. 

Good Luck

](*,)
Thanks picman1.
I would have to first learn about Raid. Let me wait[try] for Hedgehog1's reply.

---

### Post by Hedgehog1 on 2011-04-01
> **santhust said:**
> _Thanks Hedgehog1_. I had almost lost hopes of any reply. But this morning I received a notification of your reply over my mail :).

4. Question: I am able to mount the 159GB partition. Should I use
```
sudo fsck -fC /dev/sda5
``` **and** follow other command as advised by you? **Or** straight away go using the mounting of partition and restoring the grub[as you have advised; **since I had already issued e2fsck**]?

...
Thanks again. I eagerly wait for your relpy :).

Based on your very successful recovery efforts so far (**WELL DONE, by the way!**) I think you can install grub and get rolling again.

Anticipate some damage to your Ubuntu install - but all in all you should be OK.

About **picman1**'s post on RAID or time machine - his point is a good one.  I never have only 1 copy of any file that matters.  I use an external drive and make a copy of active things, and keep a Data DVD folder (now with 24 gig Data BluRays!) as a backup.

The method you choose is not as important as backing up files.

If you have more issues, please post here.  Sorry about the slow response, we had an 'off' night.

***The Hedge***

:KS

---

### Post by santhust on 2011-04-01
No success **Hedgehog1** :(
I tried to reinstall grub but couldn't. when I restart my machine, I am left at the grub prompt 
[FONT="Courier New"]Minimum bash like editing...
grub >[/FONT]

I have followed your instructions. The output of```
sudo fsck -fC  /dev/sda5
``` is
```
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure                                           
Pass 3: Checking directory connectivity                                        
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda5: 28678/9715712 files (0.9% non-contiguous), 1070762/38835121 blocks 
```
The output of ```
sudo grub-install --root-directory=/mnt /dev/sda
Installation finished. No error reported.
```
Attached is a pdf file which I have used earlier to reinstall grub when I had lost in on one of previous occasion. The steps listed there,[i have changed sda1 to sda5 therein] from
```
$ sudo mount --bind /dev /mnt/dev
output: mount: mount point /mnt/dev does not exist
```
```
$ sudo mount --bind /proc /mnt/proc 
output: mount: mount point /mnt/proc does not exist

```
....and so on...
```
sudo chroot /mnt
chroot: failed to run command `/bin/bash': No such file or directory

```

I suppose that, although the partition is being able to be mount but the files/folders inside are not recognised! :(  Since I have seen that on opening and viewing the contents of this folder, I see only** "lost+found" folder and nothing else**.

**If we can't restore the system, I would even be happy with if I could see my file on the partition, and thus recover them :(**

[COLOR="Blue"]**_Or can we start phase two (you mentioned) ?_**[/COLOR

now Windows vista would be needed to be repaired again :(

---

### Post by Hedgehog1 on 2011-04-01
Phase 2 isn't so pretty.

Please use the link below to get the .iso to make a SystemRescueCd : **[SystemRescueCd]("http://www.sysresccd.org/Main_Page")**

The tool you are looking for is called "TestDisk" on the CD.  Here is the wiki about it's operation: **[TestDisk]("http://www.cgsecurity.org/wiki/TestDisk")**

TestDisk is your best option for trying to recover your lost files.

I was hoping things were not this bad on the partition.

***The Hedge***

:KS

---

### Post by santhust on 2011-04-01
> **Hedgehog1 said:**
> Phase 2 isn't so pretty.

Please use the link below to get the .iso to make a SystemRescueCd : **[SystemRescueCd]("http://www.sysresccd.org/Main_Page")**

The tool you are looking for is called "TestDisk" on the CD.  Here is the wiki about it's operation: **[TestDisk]("http://www.cgsecurity.org/wiki/TestDisk")**

TestDisk is your best option for trying to recover your lost files.

I was hoping things were not this bad on the partition.

***The Hedge***

:KS
ok thanks. :(

---

### Post by santhust on 2011-04-01
Hedgehog1, I am making an image of my sda5. I am thinking of reinstalling Ubuntu side by side Windows Vista. I hope [since now I am unable to boot even into windows] this will also give me a dual boot of Vista and Ubuntu. I feel tired :( with this rescue business.
**Remark**: Why can't we have a graphical "rescuer" for Linux. testdisk works good at recovery, but the file names or folder name it gives makes and their sheer number[sometimes in thousands/hundred thousands] makes it literally impossible to "select the needle from chaff". [it recovers for you, but then how does one recover ones documents/files from this recovery? :(] I don't know if there's some better rescuer for Linux which is also free.
I will have to stitch my data from here and there with some loss :(. it seems easier than going through each document/file which testdisk gives me[it is just impossible if data is recovered from hard-disk; might be feasible in case of recovery from small sized flash drives].

---

### Post by oldfred on 2011-04-01
Once the file structure is damaged the link from a file name to the data on the drive is lost. The data on the drive does not have a name with some exceptions. Photos & music have the name also stored internally.

I lost a folder or two and used photorec to recover my files. While I wanted it just to recover a folder, it recovered the entire drive. But I sorted the files into file type and recovered some data. Lots of grepping & little scripts to move things around and rename the ones that could be auto renamed.

[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
How to recover lost files after you accidentally wipe your hard drive
[http://www.linux.com/archive/feed/56588](http://www.linux.com/archive/feed/56588)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

---

### Post by Hedgehog1 on 2011-04-01
> **santhust said:**
> Hedgehog1, I am making an image of my sda5. I am thinking of reinstalling Ubuntu side by side Windows Vista. I hope [since now I am unable to boot even into windows] this will also give me a dual boot of Vista and Ubuntu. I feel tired :( with this rescue business.
**Remark**: Why can't we have a graphical "rescuer" for Linux. testdisk works good at recovery, but the file names or folder name it gives makes and their sheer number[sometimes in thousands/hundred thousands] makes it literally impossible to "select the needle from chaff". [it recovers for you, but then how does one recover ones documents/files from this recovery? :(] I don't know if there's some better rescuer for Linux which is also free.
I will have to stitch my data from here and there with some loss :(. it seems easier than going through each document/file which testdisk gives me[it is just impossible if data is recovered from hard-disk; might be feasible in case of recovery from small sized flash drives].

I had forgotten about photorec; that is another option for you (Thanks oldfred!).

Recovery is a painful process; there are no two ways about it.  A graphical tool requires resources that may not be available at recovery time; however for MAC users the 'timemachine' system offers just such a tool.  It is an elegant solution.

The real long-term key is backing up data.  Even if you had a RAID array, you would still have hammered your data because your did an 'un-advisable' shutdown when you created the USB incorrectly.  Only real backups would have saved you.

Sorry for the pain.  It is usually things like this that gets us to start backing up data in one form or another.  I just make sure key data is always on at least 2 different media/devices.  That has work for 25 years and many dead drives (and a few human errors).

***The Hedge***

:KS

---

### Post by santhust on 2011-04-01
> **oldfred said:**
> Once the file structure is damaged the link from a file name to the data on the drive is lost. The data on the drive does not have a name with some exceptions. Photos & music have the name also stored internally.

I lost a folder or two and used photorec to recover my files. While I wanted it just to recover a folder, it recovered the entire drive. But I sorted the files into file type and recovered some data. Lots of grepping & little scripts to move things around and rename the ones that could be auto renamed.

[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
How to recover lost files after you accidentally wipe your hard drive
[http://www.linux.com/archive/feed/56588](http://www.linux.com/archive/feed/56588)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

thanks. i have tried it and tired also :(

---

### Post by santhust on 2011-04-01
> **Hedgehog1 said:**
> I had forgotten about photorec; that is another option for you (Thanks oldfred!).

Recovery is a painful process; there are no two ways about it.  A graphical tool requires resources that may not be available at recovery time; however for MAC users the 'timemachine' system offers just such a tool.  It is an elegant solution.

The real long-term key is backing up data.  Even if you had a RAID array, you would still have hammered your data because your did an 'un-advisable' shutdown when you created the USB incorrectly.  Only real backups would have saved you.

Sorry for the pain.  It is usually things like this that gets us to start backing up data in one form or another.  I just make sure key data is always on at least 2 different media/devices.  That has work for 25 years and many dead drives (and a few human errors).

***The Hedge***

:KS
thanks Hedgehog1, for your replies and support :)

---

