---
title: "Dual boot to Single boot"
date: 2010-11-02
forum: New to Ubuntu
---

### Post by fubeca6 on 2010-11-02
I've been using Ubuntu 10.10 and Windows Vista via dual-boot on my laptop for about 3 weeks now, and since starting Ubuntu I really haven't gone back to Windows. However, I had initially only alotted a fairly small portion of HDD space for Ubuntu, so now I need more. 

So what I want to do is delete the Windows partition(s) and make it available for use in Ubuntu. Help?

---

### Post by kwacka on 2010-11-02
You can use gparted to reduce the size of your Windows partition (or delete it).

You can install via Synaptic Package Manager or Software Centre.

You can then move your Ubuntu installation and resize your home partition; or create a separate partition for storage.

---

### Post by Rubi1200 on 2010-11-02
You should use GParted on a LiveCD to make any changes to partitions AFTER backing up important data.

Make sure to unmount all partitions including swap: right-click > Swapoff

Then, as posted above regarding deleting/resizing.

---

### Post by racie on 2010-11-02
If you installed through Wubi in Windows, DO NOT delete the Windows partition, as Ubuntu is installed there in a "fake" partition.  You need to transfer Ubuntu to a dedicated partition.  I know there is a good guide on this somewhere...

Unless you did it through the CD...

---

### Post by fatality_uk on 2010-11-02
Can you let us know if you installed Ubuntu with Wubi (Inside Windows)?

---

### Post by wilee-nilee on 2010-11-02
> **fatality_uk said:**
> can you let us know if you installed ubuntu with wubi (inside windows)?
+1

---

### Post by JoeC5 on 2010-11-02
I just went through this process and what a learning experience. wow. Going from dual to single boot and no i did not install with Wubi. Would be great if someone could explain reallocating drives on an extended partition.

