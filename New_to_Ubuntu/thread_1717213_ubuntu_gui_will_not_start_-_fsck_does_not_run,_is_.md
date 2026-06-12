---
title: "ubuntu gui will not start - fsck does not run, is it a partition issue?"
date: 2011-03-29
forum: New to Ubuntu
---

### Post by Velenjak on 2011-03-29
running ubuntu 10.10, dual booted with windows 7

this system worked fine for around a month, but i shutdown ubuntu manually at one point (it froze on the shutdown process) and ubuntu would not work properly after that.

 ubuntu will not run the gui. when it boots, it loads in a command prompt setting.

windows 7 is given 90 GB, and is labeled as NTFS
ubuntu 10.10 is given 63 GB, and is labeled ext2


when i type fsck into the command prompt while inside ubuntu installation cd, i get the message

fsck from util-linux-ng 2.17.2

what should I do? thanks.

---

### Post by cariboo on 2011-03-29
What command do you use when you try to run fsck?

---

### Post by Velenjak on 2011-03-29
ive tried 

fsck

sudo fsck

sudo fsck /dev/sda1

sudo fsck.aufs





these are the results of df if that helps


Filesystem           1K-blocks      Used Available Use% Mounted on
aufs                   1677144     47416   1629728   3% /
udev                   1677144       264   1676880   1% /dev
/dev/sr0                706532    706532         0 100% /cdrom
/dev/loop0              684032    684032         0 100% /rofs
none                   1677144       188   1676956   1% /dev/shm
tmpfs                  1677144        24   1677120   1% /tmp
none                   1677144        92   1677052   1% /var/run
none                   1677144         0   1677144   0% /var/lock
none                   1677144         0   1677144   0% /lib/init/rw

---

### Post by Velenjak on 2011-03-29
anyone know a way around this?

---

### Post by collisionystm on 2011-03-29
at the command prompt type, /etc/init.d/gdm start 

does your gui load?

---

### Post by Velenjak on 2011-03-30
> **collisionystm said:**
> at the command prompt type, /etc/init.d/gdm start 

does your gui load?

i get the message


rather than invoking init scripts through /etc/init.d, use the service(8) utility, e,g, service gdm start

since the script you are attempting to invoke has been converted to an upstart job, you may also use the start(8) utility, e.g. start gdm 
gdm start/running, process 793



when i entered      start gdm 

unable to connect to system bus: failed to connect to socket /var/run/dbus/system_bus_socket

---

### Post by collisionystm on 2011-03-30
It could be a permissions problem with the dbus folder.

in the command prompt type, cd /var/run/dbus

in the directory type ls -lh         < that is a lowercase L and H

here is what mine says, srwxrwxrwx 1 root root 0 2011-03-29 19:50 system_bus_socket

---

### Post by Velenjak on 2011-03-30
> **collisionystm said:**
> It could be a permissions problem with the dbus folder.

in the command prompt type, cd /var/run/dbus

in the directory type ls -lh         < that is a lowercase L and H

here is what mine says, srwxrwxrwx 1 root root 0 2011-03-29 19:50 system_bus_socket

i simply get 


"total 0"

---

### Post by collisionystm on 2011-03-30
okay. so we will just make the file

type, vi /var/run/dbus/system_bus_socket

you should be in a text editor

type :w!  press enter

shift + z + z  ( press z z while holding shift)

if you are still in the dbus folder you can just do ls

make sure the file is there

now do chmod 777 system_bus_socket

---

### Post by collisionystm on 2011-03-30
I opended the file on my computer and it is empty, so i think it is just there as a 'scratchpad'  for another proccess to read the config another one dumps. Once the file is made just restart your computer and see what happens

---

### Post by Velenjak on 2011-03-30
> **collisionystm said:**
> okay. so we will just make the file

type, vi /var/run/dbus/system_bus_socket

you should be in a text editor

type :w!  press enter

shift + z + z  ( press z z while holding shift)

if you are still in the dbus folder you can just do ls

make sure the file is there

now do chmod 777 system_bus_socket

when i enter :w! into the text editor i get

/var/run/dbus/system_bus_socket E212: Can't open file for writing

---

### Post by collisionystm on 2011-03-30
okay do this revised with sudo



type, 
cd /var/run/dbus/
sudo vi system_bus_socket

you should be in a text editor

type :w!  press enter

shift + z + z  ( press z z while holding shift)

type ls
make sure the file is there

now do chmod 777 system_bus_socket

type ls -lh

make sure your permissions match what mine.... rwxrwxrwx

---

