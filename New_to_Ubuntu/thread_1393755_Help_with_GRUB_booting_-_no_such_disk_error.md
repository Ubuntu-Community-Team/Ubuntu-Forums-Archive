---
title: "Help with GRUB booting - no such disk error"
date: 2010-01-29
forum: New to Ubuntu
---

### Post by Jamie_42 on 2010-01-29
Hi,
I installed Ubuntu v.9.1 on an external USB HDD to test out the OS, and GRUB was installed along with it. With my external HDD connected, GRUB loads and prompts me to boot Ubuntu (on the external) or Windows Vista (on my primary HDD, connected via SATA 0). However, if I turn on my computer with the external HDD disconnected, GRUB still tries to load, and returns an unresponsive grub recover prompt (error: no such disk).

At the time I installed Ubuntu, My removable HDD was 1st in my Boot Priority (I assumed the BIOS could boot Ubuntu from the external HDD, just like windows). When I was through testing Ubuntu and ready to put away my external HDD for a while, I changed my boot priority to make my primary HDD (and thus Windows OS) first.

My CURRENT boot priority is 1. Primary (Windows Vista 64 bit, SATA 0) 2. Removable (Ubuntu 9,1, USB) 3. CD-ROM

I'm confused as to why GRUB would even try to load if it is affiliated with the removable HDD, since the removable is second in my boot priorities. If GRUB is not dependent on my external HDD, I am confused as to why it fails to boot windows or give me the option to boot windows. My primary HDD had nothing to do with my installation of Ubuntu or GRUB.

I have read the instructions on installing GRUB, and am worried I will make my primary drive unbootable if I try. I have read the help archives and manual as well, but couldn't make sense of any troubleshooting within. I'm fairly tech-savvy for a normal user, but everything I read was way over my head.

Please help if anyone can. I can provide additional information if required. I'm unable to boot my computer without my external HDD connected, and if the external fails in some way my computer will be unusable.

Thank you for your time,
Jamie

---

### Post by pizza-is-good on 2010-01-29
OK,

Here is what I think. Grub is installed on your external, since that is where you installed Ubuntu. When the external is unplugged, your bios tries to find a boot-loader since it knows that there is one, but can't find it.

Will grub load when the external is plugged in? If so, then that proves what I said above.
Let me know ASAP. We can go from there.

~pizza

EDIT:  OK, I skipped through the part in your post where you said that it did work with the external plugged in. Sorry.
That confirms my reasoning that I stated above. Not sure that it is exactly that way, but for sure there is a part of grub or info for grub that is located in both HDDs.

It might be tricky to fix it up. 
I would install Ubuntu in your internal HDD. Then you can work without your external.
Anyway, let me know what you want to do, and I'll try to help you out.

~pizza

---

### Post by kansasnoob on 2010-01-29
> **Jamie_42 said:**
> Hi,
I installed Ubuntu v.9.1 on an external USB HDD to test out the OS, and GRUB was installed along with it. With my external HDD connected, GRUB loads and prompts me to boot Ubuntu (on the external) or Windows Vista (on my primary HDD, connected via SATA 0). However, if I turn on my computer with the external HDD disconnected, GRUB still tries to load, and returns an unresponsive grub recover prompt (error: no such disk).

At the time I installed Ubuntu, My removable HDD was 1st in my Boot Priority (I assumed the BIOS could boot Ubuntu from the external HDD, just like windows). When I was through testing Ubuntu and ready to put away my external HDD for a while, I changed my boot priority to make my primary HDD (and thus Windows OS) first.

My CURRENT boot priority is 1. Primary (Windows Vista 64 bit, SATA 0) 2. Removable (Ubuntu 9,1, USB) 3. CD-ROM

I'm confused as to why GRUB would even try to load if it is affiliated with the removable HDD, since the removable is second in my boot priorities. If GRUB is not dependent on my external HDD, I am confused as to why it fails to boot windows or give me the option to boot windows. My primary HDD had nothing to do with my installation of Ubuntu or GRUB.

I have read the instructions on installing GRUB, and am worried I will make my primary drive unbootable if I try. I have read the help archives and manual as well, but couldn't make sense of any troubleshooting within. I'm fairly tech-savvy for a normal user, but everything I read was way over my head.

