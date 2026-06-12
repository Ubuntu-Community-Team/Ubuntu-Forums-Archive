---
title: "HDD Unaccessible from Windows after using with Ubuntu"
date: 2010-02-13
forum: New to Ubuntu
---

### Post by xtsuname on 2010-02-13
First, Let me deeply apolgize if such a thread have been posted.
Secondly, let me also apologize if I post this to the wrong thread.

Here's my problem. I have an HDD that was working fine before on both Ubuntu and Windows 7. I am dual booing both of them. The HDD has 2 partitions both were formatted in Windows as NTFS. After using Ubuntu for a while(more than 6 months), I went back to Windows as I need to do some maintenance. I found out that I was greeted with a screen from diskchk and after that I was unable to access the HDD from Windows. The other partition of the HDD still works fine in both Windows and Ubuntu, but the problematic one works fine only in Ubuntu and is unaccessible in Windows.

Thank you to those that read the whole post.

I'll be really happy if someone can help me with this.

Thank you,
[--X--]

P.S:Please pardon my imperfect English.

---

### Post by bodhi.zazen on 2010-02-14
The only thing I know of is that Windows will recognize only one partition on a USB (flash) drive. What kind of a hard drive is it and how exactly are you connecting it ?

My only other suggestion is to ask on a Windows forum as the drive seems to work from Ubuntu.

---

### Post by xtsuname on 2010-02-14
It's a 1TB HDD connected to my Desktop via SATA. Windows used to be able to detect both partition. I think I might have accidentally deleted the System Volume Information that might have caused this to happend.

I would ask in a Windows Forum except I'm not sure where will be good and I'm kinda assuming their reply will be to format it. Which I can't do since there is a lot of important files there

Thank you for replying so fast.

---

### Post by bodhi.zazen on 2010-02-14
Well, if you can access the data from Ubuntu, can you back what you need to a flash drive or CD/DVD ?

---

### Post by xtsuname on 2010-02-14
I would have done that except the size is 500GB and I don't have that much free space on my other HDD

---

### Post by Mark Phelps on 2010-02-16
The fact that you said BOTH partitions are NTFS, and that Ubuntu can not be installed native into an NTFS partition, indicates that you have a Wubi install -- in which Ubuntu is installed like any other MS Windows application.  This means that if you have any further problems with Windows, you will most likely lose ALL access to Ubuntu as well.

So, the sooner you copy off the Ubuntu files & data you don't want to lose, the better off you will be.

---

### Post by presence1960 on 2010-02-16
Your description is rather vague. I need to see exactly what you have on that machine. Do the following with all hard disks plugged in. Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

### Post by xtsuname on 2010-02-16
@Mark I have multiple HDD

@Presence. Hope this helps

Thank you