### Post by Velenjak on 2011-03-30
> **collisionystm said:**
> okay do this revised with sudo



type, 
cd /var/run/dbus/
sudo vi system_bus_socket

you should be in a text editor

type :w!  press enter

shift + z + z  ( press z z while holding shift)

type ls
make sure the file is there

now do chmod 777 system_bus_socket

type ls -lh

make sure your permissions match what mine.... rwxrwxrwx

when i write :w! i get
[new file] 0 lines, 0 characters written

when i type ls i get
system_bus_socket

when i type chmod 777 system_bus_socket i get
chmod: changing permissions of 'system_bus_socket": Operation not permitted

when i check ls -lh    our permissions are the same -rwxrwxrwx 1 root


upon reboot, gui still doesnt load.

---

### Post by collisionystm on 2011-03-30
well atleast the file is there now instead of empty.

when you run /etc/init.d/gdm start

do you recieve the same error as before?

---

### Post by Velenjak on 2011-03-30
> **collisionystm said:**
> well atleast the file is there now instead of empty.

when you run /etc/init.d/gdm start

do you recieve the same error as before?

i still get the same error message =/

---

### Post by collisionystm on 2011-03-30
Hm. I am not sure what to do at the moment. I need to wake up in 5 hours for work, so I will get on tomorrow and help if you have not fixed it yet!

---

### Post by Velenjak on 2011-03-30
> **collisionystm said:**
> Hm. I am not sure what to do at the moment. I need to wake up in 5 hours for work, so I will get on tomorrow and help if you have not fixed it yet!

It's all good, thank you for your help!

---

### Post by Hedgehog1 on 2011-03-30
> **Velenjak said:**
> this system worked fine for around a month, but i shutdown ubuntu manually at one point (it froze on the shutdown process) and ubuntu would not work properly after that.

Velenjak,

If you are still up and about...

Please boot off the LiveCD/LiveUSB, select TRY, and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.


***The Hedge***

:KS

---

### Post by Velenjak on 2011-03-30
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for (,msdos4)/boot/grub.

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
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xeb275b50

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   176,842,751   176,635,904   7 HPFS/NTFS
/dev/sda3         299,724,766   312,496,379    12,771,614   5 Extended
/dev/sda5         299,724,768   312,496,379    12,771,612  82 Linux swap / Solaris
/dev/sda4         176,842,752   299,722,751   122,880,000  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        6480F1BF80F1982E                       ntfs       System Reserved               
/dev/sda2        14EAF6BEEAF69B66                       ntfs                                     
/dev/sda4        3f855ce6-e878-4689-a149-50b1d3aa46c9   ext2                                     
/dev/sda5        c058745c-98c5-4f84-8ce6-bc5dc6155154   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


=========================== sda4/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set 3f855ce6-e878-4689-a149-50b1d3aa46c9
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set 3f855ce6-e878-4689-a149-50b1d3aa46c9
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 3f855ce6-e878-4689-a149-50b1d3aa46c9
    linux    /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=3f855ce6-e878-4689-a149-50b1d3aa46c9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 3f855ce6-e878-4689-a149-50b1d3aa46c9
    echo    'Loading Linux 2.6.35-28-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=3f855ce6-e878-4689-a149-50b1d3aa46c9 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 3f855ce6-e878-4689-a149-50b1d3aa46c9
    linux    /boot/vmlinuz-2.6.35-27-generic-pae root=UUID=3f855ce6-e878-4689-a149-50b1d3aa46c9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-27-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 3f855ce6-e878-4689-a149-50b1d3aa46c9
    echo    'Loading Linux 2.6.35-27-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-27-generic-pae root=UUID=3f855ce6-e878-4689-a149-50b1d3aa46c9 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-27-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 3f855ce6-e878-4689-a149-50b1d3aa46c9
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 3f855ce6-e878-4689-a149-50b1d3aa46c9
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 6480f1bf80f1982e
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

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda4       /               ext2    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=c058745c-98c5-4f84-8ce6-bc5dc6155154 none            swap    sw              0       0

=================== sda4: Location of files loaded by Grub: ===================


 128.8GB: boot/grub/core.img
 128.8GB: boot/grub/grub.cfg
 128.7GB: boot/initrd.img-2.6.35-27-generic-pae
 128.7GB: boot/initrd.img-2.6.35-28-generic-pae
 128.7GB: boot/vmlinuz-2.6.35-27-generic-pae
 128.7GB: boot/vmlinuz-2.6.35-28-generic-pae
 128.7GB: initrd.img
 128.7GB: initrd.img.old
 128.7GB: vmlinuz
 128.7GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  c5 c7 06 2c 81 94 36 59  54 9e 6a c3 ce ed 5a ec  |...,..6YT.j...Z.|