Please help if anyone can. I can provide additional information if required. I'm unable to boot my computer without my external HDD connected, and if the external fails in some way my computer will be unusable.

Thank you for your time,
Jamie

That should be fairly easy to fix, but I'd like to see the results of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Jamie_42 on 2010-01-29
Thanks Pizza and Kansasnoob for your replies.
Pizza, I had though of that installing Ubuntu on my primary HDD too and as a final solution, I also believe it would work. I just wish there was a way I could install GRUB on my primary HDD while being sure I wasn't bricking my primary HDD...and without needlessly partitioning my drive. But if worse comes to worse it would be nice to have Ubuntu in a more native environment.

Kansasnoob, here are the results of my boot info script. The results are what I expected after reading about how GRUB works from their website - it looks like the GRUB boot loader has replaced whatever loader Windows was using, so my BIOS tries to load GRUB, which is located on my external - which is possibly why it doesn't work when the external isn't connected. This is all just an educated guess though, so hopefully you'll see something I'm missing....hope this pastes correctly:

```
============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=4649a1f3-8dfe-42d3-acf1-065c64af5fb0)/boot/grub.
 => No known boot loader is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0a70b1f5

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   976,771,071   976,769,024   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8b774678

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    74,846,834    74,846,772  83 Linux
/dev/sdb2          74,846,835    78,140,159     3,293,325   5 Extended
/dev/sdb5          74,846,898    78,140,159     3,293,262  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        ECE01B33E01B040C                       ntfs                                     
/dev/sdb1        4649a1f3-8dfe-42d3-acf1-065c64af5fb0   ext4                                     
/dev/sdb5        d4a2f576-4e75-457c-a183-653575c6e76c   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root=(hd1,1)
search --no-floppy --fs-uuid --set 4649a1f3-8dfe-42d3-acf1-065c64af5fb0
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
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 4649a1f3-8dfe-42d3-acf1-065c64af5fb0
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=4649a1f3-8dfe-42d3-acf1-065c64af5fb0 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 4649a1f3-8dfe-42d3-acf1-065c64af5fb0
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=4649a1f3-8dfe-42d3-acf1-065c64af5fb0 ro single 
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 4649a1f3-8dfe-42d3-acf1-065c64af5fb0
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=4649a1f3-8dfe-42d3-acf1-065c64af5fb0 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 4649a1f3-8dfe-42d3-acf1-065c64af5fb0
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=4649a1f3-8dfe-42d3-acf1-065c64af5fb0 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set ece01b33e01b040c
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=4649a1f3-8dfe-42d3-acf1-065c64af5fb0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=d4a2f576-4e75-457c-a183-653575c6e76c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdb

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
000001b0  00 00 00 00 00 00 00 00  78 46 77 8b 00 00 00 01  |........xFw.....|
000001c0  01 00 83 fe ff ff 3f 00  00 00 34 12 76 04 00 fe  |......?...4.v...|
000001d0  ff ff 05 fe ff ff 73 12  76 04 8d 40 32 00 00 00  |......s.v..@2...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf sdg 
```This is the boot info I get while booting with my external HDD connected, with my boot priorities the same as in my original post. I'm currently working from Ubuntu :)

---

### Post by kansasnoob on 2010-01-29
OK you need to boot into Ubuntu and run the following commands (note: we're only using Lilo as a tool so we do want to remove it when done):

```
sudo apt-get install lilo
```

Ignore the warning and just hit enter.

```
sudo lilo -M /dev/sda mbr
```

```
sudo apt-get remove lilo
```

```
sudo grub-install /dev/sdb
```

That should be it, but just FYI there should be no need to keep switching boot order. I always have mine set to boot CD 1st, USB 2nd, and hard drive 3rd. Unless it "sees" something bootable in the CD or USB then it should go on to the hard drive.

---

### Post by Jamie_42 on 2010-01-29
That worked perfectly. I was able to reboot with my external HDD disconnected after following those steps. 
That was AMAZING! Thank you so much! :D

---

### Post by pizza-is-good on 2010-01-29
Glad you got it working. I feel like newbie:lolflag:, but then again, I will always be in some sense.


Happy Ubunting

~pizza

---