```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => No known boot loader is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 373815 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sda and 
                       looks on partition #1 for /grub.
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000b499e

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63     4,883,759     4,883,697  83 Linux
/dev/sda2           4,883,760   219,737,069   214,853,310   5 Extended
/dev/sda5           4,883,823   200,202,029   195,318,207  83 Linux
/dev/sda6         200,202,093   219,737,069    19,534,977  82 Linux swap / Solaris
/dev/sda3    *    219,737,070   488,392,064   268,654,995   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000a26e5

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   921,600,854   921,600,792   7 HPFS/NTFS
/dev/sdb2         921,600,855 1,953,520,064 1,031,919,210   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00008825

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63   312,576,704   312,576,642   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        02b8ac42-2c07-43b2-bcb3-4fc80ed53bfe   ext4                                     
/dev/sda3        88EA49E1EA49CC5E                       ntfs                                     
/dev/sda5        cba96e6a-aa01-4d52-b1ac-ee530b11abea   ext4                                     
/dev/sda6        1dbd216d-97d2-44f9-a877-a65a71a1aed4   swap                                     
/dev/sdb1        82BED68ABED675DF                       ntfs       Terra                         
/dev/sdb2        4CC36ABE7FF35C0F                       ntfs       Lunar                         
/dev/sdd1        92DC2BACDC2B8A15                       ntfs       KELLY                         

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,relatime,errors=remount-ro)
/dev/sda1        /boot                    ext4       (rw,relatime)
/dev/sdb1        /media/Terra             fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb2        /media/Lunar             fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda3        /media/windows           fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdd1        /media/KELLY             fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


============================= sda1/grub/grub.cfg: =============================

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
search --no-floppy --fs-uuid --set cba96e6a-aa01-4d52-b1ac-ee530b11abea
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
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 02b8ac42-2c07-43b2-bcb3-4fc80ed53bfe
insmod png
if background_image /grub/Clannad.png ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/white
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 02b8ac42-2c07-43b2-bcb3-4fc80ed53bfe
	linux	/vmlinuz-2.6.31-19-generic root=UUID=cba96e6a-aa01-4d52-b1ac-ee530b11abea ro   quiet splash
	initrd	/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 02b8ac42-2c07-43b2-bcb3-4fc80ed53bfe
	linux	/vmlinuz-2.6.31-19-generic root=UUID=cba96e6a-aa01-4d52-b1ac-ee530b11abea ro single 
	initrd	/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 02b8ac42-2c07-43b2-bcb3-4fc80ed53bfe
	linux	/vmlinuz-2.6.31-17-generic root=UUID=cba96e6a-aa01-4d52-b1ac-ee530b11abea ro   quiet splash
	initrd	/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 02b8ac42-2c07-43b2-bcb3-4fc80ed53bfe
	linux	/vmlinuz-2.6.31-17-generic root=UUID=cba96e6a-aa01-4d52-b1ac-ee530b11abea ro single 
	initrd	/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 02b8ac42-2c07-43b2-bcb3-4fc80ed53bfe
	linux	/vmlinuz-2.6.31-16-generic root=UUID=cba96e6a-aa01-4d52-b1ac-ee530b11abea ro   quiet splash
	initrd	/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 02b8ac42-2c07-43b2-bcb3-4fc80ed53bfe
	linux	/vmlinuz-2.6.31-16-generic root=UUID=cba96e6a-aa01-4d52-b1ac-ee530b11abea ro single 
	initrd	/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 02b8ac42-2c07-43b2-bcb3-4fc80ed53bfe
	linux	/vmlinuz-2.6.31-15-generic root=UUID=cba96e6a-aa01-4d52-b1ac-ee530b11abea ro   quiet splash
	initrd	/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 02b8ac42-2c07-43b2-bcb3-4fc80ed53bfe
	linux	/vmlinuz-2.6.31-15-generic root=UUID=cba96e6a-aa01-4d52-b1ac-ee530b11abea ro single 
	initrd	/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 02b8ac42-2c07-43b2-bcb3-4fc80ed53bfe
	linux	/vmlinuz-2.6.31-14-generic root=UUID=cba96e6a-aa01-4d52-b1ac-ee530b11abea ro   quiet splash
	initrd	/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 02b8ac42-2c07-43b2-bcb3-4fc80ed53bfe
	linux	/vmlinuz-2.6.31-14-generic root=UUID=cba96e6a-aa01-4d52-b1ac-ee530b11abea ro single 
	initrd	/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda3)" {
	insmod ntfs
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 88ea49e1ea49cc5e
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== sda1: Location of files loaded by Grub: ===================


    .1GB: boot/grub/core.img
    .1GB: grub/core.img
    .1GB: grub/grub.cfg
    .1GB: initrd.img-2.6.31-14-generic
    .1GB: initrd.img-2.6.31-15-generic
    .2GB: initrd.img-2.6.31-16-generic
    .2GB: initrd.img-2.6.31-17-generic
    .2GB: initrd.img-2.6.31-19-generic
    .1GB: vmlinuz-2.6.31-14-generic
    .1GB: vmlinuz-2.6.31-15-generic
    .2GB: vmlinuz-2.6.31-16-generic
    .1GB: vmlinuz-2.6.31-17-generic
    .2GB: vmlinuz-2.6.31-19-generic

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0



# / was on /dev/sda5 during installation
UUID=cba96e6a-aa01-4d52-b1ac-ee530b11abea /               ext4    relatime,errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=02b8ac42-2c07-43b2-bcb3-4fc80ed53bfe /boot           ext4    relatime        0       2
# swap was on /dev/sda6 during installation
UUID=1dbd216d-97d2-44f9-a877-a65a71a1aed4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

#Mounting Windows Partition
/dev/sdb1		/media/Terra	 ntfs-3g gid=xtsuname,uid=xtsuname,iocharset=utf8,umask=000 0 0
/dev/sdb2		/media/Lunar	 ntfs-3g gid=xtsuname,uid=xtsuname,iocharset=utf8,umask=000 0 0
/dev/sda3		/media/windows	ntfs-3g	gid=xtsuname,uid=xtsuname,iocharset=utf8,umask=000 0 0

# Mounting Diamond
//192.168.1.13/Music /media/Music  cifs  credentials=/home/xtsuname/.smbcredentials,gid=xtsuname,uid=xtsuname,iocharset=utf8,umask=000 0 0
//192.168.1.13/PRIVATE2 /media/Private2  cifs  credentials=/root/.smbcredentials,gid=root,uid=root,iocharset=utf8,umask=000 0 0
//192.168.1.13/Anime /media/Anime  cifs  credentials=/home/xtsuname/.smbcredentials,uid=xtsuname,gid=xtsuname,iocharset=utf8,umask=000 0 0
//192.168.1.13/Private /media/Private  cifs  credentials=/home/xtsuname/.smbcredentials,uid=xtsuname,gid=xtsuname,iocharset=utf8,umask=000 0 0
//192.168.1.13/Videos /media/Videos  cifs  credentials=/home/xtsuname/.smbcredentials,uid=xtsuname,gid=xtsuname,iocharset=utf8,umask=000 0 0
//192.168.1.13/Public /media/Public  cifs  credentials=/home/xtsuname/.smbcredentials,uid=xtsuname,gid=xtsuname,iocharset=utf8,umask=000 0 0


=================== sda5: Location of files loaded by Grub: ===================


   2.7GB: initrd.img
   2.7GB: initrd.img.old
   2.7GB: vmlinuz
   2.6GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdd

00000000  90 e9 7d 01 fa 33 c0 8e  d0 8e c0 8e d8 bc 00 7c  |..}..3.........||
00000010  8b f4 fb bf 00 06 b9 00  01 f3 a5 bb 20 06 ff e3  |............ ...|
00000020  90 90 be 7d 07 81 3c aa  55 75 11 e8 58 00 73 0c  |...}..<.Uu..X.s.|
00000030  e8 65 00 72 07 e8 b1 00  72 3b eb 2c be 7d 07 c7  |.e.r....r;.,.}..|
00000040  04 00 00 ba 80 00 be be  07 b9 04 00 f6 04 80 75  |...............u|
00000050  07 83 c6 10 e2 f6 eb 1d  8a 74 01 8b 4c 02 bb 00  |.........t..L...|
00000060  7c b8 01 02 cd 13 72 0d  81 3e fe 7d 55 aa 75 05  ||.....r..>.}U.u.|
00000070  ea 00 7c 00 00 be 6a 07  ac 0a c0 74 fe bb 07 00  |..|...j....t....|
00000080  b4 0e cd 10 eb f2 bb 00  7e c6 07 13 c6 47 01 00  |........~....G..|
00000090  b2 80 b8 00 e0 cd 13 c3  bf 00 7e ba f0 01 b3 a0  |..........~.....|
000000a0  e8 84 00 72 0c b1 01 e8  48 00 72 05 e8 19 00 73  |...r....H.r....s|
000000b0  16 f6 c3 10 75 05 80 cb  10 eb e5 81 fa 70 01 74  |....u........p.t|
000000c0  05 ba 70 01 eb d8 f9 c3  81 bd fe 01 55 aa 75 17  |..p.........U.u.|
000000d0  8b 75 02 81 fe be 01 77  0e 03 f7 81 3c aa 55 75  |.u.....w....<.Uu|
000000e0  06 f6 44 02 01 75 01 f9  c3 bf 00 7c b1 0a e8 01  |..D..u.....|....|
000000f0  00 c3 52 57 83 c2 02 b0  01 ee 42 8a c1 ee 42 32  |..RW......B...B2|
00000100  c0 ee 42 ee 42 8a c3 ee  42 b0 20 ee e8 33 00 ec  |..B.B...B. ..3..|
00000110  24 fd 3c 58 75 0d 83 ea  07 b9 00 01 fa f3 6d fb  |$.<Xu.........m.|
00000120  f8 eb 01 f9 5f 5a c3 52  83 c2 07 ec a8 80 75 0f  |...._Z.R......u.|
00000130  4a 8a c3 ee 42 ec 24 d0  3c 50 75 03 f8 eb 01 f9  |J...B.$.<Pu.....|
00000140  5a c3 51 8b 0e 6c 04 83  c1 12 81 c2 ff 01 ec 8a  |Z.Q..l..........|
00000150  e0 80 e4 d8 80 fc 58 74  06 3b 0e 6c 04 75 ef 81  |......Xt.;.l.u..|
00000160  ea ff 01 b9 00 20 e2 fe  59 c3 0d 0a 45 72 72 6f  |..... ..Y...Erro|
00000170  72 20 4c 6f 61 64 69 6e  67 20 4f 53 00 aa 55 00  |r Loading OS..U.|
00000180  00 e9 80 fe 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 b5 dc 83 6c  25 88 00 00 00 00 80 01  |.......l%.......|
000001c0  01 00 07 fe ff ff 3f 00  00 00 82 8a a1 12 00 00  |......?.........|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

