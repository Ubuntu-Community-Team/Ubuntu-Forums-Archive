---
title: "Error: out of disk grub rescue&gt;"
date: 2011-03-05
forum: New to Ubuntu
---

### Post by rockwell56 on 2011-03-05
Hello everyone I have a little experience with Ubuntu 9.04 from a few years ago.  I just installed Ubuntu 10.10 on an old desktop box that has WinXP already installed.  The installation went smoothly however when the machine rebooted I received the following error.  Error: out of disk grub rescue>  The cursor blinks however I'm unable to type anything.  Is this a problem with grub?  I have searched quite a bit however am unable to figure this out.  I was able to get a results.txt which I have attached.  Thanks in advance Rockwell56

---

### Post by wep940 on 2011-03-05
I see the disk is 160GB. I ran into this exact problem on a Compaq Presario 25xx series laptop. I installed a 160GB drive to replace the older smaller one, because I wanted plenty of room for Windows, plus I wanted plenty of room for dual booting Ubuntu. After some tiring research on the web, I found out that this error can occur when your computer cannot physically address more than 137GB of disk space. This is the case if your drive is IDE. After finding this out, I check in the BIOS setup screens, and indeed the drive showed as 160GB with the warning that only 137GB was useable. This is a physical limitation on the IDE interface in your PC. The only way I found to fix it was to re-do the partitioning on the disk using gparted to create a "dummy" partition at the end of the disk with a size of 25GB (I wanted to be under the 137GB limit by a little). I can't ever put anything in this partition - it is wasted space. Everything else was allocated starting at the beginning of the disk so it stayed under the 137GB limit.
 
If the PC is an old PC I'm sure this is probably your problem. The easiest way to check is to go to the BIOS setup screens and check the disk - if it says the size is 160GB but then says only 137GB is usable, then this is your problem. It's possible your BIOS may not say what is usable, in which case I would allocate the dummy partition at the end of the disk, create the "usable" partitions at the beginning of the disk and then see if it works.

---

### Post by fabricator4 on 2011-03-05
> **wep940 said:**
>  gparted to create a "dummy" partition at the end of the disk with a size of 25GB (I wanted to be under the 137GB limit by a little). I can't ever put anything in this partition - it is wasted space. Everything else was allocated starting at the beginning of the disk so it stayed under the 137GB limit.


A better way is to make a 30 Gb boot partion at the beginning for Ubuntu, then partition the rest to be mounted as /home.  30Gb is generally plenty for a desktop install, and you have heaps of space for data and settings on /home.  An added benefit is that you can upgrade or re-install at any time without worrying about your data because it is on a separate partition.

You should of course still make proper backups of your data however...

Chris.

---

