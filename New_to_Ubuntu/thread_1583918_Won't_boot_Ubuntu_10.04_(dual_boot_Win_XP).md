---
title: "Won't boot Ubuntu 10.04 (dual boot Win XP)"
date: 2010-09-28
forum: New to Ubuntu
---

### Post by Fysikeren on 2010-09-28
I recently installed Ubuntu 10.04 on a computer which already had Windows XP installed and the installation seemed to go smoothly but when I restarted the PC it just started up XP without even asking which system I wanted to boot... how do I fix this?
 
...oh, and while shutting down after the installation of Ubuntu 10.04 I received some "...end_request, I/O error, dev sr0, sector..." messages but just pressing enter restarted the computer - afterwards I read that this was the appropriate action, so I guess that doesn't really mean much (just wanted to mention it in case it had relevance).

---

### Post by spiky001 on 2010-09-28
try   ```
sudo upate-grub
```

---

### Post by Fysikeren on 2010-09-28
> **spiky001 said:**
> try ```
sudo upate-grub
```
 
 
Where do I try this? I tried running from the Ubuntu installation CD (the "try Ubuntu"-thing or whatever it's called) and used the "sudo update-grub" previously but to no avail - other than that I don't know where to use the command since the PC is booting into Windows XP.
 
Oh, was also wondering if the place I installed Ubuntu mattered? It's on something called "/dev/sda5" as far as I can tell :-/

---

### Post by spiky001 on 2010-09-28
yes it is run from live cd in terminal but as you have tried this i,m not sure, the reason for the command is in case grub didn,t load properly, it normally finds xp ok then,

---

### Post by Rubi1200 on 2010-09-28
From the LiveCD post the results of the bootscript linked at the bottom of my post please.

Thanks.

---

### Post by astrobob.tk on 2010-09-28
> **Fysikeren said:**
> Where do I try this? I tried running from the Ubuntu installation CD (the "try Ubuntu"-thing or whatever it's called) and used the "sudo update-grub" previously but to no avail - other than that I don't know where to use the command since the PC is booting into Windows XP.
 
Oh, was also wondering if the place I installed Ubuntu mattered? It's on something called "/dev/sda5" as far as I can tell :-/

I believe the grub didnt show up coz (i think) u changed the default settings of the boot loader during the installation of Ubuntu.

Let's try this: Boot again from the live disk & open a terminal & issue the command: ```
fdisk -l
``` {l being a lower case L}
the command should output a table. copy that table as is & post it here. Alternatively if for some reason the command doesn't work open System > Administration.
Under administration there should be a disk utility other than "Disk utility". Launch it & take a screenshot of the partitioning & post it here. I hope to be able to figure out what went wrong.

---

### Post by wilee-nilee on 2010-09-28
> **Rubi1200 said:**
> From the LiveCD post the results of the bootscript linked at the bottom of my post please.

Thanks.

**+1 do this first**, it will give us the lowdown on the OS. The help so far missed the fact you couldn't even get into the installed Ubuntu, except for rubi1200

---

### Post by Fysikeren on 2010-09-29
> **spiky001 said:**
> yes it is run from live cd in terminal but as you have tried this i,m not sure, the reason for the command is in case grub didn,t load properly, it normally finds xp ok then,

Hey - did a reinstall of Ubuntu 10.04 (thought it might help somehow) but now when I typed in

```
sudo update-grub
```

I got "/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?)." ...dunno what that means though but I guess it has somehow problems finding the Ubuntu OS? (which is still on /dev/sda5)

---

### Post by Fysikeren on 2010-09-29
> **Rubi1200 said:**
> From the LiveCD post the results of the bootscript linked at the bottom of my post please.

Thanks.

Hi - the results of the bootscript were (quite a lot):

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   829,898,963   829,898,901   7 HPFS/NTFS
/dev/sda2         829,900,798   976,773,119   146,872,322   5 Extended
/dev/sda5         829,900,800   970,696,703   140,795,904  83 Linux
/dev/sda6         970,698,752   976,773,119     6,074,368  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   153,604,079   153,604,017   7 HPFS/NTFS
/dev/sdb2         153,604,080   621,579,099   467,975,020   7 HPFS/NTFS
/dev/sdb3         621,579,100   976,767,119   355,188,020   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        CA78963278961CEF                       ntfs       Storage                       
/dev/sda2: PTTYPE="dos" 
/dev/sda5        82f3eaf9-980c-4527-bc98-46cce1be51a8   ext4                                     
/dev/sda6        236ea045-6f2c-4272-863d-e5418f56cfe3   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        5878DDAA78DD8762                       ntfs       System                        
/dev/sdb2        2264AFC064AF9557                       ntfs       Data                          
/dev/sdb3        7CC060EFC060B156                       ntfs       Fun                           
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /media/82f3eaf9-980c-4527-bc98-46cce1be51a8 ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set 82f3eaf9-980c-4527-bc98-46cce1be51a8
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
search --no-floppy --fs-uuid --set 82f3eaf9-980c-4527-bc98-46cce1be51a8
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 82f3eaf9-980c-4527-bc98-46cce1be51a8
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=82f3eaf9-980c-4527-bc98-46cce1be51a8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 82f3eaf9-980c-4527-bc98-46cce1be51a8
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=82f3eaf9-980c-4527-bc98-46cce1be51a8 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 82f3eaf9-980c-4527-bc98-46cce1be51a8
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 82f3eaf9-980c-4527-bc98-46cce1be51a8
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 5878ddaa78dd8762
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=82f3eaf9-980c-4527-bc98-46cce1be51a8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=236ea045-6f2c-4272-863d-e5418f56cfe3 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 480.8GB: boot/grub/core.img
 457.3GB: boot/grub/grub.cfg
 480.8GB: boot/initrd.img-2.6.32-24-generic
 425.1GB: boot/vmlinuz-2.6.32-24-generic
 480.8GB: initrd.img
 425.1GB: vmlinuz

================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  ff ff ff e2 ff ff ff ff  ff e0 ff ff ff ff ff e5  |................|
00000010  ff e5 f2 28 8e 3a e3 43  24 2b fa 72 12 cb e5 51  |...(.:.C$+.r...Q|
00000020  10 15 96 47 23 27 b8 9a  84 c1 a6 3f 02 2b dc c5  |...G#'.....?.+..|
00000030  26 d1 54 d7 76 20 13 84  c3 94 bf ed 64 62 4d 61  |&.T.v ......dbMa|
00000040  63 fa e3 4a ce 28 6e ee  ab 81 0e 75 9c 2f ed cb  |c..J.(n....u./..|
00000050  db b0 02 0d 4f f1 55 b4  f1 d1 c1 54 7f d8 dc 13  |....O.U....T....|
00000060  11 36 61 33 e7 a9 7c c2  c6 7c 66 7c 7b 56 29 96  |.6a3..|..|f|{V).|
00000070  59 49 0e d5 d3 b4 d0 7d  15 94 01 9f 53 2a ea 89  |YI.....}....S*..|
00000080  3f 0e cb 76 da 84 8f c7  8f 59 3f 53 47 da 0e 44  |?..v.....Y?SG..D|
00000090  79 d1 26 a8 fa 64 8d 38  db e8 a8 c3 fa d8 25 ce  |y.&..d.8......%.|
000000a0  57 44 ce d9 4e 96 2d 9c  7d 51 39 32 f2 7d 89 bf  |WD..N.-.}Q92.}..|
000000b0  7b 12 e3 59 03 a7 35 fd  ec b3 ff 74 3c 28 e7 3f  |{..Y..5....t<(.?|
000000c0  0d 54 69 e1 ed 7f a2 d9  c7 71 20 fa fc 8a d8 d2  |.Ti......q .....|
000000d0  26 06 37 f5 c8 6f c5 c6  bd fb d2 ed 3d 64 91 5b  |&.7..o......=d.[|
000000e0  23 35 e3 54 b9 d5 1c 85  d8 31 83 d0 cd a1 22 a7  |#5.T.....1....".|
000000f0  f7 e0 32 46 23 35 67 a7  32 15 24 a7 f6 44 32 d6  |..2F#5g.2.$..D2.|
00000100  4f 68 a5 47 6a 9c ba 76  b9 a1 57 66 73 12 ff 67  |Oh.Gj..v..Wfs..g|
00000110  8d 4e 3e ee 4b 76 8d 05  9d 64 9a 65 9b f5 3f af  |.N>.Kv...d.e..?.|
00000120  ec ad d7 24 ea 95 79 03  db d4 98 b1 34 f4 07 c5  |...$..y.....4...|
00000130  bb c3 73 94 b2 cb 67 af  3c 2e 46 96 d8 d4 d8 53  |..s...g.<.F....S|
00000140  f5 a6 d7 50 1c d2 30 95  73 69 15 d1 d0 4a a7 83  |...P..0.si...J..|
00000150  06 cc b7 d9 3f a7 7d 4f  f3 6a 71 d9 77 70 53 f0  |....?.}O.jq.wpS.|
00000160  a1 74 e4 f7 c5 45 77 66  be c8 ee 93 1d 5a 9c a0  |.t...Ewf.....Z..|
00000170  16 b8 ba 68 31 95 0b f2  49 be 57 3d b7 a5 45 57  |...h1...I.W=..EW|
00000180  65 3f 31 37 05 97 4a 07  25 85 c7 d6 f3 05 0f c7  |e?17..J.%.......|
00000190  a0 b4 17 1f f3 1c 53 bb  ab b6 97 ae 4d f0 50 b5  |......S.....M.P.|
000001a0  5e 6e 16 f3 19 bc a0 53  cf bc 98 3b 0e 9b 4d 2c  |^n.....S...;..M,|
000001b0  fa 74 63 3e 57 f6 7f dc  74 0d e8 85 f7 98 00 fe  |.tc>W...t.......|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 60 64 08 00 fe  |...........`d...|
000001d0  ff ff 05 fe ff ff 02 60  64 08 00 b8 5c 00 00 00  |.......`d...\...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by Fysikeren on 2010-09-29
> **astrobob.tk said:**
> I believe the grub didnt show up coz (i think) u changed the default settings of the boot loader during the installation of Ubuntu.

Let's try this: Boot again from the live disk & open a terminal & issue the command: ```
fdisk -l
``` {l being a lower case L}
the command should output a table. copy that table as is & post it here. Alternatively if for some reason the command doesn't work open System > Administration.
Under administration there should be a disk utility other than "Disk utility". Launch it & take a screenshot of the partitioning & post it here. I hope to be able to figure out what went wrong.

The ```
fdisk -l
``` didn't work so I've attached the screenshots instead.

---

### Post by wilee-nilee on 2010-09-29
So the script looks correct, but the sda HD needs to be the booting drive, the script says it is, but make sure. I would also remove the boot flag from the sda1 partition, that is a ntfs partition and Ubuntu doesn't need a flag anyway, leave the flag in sdb. Do this flag removal with gparted on a live cd, right click on sda1 then manage flags and untick.

To make sure you booting the sda hd first check the bios for the order of the booting media. You can also with a f-key prompt bring up a per session booting list, mine is f12, try f11 or escape of really any of the f-keys, f2 is generally for getting into the bios.

Maybe it was a bad install, or grub was not loaded to the sda hd master boot record correctly. To reload grub follow this link it defaults to the live cd reloading grub section.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

If your confused the first set of commands from a live cd should be this.
```
sudo mount /dev/sda5 /mnt
```
then
```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

Reboot to Ubuntu and run 
```
sudo update-grub
```

This reloading of grub alone needs to be done after following the instructions proceeding it. Honestly I think grub installed correctly though.

---

### Post by oldfred on 2010-09-29
If you are directly booting windows then you must be booting sdb from BIOS. Change to the other 500GB drive and try booting. In BIOS you cannot tell them apart. I have two 160GB drives and sometime I just have to boot a second time and switch drives after I have moved things around. If it does not boot, then the  reinstall grub may fix it.

The error on shutdown seems to be that it ejects the CD then wants to run a final command from the cD and cannot find it.

---

### Post by Fysikeren on 2010-10-01
> **wilee-nilee said:**
> So the script looks correct, but the sda HD needs to be the booting drive, the script says it is, but make sure. I would also remove the boot flag from the sda1 partition, that is a ntfs partition and Ubuntu doesn't need a flag anyway, leave the flag in sdb. Do this flag removal with gparted on a live cd, right click on sda1 then manage flags and untick.

To make sure you booting the sda hd first check the bios for the order of the booting media. You can also with a f-key prompt bring up a per session booting list, mine is f12, try f11 or escape of really any of the f-keys, f2 is generally for getting into the bios.

Maybe it was a bad install, or grub was not loaded to the sda hd master boot record correctly. To reload grub follow this link it defaults to the live cd reloading grub section.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

If your confused the first set of commands from a live cd should be this.
```
sudo mount /dev/sda5 /mnt
```then
```
sudo grub-install --root-directory=/mnt/ /dev/sda
```Reboot to Ubuntu and run 
```
sudo update-grub
```This reloading of grub alone needs to be done after following the instructions proceeding it. Honestly I think grub installed correctly though.

Hey again - I changed the order of booting and it worked! ...what was that with the booting flag? (is it necessary now/can I do it from inside Ubuntu?)

Thanks for the help!

---

### Post by wilee-nilee on 2010-10-01
> **Fysikeren said:**
> Hey again - I changed the order of booting and it worked! ...what was that with the booting flag? (is it necessary now/can I do it from inside Ubuntu?)

Thanks for the help!

The boot flag on the sda1 partition is not a problem. If you want to know how to remove and add this flag though, boot the live Ubuntu cd open gparted and right click on sda1 then manage flags and untick the flag. Be very careful with gparted, always use a live cd when using it until you understand it best. gparted is like the windows disc manager designed to wipe and build the HD partitions.

Also when using gparted it is imperative that any partition you mess with is not mounted and that you turn off the swap by right clicking on the swap partition then swap off.

---

