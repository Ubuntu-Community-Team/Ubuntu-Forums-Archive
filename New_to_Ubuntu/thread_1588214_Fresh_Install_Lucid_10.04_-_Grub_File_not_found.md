---
title: "Fresh Install Lucid 10.04 - Grub: File not found"
date: 2010-10-04
forum: New to Ubuntu
---

### Post by Mega_Fauna on 2010-10-04
Hi on a newly wiped hard-drive I installed *ubuntu 10.04* with one *root* and one *swap* partition. File system is **Ext3**.

Grub says file not found and then the computer boots. Can someone advise?

---

### Post by Hippytaff on 2010-10-04
I think ubuntu uses FAT32, but I don't know if this has anything to do with it

---

### Post by da burger on 2010-10-04
> **Hippytaff said:**
> I think ubuntu uses FAT32, but I don't know if this has anything to do with it

Ubuntu uses Ext3 for its file system (Ext4 from 10.10). FAT is primarily used on USB sticks and the like because it can be read by all major operating systems.

@OP when you say the computer boots do you mean it starts up normally after the error message? Also would you please post the RESULTS.txt file from following these instructions [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Thanks
Angus

EDIT: In fact before you try that, if you are getting into ubuntu it might be worth running sudo update-grub from the terminal.

---

### Post by Rubi1200 on 2010-10-04
> **Hippytaff said:**
> I think ubuntu uses FAT32, but I don't know if this has anything to do with it
FAT32!?!
[http://en.wikipedia.org/wiki/FAT32#FAT32](http://en.wikipedia.org/wiki/FAT32#FAT32)

By default, Ubuntu uses the Ext4 file-system since version 9.10

@Mega_Fauna

Use the Ubuntu CD in live mode and post the results of the boot-script linked at the bottom of my post please.

If there is an issue with GRUB, the results should help us determine the cause and make offering solutions easier.

Thanks.

---

### Post by Hippytaff on 2010-10-04
:-s I should cross reference my stuff before relaying what I read in posts...*gets coat*

---

### Post by amjjawad on 2010-10-04
> **Rubi1200 said:**
> FAT32!?!
[http://en.wikipedia.org/wiki/FAT32#FAT32](http://en.wikipedia.org/wiki/FAT32#FAT32)

By default, Ubuntu uses the Ext4 file-system since version 9.10

.

Ditto.

---

### Post by amjjawad on 2010-10-04
> **Mega_Fauna said:**
> Hi on a newly wiped hard-drive I installed *ubuntu 10.04* with one *root* and one *swap* partition. File system is **Ext3**.

Grub says file not found and then the computer boots. Can someone advise?

Can you provide more details please?

Thank you!

---

### Post by Mega_Fauna on 2010-10-04
> **da burger said:**
> @OP when you say the computer boots do you mean it starts up normally after the error message? Also would you please post the RESULTS.txt file from following these instructions


Hi Angus,

Thanks for your interest and rapid response:)

Yes, today it boots into ubuntu. It is starting normally.


> **da burger said:**
> EDIT: In fact before you try that, if you are getting into ubuntu it might be worth running sudo update-grub from the terminal.

That won't screw things up? I mean, when I did exactly the same install on a newly wiped HD using Ext4, it wouldn't boot. I don't want to upgrade Grub to the latest version which may or may not boot. I do want to fix the "file not found" problem which I assume is the Grub - select Regular or Recovery Linux screen, but I am a newb.


RESULTS.txt

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   387,743,743   387,741,696  83 Linux
/dev/sda2         387,745,790   390,719,487     2,973,698   5 Extended
/dev/sda5         387,745,792   390,719,487     2,973,696  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   973,796,039   973,795,977  83 Linux
/dev/sdb2         973,797,374   976,773,119     2,975,746   5 Extended
/dev/sdb5         973,797,376   976,773,119     2,975,744  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 999.5 GB, 999501594624 bytes
255 heads, 63 sectors/track, 121515 cylinders, total 1952151552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 1,952,138,474 1,952,138,412  83 Linux


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63   976,768,064   976,768,002  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07b63cd6-3890-40f1-aeee-e6a660a17bf7   ext3                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        7b9dfd59-5b2d-48c0-bd32-a0bb6dce5941   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        b0494ef6-73ed-4282-940a-10e96af634c5   ext3       MIRROR_02_OF_02               
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        ea4ae85e-6580-4f74-bd82-03f942d8bda9   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        8e47b60e-a6b9-4d69-b790-df17d3aaf23b   ext3       ST_JEROME                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        02b80c63-93c7-4081-8284-d9faffe1d0c4   ext3       MIRROR_01_OF_02               
/dev/sdd: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext3       (rw,errors=remount-ro)
/dev/sdb1        /media/MIRROR_02_OF_02   ext3       (rw)
/dev/sdc1        /media/ST_JEROME         ext3       (rw)
/dev/sdd1        /media/MIRROR_01_OF_02   ext3       (rw)
/dev/sr2         /media/WD SmartWare      udf        (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 07b63cd6-3890-40f1-aeee-e6a660a17bf7
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 07b63cd6-3890-40f1-aeee-e6a660a17bf7
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
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 07b63cd6-3890-40f1-aeee-e6a660a17bf7
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=07b63cd6-3890-40f1-aeee-e6a660a17bf7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 07b63cd6-3890-40f1-aeee-e6a660a17bf7
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=07b63cd6-3890-40f1-aeee-e6a660a17bf7 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 07b63cd6-3890-40f1-aeee-e6a660a17bf7
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=07b63cd6-3890-40f1-aeee-e6a660a17bf7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 07b63cd6-3890-40f1-aeee-e6a660a17bf7
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=07b63cd6-3890-40f1-aeee-e6a660a17bf7 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 07b63cd6-3890-40f1-aeee-e6a660a17bf7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 07b63cd6-3890-40f1-aeee-e6a660a17bf7
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=07b63cd6-3890-40f1-aeee-e6a660a17bf7 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=7b9dfd59-5b2d-48c0-bd32-a0bb6dce5941 none            swap    sw              0       0
# swap was on /dev/sdb5 during installation
UUID=ea4ae85e-6580-4f74-bd82-03f942d8bda9 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

## MIRROR_01_OF_02 AS EXT3
## /dev/sdd1: LABEL="MIRROR_01_OF_02" UUID="02b80c63-93c7-4081-8284-d9faffe1d0c4" TYPE="ext3" 
UUID=02b80c63-93c7-4081-8284-d9faffe1d0c4 /media/MIRROR_01_OF_02        ext3         defaults                                                                   0  0


## MIRROR_02_OF_02 AS EXT3: Internal drive Disk identifier: 0x000dccf7
UUID=b0494ef6-73ed-4282-940a-10e96af634c5 /media/MIRROR_02_OF_02        ext3         defaults                                                                   0  0


## NEW 1 TB ST_JEROME AS EXT3 [St. Jerome is the patron saint of librarians]
## LABEL="ST_JEROME" UUID="8e47b60e-a6b9-4d69-b790-df17d3aaf23b" TYPE="ext3" 
UUID=8e47b60e-a6b9-4d69-b790-df17d3aaf23b /media/ST_JEROME        ext3         defaults                                                                   0  0


=================== sda1: Location of files loaded by Grub: ===================


  19.8GB: boot/grub/core.img
  19.9GB: boot/grub/grub.cfg
  19.9GB: boot/initrd.img-2.6.32-24-generic
  19.9GB: boot/initrd.img-2.6.32-25-generic
  19.8GB: boot/vmlinuz-2.6.32-24-generic
  19.8GB: boot/vmlinuz-2.6.32-25-generic
  19.9GB: initrd.img
  19.9GB: initrd.img.old
  19.8GB: vmlinuz
  19.8GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  4f 6a 34 71 37 a1 24 06  ca d9 7a 9f ff ff ff fe  |Oj4q7.$...z.....|
00000010  6a e9 58 9a 23 b6 6b 50  ec ad 9a d2 9f cc ca bb  |j.X.#.kP........|
00000020  13 eb 95 78 ae 9f ff d3  a7 1c e3 c1 24 82 81 90  |...x........$...|
00000030  6c 38 1e 17 ff fb 52 c0  7d 80 0b 05 17 5e 6c 30  |l8....R.}....^l0|
00000040  6b 89 53 a2 ab cd 84 89  71 d6 40 69 92 2f 19 ff  |k.S.....q.@i./..|
00000050  fa 00 00 11 36 c9 6c 0a  b8 88 02 51 52 84 05 26  |....6.l....QR..&|
00000060  2a d4 55 50 ca 43 a4 c3  23 54 8f 6d 17 54 c6 6b  |*.UP.C..#T.m.T.k|
00000070  9d ea 04 ef 5e 5a b9 6b  8a 20 22 09 43 3b 2f ff  |....^Z.k. ".C;/.|
00000080  f5 62 91 ce 58 eb 62 24  ac 65 5b 32 18 b1 45 94  |.b..X.b$.e[2..E.|
00000090  f6 f7 46 ac c6 cb a7 bf  ff f2 8c 49 04 b1 66 d8  |..F........I..f.|
000000a0  18 c6 ff f2 9b 44 14 96  ea 00 00 00 0d db 26 e6  |.....D........&.|
000000b0  db 0f 70 58 68 22 51 a1  b3 a5 f3 73 97 41 28 30  |..pXh"Q....s.A(0|
000000c0  9c 6a 85 ce e3 3f ef b9  bc 6a 8d 96 53 71 58 13  |.j...?...j..SqX.|
000000d0  d4 26 b7 d9 5b ff ea ac  64 73 23 8a 4b 1d 26 4b  |.&..[...ds#.K.&K|
000000e0  a6 97 32 39 95 bb a5 d6  ca e4 57 21 99 5c 9b 7e  |..29......W!.\.~|
000000f0  a8 90 a6 12 16 35 f1 98  9a 1b ff f1 35 89 d9 ad  |.....5......5...|
00000100  cc 00 00 99 b4 ff fb 52  c0 85 00 0a c9 07 60 6c  |.......R......`l|
00000110  20 6b 81 5f 96 6b 4d 87  89 31 da 75 0c dc 21 a8  | k._.kM..1.u..!.|
00000120  26 5a 6a 52 19 e4 fd 7d  da b3 d0 55 10 64 4c 7a  |&ZjR...}...U.dLz|
00000130  b9 ad 77 d4 0a 50 81 68  8e d2 e9 08 c8 6c 87 3b  |..w..P.h.....l.;|
00000140  ff ff ff cc 60 70 75 86  34 a7 73 58 6b 09 b5 67  |....`pu.4.sXk..g|
00000150  51 57 29 e5 2c 28 49 94  a4 a0 8c 66 3b a8 7a 02  |QW).,(I....f;.z.|
00000160  a0 22 41 44 1c 18 8e b4  11 18 8f ff f5 20 00 00  |."AD......... ..|
00000170  4e da 85 22 4b 11 cb 46  8d 1c 04 74 34 0c 9c 94  |N.."K..F...t4...|
00000180  aa c8 eb 09 17 9b 24 a9  6f a9 ed 5b 73 d3 c4 a3  |......$.o..[s...|
00000190  2b c2 ed bd a8 6d 42 ed  df ff fb 10 ce 64 31 dd  |+....mB......d1.|
000001a0  9d 2e 88 ee 96 55 18 aa  e4 b3 75 b1 92 7b 15 4a  |.....U....u..{.J|
000001b0  e6 4a d9 bd 52 67 25 82  a9 44 85 40 51 2c 00 fe  |.J..Rg%..D.@Q,..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 68 2d 00 00 00  |...........h-...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by da burger on 2010-10-05
I'm afraid I can't work out what's wrong with your set up. However I can see a few things that might just help:
1) What have you tried to do with drives b,c and d? They all have a set up that looks like a ubuntu install but one of them has a windows boot loader...
2) I would give sudo update-grub a run. I shouldn't do any damage and there's an outside chance it might fix something I didn't even notice.
 
Beyond that I can' help you I'm afraid.
I hope someone else will have a better idea what's going on than me.
Angus

---

### Post by Rubi1200 on 2010-10-05
First of all, there are some things you need to tell us so we can advise you further.

1. why does it say Windows is installed in the MBR of sdc when it appears you have a Linux file system there?

2. are all these devices external except for sda?

3. how have you been booting/mounting them until now i.e. via BIOS each time the computer starts?

4. please explain to us the terminology and usage of>   MIRROR_02_OF_02>   ST_JEROME > MIRROR_01_OF_02 Are these just labels for backup drives?

5. what are you using this for? > /dev/sr2         /media/WD SmartWare      udf6. why do you have 2 swap partitions?

It is important that you tell us what you want your setup to do so we can advise you how to get it working the way you want it.

It would be pointless telling you to reinstall this, update that, or delete the next thing if it ends up causing more problems than it solves.

Thanks in advance.

---

### Post by Mega_Fauna on 2010-10-06
> **Rubi1200 said:**
> First of all, there are some things you need to tell us so we can advise you further....


**da burger** Angus, thanks for your help.

**Rubi1200**	Thanks for your detailed response and interest. I apologize for the delay in replying. Here are the answers to your questions.

Questions 1-6: They are all data drives (details below if you're curious). I can unmount or manually unplug them at any time. The main is 1TB and there are two 500gig mirrors. All we should be concerned about here is /sda, the internal ancient 200 gig drive with 10.04 installed.


		1)>  1. why does it say Windows is installed in the MBR of sdc when it appears you have a Linux file system there? 

It is whatever the manufacturer set up. I formatted the drive entirely with Gparted and was a little surprised to see that it missed that partition bit. I'll check it out again, it is superfluous at best.


	2)> 2. are all these devices external except for sda?

Two External, Two Internal.
		/sda	Internal (OS only)
		/sdb1	Internal MIRROR_02_OF_02

		/sdd1	External MIRROR_01_OF_02
		/sdc1	External ST_JEROME


		3)> 3. how have you been booting/mounting them until now i.e. via BIOS each time the computer starts?

Yes, they are mounted at boot.


		4)> please explain to us the terminology and usage of...

Yes, these are labels for backup drives.

		ST_JEROME	     1Terabyte	     Main data drive - all my stuff except OS
		MIRROR_01_OF_02		     500 gig	  First half of backup drive
		MIRROR_02_OF_02		     500 gig  	Second half of backup

I use grsync to mirror the drives back and forth.


		5) > 5. what are you using this for?
