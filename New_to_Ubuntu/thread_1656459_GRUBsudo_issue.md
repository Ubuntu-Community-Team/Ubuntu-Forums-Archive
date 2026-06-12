---
title: "GRUB/sudo issue"
date: 2010-12-30
forum: New to Ubuntu
---

### Post by Sebrithil on 2010-12-30
Ok so I'm pretty new to the world of computers especially Linux, and am in need of some assistance. I've been doing some research and cant quite seem to figure how to get GRUB installed on my machine. So let me give you a run down of what's happened thus far. I have a 250g HD partitioned into about halves. Windows Vista on one, and Ubuntu on the other all installed and ready to go. However when I boot my computer it boots Vista, I can boot Ubuntu from my live pendrive. so I load live Ubuntu and open a terminal to try and install Grub.  My issue lies in when i type:
ubuntu@ubuntu:~$ sudo grub = sudo: grub: command not found

now some information that may help you advance users decipher my problem: 

ubuntu@ubuntu:~$ grub-install -v = grub-install (GRUB) 1.98+20100804-5ubuntu3

ubuntu@ubuntu:~$ which sudo = /usr/bin/sudo

ubuntu@ubuntu:~$ echo $PATH = /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

Any help on this would be greatly appreciated!

---

### Post by presence1960 on 2010-12-30
stop typing those commands and do this. We need to see your setup & boot process , then we can hopefully give you the correct commands to install GRUB, which BTW should have been placed on the MBR when you installed ubuntu.

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by Sebrithil on 2010-12-30
Alright I've done as directed and thank you for taking a look at this.

```
 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => HP/Gateway is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 337900815 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   266,662,934   266,662,872   7 HPFS/NTFS
/dev/sda2         266,662,935   471,090,059   204,427,125  83 Linux
/dev/sda3         471,090,060   488,392,064    17,302,005   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7856127 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             38     7,839,719     7,839,682   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        01CBA5EFB21860E0                       ntfs                                     
/dev/sda2        b1a16a2f-77c4-4746-a9a1-19295c403936   ext2                                     
/dev/sda3        2C88743C8874071C                       ntfs       HP_RECOVERY                   
/dev/sda: PTTYPE=&quot;dos&quot; 
/dev/sdb1        9003-250F                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE=&quot;dos&quot; 

============================ &quot;mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/b1a16a2f-77c4-4746-a9a1-19295c403936 ext2       (rw,nosuid,nodev,uhelper=udisks)


=========================== sda2/boot/grub/grub.cfg: ===========================

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
set default=&quot;0&quot;
if [ &quot;${prev_saved_entry}&quot; ]; then
  set saved_entry=&quot;${prev_saved_entry}&quot;
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z &quot;${boot_once}&quot; ]; then
    saved_entry=&quot;${chosen}&quot;
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n &quot;${have_grubenv}&quot; ]; then if [ -z &quot;${boot_once}&quot; ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set b1a16a2f-77c4-4746-a9a1-19295c403936
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set b1a16a2f-77c4-4746-a9a1-19295c403936
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ &quot;${recordfail}&quot; = 1 ]; then
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
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set b1a16a2f-77c4-4746-a9a1-19295c403936
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=b1a16a2f-77c4-4746-a9a1-19295c403936 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set b1a16a2f-77c4-4746-a9a1-19295c403936
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=b1a16a2f-77c4-4746-a9a1-19295c403936 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry &quot;Memory test (memtest86+)&quot; {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set b1a16a2f-77c4-4746-a9a1-19295c403936
    linux16    /boot/memtest86+.bin
}
menuentry &quot;Memory test (memtest86+, serial console 115200)&quot; {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set b1a16a2f-77c4-4746-a9a1-19295c403936
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry &quot;Windows Vista (loader) (on /dev/sda1)&quot; {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 01cba5efb21860e0
    chainloader +1
}
menuentry &quot;Windows Vista (loader) (on /dev/sda3)&quot; {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 2c88743c8874071c
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

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda2       /               ext2    errors=remount-ro 0       1

=================== sda2: Location of files loaded by Grub: ===================


 173.0GB: boot/grub/core.img
 172.9GB: boot/grub/grub.cfg
 172.8GB: boot/initrd.img-2.6.35-22-generic
 172.7GB: boot/vmlinuz-2.6.35-22-generic
 172.8GB: initrd.img
 172.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 40 20 00  |.X.SYSLINUX..@ .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 26 00 00 00  |........?...&...|
00000020  c2 9f 77 00 bd 03 00 00  00 00 00 00 02 00 00 00  |..w.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 0f 25 03 90 4e  4f 20 4e 41 4d 45 20 20  |..).%..NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 da 07 00 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by presence1960 on 2010-12-30
boot the Ubuntu Live Cd/USB, choose "try ubuntu without any changes". When the desktop loads open a terminal and run ```
sudo mount /dev/sda2 /mnt
```This will mount your ubuntu / partition.

Next in terminal run ```
sudo grub-install --root-directory=/mnt/ /dev/sda
```When completed GRUB will be on the MBR of your hard disk. You can then reboot without the Ubuntu live CD/USB and you should be good to go. Please note you will have 2 windows entries. The entry on sda1 is your windows OS and the entry for sda3 is your Recovery Partition.

P.S. here is a good [link]("https://help.ubuntu.com/community/Grub2") about GRUB2, which is very, very different from Legacy GRUB.

---

### Post by Sebrithil on 2010-12-31
Look's like every thing's working properly. Thank you very much for the help. I am happy to be trying Linux and hopefully some Bash-scripting next.

---

### Post by presence1960 on 2010-12-31
> **Sebrithil said:**
> Look's like every thing's working properly. Thank you very much for the help. I am happy to be trying Linux and hopefully some Bash-scripting next.

You are welcome. Enjoy Ubuntu!

---

