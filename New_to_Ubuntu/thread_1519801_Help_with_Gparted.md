---
title: "Help with Gparted"
date: 2010-06-28
forum: New to Ubuntu
---

### Post by amir1981 on 2010-06-28
Hi, I have  a dual  boot system (win XP and  ubuntu) 
I encountered a  problem  with  grub today. After fixing it using super grub  live cd I  can  see the  grub menu and   load into  linux or  win xp  but   now  I  could not  use Gparted.!!!  It  does not  recognize my HDD. (UNALLOCATED MESSAGE)   
here is  the result of fdsik -l

amir@amir-laptop:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        3921    31447237+   7  HPFS/NTFS
/dev/sda3            3922       14331    83618324+   f  W95 Ext'd (LBA)
/dev/sda5            3922        5479    12514572   83  Linux
/dev/sda6            5480        5543      514048+  82  Linux swap / Solaris
/dev/sda7            5544       14331    70589610    7  HPFS/NTFS
amir@amir-laptop:~$ 

What is wrong? what should I  do?

thanks

amir

---

### Post by rollin on 2010-06-28
Hi. Just a suggestion but are you running the gparted cd? As I have issues when things are accidentally mounted if I'm using it with Ubuntu etc. If this helps and you need a link for the iso, it's here: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php).
I just find booting from the gparted cd much easier as that way nothing gets mounted. Just my 2c. :smile:

---

### Post by amir1981 on 2010-06-28
Hi, 
thanks for the response but  I  have  no problem on  booting. Everything seems  fine, the  only problem seems to be  a kind  of problem  in  Partition table  or  something like that. I  think   while I  recovered "MBR" something  goes  wrong and  now  the  partition table need to get  fixed.  Do you  think  using Live  cd  can be  helpful?How?

---

### Post by rollin on 2010-06-28
Hi there. Bit of a mis-communication between us I think. I meant as you are having trouble with gparted. Try the live CD. This CD boots like the ubuntu live CD but with all the goodies gparted has.
If you boot the gparted live cd you can see everything as it is without loading your OS or anything. I think it would recognise the HDD. 

My theory is you are using gparted within ubuntu therefore the HDD must be mounted hence the error.

Try the gparted live cd [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php). and see if it recognises your HDD?

---

### Post by jtarin on 2010-06-28
First....what was wrong with Grub that needed attention? Second....what steps did you take with the super grub live cd ?

[Possibly your repair of Grub went slightly astray.]("http://gparted.sourceforge.net/docs/help-manual/C/gparted.html#gparted-fix-grub-boot-problem")

---

### Post by amir1981 on 2010-06-28
> **jtarin said:**
> First....what was wrong with Grub that needed attention? Second....what steps did you take with the super grub live cd ?

[Possibly your repair of Grub went slightly astray.]("http://gparted.sourceforge.net/docs/help-manual/C/gparted.html#gparted-fix-grub-boot-problem")
 I do as follow:
1- I  used  super grub to login into Linux
2-sudo dpkg-reconfigure grub-pc -pcritical

And then restart the computer and it works  but   I have this  new problem


I try to  use liveCD and  see what's happening

---

### Post by wilee-nilee on 2010-06-28
To really help we need to see the bootscript in my signature posted in code tags as described.