Came with ST_JEROME from the manufacturer. When I wiped the drive with Gparted and installed Ext3 I assumed it would go away, it hasn't. The windows MBR that mounts in Question (1) is this one.


		6)> 6. why do you have 2 swap partitions?

Somewhere (and I can't find where) I read that to speed up ubuntu add a second swap (I am on an old Dell Dimension). Presently it isn't mounted and is simply taking up space. If you advise against it, I'll wipe it instead of mounting it. I'm not sure it made all that much a difference at all.

--------------------------------------
If that hasn't wasted your time, I don't know what will;)

Any OS problems will be occuring on /sda which is the internal drive exclusive for running ubuntu. The OS is under such heavy developement (and will be IMHO for approaching half a decade to come) that I've found that it is simplist for a newb like me just to mess with the updates and upgrades on one drive, and to keep all my stuff on other removable and untouched drives.

So back to my file not found Grub(?) question if we're not OT yet.

Thanks again for the interest.

---

### Post by oldfred on 2010-10-06
Not using swap at all is what speeds up things. Swap is 10 times slower than RAM. If you have more the 3GB you may not be using swap at all.

Having windows in the MBR of sdc is not an issue as long as you do not try to boot sdc.

If it boots after an error it seems like it is having trouble mounting one of the drives in fstab. After you have booted is a drive missing?