### Post by wilee-nilee on 2011-03-05
Here is the script.
```
     Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   156,280,351   156,280,289   7 HPFS/NTFS
/dev/sda2         156,280,830   312,580,095   156,299,266   5 Extended
/dev/sda5         156,280,832   306,124,799   149,843,968  83 Linux
/dev/sda6         306,126,848   312,580,095     6,453,248  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        7864A4D764A49980                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        daca5775-6f6c-4bee-bb60-c0b66cbc2cb4   ext4                                     
/dev/sda6        9528fe95-69eb-44b3-a788-8a7d94bbb721   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/7864A4D764A49980  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /media/daca5775-6f6c-4bee-bb60-c0b66cbc2cb4 ext4       (rw,nosuid,nodev,uhelper=udisks)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set daca5775-6f6c-4bee-bb60-c0b66cbc2cb4
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set daca5775-6f6c-4bee-bb60-c0b66cbc2cb4
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
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set daca5775-6f6c-4bee-bb60-c0b66cbc2cb4
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=daca5775-6f6c-4bee-bb60-c0b66cbc2cb4 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set daca5775-6f6c-4bee-bb60-c0b66cbc2cb4
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=daca5775-6f6c-4bee-bb60-c0b66cbc2cb4 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set daca5775-6f6c-4bee-bb60-c0b66cbc2cb4
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set daca5775-6f6c-4bee-bb60-c0b66cbc2cb4
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 7864a4d764a49980
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
UUID=daca5775-6f6c-4bee-bb60-c0b66cbc2cb4 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=9528fe95-69eb-44b3-a788-8a7d94bbb721 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 140.2GB: boot/grub/core.img
 101.6GB: boot/grub/grub.cfg
 127.9GB: boot/initrd.img-2.6.35-22-generic
 140.2GB: boot/vmlinuz-2.6.35-22-generic
 127.9GB: initrd.img
 140.2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  c6 51 0e 44 4d e5 3b e1  e3 54 43 d3 b7 0e b6 7f  |.Q.DM.;..TC.....|
00000010  47 e3 6a 3b 42 9a 64 3a  d8 3c 9f 69 94 93 39 5f  |G.j;B.d:.<.i..9_|
00000020  b6 a6 f0 7b 2a fc 39 0b  7f ac c8 82 2a a1 38 f4  |...{*.9.....*.8.|
00000030  e5 5c c8 88 7e bf 01 2a  83 a2 60 93 1f a9 87 33  |.\..~..*..`....3|
00000040  c6 67 a8 18 32 63 d0 3e  01 19 30 ac 2d 80 0a a1  |.g..2c.>..0.-...|
00000050  20 03 21 07 a0 6a 7e bf  8a 3f c3 00 f9 c1 87 4c  | .!..j~..?.....L|
00000060  a8 02 8a 69 8e b1 0f f2  72 c5 b1 40 a5 50 44 0b  |...i....r..@.PD.|
00000070  42 4e 41 ee 2d 09 49 85  8a a0 10 37 9c a5 41 0a  |BNA.-.I....7..A.|
00000080  26 84 b9 50 01 14 d8 8a  90 3d 50 15 94 d0 1a e3  |&..P.....=P.....|
00000090  3b e4 db 86 90 0c a8 1c  8a 46 01 9c 83 3c db 12  |;........F...<..|
000000a0  92 06 95 40 61 28 87 93  90 6b 7b 42 52 a0 2b 50  |...@a(...k{BR.+P|
000000b0  b0 27 21 d9 9e 96 3f 74  91 0c e5 43 fe 1d e1 3f  |.'!...?t...C...?|
000000c0  54 09 c5 61 e0 ce 85 8c  5e f0 1f 2a 83 a2 ee 85  |T..a....^..*....|
000000d0  ff 90 47 27 f8 0f 15 43  e6 fb e0 3f 64 40 c1 2e  |..G'...C...?d@..|
000000e0  80 0a a1 20 6f f8 0f 55  43 89 3e f0 1f f2 eb 0c  |... o..UC.>.....|
000000f0  ff a1 0a 28 c6 17 fe 43  5e f7 c3 7f a8 14 8a e8  |...(...C^.......|
00000100  02 ff 21 f7 ae f0 1f 2a  82 42 d0 00 8f 40 4a 37  |..!....*.B...@J7|
00000110  f8 0f 15 40 81 dd e1 3f  54 05 25 f4 80 ff 90 af  |...@...?T.%.....|
00000120  3f fc 87 ca a1 e8 9e f0  1f f2 44 67 4d 83 4a a0  |?.........DgM.J.|
00000130  b0 07 e0 3f e4 8a c1 38  05 ba 02 05 e3 6c 32 bb  |...?...8.....l2.|
00000140  97 e5 0f 59 24 43 f9 90  7f 1f f8 0f 55 42 71 98  |...Y$C......UBq.|
00000150  4a 72 21 63 5f f8 0f 95  41 51 fd e0 3f e4 d1 1f  |Jr!c_...AQ..?...|
00000160  fe 43 c5 90 39 18 fe 43  86 01 f0 1f 2a 84 82 06  |.C..9..C....*...|
00000170  c2 7f a8 1a 4a 1c 04 ff  21 bf 10 f8 0f 55 40 31  |....J...!....U@1|
00000180  38 73 ba 08 79 85 5a be  59 97 ca 37 f9 4f 41 ee  |8s..y.Z.Y..7.OA.|
00000190  38 eb 4b 85 8a a0 90 21  f0 1f 52 30 c5 cd 85 0a  |8.K....!..R0....|
000001a0  a0 c0 61 f0 1f aa 82 12  d0 f1 f2 20 df 70 f8 0f  |..a........ .p..|
000001b0  95 43 d1 c3 e1 3f e4 39  02 fe 43 25 50 18 00 fe  |.C...?.9..C%P...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 70 ee 08 00 fe  |...........p....|
000001d0  ff ff 05 fe ff ff 02 70  ee 08 00 80 62 00 00 00  |.......p....b...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by wep940 on 2011-03-05
I just noticed you said you have Windows XP on the PC as well, so I am going to assume the following:
 
- you are dual-booting- Boot using the LiveCD
 
- Windows XP was installed first, so that it is the first partition on the disk (or second if there is a recovery partition)
 
- you shrank the size of your Windows partition in order to make room for Ubuntu
 
 
This is exactly what I did, and to get around the error I had to do the following.  Be aware that you stand the very real possibility of losing Windows as well if you don't understand and carefully follow what you are doing with the partitioning of your hard disk.  If you have *ANY* questions, please don't do anything and just post back here.
These steps are what I did, and I was fortunate enough not to lose anything from Windows - just lost my Ubuntu installation (which was new anyway).
 
- Boot using the Ubuntu LiveCD
 
- Open a terminal window and type "swapoff" so the existing swap space on the disk is free from usage.
 
- Start the disk manager or gparted
 
- Shrink the size of your Windows partition to allow about 25GB more free space.  It is very important to note 2 things here:
 
[LIST]
[*]normally you would NEVER shrink the Windows partition without running the Windows defrag of the disk a couple of times even if Windows says it doesn't need to be defragmented.  Loss of data could result.  It would be best to restore the Windows MBR so you can boot Windows and run the defrag first.
[*]when you boot Windows after shrinking the size of the partition, it will run a disk check the first time you boot.  It should find NO errors.
[/LIST]- delete the Ubuntu partitions you created (if they are AFTER the Windows partition - if not, don't do this step and post back)
 
- allocate a partition of 25GB and select the "at end of disk" option (can't remember the exact wording)
 
- Start the installation process again for Ubuntu, manually specifying the partitions and placing them in the free space between your Windows partition and the 25gb partition at the end of the disk.
 
In this way, my "normal" partitions where first on the disk, followed by my ubuntu partitions, followed lastly by the 25gb partition (a "dummy" partition as I can never put anything there due to addressing limits).

---

### Post by wep940 on 2011-03-05
> **fabricator4 said:**
> A better way is to make a 30 Gb boot partion at the beginning for Ubuntu, then partition the rest to be mounted as /home. 30Gb is generally plenty for a desktop install, and you have heaps of space for data and settings on /home. An added benefit is that you can upgrade or re-install at any time without worrying about your data because it is on a separate partition.
 
You should of course still make proper backups of your data however...
 
Chris.
 
Yes, a seperate partition for /home is great, but the most important thing here is that there *MUST* be a partition of 25GB or so at the *END* of the disk that will never get used.  If the OP's problem is the same as mine, it's a physical limit in the addressing of the hardware.  Without that "dummy" parition at the end of the disk, you will continue to get the error from grub.

---

### Post by wep940 on 2011-03-05
I should add the following for anyone who may be wondering:
 
- when I first replaced the small disk with the 160gb disk and installed Windows, Windows and it's boot loader never complained about the 137gb limit.  If I ever had started trying to read or write in that area (as I found out when I ran chkdsk but never realized what the error was) I would have gotten errors.

---

### Post by fabricator4 on 2011-03-05
> **wep940 said:**
> Yes, a seperate partition for /home is great, but the most important thing here is that there *MUST* be a partition of 25GB or so at the *END* of the disk that will never get used.  If the OP's problem is the same as mine, it's a physical limit in the addressing of the hardware.  Without that "dummy" parition at the end of the disk, you will continue to get the error from grub.

There may be limit on partition size, for the boot partition, but there is NO limit on disk size.  You don't have to throw away that 25Mb.  I'm on a 200 GB IDE drive right now, and I can use all of it.

To prove it to yourself, run Gparted and partition that unused space and format it.  You'll be able to mount it and write to it just fine.

Chris.

---

### Post by wep940 on 2011-03-05
> **fabricator4 said:**
> There may be limit on partition size, for the boot partition, but there is NO limit on disk size. You don't have to throw away that 25Mb. I'm on a 200 GB IDE drive right now, and I can use all of it.
 
To prove it to yourself, run Gparted and partition that unused space and format it. You'll be able to mount it and write to it just fine.
 
Chris.
 
I don't know how to tell you this, but you are wrong. Just look up the specs on a 16-bit IDE interface(not enhanced IDE or EIDE is it is referred to) - it physically, even with LBA mode enabled, cannot address more than 137GB. This is a hardware limit on the IDE interface. SATA is a completely different animal. If I had kept track of all the things I had to read through on the web to find this out, I would post them here.
 
I'm not trying to argue with anyone, nor start an arguement. Just stating a fact about the physical limitations of the 16-bit IDE interface. Some new MB's might have other version of IDE that gets around this - I don't know. I just know that for mine it is fact, no ifs, ands or buts as they say about it. Guaranteed.
 
If anyone has any questions about this, please PM me and I'll track down the related articles on the web. Right now I would be more interested in the user checking their BIOS to see if it states the "usable" as mine does. They might also need to check technical specification sheets for their motherboard.
 
And no - I can partition it, but I CANNOT write to it. Already proven on my PC. And I guarantee that at least for my laptop you cannot get grub to work with it either - it's just plain beyond the physical addressing limitations of the original IDE interface hardware.
 
EDIT: though not on of the pages I followed, there is a table in this article that explains this - IDE versus enhanced IDE:
 
[http://philipstorr.id.au/pcbook/book4/hdlimit.htm](http://philipstorr.id.au/pcbook/book4/hdlimit.htm)
 
and please note, I am *NOT* referring to limits imposed by DOS or earlier Windows SOFTWARE, but rather on the physical limits of older IDE interface HARDWARE.
 
EDIT-EDIT: I should probably also add in case anyone questions more, my 160gb is indeed EIDE, but my motherboards' IDE interface and BIOS implementation is not - it's just the old IDE with 2 to the 16th power limit on addressing.
 
And, as always, this is based on my understanding from the articles I read about disk size limit with the interface, not partition size.  In my experience with my laptop it's how things indeed works.  If anyone can point me to an article on the net that states that the physical limitation of standard IDE addressing is not 137GB (2 to the 16th power combination of heads/cylinders used in the calculations) I'd sure be interested in seeing it.  You see, I've also owned other PC with EIDE and they had no problem about 137GB - my laptop does.  And everything I read on the web points to my answer.

---

### Post by JKyleOKC on 2011-03-05
Actually, you're both right, just at different points in time. The original HD interfaces, back in the days of Win3.1, were limited to around 8 GB because of CHS addressing. That got replaced by LBA addressing, which initially had the 137 GB limit. Later, updated BIOSes worked around the 137-GB limit by going to 32-bit addressing. Just where the limit is for any specific box depends on the age of the box and its BIOS!

At one time certain Maxtor IDE drives had an additional pair of jumper pins along with the master/slave/cable-select ones, to disable or enable the excess capacity and make them compatible with the older BIOSes without having to create an unused dummy partition. The "OnTrack" disk manager was also popular in those days as another way to overcome the limits. Be glad you didn't have to live through those times!

---

### Post by wep940 on 2011-03-05
Thank you for stating so simply what my mind was trying to say and just couldn't - it's the hardware limits and the BIOS implementation of how to use the interface (16 versus 24 bits, etc., in the BIOS int functions) that result in the limit. Most older machines are going to be limited by that to the 137GB limit I ran into. EDIT-EDIT: Forgot to say - that move to 32-bit int17 handling is what EIDE is about, if I remember correctly. 32 bits obviously sets a really high addressing limit! ;)
 
Thanks again for the simple and to the point explanation.
 
EDIT: BTW - I finally found someone who also remembers the old days! I go back to poking bits on the box, and then paper tape, and then we actually got an OS - CP/M. I sure do remember all the old disk limits, and the various ways to "fool" the BIOS - On-Track being one of several. Nice to know I'm not the only person around to remember that. I'm not going to guess you're actually old enough to remember, just that you KNOW ;) I am, on the other hand, an old fart. ;) I should also add that I remember writing our own disk drivers - first for floppies where you had to calculate head stepping and head settling times, etc., and also into some of the first hard disk drivers for micros using some of the old WD chips.
 
Jeez - I see I did it again as well - it's the int 13h, 19 decimal, function.  I believe the new limit is 64 bit addressing, isn't it?

---

### Post by wep940 on 2011-03-05
I should probably point anyone who might be interested to a long read that explains some of this:
 
[http://www.storagereview.com/hard_disk_drive_reference_guide](http://www.storagereview.com/hard_disk_drive_reference_guide)

---

### Post by JKyleOKC on 2011-03-05
Now you really got me going with the mention of the old WD chips. I wrote a little package for the TRS-80 Model 4 called "Fast 4" that sped up the clock rate to take full advantage of the hardware, and found that disk access became intermittent. Since my day job was as a tech writer for Seagate I had access to topnotch engineers for help, and they told me about the chip's need for a several-microsecond delay between setting its registers and initiating access. I found a way to introduce the needed delay by changing some instructions in the driver, at machine-code level of course, and that was my first "commercially successful" software. I think I sold a couple of dozen copies for $7.95 each...

I might be a bit older than you; I started in computers in 1965, working first with G-E mainframes and later with Multics. My first modems were Bell 103s, 110 baud. Came into the micro world a bit late, with the TRS-80s about 1980, and avoided MS-DOS as long as I could after experimenting with ZDOS 1.25 (the first non-IBM DOS package sold by Tim Paterson to Zenith). In a couple of weeks I'll turn 80, but keeping up with Linux helps keep me young mentally...

---

### Post by wep940 on 2011-03-05
> **JKyleOKC said:**
> Now you really got me going with the mention of the old WD chips. I wrote a little package for the TRS-80 Model 4 called "Fast 4" that sped up the clock rate to take full advantage of the hardware, and found that disk access became intermittent. Since my day job was as a tech writer for Seagate I had access to topnotch engineers for help, and they told me about the chip's need for a several-microsecond delay between setting its registers and initiating access. I found a way to introduce the needed delay by changing some instructions in the driver, at machine-code level of course, and that was my first "commercially successful" software. I think I sold a couple of dozen copies for $7.95 each...
 
I might be a bit older than you; I started in computers in 1965, working first with G-E mainframes and later with Multics. My first modems were Bell 103s, 110 baud. Came into the micro world a bit late, with the TRS-80s about 1980, and avoided MS-DOS as long as I could after experimenting with ZDOS 1.25 (the first non-IBM DOS package sold by Tim Paterson to Zenith). In a couple of weeks I'll turn 80, but keeping up with Linux helps keep me young mentally...
 
GE -> sold to Honeywell ( I worked on some of the old 200 and 2000 series from Honeywell), then Honeywell Bull, then Bull H/N , now just Bull (and no longer in the US apparently). I never directly worked with Multics but had many friends who did. We started working on what they would later call a CASE tool back in the late '70's - I was working on the adaptations needed what was then GCOS64 (remember GECOS? - basically I think [it's been a long time since I thought about it] repackage under Honeywell), the old 7100 and 7700 series terminals, and eventually GCOS7 and some of the newer tubes. We never went anywhere with it and the project died quite quickly. I sure remember the old slow modems - I remember when I first started using a FAST 300 baud - thought we had the world in our hands! ;) I was thinking also - I think Digital Research (not DEC) had a CP/M DOS in the late 70's or early 80's as well as I remember having to re-do BIOS's (the software BIOS that CP/M had, not the hardware BIOS) for different versions of CP/M, etc.. While I'm old enough now and am on disability so I haven't worked since '96, i've also become more of a "user" now and haven't dug so much into technical things in a long time. I remember my first Linux installation back in the very early 90's (had used Coherent for a while before that at home, as well as some Unix at work on a symmetrical (sp?) multi-processor box. When I did my first install of Linux at home, there wasn't any of the GUI installation things like we have now, and my first thought was WOW - something new to dig into! But as I've gotten older I guess I've gotten lazy. I really should wake up that part of me that found all the technical stuff so fun in those days and start really learning about Linux. I'm not even that great of a Linux user - I just do what I need to, so it wouldn't hurt to learn the externals well before working towards the internals again.
 
Thanks for waking up some old memories!!
 
;)
 
I hope you don't mind me saying that I sure hope I'm as sharp as you are when I reach 80!!
 
EDIT: Just remembered - there's a gentleman who works at our local MicroCenter here in the twin cities that used to be an engineer at Seagate as well - I just wish I could remember his name right now! ;)

---

### Post by wep940 on 2011-03-06
Back to the original poster:  Please check your BIOS and see if it shows your disk as 160GB but only 137GB available.  Also, what is the make, model and age of the PC you are having the problem with?

---

### Post by rockwell56 on 2011-03-06
Ok I have reinstalled Grub2 but have no idea how to set it up.  I have 1  160gb hd split in half one half has WinXP the other Ubuntu 10.10.  

Partitions are as follows: 

/dev/sda1 ntfs (WinXP)
/dev/sda2 extended
/dev/sda5 ext4 (Ubuntu 10.10 I believe)
/dev/sda6 linux swap

I  have installed Ubuntu 10.10 from a live cd.  The PC's bios is set to  boot cd-rom 1st HD 2nd.  Would this be causing the problem?  When I  reboot my computer now I have the grub prompt.  I can now use the prompt  since I hooked up a ps2 keyboard, it wouldn't recognize the usb  keyboard. I'm not sure where to go from here,  Rockwell56

---

### Post by drs305 on 2011-03-06
It's time to rerun the boot info script and post a new RESULTS.txt so we can see how your system is now configured.

---

### Post by rockwell56 on 2011-03-06
Wow what a great response.  I thought that my Grub2 was to blame so I reinstalled grub.  I haven't tried changing partitions yet.  I think the bios is to blame and recall that in windows the drive appeared as 137gb.  Never thought about that when installing Ubuntu I split the drive in 2 partitions of 80gb.  Laptop battery died on me before I read your posts.  I'll proceed as recommended and let you know the results.  Thanks for the great advice  Rockwell56

---

### Post by drs305 on 2011-03-06
Even with two 80GB partitions, the Grub files may end up beyond the 137GB limit. It's something we look for when we study the RESULTS.txt. And even if all the boot files start within the first 137GB, they may move beyond it during updates, moving files, etc.

If you can, find out if there is a BIOS update for your system. Generally updating BIOS's should only be done when necessary, but this is a case where it would be warranted if your BIOS can only read the first 137GB.

---

### Post by rockwell56 on 2011-03-06
Ok did as you said wep940 resized my WinXP as low as Gparted would allow me which was 50,899 mb. (Reduced by 24.81 gb) Then deleted the Ubuntu partition an swap partition, which was installed after WinXP.  After rebooting my computer boots to the grub prompt.  Gonna try installing Ubuntu from the live cd again.  I have attatched my results text.

---

### Post by rockwell56 on 2011-03-06
Wep940 The machine is an old Gateway LP mini tower Sel K7-600 running bios version 0AASNP06.  I think I have updated this bios once before, not sure this computer was given to me after the hard drive failed and my friend didn't want to put any $ into it.  The pc had been sitting around for a while & I got bored an thought I'd install linux on it.  Never even thought of the bios & hard drive limits.  This machine runs WinXP decent even though with a virus scanner I have only 20 processes running.  I assumed that since it can run Xp that Ubuntu wouldn't be a problem although I didn't check the min requirements.  Has an AMD 600 with 768 mb of Ram.  I have partioned the HD as recommended and am in the process of installing Ubuntu as I type this.  Hoping this will setup Grub boot loader with WinXp as a boot option.  Will keep you posted
UPDATE: Problem solved wep940 thanks your solution worked WinXp is in the grub menu now.  Ubuntu is installed and I am currently running installing the 275 security updates.  Really appreciate the help, I'm wanting to learn Linux/Ubuntu if anyone has any recommended tips or forum stickys I should read up on I'd be very grateful. Thanks again

---

### Post by wep940 on 2011-03-06
It's a pretty obscure problem anymore, that's why it took me so long to find the answer for myself.  I think it is only going to happen on older PC's that only have a regular IDE interface and not an EIDE interface (again, BIOS int 13h).  I'm just glad it was able to help someone else.

---

