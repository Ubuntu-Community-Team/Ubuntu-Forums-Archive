---
title: "Ubuntu (usually) will not boot!"
date: 2011-04-09
forum: New to Ubuntu
---

### Post by joga24 on 2011-04-09
Hello! I am new to this forum and to Linux. My shiny new ThinkPad T410 came in the mail yesterday, and I would like very much to use a Linux distribution as my primary OS. So I chose Ubuntu. First off, I am amazed at how big the Ubuntu community is on this forum alone, so I hope that I can learn a lot from the more experienced folks, and working out problems with other newbies.
 
Now, on to my problem description. I have heard from many sources that Ubuntu is as easy as download, burn, and boot. Not for this guy...
 
I created a USB drive to install Ubuntu on my system. I did the 64 bit 10.10 version from the official website. I shut down Windows (thank God, it was starting to annoy me already) and booted directly from the USB drive. As far as I know, installation went perfectly fine. Soon I was operating Ubuntu off partition, downloading things, setting up my email, doing all sorts of fun stuff like that. I also installed an update package of some 300Mb+ in size. When it was done it told me I had ot restart my computer at some point, so I chose to do it right then and there, because why not?
 
So eventually that GNU GRUB screen comes on, and I choose Ubuntu. The thing doesn't boot though. It gets caught up, often after the line of code "*Checking battery state..." appears. I actually fell asleep at this point for about 4 hours, and when I woke up it nothing changed so I decided to turn my machine off. Turn it back on again, GRUB comes up, choose Ubuntu, this time I boot all the way into some text-only mode. I don't like this, so I do some command thing to reboot the computer, and screw it, I choose to go back to Windows 7 this time at the GRUB menu.
 