If you run this do you get any error as it will mount fstab. If it just returns to a command line then it is ok.
sudo mount -a

---

### Post by Mega_Fauna on 2010-10-06
> **oldfred said:**
> Not using swap at all is what speeds up things. Swap is 10 times slower than RAM. If you have more the 3GB you may not be using swap at all.

Having windows in the MBR of sdc is not an issue as long as you do not try to boot sdc.

If it boots after an error it seems like it is having trouble mounting one of the drives in fstab. After you have booted is a drive missing?

If you run this do you get any error as it will mount fstab. If it just returns to a command line then it is ok.
sudo mount -a


Hi oldfred, thanks for your response.

I've got 500 meg of ram, and to buy more would be prohibitively expensive, believe me, I've checked. Mine is obsolete and I'll upgrade the computer as soon as the economy improves.

All the drives are mounting correctly.

---

### Post by oldfred on 2010-10-06
Try looking in the logs. System, Administration, Log File Viewer. It may tell you something or show a long time between events or repeated trying to load something.

I look at all, but you may want to look at messages & syslog first.

---

### Post by Mega_Fauna on 2010-10-06
**Thanks oldfred**

If this helps. Otherwise, which log should I post?

System --> Administration --> Log File View --> boot.log

```

fsck from util-linux-ng 2.17.2

/dev/sda1: clean, 191828/12124160 files, 2595498/48467712 blocks

init: ureadahead-other main process (670) terminated with status 4


init: ureadahead-other main process (731) terminated with status 4


 * Starting AppArmor profiles       [160G Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox


[154G[ OK ]

 * Setting sensors limits       [160G 
[154G[ OK ]

```

---

### Post by amjjawad on 2010-10-06
I don't mean to get in the way but out of curiosity, have you considered to format and install a fresh copy again? I think that would save your time beside the installation process should not take more than 30mins anyway.

:)

---

### Post by Mega_Fauna on 2010-10-06
> **amjjawad said:**
> I don't mean to get in the way but out of curiosity, have you considered to format and install a fresh copy again? I think that would save your time beside the installation process should not take more than 30mins anyway.

:)

Hi **amjjawad**,

Thanks for your response.

Reinstalling is out of the question. It took two installs on a freshly wiped w/ Gparted drive till Lucid booted. I'd rather leave things as they are than risk a non-booting computer again.

---

### Post by oldfred on 2010-10-06
Your boot log looks just like mine.

Look at the times each activity occurs in messages or syslog. If a lot of time that may be an issue. Or if you see a message like it is trying to load something and repeats many times before it works (or not).

---

