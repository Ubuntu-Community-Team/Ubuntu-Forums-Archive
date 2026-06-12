---
title: "cannot boot.. please help"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by charly555 on 2009-11-04
i m new to ubuntu. i have ubuntu 9.10. and xp as well. at first i had 5 boot option including normal ubuntu and xp boot. at that time i had errors while booting xp but ubuntu worked fine. then i changed the boot configs in bios. then onwards only xp boots..even ubuntu option is not available.. i tried all boot config options again but cant see ubuntu in boot page. so i inserted the installation cd. there s no recovery mode. just go directly to setup??? 

what can i do to get back to ubuntu again without fresh installation.. please help???

---

### Post by ibizatunes on 2009-11-04
boot to you live ubuntu cd and reinstall grub

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

---

### Post by phillw on 2009-11-04
> **charly555 said:**
> i m new to ubuntu. i have ubuntu 9.10. and xp as well. at first i had 5 boot option including normal ubuntu and xp boot. at that time i had errors while booting xp but ubuntu worked fine. then i changed the boot configs in bios. then onwards only xp boots..even ubuntu option is not available.. i tried all boot config options again but cant see ubuntu in boot page. so i inserted the installation cd. there s no recovery mode. just go directly to setup??? 

what can i do to get back to ubuntu again without fresh installation.. please help???

Hi, I'm not sure what you did to your BIOS... But, if you're after repairing grub2 this thread may be of help.