Also dell has a dell data safe program that overwrites the boot so we need to see if that is in the windows add remove.
[http://ubuntuforums.org/showpost.php?p=9330849&postcount=9](http://ubuntuforums.org/showpost.php?p=9330849&postcount=9)

You probably don't have this but post the bootscript first.

---

### Post by amir1981 on 2010-06-28
> **wilee-nilee said:**
> To really help we need to see the bootscript in my signature posted in code tags as described.

Also dell has a dell data safe program that overwrites the boot so we need to see if that is in the windows add remove.
[http://ubuntuforums.org/showpost.php?p=9330849&postcount=9](http://ubuntuforums.org/showpost.php?p=9330849&postcount=9)

You probably don't have this but post the bootscript first.
thanks  the  result  file is attached

---

### Post by wilee-nilee on 2010-06-28
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000080

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        96,389        96,327  de Dell Utility
/dev/sda2    *         96,390    62,990,864    62,894,475   7 HPFS/NTFS
/dev/sda3          62,990,866   230,227,514   167,236,649   f W95 Ext d (LBA)
/dev/sda5          62,990,991    88,020,134    25,029,144  83 Linux
/dev/sda6          88,020,198    89,048,294     1,028,097  82 Linux swap / Solaris
/dev/sda7          89,048,295   230,227,514   141,179,220   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07D7-0414                              vfat       DellUtility                   
/dev/sda2        E000CB3300CB0F88                       ntfs       OS                            
/dev/sda5        f7e9e1df-50e7-4cc0-a081-b094998159f7   ext4                                     
/dev/sda6        4e371e88-8678-4eca-9d3c-9d1f354652f1   swap                                     
/dev/sda7        04987A049879F510                       ntfs       Information                   

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


================================ sda2/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set f7e9e1df-50e7-4cc0-a081-b094998159f7
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-22-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set f7e9e1df-50e7-4cc0-a081-b094998159f7
	linux	/boot/vmlinuz-2.6.31-22-generic root=UUID=f7e9e1df-50e7-4cc0-a081-b094998159f7 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set f7e9e1df-50e7-4cc0-a081-b094998159f7
	linux	/boot/vmlinuz-2.6.31-22-generic root=UUID=f7e9e1df-50e7-4cc0-a081-b094998159f7 ro single 
	initrd	/boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set f7e9e1df-50e7-4cc0-a081-b094998159f7
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=f7e9e1df-50e7-4cc0-a081-b094998159f7 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set f7e9e1df-50e7-4cc0-a081-b094998159f7
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=f7e9e1df-50e7-4cc0-a081-b094998159f7 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda2)" {
	insmod ntfs
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set e000cb3300cb0f88
	drivemap -s (hd0) ${root}
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=f7e9e1df-50e7-4cc0-a081-b094998159f7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=4e371e88-8678-4eca-9d3c-9d1f354652f1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


=================== sda5: Location of files loaded by Grub: ===================


  32.6GB: boot/grub/core.img
  36.1GB: boot/grub/grub.cfg
  33.1GB: boot/initrd.img-2.6.31-14-generic
  41.6GB: boot/initrd.img-2.6.31-22-generic
  35.3GB: boot/vmlinuz-2.6.31-14-generic
  33.0GB: boot/vmlinuz-2.6.31-22-generic
  41.6GB: initrd.img
  33.1GB: initrd.img.old
  33.0GB: vmlinuz
  35.3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  eb 50 90 44 65 6c 6c 20  38 2e 31 00 02 04 01 00  |.P.Dell 8.1.....|
00000010  02 00 02 00 00 f8 5e 00  3f 00 ff 00 3f 00 00 00  |......^.?...?...|
00000020  47 78 01 00 80 00 29 14  04 d7 07 44 65 6c 6c 55  |Gx....)....DellU|
00000030  74 69 6c 69 74 79 46 41  54 31 36 20 20 20 10 00  |tilityFAT16   ..|
00000040  01 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000050  00 00 fa 33 c0 8e d0 bc  00 07 fb fc b9 80 00 8e  |...3............|
00000060  d8 be 00 7c b8 00 20 8e  c0 33 ff f3 66 a5 ea 73  |...|.. ..3..f..s|
00000070  00 00 20 0e 1f 66 0f b7  06 16 00 66 d1 e0 03 06  |.. ..f.....f....|
00000080  0e 00 66 03 06 1c 00 66  a3 46 00 a1 11 00 a3 4e  |..f....f.F.....N|
00000090  00 c1 e8 04 a2 40 00 b8  00 30 a3 44 00 8e c0 e8  |.....@...0.D....|
000000a0  f0 00 33 db b9 0b 00 be  ba 01 8b fb f3 a6 74 0f  |..3...........t.|
000000b0  83 c3 20 ff 0e 4e 00 75  eb be b0 01 e9 b4 00 26  |.. ..N.u.......&|
000000c0  8b 47 1a a3 50 00 a1 16  00 a3 4e 00 66 a1 1c 00  |.G..P.....N.f...|
000000d0  03 06 0e 00 66 a3 46 00  a1 4e 00 3d 40 00 76 03  |....f.F..N.=@.v.|
000000e0  b8 40 00 a2 40 00 e8 a9  00 66 0f b6 06 40 00 66  |.@..@....f...@.f|
000000f0  01 06 46 00 29 06 4e 00  74 09 c1 e0 05 01 06 44  |..F.).N.t......D|
00000100  00 eb d5 c7 06 44 00 70  00 a0 0d 00 a2 40 00 66  |.....D.p.....@.f|
00000110  0f b7 06 50 00 66 83 e8  02 66 0f b6 0e 0d 00 66  |...P.f...f.....f|
00000120  f7 e1 66 0f b7 0e 16 00  66 d1 e1 03 06 0e 00 66  |..f.....f......f|
00000130  03 0e 1c 00 66 03 c1 66  0f b7 0e 11 00 66 c1 e9  |....f..f.....f..|
00000140  04 66 03 c1 66 a3 46 00  e8 47 00 8b 36 50 00 b8  |.f..f.F..G..6P..|
00000150  00 30 d1 e6 73 03 05 00  10 8e c0 26 ad 3d f8 ff  |.0..s......&.=..|
00000160  73 16 a3 50 00 0f b6 06  0d 00 c1 e0 09 01 06 42  |s..P...........B|
00000170  00 eb 9c e8 0d 00 eb fe  8a 16 24 00 33 ed ea 00  |..........$.3...|
00000180  00 70 00 ac 3c 00 74 09  b4 0e bb 07 00 cd 10 eb  |.p..<.t.........|
00000190  f2 c3 b4 42 8a 16 24 00  be 3e 00 cd 13 72 01 c3  |...B..$..>...r..|
000001a0  be a5 01 eb ce 44 69 73  6b 20 65 72 72 6f 72 00  |.....Disk error.|
000001b0  4e 6f 20 4c 6f 61 64 65  72 00 44 45 4c 4c 42 49  |No Loader.DELLBI|
000001c0  4f 20 42 49 4e 00 00 00  00 00 00 00 00 00 00 00  |O BIN...........|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by wilee-nilee on 2010-06-28
Could you give a concise description of what your trying to do and a screenshot of gparted showing unallocated and whether it is on the live Ubuntu install. Also boot a live Ubuntu cd and take a screenshot of its gparted.

