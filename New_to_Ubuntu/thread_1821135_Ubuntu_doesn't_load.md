---
title: "Ubuntu doesn't load?"
date: 2011-08-08
forum: New to Ubuntu
---

### Post by Soren470 on 2011-08-08
Okay. When I try to boot up ubuntu all I get is a black screen. From what I have read this just means that I don't have GRUB installed. I have tried doing things posted on other threads but either their commands are "not found" or other stuff. I just want to be able to use Ubuntu on my crappy old dell pc rather than windows...it runs faster and I like it. If someone could explain what I need to do in the simplest terms possible I would be very appreciative.

Fyi I just replaced Windows XP with Ubuntu 11.04 completely. Never installed GRUB unless that is supposed to happen automatically, which probably explains Ubuntu not loading.

---

### Post by retchid on 2011-08-08
try open suse instead a much more stable experience
got sick of Ubuntu crashing the grub and locking up the ssd on acer one netbook
slicker and faster than ubuntu available on dvd and live usb (although need to update on the usb as only 600mb rather than 4gb) 

I give up fighting my computer every weekend since installing opensuse (on HP desktop duel boot with win7, Sony Vio laptop, Acer One Netbook 16 gb SSD version) - it now just does what I want it to when I want it to rather than boot not found screens (ubuntu experience now as bad as windows and it is soooooooo sloooow.


PS Install KDE not Gnome version 32bit and 64bit available

---

### Post by amjjawad on 2011-08-08
> **Soren470 said:**
> Okay. When I try to boot up ubuntu all I get is a black screen. From what I have read this just means that I don't have GRUB installed. I have tried doing things posted on other threads but either their commands are "not found" or other stuff. I just want to be able to use Ubuntu on my crappy old dell pc rather than windows...it runs faster and I like it. If someone could explain what I need to do in the simplest terms possible I would be very appreciative.

Fyi I just replaced Windows XP with Ubuntu 11.04 completely. Never installed GRUB unless that is supposed to happen automatically, which probably explains Ubuntu not loading.

GRUB2 should be installed automatically unless otherwise (you changed something while installing).

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Please read the steps in the above link carefully and do exactly as explained in that link.

---

### Post by Soren470 on 2011-08-08
> **amjjawad said:**
> GRUB2 should be installed automatically unless otherwise (you changed something while installing).

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Please read the steps in the above link carefully and do exactly as explained in that link.

Here are the RESULTS.txt file:

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.02 debian-20101016 ...........>...r>.......XD.....0...~.k...~...f...M.f.f....f..8~....>2}
    Boot sector info:   Syslinux looks at sector 1410776 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. According 
                       to the info in the boot sector, sdb1 starts at sector 
                       0. But according to the info from fdisk, sdb1 starts 
                       at sector 62.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   153,108,479   153,106,432  83 Linux