For example I finally moved and resized my extended partition to cover the whole drive ... now I just added a boot partition to the start of the disk .. (I'm not really sure it is booting from the new partition - Is there any way to test?)

Also I'd love to know how to make a home partition and a temp partition and from what I read it's smart to make two root partitions for the current os and the next os instead of upgrading ..  Does anyone know where I can get this type of smart partitioning guidance?

Thanks.

---

### Post by wilee-nilee on 2010-11-02
> **JoeC5 said:**
> I just went through this process and what a learning experience. wow. Going from dual to single boot and no i did not install with Wubi. Would be great if someone could explain reallocating drives on an extended partition.

For example I finally moved and resized my extended partition to cover the whole drive ... now I just added a boot partition to the start of the disk .. (I'm not really sure it is booting from the new partition - Is there any way to test?)

Also I'd love to know how to make a home partition and a temp partition and from what I read it's smart to make two root partitions for the current os and the next os instead of upgrading ..  Does anyone know where I can get this type of smart partitioning guidance?

Thanks.

You don't need a boot partition run the bootscript in my signature and post the text in code tags as described in my signature.

---

### Post by JoeC5 on 2010-11-02
Sorry for hijacking your thread fubeca6

here is my boot script results:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /etc/fstab

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
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

/dev/sda4           1,028,160   625,137,344   624,109,185   5 Extended
/dev/sda5           5,735,205   138,287,519   132,552,315  83 Linux
/dev/sda6    *      1,028,286     1,445,849       417,564  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2003 MB, 2003795968 bytes
32 heads, 63 sectors/track, 1941 cylinders, total 3913664 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63     3,913,055     3,912,993   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mmcblk0p1   8026babb-cbdc-4cfd-a143-578fc2e3ac1a   ext4                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        3919c416-8a1a-4cd1-8780-695ba5b737c2   ext4                                     
/dev/sda6        f1974e2a-c065-4d94-a1d3-107b4ec6e820   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        4C6D-49C8                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw)
/dev/sda6        /boot                    ext4       (ro)
/dev/sdb1        /media/4C6D-49C8         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/mmcblk0p1   /media/8026babb-cbdc-4cfd-a143-578fc2e3ac1a ext4       (rw,nosuid,nodev,uhelper=udisks)


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
#UUID=3919c416-8a1a-4cd1-8780-695ba5b737c2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
#UUID=c54ff61a-4922-4636-be07-2c9f3c583020 none            swap    sw              0       0
/dev/sda6 /boot	ext4 ro	      0 0



=================== sda5: Location of files loaded by Grub: ===================


   3.0GB: initrd.img
   3.1GB: initrd.img.old
   3.0GB: vmlinuz
   3.0GB: vmlinuz.old

============================= sda6/grub/grub.cfg: =============================

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
search --no-floppy --fs-uuid --set 3919c416-8a1a-4cd1-8780-695ba5b737c2
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
search --no-floppy --fs-uuid --set 3919c416-8a1a-4cd1-8780-695ba5b737c2
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
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 3919c416-8a1a-4cd1-8780-695ba5b737c2
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=3919c416-8a1a-4cd1-8780-695ba5b737c2 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 3919c416-8a1a-4cd1-8780-695ba5b737c2
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=3919c416-8a1a-4cd1-8780-695ba5b737c2 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 3919c416-8a1a-4cd1-8780-695ba5b737c2
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=3919c416-8a1a-4cd1-8780-695ba5b737c2 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 3919c416-8a1a-4cd1-8780-695ba5b737c2
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=3919c416-8a1a-4cd1-8780-695ba5b737c2 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 3919c416-8a1a-4cd1-8780-695ba5b737c2
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 3919c416-8a1a-4cd1-8780-695ba5b737c2
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== sda6: Location of files loaded by Grub: ===================


    .7GB: grub/core.img
    .6GB: grub/grub.cfg
    .7GB: initrd.img-2.6.32-24-generic
    .6GB: initrd.img-2.6.32-25-generic
    .6GB: vmlinuz-2.6.32-24-generic
    .6GB: vmlinuz-2.6.32-25-generic
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  00 66 0f be c0 66 89 46  06 5f 5e 5d c2 10 00 cc  |.f...f.F._^]....|
00000010  cc cc cc cc 8b ff 55 8b  ec 51 53 56 8b 75 14 56  |......U..QSV.u.V|
00000020  ff 75 10 33 db ff 75 0c  88 5d ff ff 75 08 e8 6d  |.u.3..u..]..u..m|
00000030  bd ff ff 3b c3 89 45 10  75 03 89 75 10 57 53 53  |...;..E.u..u.WSS|
00000040  ff 75 10 e8 2b b1 ff ff  8b 35 5c 10 8e 1c 8b f8  |.u..+....5\.....|
00000050  83 ff ff 0f 84 b5 00 00  00 38 5d 1c 0f 84 a8 00  |.........8].....|
00000060  00 00 57 6a 08 ff d6 50  ff 15 68 10 8e 1c 3b c3  |..Wj...P..h...;.|
00000070  89 45 1c 0f 84 95 00 00  00 ff 75 10 57 50 bf c8  |.E........u.WP..|
00000080  5a 8e 1c 57 53 68 d0 61  8e 1c ff 15 a8 10 8e 1c  |Z..WSh.a........|
00000090  85 c0 76 67 57 8b 7d 1c  57 e8 6d ad ff ff 85 c0  |..vgW.}.W.m.....|
000000a0  74 59 8b c7 38 18 74 53  57 53 e8 64 b0 ff ff 3b  |tY..8.tSWS.d...;|
000000b0  c3 89 45 0c 74 2e 50 e8  67 b3 ff ff ff 75 0c 0f  |..E.t.P.g....u..|
000000c0  b7 c0 53 89 45 08 ff d6  50 ff 15 58 10 8e 1c 8b  |..S.E...P..X....|
000000d0  45 08 3b 45 18 74 20 8b  4d 18 81 e1 ff 03 00 00  |E.;E.t .M.......|
000000e0  3b c1 74 13 ff 75 1c ff  15 a4 10 8e 1c 8d 7c 07  |;.t..u........|.|
000000f0  01 38 1f 75 b3 eb 04 c6  45 ff 01 ff 75 1c 53 ff  |.8.u....E...u.S.|
00000100  d6 50 ff 15 58 10 8e 1c  eb 04 c6 45 ff 01 8b 45  |.P..X......E...E|
00000110  10 3b 45 14 5f 74 0f 3b  c3 74 0b 50 53 ff d6 50  |.;E._t.;.t.PS..P|
00000120  ff 15 58 10 8e 1c 8a 45  ff 5e 5b c9 c2 18 00 cc  |..X....E.^[.....|
00000130  cc cc cc cc 8b ff 55 8b  ec 8b 4d 0c 33 c0 85 c9  |......U...M.3...|
00000140  74 08 81 f9 ff ff ff 7f  76 05 b8 57 00 07 80 85  |t.......v..W....|
00000150  c0 7c 38 53 56 57 8b 7d  08 8d 45 14 50 ff 75 10  |.|8SVW.}..E.P.u.|
00000160  8d 71 ff 56 57 33 db e8  7f 6e 00 00 83 c4 10 85  |.q.VW3...n......|
00000170  c0 7c 0b 3b c6 77 07 75  0d 88 1c 3e eb 08 88 1c  |.|.;.w.u...>....|
00000180  3e bb 7a 00 07 80 5f 5e  8b c3 5b 5d c3 cc cc cc  |>.z..._^..[]....|
00000190  cc cc 8b ff 55 8b ec 81  ec 78 02 00 00 a1 ac 71  |....U....x.....q|
000001a0  91 1c 33 c5 89 45 fc 8b  4d 14 8b 45 08 53 56 57  |..3..E..M..E.SVW|
000001b0  8b 7d 10 33 db 53 53 53  89 8d 90 fd ff ff 00 00  |.}.3.SSS........|
000001c0  41 65 83 fe ff ff e5 d2  47 00 7b 96 e6 07 00 00  |Ae......G.{.....|
000001d0  02 40 05 fe 3f 59 01 00  00 00 99 5f 06 00 00 00  |.@..?Y....._....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by wilee-nilee on 2010-11-02
That is great, the script will get you the answers. I see missing files from what appears most likely to be Ubuntu sda6 is sda5 the boot you tried to build. I think I have it backwards here is why I ask.

Anyway more experienced help is needed here, it may be just reloading grub2 and the mbr with the correct pointing at the correct partition, is all that is needed. There is stuff missing from the script due to missing files.

Lets see what the others say.

---

### Post by fubeca6 on 2010-11-02
No I didn't use Wubi, I installed from Disk. So (here's where I show how much of a Noob I am) How do I tell which partitions are Windows? Would it make sense to assume that the NTFS partition is the main Windows part?

---

### Post by racie on 2010-11-02
You are correct, NTFS is Windows.

*edit*  Here's a link that may be helpful to you: [https://help.ubuntu.com/community/HowToRemoveWindows](https://help.ubuntu.com/community/HowToRemoveWindows)

---

### Post by onaridge on 2010-11-02
Fpr Wubi migration: [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

### Post by wilee-nilee on 2010-11-03
> **fubeca6 said:**
> No I didn't use Wubi, I installed from Disk. So (here's where I show how much of a Noob I am) How do I tell which partitions are Windows? Would it make sense to assume that the NTFS partition is the main Windows part?

Welcome back, you will need a live Ubuntu cd to do all of this so boot one and take a screenshot of the gparted partitioner, and post it so we can just be sure of your setup.

Generally if you just have a dual boot with windows and linux and grub is the bootloader you can wipe away windows if thats what you want. You have confirmed it is not a wubi so lets see the screenshot.

---