Never use gparted except from a bootable gparted cd or the live cd until you know how to recognize a mounted partition and how to unmount it and what to do with partitions.

Linux doesn't have a virtual partition manger like W7 disk manager.

---

### Post by amir1981 on 2010-06-28
> **wilee-nilee said:**
> Could you give a concise description of what your trying to do and a screenshot of gparted showing unallocated and whether it is on the live Ubuntu install. Also boot a live Ubuntu cd and take a screenshot of its gparted.

Never use gparted except from a bootable gparted cd or the livecd until you know how to recognize a mounted partition and how to unmount it and what to do with partitions.

Linux doesn't have a virtual partition manger like W7 disk manager.

I tired liveCD but it  gives  the  same message, actually  I tried  to take the screenshot (and I did) but I  for some reason (unknown to me ) the result is not  saved . Anyway, the result was exactly like the below image(attached)

[ATTACH]161859[/ATTACH]

I want to resize my  linux partition. I have installed  linux in a  10 Gig partition but know I  need  more space (I have to debug an old program and  when I  compile the  program with debug  option it becomes larger than my partition!)

---

### Post by wilee-nilee on 2010-06-28
n

---

### Post by jtarin on 2010-06-28
[Look through this guide]("https://help.ubuntu.com/community/Grub2") and satisfy yourself your procedure was correct for reinstalling GRUB,as I believe something is wrong with your partition record....what does it look like from XP?

---

### Post by rollin on 2010-06-29
Hi amir1981. From the screenshot it would seem gparted does not recognise the partitions at all. Unfortunately or fortunately depending which way you look at it this is not the first time this has happened apparently!

I did some digging and found this thread: [http://ubuntuforums.org/showthread.php?t=413745](http://ubuntuforums.org/showthread.php?t=413745)
Post #10 from sunset blvd seemed to find a solution using TestDisk.

Have a read through the thread and links associated. See if it matches what you think you are experiencing and perhaps try sunsets fix in #10?

---

### Post by amir1981 on 2010-06-29
Hi everyone, Thanks  for  helping  ... The  problem  seems  to  get  resolved. I  run  chkdsk /f   under Windows XP  and  after that I  try  Gparted  and it  shows  the  disk  adequately.  Anyway, thanks

---

### Post by rollin on 2010-06-29
> **amir1981 said:**
> Hi everyone, Thanks  for  helping  ... The  problem  seems  to  get  resolved. I  run  chkdsk /f   under Windows XP  and  after that I  try  Gparted  and it  shows  the  disk  adequately.  Anyway, thanks

I'm glad you managed to find a solution. Well done for coming back on the thread and posting what worked for you, I think that will definitely help someone one day.

---

### Post by jtarin on 2010-06-29
> **amir1981 said:**
> Hi everyone, Thanks  for  helping  ... The  problem  seems  to  get  resolved. I  run  chkdsk /f   under Windows XP  and  after that I  try  Gparted  and it  shows  the  disk  adequately.  Anyway, thanks

That resolved your partition record.

---

