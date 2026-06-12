---
title: "2 hard drives 1 problem"
date: 2010-04-02
forum: New to Ubuntu
---

### Post by vault55 on 2010-04-02
[COLOR=black][FONT=Verdana]I have searched these and other forums for days looking for the right solution.  I now need your help.  I unplugged HD1 (windows) and installed Ubuntu on HD2. Now with both plugged in, it boots to windows automagically and when I press F6, the only option is windows.  [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I have dual-booted on one HD before and I am familiar with the functionality of GRUB.  Please instruct me on being able to boot into Linux w/ both drives hooked up.  In the BIOS, the drives are set as 0 Master and 1 Master.  I’ve tried to make the second slave but I cannot figure out how to do that either.  OK, this is the beginner forum, go easy![/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Thanks[/FONT][/COLOR]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]

---

### Post by Bradtek on 2010-04-02
Who advised you to unplug a hard drive ?
Of course it only boots windows because the mbr only knows windows is there.
Install grub again with BOTH drives plugged in and it will recognise both

---

### Post by vault55 on 2010-04-02
I was trying to prevent GRUB from taking over the MBR and not have anything Ubuntu related written to my windows HD.

---

### Post by sandyd on 2010-04-02
reatach the hard drive
then,
you can install grub directly onto the partition using...
```

sudo grub-install /dev/sdax
```
replace sdax with the correct hard drive.

you can find out the correct hard drive by using
```

sudo fdisk -l
```

---

### Post by Jeffster999 on 2010-04-02
Hey read my threads. I just went thru this today.

It worked better for me to install from inside windows.
I understand why you unplugged the drive but have some faith in your backup...lol

[http://ubuntuforums.org/showthread.php?t=1445283](http://ubuntuforums.org/showthread.php?t=1445283)

---

### Post by Bradtek on 2010-04-02
It might be the beginner forum, but for Ubuntu Beginners.

ANyway, if you really can't work out how to set the 2nd drive as slave
(there should be a diaram how to set the jumper on the actual drive)
Can you plug the drive into the secondary IDE channel ?

---

### Post by vault55 on 2010-04-02
> **carlee said:**
> reatach the hard drive
then,
you can install grub directly onto the partition using...
```

sudo grub-install /dev/sdax
```replace sdax with the correct hard drive.

you can find out the correct hard drive by using
```

sudo fdisk -l
```

Carlee, Thank you for the reply and advice.  I have to figure out how to boot into Linux with both attached first.  How might this be done? Ive tried the F keys.

---

### Post by Bradtek on 2010-04-02
[http://www.pcguide.com/byop/byop_SettingHardDriveJumpers.htm](http://www.pcguide.com/byop/byop_SettingHardDriveJumpers.htm)

---

### Post by vault55 on 2010-04-02
> **Bradtek said:**
> [http://www.pcguide.com/byop/byop_SettingHardDriveJumpers.htm](http://www.pcguide.com/byop/byop_SettingHardDriveJumpers.htm)

This would be great if I were using hard drives from pre 2003 non sata.  This isnt my first build however, its been a long time since the last one.

---

### Post by Bradtek on 2010-04-02
Unless you tell us what drive you have we can only guess

Make / Model = ?

---

### Post by vault55 on 2010-04-02
> **Bradtek said:**
> Unless you tell us what drive you have we can only guess

Make / Model = ?

both SATA seagate 7200 rpm

drive 0 is 1TB
drive 1 (Ubuntu) is 300gb


thanks

---

### Post by vault55 on 2010-04-02
which one of these options should choose to install GRUB properly?

---

### Post by Bradtek on 2010-04-02
Sorry , still half asleep

[http://www.seagate.com/ww/v/index.jsp?locale=en-US&name=Serial_ATA_Jumpers_and_Cabling&vgnextoid=4a02242cb043e010VgnVCM100000dd04090aRCRD](http://www.seagate.com/ww/v/index.jsp?locale=en-US&name=Serial_ATA_Jumpers_and_Cabling&vgnextoid=4a02242cb043e010VgnVCM100000dd04090aRCRD)

No slave /master setting necessary on SATA

Now you mention pressing F6, what is that supposed to do ?

My PC uses differnt F key for Bios / Boot selection

---

### Post by vault55 on 2010-04-02
> **Bradtek said:**
> Sorry , still half asleep

[http://www.seagate.com/ww/v/index.jsp?locale=en-US&name=Serial_ATA_Jumpers_and_Cabling&vgnextoid=4a02242cb043e010VgnVCM100000dd04090aRCRD](http://www.seagate.com/ww/v/index.jsp?locale=en-US&name=Serial_ATA_Jumpers_and_Cabling&vgnextoid=4a02242cb043e010VgnVCM100000dd04090aRCRD)

No slave /master setting necessary on SATA

Now you mention pressing F6, what is that supposed to do ?

My PC uses different F key for Bios / Boot selection

I just thought I would be able to hit an F key and have use windows or something to boot into Ubuntu.  So, the ideal scenario would be to boot into windows without any action on behalf of the user and if I want to use Linux, I would press something etc.

---

### Post by sandyd on 2010-04-02
> **vault55 said:**
> which one of these options should choose to install GRUB properly?
You have to choose the correct hard drive,

For example, in my computer, ubuntu is installed on /dev/md0

so, for me,
```

sudo grub-install /dev/md0
```

if it was installed on /dev/sda
then
```

sudo grub-install /dev/sda
```
and so on...

---

### Post by presence1960 on 2010-04-02
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

### Post by louieb on 2010-04-02
:D1st time I installed Linux - I unplugged the drive with windows on it too. Like you I wanted to be sure windows did not get messed up.

You should have a BIOS boot menu - that lets you choose which drive to boot. You just have to figure out how to get to it - then have it boot the drive with Ubuntu. Would tell you how but every PC I have been on does it sightly different - usually one of the PF keys brings up the menu.  Find your PC documentation or Google for it.

Once you get it booting Ubuntu - its easy to fix GRUB so that it will boot Windows on the other drive too.

Open Applications>Accessories>Terminal
Update the device.map file - lets grub know you have 2 hard drives 
```
sudo grub-mkdevicemap
```then add windows to the grub menu

```
sudo update-grub
```

---

### Post by vault55 on 2010-04-02
> **presence1960 said:**
> Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

sorry for he delay

```

 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

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

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848 1,953,508,719 1,953,301,872   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 300.1 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   563,836,927   563,834,880  83 Linux
/dev/sdb2         563,838,975   586,072,063    22,233,089   5 Extended
/dev/sdb5         563,838,976   586,072,063    22,233,088  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        7646563D4655FE75                       ntfs       System Reserved               
/dev/sda2        FA92589D92585FE5                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        dca094cb-0fbd-49c0-be9c-fb497376dcb4   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        f5650097-d902-4e06-82f7-f4ca4ccf5a31   swap                                     
/dev/sdb: PTTYPE="dos" 

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
search --no-floppy --fs-uuid --set dca094cb-0fbd-49c0-be9c-fb497376dcb4
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
search --no-floppy --fs-uuid --set dca094cb-0fbd-49c0-be9c-fb497376dcb4
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
menuentry "Ubuntu, with Linux 2.6.32-19-generic" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set dca094cb-0fbd-49c0-be9c-fb497376dcb4
    linux    /boot/vmlinuz-2.6.32-19-generic root=UUID=dca094cb-0fbd-49c0-be9c-fb497376dcb4 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-19-generic
}
menuentry "Ubuntu, with Linux 2.6.32-19-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set dca094cb-0fbd-49c0-be9c-fb497376dcb4
    echo    Loading Linux 2.6.32-19-generic ...
    linux    /boot/vmlinuz-2.6.32-19-generic root=UUID=dca094cb-0fbd-49c0-be9c-fb497376dcb4 ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.32-19-generic
}
menuentry "Ubuntu, with Linux 2.6.32-16-generic" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set dca094cb-0fbd-49c0-be9c-fb497376dcb4
    linux    /boot/vmlinuz-2.6.32-16-generic root=UUID=dca094cb-0fbd-49c0-be9c-fb497376dcb4 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-16-generic
}
menuentry "Ubuntu, with Linux 2.6.32-16-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set dca094cb-0fbd-49c0-be9c-fb497376dcb4
    echo    Loading Linux 2.6.32-16-generic ...
    linux    /boot/vmlinuz-2.6.32-16-generic root=UUID=dca094cb-0fbd-49c0-be9c-fb497376dcb4 ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.32-16-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set dca094cb-0fbd-49c0-be9c-fb497376dcb4
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set dca094cb-0fbd-49c0-be9c-fb497376dcb4
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=dca094cb-0fbd-49c0-be9c-fb497376dcb4 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f5650097-d902-4e06-82f7-f4ca4ccf5a31 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


 186.9GB: boot/grub/core.img
  66.7GB: boot/grub/grub.cfg
 187.0GB: boot/initrd.img-2.6.32-16-generic
 187.0GB: boot/initrd.img-2.6.32-19-generic
 186.9GB: boot/vmlinuz-2.6.32-16-generic
 186.9GB: boot/vmlinuz-2.6.32-19-generic
 187.0GB: initrd.img
 187.0GB: initrd.img.old
 186.9GB: vmlinuz
 186.9GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  00 00 01 ba 21 04 79 2c  4f 80 1b 85 00 00 01 e0  |....!.y,O.......|
00000010  07 ee 0f 68 75 b2 02 21  47 e3 87 c8 19 92 7e a8  |...hu..!G.....~.|
00000020  79 13 d8 49 c4 82 7f af  fb 87 1d 80 36 ab b7 73  |y..I........6..s|
00000030  0a 28 86 82 19 21 5c d4  12 13 84 eb 5c 8e 83 40  |.(...!\.....\..@|
00000040  f9 9d a4 ee f9 6a 1e 68  a8 d0 e3 08 11 e1 c4 f0  |.....j.h........|
00000050  fa 22 29 3a 7c 96 b0 01  c4 9a 22 bb d9 a7 d1 1b  |."):|.....".....|
00000060  07 38 78 76 5c 1a 82 86  f5 0e 5c 8f d2 51 09 29  |.8xv\.....\..Q.)|
00000070  0c 61 a1 9d d4 cf d7 3a  58 f0 35 42 4e 89 15 22  |.a.....:X.5BN.."|
00000080  88 a4 38 33 c6 c9 1e 1d  2e d2 62 c6 fd a4 04 f2  |..83......b.....|
00000090  f8 ac 16 f0 cc b5 4d 96  e2 e1 bd 98 4c d4 7f 2d  |......M.....L..-|
000000a0  00 b7 23 a1 0e db 28 9d  29 60 3b 2b 66 c6 bb b0  |..#...(.)`;+f...|
000000b0  eb be 01 ae 21 a0 b7 41  49 4e 1f ad 5d ca 2b 90  |....!..AIN..].+.|
000000c0  f7 03 28 39 39 ba 12 50  9d 75 ac ae 71 96 3b e4  |..(99..P.u..q.;.|
000000d0  da 07 30 30 04 2e 06 09  83 0d 23 bd 23 36 da c0  |..00......#.#6..|
000000e0  6e 50 69 45 12 80 70 80  1c 0f 5c 82 48 b4 db a7  |nPiE..p...\.H...|
000000f0  b6 cb f4 b0 d1 1b c5 5e  d0 eb 6b d6 96 f1 9d 85  |.......^..k.....|
00000100  3c e4 fb e0 d0 fa 22 54  59 bc 26 5d 11 59 80 d9  |<....."TY.&].Y..|
00000110  f0 ea 42 46 92 17 50 9a  23 d8 5d df 6f fe 24 58  |..BF..P.#.].o.$X|
00000120  c0 81 bc 7f 12 10 ce 47  af 69 10 2c 9a ee 37 81  |.......G.i.,..7.|
00000130  fc 46 08 e4 fd 00 98 35  20 57 93 73 30 cc 96 40  |.F.....5 W.s0..@|
00000140  23 81 9b 80 5f 5a a8 49  95 69 7f d7 77 6a 23 05  |#..._Z.I.i..wj#.|
00000150  4e 05 db c9 26 a9 b6 70  ff 5d fe 1e b9 4a e3 e5  |N...&..p.]...J..|
00000160  b5 a4 c4 86 2c d2 71 12  49 37 30 69 68 cb db 81  |....,.q.I70ih...|
00000170  d5 8f f2 49 8f 96 78 c3  b6 53 f3 30 ed 8d ea f0  |...I..x..S.0....|
00000180  68 15 0d c5 25 03 31 65  8c e1 27 32 53 d7 c9 58  |h...%.1e..'2S..X|
00000190  dc 2f f7 e2 a5 b6 8d 3a  d7 0a 25 71 a8 28 6f 49  |./.....:..%q.(oI|
000001a0  21 f2 3f 5b 3f 37 7e 71  bc 3a 84 83 f8 c5 39 e2  |!.?[?7~q.:....9.|
000001b0  0c 13 2f 4a a2 39 48 07  fa 0b 29 dc 91 f1 00 fe  |../J.9H...).....|
000001c0  ff ff 82 fe ff ff 01 00  00 00 00 40 53 01 00 00  |...........@S...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by vault55 on 2010-04-02
> **louieb said:**
> :D1st time I installed Linux - I unplugged the drive with windows on it too. Like you I wanted to be sure windows did not get messed up.

You should have a BIOS boot menu - that lets you choose which drive to boot. You just have to figure out how to get to it - then have it boot the drive with Ubuntu. Would tell you how but every PC I have been on does it sightly different - usually one of the PF keys brings up the menu.  Find your PC documentation or Google for it.

Once you get it booting Ubuntu - its easy to fix GRUB so that it will boot Windows on the other drive too.

Open Applications>Accessories>Terminal
Update the device.map file - lets grub know you have 2 hard drives 
```
sudo grub-mkdevicemap
```then add windows to the grub menu

```
sudo update-grub
```

I followed your instructions and Thanks... I think...GRUB has taken over and Im not sure if its loaded on HD2 which is the dedicated Linux drive.  I wasnt crazy about grub taken over my MBR. Has it done so? It displays on system start so Im assuming it has.

---

### Post by vault55 on 2010-04-02
> **louieb said:**
> :D1st time I installed Linux - I unplugged the drive with windows on it too. Like you I wanted to be sure windows did not get messed up.

You should have a BIOS boot menu - that lets you choose which drive to boot. You just have to figure out how to get to it - then have it boot the drive with Ubuntu. Would tell you how but every PC I have been on does it sightly different - usually one of the PF keys brings up the menu.  Find your PC documentation or Google for it.

Once you get it booting Ubuntu - its easy to fix GRUB so that it will boot Windows on the other drive too.

Open Applications>Accessories>Terminal
Update the device.map file - lets grub know you have 2 hard drives 
```
sudo grub-mkdevicemap
```then add windows to the grub menu

```
sudo update-grub
```

that might have been the answer, I unplugged the Linux drive and it booted Win7 no problem (without GRUB making an appearance) ;) Im now awaiting analysis by presence1960. Thanks

---

### Post by louieb on 2010-04-03
You have 2 hard drives = 2 MBRs - The boot info script shows GRUB code is in 1 MBR and WIn7 code in the other. 

All is good - you should be able to use the BIOS menu to choose which OS to boot.

or alway use GRUB - just  add Win7 to its menu.

---