/dev/sda2         153,110,526   156,248,063     3,137,538   5 Extended
/dev/sda5         153,110,528   156,248,063     3,137,536  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2004 MB, 2004877312 bytes
62 heads, 62 sectors/track, 1018 cylinders, total 3915776 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             62     3,913,191     3,913,130   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        3350efb6-c60f-489f-97d8-69784f989c95   ext4       
/dev/sdb1        7281-CB16                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 3350efb6-c60f-489f-97d8-69784f989c95
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 3350efb6-c60f-489f-97d8-69784f989c95
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 3350efb6-c60f-489f-97d8-69784f989c95
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=3350efb6-c60f-489f-97d8-69784f989c95 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 3350efb6-c60f-489f-97d8-69784f989c95
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=3350efb6-c60f-489f-97d8-69784f989c95 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 3350efb6-c60f-489f-97d8-69784f989c95
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=3350efb6-c60f-489f-97d8-69784f989c95 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 3350efb6-c60f-489f-97d8-69784f989c95
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=3350efb6-c60f-489f-97d8-69784f989c95 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 3350efb6-c60f-489f-97d8-69784f989c95
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 3350efb6-c60f-489f-97d8-69784f989c95
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
#UUID=54637e46-86b7-45b6-a72f-9d393e504d88 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   2.135009766 = 2.292449280    boot/grub/core.img                             1
  32.246467590 = 34.624380928   boot/grub/grub.cfg                             1
   1.684570312 = 1.808793600    boot/initrd.img-2.6.38-10-generic              2
   1.062534332 = 1.140887552    boot/initrd.img-2.6.38-8-generic               2
   0.950504303 = 1.020596224    boot/vmlinuz-2.6.38-10-generic                 1
   2.133281708 = 2.290593792    boot/vmlinuz-2.6.38-8-generic                  1
   1.684570312 = 1.808793600    initrd.img                                     2
   1.062534332 = 1.140887552    initrd.img.old                                 2
   0.950504303 = 1.020596224    vmlinuz                                        1
   2.133281708 = 2.290593792    vmlinuz.old                                    1

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  10 2b c8 83 f9 04 0f 8c  a3 00 00 80 21 33 c9 03  |.+..........!3..|
00000010  00 80 c2 33 d2 8a 28 8a  50 02 8a 48 01 c1 e1 08  |...3..(.P..H....|
00000020  0b 60 6d a8 22 8a 50 03  a2 9e 8b 10 8e 24 40 11  |.`m.".P......$@.|
00000030  d8 c1 26 7c 24 70 e2 39  0b 9a 01 00 a5 39 8b e8  |..&|$p.9.....9..|
00000040  8b 41 10 03 c5 3b c3 7d  52 8b c7 99 83 02 41 e2  |.A...;.}R.....A.|
00000050  41 ec 56 10 c1 f8 03 03  20 77 0c 3b c2 7f 3b 91  |A.V..... w.;..;.|
00000060  c9 39 41 8c 60 4c dd 24  02 8b d7 01 88 80 e2 01  |.9A.`L.$........|
00000070  80 d4 d1 46 f7 da 42 c0  98 1d 7a a1 4a 94 82 38  |...F..B...z.J..8|
00000080  d0 ad 63 43 8b ea e9 53  50 79 8b 43 c3 e1 39 a4  |..cC...SPy.C..9.|
00000090  e1 50 79 ff 74 86 e8 3d  c3 26 10 83 f8 b0 41 d0  |.Py.t..=.&....A.|
000000a0  f0 e8 f8 10 d0 e0 e1 20  83 c4 08 11 e9 46 62 89  |....... .....Fb.|
000000b0  01 00 b2 fe 8b 56 10 90  2e 2b ca e0 ce 06 8b c1  |.....V...+......|
000000c0  30 01 71 1e 1c 4a 4d 51  83 f8 50 e0 11 03 c2 f0  |0.q..JMQ..P.....|
000000d0  70 79 13 d0 2c 80 eb 10  e9 84 a7 00 00 01 00 80  |py..,...........|
000000e0  46 10 eb 32 85 c0 74 0e  3d ff ff 00 41 7e 70 61  |F..2..t.=...A~pa|
000000f0  ee 00 1a 41 7f 69 85 c9  7e 7d 55 57 00 bf d6 70  |...A.i..~}UW...p|
00000100  49 db 2d f8 89 7c e0 ff  24 10 85 ed 0f 59 5c 00  |I.-..|..$....Y\.|
00000110  00 00 00 00 00 8f e1 fd  ff ff eb 66 8b 96 14 20  |...........f... |
00000120  00 00 52 eb 55 04 01 8b  86 21 a0 50 eb 4c 8b 8e  |..R.U....!.P.L..|
00000130  21 a0 51 e8 8b 03 00 00  83 00 00 c4 04 85 ff 74  |!.Q............t|
00000140  41 8b 5c 24 14 8b cd 2b  cb 8b d1 00 00 33 c0 c1  |A.\$...+.....3..|
00000150  e9 02 f3 ab 8b ca 83 e1  03 f3 aa eb 27 81 40 64  |............'.@d|
00000160  00 e8 8e 01 00 00 c7 72  ca 00 00 00 00 eb 0c 85  |.......r........|
00000170  f8 46 01 30 13 d0 8b 4c  24 78 5f 5e 5d 5b 64 89  |.F.0...L$x_^][d.|
00000180  0d 00 00 e0 a8 74 c2 20  00 08 00 90 90 90 d8 c7  |.....t. ........|
00000190  56 8b 74 24 08 85 f6 75  07 b8 01 81 50 f0 c0 5e  |V.t$...u....P..^|
000001a0  c3 8b 44 24 18 10 d9 14  8b 54 24 10 50 e0 e1 40  |..D$.....T$.P..@|
000001b0  00 10 51 52 50 e8 17 00  00 83 c4 10 89 06 00 fe  |..QRP...........|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 e0 2f 00 00 00  |............/...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

Thanks!

---

### Post by wildmanne39 on 2011-08-08
Hi, from what I see your boot information for ubuntu looks good.


Did this problem only occur after you ran updates on your system?

---

### Post by Soren470 on 2011-08-08
> **wildmanne39 said:**
> Hi, from what I see your boot information for ubuntu looks good.


Did this problem only occur after you ran updates on your system?

I can't say that it has only happened after updating because both times I've installed it I ran the updater and downloaded/installed the updates...but yes, this has happened after running updates. Should I reinstall and ignore the updates and/or a certain update?

Here's a little more info on what I've done:

Installed Ubuntu and shortly thereafter updated. It would restart to complete and it would restart ok, but will not boot back up after shutdown. But then again I have never tried to shut it down and reboot without installing updates so...yeah.

---

### Post by wildmanne39 on 2011-08-08
Hi, when you boot your system hold down the shift key and if you get the grub menu choose to boot with this kernel **2.6.38-8-generic 2** and see if you can boot then.

---

### Post by Soren470 on 2011-08-08
Holding shift gave me the grub menu. Clicking on previous Linux version gave me the option to boot using 2.6.38-8-generic. There was no "2" after it. It is doing what it did before...it gives you the slightly brownish/tan color of booting Ubuntu and then switches to a black screen.

---

### Post by Soren470 on 2011-08-08
Woah....umm...well I tried rebooting again...I hit shift...it was about to show the grub menu and then it decided not to and booted into Ubuntu....apparently it decided to work at least once...

---

### Post by wildmanne39 on 2011-08-08
Hi, it sounds like you should try nomodeset.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by Soren470 on 2011-08-08
> **wildmanne39 said:**
> Hi, it sounds like you should try nomodeset.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Hmm. That thread says that after installing Nvidia's proprietary drivers you should be okay. I did that because it prompted me to after I installed the updates.

---

### Post by wildmanne39 on 2011-08-08
Hi, which driver did you install and what card do you have?

---

### Post by Soren470 on 2011-08-08
It is a Nvidia GeForce FX 5200...I just searched for additional drivers and apparently I downloaded Nvidia's driver but did not activate it...this is most likely the problem...also...how do I activate it? XD

---

### Post by Soren470 on 2011-08-08
Dammit. apparently it is activated but it says it is "not in use"...

---

### Post by Soren470 on 2011-08-08
Fyi I installed the Nvidia accelerated graphics driver version 173...the one ubuntu recommended.

---

### Post by wildmanne39 on 2011-08-08
Hi, that is the one I use and it works great, but my card is 6150. 

That is just a bug that says it is active and not in use, it really is if you have seen the unity desktop. 

I will research and see what I can find on your card, with it being older it may not be will supported in 11.04.

---

### Post by Soren470 on 2011-08-08
Thank you so much for your help! It is greatly appreciated.

---

### Post by wildmanne39 on 2011-08-08
Hi, here is what I found, you should try the nouveau driver, it should be labelled 'experimental 3d' The graphics may not be as good but it should fix the boot issue, if it is caused by the driver.

---

### Post by madjr on 2011-08-08
> **wildmanne39 said:**
> Hi, here is what I found, you should try the nouveau driver, it should be labelled 'experimental 3d' The graphics may not be as good but it should fix the boot issue, if it is caused by the driver.

yes, i think i read somewhere that nvidia is not supporting the 5200 anymore officially, because is very old card (not totally sure, you may need to look that up).

but the unofficial open source driver is supporting it, so yes, use the nouveau driver for now.

---