00000010  6e 53 dc 62 13 b7 fe 39  85 8c 64 bf 6f 43 4b 0b  |nS.b...9..d.oCK.|
00000020  27 72 01 a2 47 66 d1 1c  9c b4 fc 61 12 a9 88 40  |'r..Gf.....a...@|
00000030  c6 1c 11 98 30 04 2c 62  00 81 d7 b8 f0 38 a0 ae  |....0.,b.....8..|
00000040  59 92 cf 96 74 23 48 56  69 1b 29 67 68 48 08 74  |Y...t#HVi.)ghH.t|
00000050  9d 8b b0 d4 86 4b 57 59  31 14 83 18 6e e3 51 53  |.....KWY1...n.QS|
00000060  15 35 8c a8 33 b2 d6 d4  1e 24 a9 61 f5 f3 d8 95  |.5..3....$.a....|
00000070  88 17 ad 67 22 9d ba 04  f4 a4 16 a6 b6 07 25 12  |...g".........%.|
00000080  96 ce d4 ea d4 9c 25 1b  84 56 27 99 bf f4 cc 99  |......%..V'.....|
00000090  6d 8b 4c 6f 78 ac 58 0c  0a 70 e5 12 fa 46 66 3d  |m.Lox.X..p...Ff=|
000000a0  7e f7 78 f2 27 e3 3c b1  da a3 02 7e 6a 7f ff fb  |~.x.'.<....~j...|
000000b0  a5 f7 fe 29 b8 b5 00 00  83 2a 9a 07 32 b8 0f 03  |...).....*..2...|
000000c0  10 20 e0 0e 1b 53 06 e0  3e 30 77 12 53 08 d0 d5  |. ...S..>0w.S...|
000000d0  30 75 11 73 12 f1 39 31  bc 18 43 14 21 2c 30 dc  |0u.s..91..C.!,0.|
000000e0  09 83 70 62 3b cb 83 94  44 32 d8 b3 c5 67 35 b5  |..pb;...D2...g5.|
000000f0  53 16 1e 34 67 a3 c4 d4  3e 4a 43 7c 8e 3b 2c a3  |S..4g...>JC|.;,.|
00000100  c2 d0 39 e6 03 2c 0c 33  55 93 7b 79 36 d4 b3 47  |..9..,.3U.{y6..G|
00000110  15 34 d4 53 0d 14 32 03  c3 54 3c 32 a1 26 c8 61  |.4.S..2..T<2.&.a|
00000120  26 e6 ce f2 72 af e6 e2  ae 6b 25 a0 a0 a0 20 f1  |&...r....k%... .|
00000130  50 18 c2 44 4a 80 86 58  34 50 4a 64 25 a6 82 96  |P..DJ..X4PJd%...|
00000140  6a 2b a6 92 46 63 96 71  30 73 20 64 38 6f 3c 06  |j+..Fc.q0s d8o<.|
00000150  91 60 16 08 cc 58 ec 78  db 4d 14 8b 20 de a3 62  |.`...X.x.M.. ..b|
00000160  72 17 b0 c4 08 48 02 f5  aa 77 3d 33 cc d3 4d 57  |r....H...w=3..MW|
00000170  4e 38 cd f5 4c b0 4c 40  8c 60 98 ac 89 61 19 25  |N8..L.L@.`...a.%|
00000180  ff fb d4 64 65 0e 09 78  51 49 93 db ca f4 76 85  |...de..xQI....v.|
00000190  99 d3 6b 0f 4c 1d 5d 2b  3c 6e eb 0b c1 a1 a1 aa  |..k.L.]+<n......|
000001a0  5d 87 a1 75 d7 8d 00 ec  e5 3e df 04 02 16 41 05  |]..u.....>....A.|
000001b0  1d 46 e6 d0 c2 a0 98 60  98 62 98 e1 97 ad 00 fe  |.F.....`.b......|
000001c0  ff ff 82 fe ff ff 02 00  00 00 1c e1 c2 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by Velenjak on 2011-03-30
bump :(

---

### Post by Velenjak on 2011-03-31
/bump:(

been unable to use ubuntu for a couple days now...

your help is really appreciated

---

### Post by cahruhr2795 on 2011-11-09
Hello Velenjak,

I seem to be having a similar problem after a freeze and a hard reboot. Did you ever find a solution?

---