I then search these forums and find a thread ([http://ubuntuforums.org/showthread.php?t=1724215](http://ubuntuforums.org/showthread.php?t=1724215)) in which a Ubuntu user has a problem that has some similarities to mine. I read the advice given to the original poster by Rubi1200 and decide to follow the advice. I then shut down Windows and start running Ubuntu off my live USB stick. I download that program and excecute the command to get the boot info script file. 
 
For some reason, I try to boot in Ubuntu from my hard disk one more time before asking the forum for help. I choose Ubuntu at the GRUB menu, and lo and behold, it boots fine! I'm back in again, and this time I'm downloading software and doing all sorts of fun things. Somehow the toolbars on the top and bottom of the screen get locked up, and after strugging to fix this for a while, I just give up and decide to reboot from ctrl+alt+delete. 
 
Now the problem comes back, and once again I can not get past that text-only mode. So here I am, posting on these forms for help, using Windows 7. I tried numerous times to run Ubuntu live from my USB stick again to no avail. I get the GRUB screen every time. Consequently, I can not get that boot_info_script file that may help a more experienced user diagnose my problem. From what I remember, it was saying awful things such as "can not find display" and "can not find this driver" or "can not find that driver". 
 
One thought that came to my mind was that my machine has switchable graphics, with some NVIDIA3100m video card working in tandem with the Intel graphics. But alas I know none of the answers to my problems, and I am stuck in Windows 7. 
 
Help of any form would be greatly appreciated.

---

### Post by taseedorf on 2011-04-09
when you are in text only mode, can you do startx?

---

### Post by joga24 on 2011-04-09
This time I typed startx in the text only mode. Some notable things that popped up:
 
```
 
Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
Current Operating System: Linux (my computer name) 2.6.35-22-generic (then some other stuff)

```This was interesting to me, because in the GNU GRUB startup menu, there are two entries for Linux, as follows:
 
```
 
Ubuntu, with Linux 2.6.35-28-generic
Ubuntu, with Linux 2.6.35-28-generic (recovery mode)
Ubuntu, with Linux 2.6.35-22-generic
Ubuntu, with Linux 2.6.35-22-generic (recovery mode)

```There are also two entries for Windows 7. I don't know if this means anything, but the startup seems to lock up on 2.6.35-28 100% of the time. I can get to the text only mode in 2.6.35-22 about 50% of the time.
 
Below is another portion of the resulting text from startx:
 
```
 
(EE) No devices detected
 
Fatal Server Error:
no screens found

```skip a few lines
```
 
...check log file at "/var/log.Xorg.0.log"
ddxSigGiveUp: closing log
giving up
xinit: No such file or directory (errno 2): unable to connect to X server
xinit: No such process (errno 3): server error

```I checked out that .log file, and here are some interesting lines from that file:
 
```
 
ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers "kbd", "mouse", or "vmmouse" will be disabled
(WW) Disabling Keyboard0
(WW) Disabling Mouse0

```Then there was a line something to the nature of "(EE) No devices detected".
 
Thanks for the reply. I'm going to try to do some more digging. Any further help is appreciated.
 
 
Edit: don't know if this is helpful, but I downloaded the .iso for the 64 bit Ubuntu OS. The instructions said a 2gb USB stick is REQUIRED, but the file was only 600 something megabytes. My USB stick has a 1gb storage capacity. Even after everything was mounted, there is still almost 300 megs of free space.

I finally got it to boot live from USB, and I got the boot_info_script file from the procedure in the thread linked above.

```
     Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

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

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048     2,459,647     2,457,600   7 HPFS/NTFS
/dev/sda2           2,459,648   198,359,867   195,900,220   7 HPFS/NTFS
/dev/sda3         956,291,072   976,771,071    20,480,000   7 HPFS/NTFS
/dev/sda4         198,361,086   956,291,071   757,929,986   5 Extended
/dev/sda5         198,361,088   933,730,303   735,369,216  83 Linux
/dev/sda6         933,732,352   956,291,071    22,558,720  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1039 MB, 1039663104 bytes
256 heads, 32 sectors/track, 247 cylinders, total 2030592 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32     2,030,591     2,030,560   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        BA42D1B942D17A99                       ntfs       SYSTEM_DRV                    
/dev/sda2        3CBED474BED42862                       ntfs       Windows7_OS                   
/dev/sda3        E6A0D7D9A0D7AE75                       ntfs       Lenovo_Recovery               
/dev/sda4: PTTYPE="dos" 
/dev/sda5        6d047462-cb63-4759-819d-ce7375e991cf   ext4                                     
/dev/sda6        ac3a904f-a804-4ded-972e-7839df50063f   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        A45A-982F                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
search --no-floppy --fs-uuid --set 6d047462-cb63-4759-819d-ce7375e991cf
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 6d047462-cb63-4759-819d-ce7375e991cf
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 6d047462-cb63-4759-819d-ce7375e991cf
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=6d047462-cb63-4759-819d-ce7375e991cf ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 6d047462-cb63-4759-819d-ce7375e991cf
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=6d047462-cb63-4759-819d-ce7375e991cf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 6d047462-cb63-4759-819d-ce7375e991cf
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=6d047462-cb63-4759-819d-ce7375e991cf ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 6d047462-cb63-4759-819d-ce7375e991cf
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=6d047462-cb63-4759-819d-ce7375e991cf ro single 
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 6d047462-cb63-4759-819d-ce7375e991cf
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 6d047462-cb63-4759-819d-ce7375e991cf
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set ba42d1b942d17a99
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 3cbed474bed42862
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
UUID=6d047462-cb63-4759-819d-ce7375e991cf /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=ac3a904f-a804-4ded-972e-7839df50063f none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 312.1GB: boot/grub/core.img
 213.4GB: boot/grub/grub.cfg
 103.0GB: boot/initrd.img-2.6.35-22-generic
 103.1GB: boot/initrd.img-2.6.35-28-generic
 312.1GB: boot/vmlinuz-2.6.35-22-generic
 312.1GB: boot/vmlinuz-2.6.35-28-generic
 103.1GB: initrd.img
 103.0GB: initrd.img.old
 312.1GB: vmlinuz
 312.1GB: vmlinuz.old

=========================== sdb1/boot/grub/grub.cfg: ===========================


if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}

=================== sdb1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/grub.cfg
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 ef  |................|
000001c0  ff ff 83 ef ff ff 02 00  00 00 00 d8 d4 2b 00 ef  |.............+..|
000001d0  ff ff 05 ef ff ff 02 d8  d4 2b 00 40 58 01 00 00  |.........+.@X...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 92 10  |.X.SYSLINUX.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 20 00 00 00  |........?... ...|
00000020  e0 fb 1e 00 b7 07 00 00  00 00 00 00 02 00 00 00  |................|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 2f 98 5a a4 4e  4f 20 4e 41 4d 45 20 20  |..)/.Z.NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 1e 56  8e c1 b1 26 bf 78 7b f3  |.v{R.W.V...&.x{.|
00000070  a5 8e d9 bb 78 00 0f b4  37 0f a0 56 20 d2 78 1b  |....x...7..V .x.|
00000080  31 c0 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |1....?.G..d....||
00000090  88 4d bc 50 50 50 50 cd  13 eb 5c 8b 55 aa 8b 75  |.M.PPPP...\.U..u|
000000a0  a8 c1 ee 04 01 f2 81 fa  b7 07 73 2b f6 45 b4 7f  |..........s+.E..|
000000b0  75 25 38 4d b8 74 20 66  3d 21 47 50 54 75 10 80  |u%8M.t f=!GPTu..|
000000c0  7d b8 ed 75 0a 66 ff 75  ec 66 ff 75 e8 eb 0f 51  |}..u.f.u.f.u...Q|
000000d0  51 66 ff 75 bc eb 07 51  51 66 ff 36 1c 7c b4 08  |Qf.u...QQf.6.|..|
000000e0  cd 13 72 13 20 e4 75 0f  c1 ea 08 42 89 16 1a 7c  |..r. .u....B...||
000000f0  83 e1 3f 89 0e 18 7c fb  bb aa 55 b4 41 8a 16 74  |..?...|...U.A..t|
00000100  7b cd 13 72 10 81 fb 55  aa 75 0a f6 c1 01 74 05  |{..r...U.u....t.|
00000110  c6 06 45 7d 00 66 b8 00  20 10 00 66 ba 00 00 00  |..E}.f.. ..f....|
00000120  00 bb 00 7e e8 10 00 66  81 3e 24 7e d4 ff 73 72  |...~...f.>$~..sr|
00000130  75 76 ea 38 7e 00 00 66  03 06 60 7b 66 13 16 64  |uv.8~..f..`{f..d|
00000140  7b b9 10 00 eb 2b 66 52  66 50 06 53 6a 01 6a 10  |{....+fRfP.Sj.j.|
00000150  89 e6 66 60 b4 42 e8 7f  00 66 61 8d 64 10 72 01  |..f`.B...fa.d.r.|
00000160  c3 66 60 31 c0 e8 70 00  66 61 e2 da c6 06 45 7d  |.f`1..p.fa....E}|
00000170  2b 66 60 66 0f b7 36 18  7c 66 0f b7 3e 1a 7c 66  |+f`f..6.|f..>.|f|
00000180  f7 f6 31 c9 87 ca 66 f7  f7 66 3d ff 03 00 00 77  |..1...f..f=....w|
00000190  17 c0 e4 06 41 08 e1 88  c5 88 d6 b8 01 02 e8 37  |....A..........7|
000001a0  00 66 61 72 01 c3 e2 c9  31 f6 8e d6 bc 68 7b 8e  |.far....1....h{.|
000001b0  de 66 8f 06 78 00 be df  7d e8 09 00 31 c0 cd 16  |.f..x...}...1...|
000001c0  cd 19 f4 eb fd 66 60 ac  20 c0 74 09 b4 0e bb 07  |.....f`. .t.....|
000001d0  00 cd 10 eb f2 66 61 c3  8a 16 74 7b cd 13 c3 42  |.....fa...t{...B|
000001e0  6f 6f 74 20 65 72 72 6f  72 0d 0a 00 00 00 00 00  |oot error.......|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by joga24 on 2011-04-10
After reading that installing 10.10 from a USB storage device is NOT preferable, I mounted the .iso file to a CD-R and re-installed. Things went much smoother this time. After setting up the partitions, I booted between Windows and Ubuntu a couple times just to make sure both were working properly. For now, everything is good. For whatever reason, using a CD worked a whole better than a USB storage device for 10.10.

---

### Post by idoitprone on 2011-04-10
> **joga24 said:**
> After reading that installing 10.10 from a USB storage device is NOT preferable, I mounted the .iso file to a CD-R and re-installed. Things went much smoother this time. After setting up the partitions, I booted between Windows and Ubuntu a couple times just to make sure both were working properly. For now, everything is good. For whatever reason, using a CD worked a whole better than a USB storage device for 10.10.

i am interested, what did you use to make the live usb. Unetbooting always works for me and i kidda had to use it since this is a netbook after all.

---

### Post by joga24 on 2011-04-13
I made the live USB with [www.pendrivelinux.com](www.pendrivelinux.com).

---

### Post by K_45 on 2011-04-13
That part that is checking battery state; when you created the pen drive, did you make it persistent, so it could save files?

---