[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

Grub2 is still pretty new to me, but the above has previously been recommended on this forum.

Hope it is of help.

Phill.

---

### Post by charly555 on 2009-11-05
i am having 2 sata hard disks.. one has a single 160 gb in which windows installed {hereinafter called A) and another 160 which is having four drives{hereinafter called B). installed ubuntu 9.10 in B.. as u adviced i reinstalled grub.. but no difference. but now i can boot ubuntu if i dont connect A to my cpu.. when i connect A and B win xp boots automatically without giving an option..

the sad part is within hours i like ubuntu very much but i cant use it now.. what should i do to use ubutnu without risking lose to my data in A and B,.... Please help me... anyone having any ideas??????  

if i need to reinstall ubutnu how should i do it in my present system??

---

### Post by kansasnoob on 2009-11-05
Don't reinstall yet.

It sounds like you can't boot Ubuntu with the Windows drive plugged in. If that's correct plug in both drives as they originally were and boot the Live CD choosing to "try without changes to disc" and from the Live Desktop run the boot info script as described here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

Then please post the results here. Using the quote tags makes it much easier for this blind old fart to read.

I can't guarantee I'll be able to get it sorted, but it's definitely worth a try.

---

### Post by ST3ALTHPSYCH0 on 2009-11-05
I think you'll need to make sure that Grub is installed to both drives.

---

### Post by charly555 on 2009-11-06
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No known boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /grub/grub.cfg /boot/grub/grub.cfg /etc/fstab 
                       /grub/core.img /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd30ed30e

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   312,560,639   312,560,577   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4b034b02

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    60,934,544    60,934,482   7 HPFS/NTFS
/dev/sdb2          60,934,545   133,114,589    72,180,045  83 Linux
/dev/sdb3         133,114,590   312,576,704   179,462,115   f W95 Ext d (LBA)
/dev/sdb5         133,114,653   215,030,024    81,915,372   7 HPFS/NTFS
/dev/sdb6         215,030,088   302,327,234    87,297,147   7 HPFS/NTFS
/dev/sdb7         302,327,298   312,576,704    10,249,407   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="F6D0D087D0D0500B" TYPE="ntfs" 
/dev/sdb1: UUID="FCD0C687D0C6479A" TYPE="ntfs" 
/dev/sdb2: UUID="45ede92a-697b-41c2-b660-60e79325ec44" TYPE="ext4" 
/dev/sdb5: UUID="B48CE8E58CE8A35A" TYPE="ntfs" 
/dev/sdb6: UUID="4AA43028A43018C1" TYPE="ntfs" 
/dev/sdb7: UUID="164C4E154C4DEFD3" LABEL="test area" TYPE="ntfs" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sdb7 on /cdrom type fuseblk (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sr0 on /media/Ubuntu 9.10 i386 type iso9660 (ro,nosuid,nodev,uhelper=devkit,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500)
/dev/sda1 on /media/F6D0D087D0D0500B type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


================================ sdb1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


============================= sdb2/grub/grub.cfg: =============================

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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=========================== sdb2/boot/grub/grub.cfg: ===========================

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
set root=(hd0,2)
search --no-floppy --fs-uuid --set 45ede92a-697b-41c2-b660-60e79325ec44
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 45ede92a-697b-41c2-b660-60e79325ec44
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=45ede92a-697b-41c2-b660-60e79325ec44 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 45ede92a-697b-41c2-b660-60e79325ec44
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=45ede92a-697b-41c2-b660-60e79325ec44 ro single 
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
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set fcd0c687d0c6479a
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=45ede92a-697b-41c2-b660-60e79325ec44 /               ext4    errors=remount-ro 0       1
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb2: Location of files loaded by Grub: ===================


  31.1GB: boot/grub/grub.cfg
  31.1GB: boot/initrd.img-2.6.31-14-generic
  31.1GB: boot/vmlinuz-2.6.31-14-generic
  31.1GB: grub/grub.cfg
  31.1GB: initrd.img
  31.1GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdb

00000000  eb 63 90 d0 bc 00 7c fb  50 07 50 1f fc be 1b 7c  |.c....|.P.P....||
00000010  bf 1b 06 50 57 b9 e5 01  f3 a4 cb bd be 07 b1 04  |...PW...........|
00000020  38 6e 00 7c 09 75 13 83  c5 10 e2 f4 cd 18 8b f5  |8n.|.u..........|
00000030  83 c6 10 49 74 19 38 2c  74 f6 a0 b5 07 b4 07 8b  |...It.8,t.......|
00000040  f0 ac 3c 00 74 fc bb 07  00 b4 0e cd 10 eb f2 88  |..<.t...........|
00000050  4e 10 e8 46 00 73 2a fe  46 10 00 80 01 00 00 00  |N..F.s*.F.......|
00000060  00 00 00 00 ff fa eb 07  f6 c2 80 75 02 b2 80 ea  |...........u....|
00000070  74 7c 00 00 31 c0 8e d8  8e d0 bc 00 20 fb a0 64  |t|..1....... ..d|
00000080  7c 3c ff 74 02 88 c2 52  be 88 7d e8 24 01 be 05  ||<.t...R..}.$...|
00000090  7c f6 c2 80 74 48 b4 41  bb aa 55 cd 13 5a 52 72  ||...tH.A..U..ZRr|
000000a0  3d 81 fb 55 aa 75 37 83  e1 01 74 32 31 c0 89 44  |=..U.u7...t21..D|
000000b0  04 40 88 44 ff 89 44 02  c7 04 10 00 66 8b 1e 5c  |.@.D..D.....f..\|
000000c0  7c 66 89 5c 08 66 8b 1e  60 7c 66 89 5c 0c c7 44  ||f.\.f..`|f.\..D|
000000d0  06 00 70 b4 42 cd 13 72  05 bb 00 70 eb 73 b4 08  |..p.B..r...p.s..|
000000e0  cd 13 73 0a f6 c2 80 0f  84 d8 00 e9 82 00 66 0f  |..s...........f.|
000000f0  b6 c6 88 64 ff 40 66 89  44 04 0f b6 d1 c1 e2 02  |...d.@f.D.......|
00000100  88 e8 88 f4 40 89 44 08  0f b6 c2 c0 e8 02 66 89  |....@.D.......f.|
00000110  04 66 a1 60 7c 66 09 c0  75 4e 66 a1 5c 7c 66 31  |.f.`|f..uNf.\|f1|
00000120  d2 66 f7 34 88 d1 31 d2  66 f7 74 04 3b 44 08 7d  |.f.4..1.f.t.;D.}|
00000130  37 fe c1 88 c5 30 c0 c1  e8 02 08 c1 88 d0 5a 88  |7....0........Z.|
00000140  c6 bb 00 70 8e c3 31 db  b8 01 02 cd 13 72 29 8c  |...p..1......r).|
00000150  c3 60 1e b9 00 01 8e db  31 f6 bf 00 80 8e c6 fc  |.`......1.......|
00000160  f3 a5 1f 61 ff 26 5a 7c  be 8e 7d e8 44 00 eb 0e  |...a.&Z|..}.D...|
00000170  be 93 7d e8 3c 00 eb 06  be 9d 7d e8 34 00 be a2  |..}.<.....}.4...|
00000180  7d e8 2e 00 cd 18 eb fe  47 52 55 42 20 00 47 65  |}.......GRUB .Ge|
00000190  6f 6d 00 48 61 72 64 20  44 69 73 6b 00 52 65 61  |om.Hard Disk.Rea|
000001a0  64 00 20 45 72 72 6f 72  0d 0a 00 bb 01 00 b4 0e  |d. Error........|
000001b0  cd 10 ac 3c 00 75 f4 c3  02 4b 03 4b 00 00 80 01  |...<.u...K.K....|
000001c0  01 00 07 fe ff ff 3f 00  00 00 52 c9 a1 03 00 fe  |......?...R.....|
000001d0  ff ff 83 fe ff ff 91 c9  a1 03 4d 61 4d 04 00 fe  |..........MaM...|
000001e0  ff ff 0f fe ff ff de 2a  ef 07 e3 5f b2 0a 00 00  |.......*..._....|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


sudo bash ~/Desktop/boot_info_script*.sh

---

### Post by charly555 on 2009-11-06
S.o.s

---

### Post by kansasnoob on 2009-11-06
I'm just about to leave the house and won't be back until late this evening.

If no one has been able to help before then I'll parse all the info and see what I can come up with.

---

### Post by charly555 on 2009-11-06
please do tat.. thank u..

---

### Post by kansasnoob on 2009-11-06
I'm really trying to get my head around this!

One thing I fear is that you may have fiddled with cables, boot order, and such since you sent that .txt!

Give me about 30 minutes and I'll try my best to explain.

---

### Post by musarraf172 on 2009-11-06
I am having a very bitter experience with ubuntu 9.10.on my IBM R51 2887 AE4 laptop.

9.04 worked flawlessly with any problem. Sound , wifi , booting time
everything was very good. But after 9.10 upgrade I had the following issue.

1. Can not boot with 2.6.31-14 kernel. The boot process does not end
while premounting local file systems.

2. Can boot with old 2.6.28-16 but synaptic touchpad does not work. It has conflict with ps2 mouse. ps2 or usb mouse is working. Sound hardware is not detected.Tried manual probing but without success.

3. Total system is jerky. Firefox stucks. Boot time is longer than 9.04..

4. If the default uspalsh theme is changed system does not boot.

5. got touchpad working by this work around : "echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe"

6. X server hangs when system is idol for a long time. If we change the console and again comeback tty7 then x is working again.

---

### Post by kansasnoob on 2009-11-07
Sorry I dozed off, but honestly the more I look at this the more confused I get!

I'm just not comfortable trying to advise you on this. If I had the computer right in front of me I'm sure I could figure it out, but in this scenario I'm just stumped.

---

### Post by quinnten83 on 2009-11-07
> **ST3ALTHPSYCH0 said:**
> I think you'll need to make sure that Grub is installed to both drives.

Or make sure you can start from drive B

---

### Post by kansasnoob on 2009-11-09
Were you able to ever resolve this?

Consider this a shameless bump;)

Sometimes thse multi-drive problems leave me boggled as you can see here:

[http://ubuntuforums.org/showthread.php?t=1318415&page=5](http://ubuntuforums.org/showthread.php?t=1318415&page=5)

I can't quite figure that one out either!

---

### Post by charly555 on 2009-11-09
prblem solved somehow... i think i copied boot.ini into my ubuntu root drive also and installed grub 2.. now its working fine... thanks for help friends... 

"i think this is a beginning of a beautiful friendship"

---

### Post by kansasnoob on 2009-11-09
Please mark this solved. 

You actually gave me an idea about another boot problem that might be worth pursuing!

---

