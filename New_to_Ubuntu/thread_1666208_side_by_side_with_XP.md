---
title: "side by side with XP"
date: 2011-01-13
forum: New to Ubuntu
---

### Post by jagdefalke on 2011-01-13
First of all, let me say that I am a complete and utter newbie so please be gentle with me....
I'm the kind of person that could not follow the recipe's in a cookbook to save my life, so ofcourse I had to do this with no book or guidance of any sort.   But have been trying to get to the library so I can find one.    

I downloaded the newest Ubuntu and burned it to disk a few weeks ago and it was working great so I decided to install side by side to the XP on the hard drive.    I've got plenty of space.    
Right away I couldn't boot up into Windows anymore, but it booted up into Ubuntu without a problem.  Which was fine at the time until last night when the internet stopped staying connected.   It would be connected at restart only for about 15-20 seconds and no matter what I did it wouldn't reconnect.   I should mention that I'm hooked up by LAN though my fiances computer (who wants nothing to do with linux and has been criticizing me for doing this).

I got tired of messing with that so decided to go back to figuring out why I couldn't get into Windows.    What happens is at boot up it lists 5 different choices: the two different OS's and the rest are tools I think, like the XP loader.    If I pick XP, it will then ask again just between the two OS's, and if I pick XP again it will then ask if I want to open in the different Safe Mode's or open Normally.   Which I thought it was weird that it would ask that, but whatever I pick there something trips it into rebooting again.   It's a vicious cycle.      So last night I picked XP from the list of 5, then Ubuntu from the list of 2 just to see what would happen.   It sat and thought about it in the purble Ubuntu screen for a couple minutes then gave me the: "(initramfs) Unable to find a medium containing a live file system".
Sooo... I got on the fiances computer this morning and did a search and what looks most likely is either the storage controller or maybe I should have left the boot disk in?

I've got a refurbed hp 64 with a registered XP but no disk for it.

My first concern is what to do in this screen.   (like I said, I'm a utter newbie, here)  I don't want to put in the wrong command and screw things up.  I'm pulling a complete blank on what to do from this point on.

I think the internet problem is a router or other unrelated issue because I'd lose it with Windows on occasion too and restarting both computers usually fixed it.

Someday I'm gonna be one of those linux geek types :P, but right now is my initiation and I'm a bit stumped to say the least.

---

### Post by SuaSwe on 2011-01-13
Hey there jagdefalke!

Would you be able to follow the instructions of and post the results from [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) ? Instructions on the page. :)

If you're losing wireless on both PC's I'd agree it's likely a problem with the router/transmission. How strong is the signal when it drops? Anyway, perhaps best to sort one problem at a time! ;)

---

### Post by jagdefalke on 2011-01-13
Thankyou, I'll try that as soon as I get home.

I used Wubi to install, under the impression that it would partition my hard drive, and it sure did look like that's what it was doing.   But I'm being told from elsewhere that it may not have, and I could be screwed.     Is there a chance that it didn't?

---

### Post by Hippytaff on 2011-01-13
+1 swaswe

also your not screwed, Wubi installs ubuntu inside windows...looks like a dual boot though (I was convinced I had a dual boot when asking for help on these forums a while ago when I did a Wubi install) you might want to have a look [here]("http://ubuntuforums.org/showthread.php?t=1639198") - an excellent thread about Wubi when it goes wrong and some fixes

---

### Post by jagdefalke on 2011-01-13
> **Hippytaff said:**
> +1 swaswe

also your not screwed, Wubi installs ubuntu inside windows...looks like a dual boot though (I was convinced I had a dual boot when asking for help on these forums a while ago when I did a Wubi install) you might want to have a look [here]("http://ubuntuforums.org/showthread.php?t=1639198") - an excellent thread about Wubi when it goes wrong and some fixes

Thankyou!   I feel better already.

I have, I wanna say, a 110 G drive and it showed allowing fifty something G for Windows and forty something G for Ubuntu, so it sure did look like it was getting separated.    In retrospect, I didn't defrag or anything before I did this and I'm sure that would've helped.

---

### Post by Hippytaff on 2011-01-13
defragging is a good idea if your going to resize your windows partition, but it doesn't make much difference if you did a Wubi install. Anyway, check the link and post results of the script  that Swaswe suggested and we can take it from there...there are a number of experts here who know far more than me who will jump in once the information is made available ;-)

---

### Post by wilee-nilee on 2011-01-13
> **jagdefalke said:**
> Thankyou!   I feel better already.

I have, I wanna say, a 110 G drive and it showed allowing fifty something G for Windows and forty something G for Ubuntu, so it sure did look like it was getting separated.    In retrospect, I didn't defrag or anything before I did this and I'm sure that would've helped.

For any real help beyond a calmed psyche though run that bootscript, and post it in code tags. When putting all the text into a reply, first click on this **(#)** in the reply panel and paste the text in between the code tags.

---

### Post by Hippytaff on 2011-01-13
> **wilee-nilee said:**
> For any real help beyond a calmed psyche though run that bootscript, and post it in code tags. When putting all the text into a reply, first click on this **(#)** in the reply panel and paste the text in between the code tags.

I already suggested the bootscript via Swaswe's post...and I like calming psyche's...;-)
:-D but you were the expert I was alluding to :-)

---

### Post by ppv on 2011-01-13
The experts being already in...its now with them...just one thing that comes out...is it actually a wubi installation as the OP seems to mention that he has 40G for Ubuntu and Wubi only supports 30G. Or was it just an example.

---

### Post by medic2000 on 2011-01-13
> **jagdefalke said:**
> First of all, let me say that I am a complete and utter newbie so please be gentle with me....
I'm the kind of person that could not follow the recipe's in a cookbook to save my life, so ofcourse I had to do this with no book or guidance of any sort.   But have been trying to get to the library so I can find one.    

I downloaded the newest Ubuntu and burned it to disk a few weeks ago and it was working great so I decided to install side by side to the XP on the hard drive.    I've got plenty of space.    
Right away I couldn't boot up into Windows anymore, but it booted up into Ubuntu without a problem.  Which was fine at the time until last night when the internet stopped staying connected.   It would be connected at restart only for about 15-20 seconds and no matter what I did it wouldn't reconnect.   I should mention that I'm hooked up by LAN though my fiances computer (who wants nothing to do with linux and has been criticizing me for doing this).

I got tired of messing with that so decided to go back to figuring out why I couldn't get into Windows.    What happens is at boot up it lists 5 different choices: the two different OS's and the rest are tools I think, like the XP loader.    If I pick XP, it will then ask again just between the two OS's, and if I pick XP again it will then ask if I want to open in the different Safe Mode's or open Normally.   Which I thought it was weird that it would ask that, but whatever I pick there something trips it into rebooting again.   It's a vicious cycle.      So last night I picked XP from the list of 5, then Ubuntu from the list of 2 just to see what would happen.   It sat and thought about it in the purble Ubuntu screen for a couple minutes then gave me the: "(initramfs) Unable to find a medium containing a live file system".
Sooo... I got on the fiances computer this morning and did a search and what looks most likely is either the storage controller or maybe I should have left the boot disk in?

I've got a refurbed hp 64 with a registered XP but no disk for it.

My first concern is what to do in this screen.   (like I said, I'm a utter newbie, here)  I don't want to put in the wrong command and screw things up.  I'm pulling a complete blank on what to do from this point on.

I think the internet problem is a router or other unrelated issue because I'd lose it with Windows on occasion too and restarting both computers usually fixed it.

Someday I'm gonna be one of those linux geek types :P, but right now is my initiation and I'm a bit stumped to say the least.

I know you will. Everyone's past with Linux is like that. Maybe worse. My friend installed Linux into my computer then something happened and i said "Your Linux broke my computer!" Well i think that was 5 years ago :)

Now i use a Linux that is building from scratch and a window manager that does not anything on the desktop :)

---

### Post by jagdefalke on 2011-01-13
> **wilee-nilee said:**
> For any real help beyond a calmed psyche though run that bootscript, and post it in code tags. When putting all the text into a reply, first click on this **(#)** in the reply panel and paste the text in between the code tags.

OK!    So I got home and have internet this time.   I think what the problem is with that is for some reason our computers can't find eachother when we try to use wireless so that function is, supposedly, disabled...  but every once in awhile it tries to use the wireless and it won't work.     go fig...


I tried the bootinfoscrip and here's what I got:

```
bash: -/: invalid option
Usage:    bash [GNU long option] [option] ...
    bash [GNU long option] [option] script-file ...
GNU long options:
    --debug
    --debugger
    --dump-po-strings
    --dump-strings
    --help
    --init-file
    --login
    --noediting
    --noprofile
    --norc
    --posix
    --protected
    --rcfile
    --restricted
    --verbose
    --version
Shell options:
    -irsD or -c command or -O shopt_option        (invocation only)
    -abefhkmnptuvxBCHP or -o option
sparverius@sparverius-desktop:~$ 

```

---

### Post by wilee-nilee on 2011-01-13
Click on the link again, drag the downloaded script to the desktop and run this command then copy-paste all the text from the generated file.
sudo bash ~/Desktop/boot_info_script*.sh

---

### Post by jagdefalke on 2011-01-14
> **wilee-nilee said:**
> Click on the link again, drag the downloaded script to the desktop and run this command then copy-paste all the text from the generated file.
sudo bash ~/Desktop/boot_info_script*.sh

Ah, I see...   here ya go:

```
============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr

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
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr /wubildr

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   127,452,867   127,452,805   7 HPFS/NTFS
/dev/sda2         127,453,182   234,440,703   106,987,522   5 Extended
/dev/sda5         127,453,184   231,481,343   104,028,160  83 Linux
/dev/sda6         231,483,392   234,440,703     2,957,312  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders, total 39876480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    39,857,264    39,857,202   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3024FE6224FE2B0C                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        ecb99bd0-c053-439c-95ca-ced208a9fd50   ext4                                     
/dev/sda6        2fde622a-ee53-4042-87cf-bea063b043b3   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        00149F26149F1E2A                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=0 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
C:\wubildr.mbr = "Ubuntu" 

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
search --no-floppy --fs-uuid --set ecb99bd0-c053-439c-95ca-ced208a9fd50
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
search --no-floppy --fs-uuid --set ecb99bd0-c053-439c-95ca-ced208a9fd50
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
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set ecb99bd0-c053-439c-95ca-ced208a9fd50
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=ecb99bd0-c053-439c-95ca-ced208a9fd50 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set ecb99bd0-c053-439c-95ca-ced208a9fd50
    echo    'Loading Linux 2.6.32-27-generic ...'
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=ecb99bd0-c053-439c-95ca-ced208a9fd50 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set ecb99bd0-c053-439c-95ca-ced208a9fd50
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=ecb99bd0-c053-439c-95ca-ced208a9fd50 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set ecb99bd0-c053-439c-95ca-ced208a9fd50
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=ecb99bd0-c053-439c-95ca-ced208a9fd50 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set ecb99bd0-c053-439c-95ca-ced208a9fd50
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set ecb99bd0-c053-439c-95ca-ced208a9fd50
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3024fe6224fe2b0c
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 00149f26149f1e2a
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
UUID=ecb99bd0-c053-439c-95ca-ced208a9fd50 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=2fde622a-ee53-4042-87cf-bea063b043b3 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  74.0GB: boot/grub/core.img
  91.5GB: boot/grub/grub.cfg
  74.1GB: boot/initrd.img-2.6.32-24-generic
  74.1GB: boot/initrd.img-2.6.32-27-generic
  74.1GB: boot/vmlinuz-2.6.32-24-generic
  74.1GB: boot/vmlinuz-2.6.32-27-generic
  74.1GB: initrd.img
  74.1GB: initrd.img.old
  74.1GB: vmlinuz
  74.1GB: vmlinuz.old

================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\wubildr.mbr = "Ubuntu" 
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  18 4e 77 83 66 38 00 33  c0 39 46 10 5f 0f 95 c0  |.Nw.f8.3.9F._...|
00000010  5e 5d c2 0c 00 90 90 90  90 90 8b ff 55 8b ec 81  |^]..........U...|
00000020  ec 04 02 00 00 a1 04 70  60 77 56 33 f6 66 39 75  |.......p`wV3.f9u|
00000030  08 57 8b 7d 0c 89 45 fc  89 37 74 76 68 00 01 00  |.W.}..E..7tvh...|
00000040  00 8d 85 fc fd ff ff 50  ff 75 08 ff 15 dc 13 4e  |.......P.u.....N|
00000050  77 66 39 b5 fc fd ff ff  8d 85 fc fd ff ff 74 52  |wf9...........tR|
00000060  66 83 38 2f 74 0c 50 ff  15 2c 19 4e 77 66 39 30  |f.8/t.P..,.Nwf90|
00000070  75 ee 66 39 30 74 3b 66  89 30 83 c0 02 50 ff 15  |u.f90t;f.0...P..|
00000080  f4 13 4e 77 66 3b c6 74  2d 66 3b 05 e0 c6 60 77  |..Nwf;.t-f;...`w|
00000090  74 20 66 3b 05 e4 c6 60  77 75 08 c7 07 01 00 00  |t f;...`wu......|
000000a0  00 eb 0f 66 3b 05 dc c6  60 77 75 0a c7 07 02 00  |...f;...`wu.....|
000000b0  00 00 33 c0 eb 05 b8 10  00 01 80 8b 4d fc 5f 5e  |..3.........M._^|
000000c0  e8 7e c7 f3 ff c9 c2 08  00 90 90 90 90 90 8b ff  |.~..............|
000000d0  55 8b ec 53 56 8b 75 08  33 db 66 39 5e 1c 74 74  |U..SV.u.3.f9^.tt|
000000e0  57 6a 01 ff 76 0c ff 15  80 18 4e 77 8b 46 44 3b  |Wj..v.....Nw.FD;|
000000f0  c3 8b 3d d0 13 4e 77 66  89 5e 1c 74 06 50 ff d7  |..=..Nwf.^.t.P..|
00000100  89 5e 44 8b 46 40 3b c3  74 06 50 ff d7 89 5e 40  |.^D.F@;.t.P...^@|
00000110  8b 4e 38 3b cb 74 37 8b  46 34 3b c3 74 30 83 f9  |.N8;.t7.F4;.t0..|
00000120  04 50 75 04 ff d7 eb 16  0f b7 46 30 50 e8 0f de  |.Pu.......F0P...|
00000130  ff ff 66 3b c3 74 07 50  ff 15 e0 13 4e 77 0f b7  |..f;.t.P....Nw..|
00000140  46 30 ff 76 34 50 e8 35  3e 03 00 89 5e 34 33 c0  |F0.v4P.5>...^43.|
00000150  40 5f eb 02 33 c0 5e 5b  5d c2 04 00 90 90 90 90  |@_..3.^[].......|
00000160  90 8b ff 55 8b ec 53 e8  0c 27 fc ff 39 45 0c 73  |...U..S..'..9E.s|
00000170  12 ff 75 0c 68 02 20 00  00 ff 15 d4 13 4e 77 8b  |..u.h. ......Nw.|
00000180  d8 eb 02 33 db 85 db 74  37 53 ff 15 7c 12 4e 77  |...3...t7S..|.Nw|
00000190  85 c0 74 25 8b 4d 0c 56  8b 75 08 57 8b f8 8b c1  |..t%.M.V.u.W....|
000001a0  c1 e9 02 f3 a5 8b c8 83  e1 03 53 f3 a4 ff 15 78  |..........S....x|
000001b0  12 4e 77 5f 8b c3 5e eb  09 53 ff 15 d0 13 00 fe  |.Nw_..^..S......|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 58 33 06 00 fe  |...........X3...|
000001d0  ff ff 05 fe ff ff 02 58  33 06 00 28 2d 00 00 00  |.......X3..(-...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf  
```

---

### Post by wilee-nilee on 2011-01-14
So you let the Ubuntu install resize the XP partition sda1?

sda1 appears to have a wubi=install from live XP session.

I think your main problem here may have been this resizing of XP if done this way. This will need a XP disc, to fix or worse case scenario, reinstall. It may be that XP just needs its chkdsk run, on resizing there is a automatic running of this when rebooted. If you disturb it enough though a manual run is needed at times.

Your second hd sdb has the XP boot files and a couple of wubi files there as well.

If you can get to that safe mode screen and open the command terminal try to run this
chkdsk /f/r
It will ask for a yes or no on reboot choose yes

---

### Post by jagdefalke on 2011-01-14
> **wilee-nilee said:**
> So you let the Ubuntu install resize the XP partition sda1?

sda1 appears to have a wubi=install from live XP session.

I think your main problem here may have been this resizing of XP if done this way. This will need a XP disc, to fix or worse case scenario, reinstall. It may be that XP just needs its chkdsk run, on resizing there is a automatic running of this when rebooted. If you disturb it enough though a manual run is needed at times.

Your second hd sdb has the XP boot files and a couple of wubi files there as well.

If you can get to that safe mode screen and open the command terminal try to run this
chkdsk /f/r
It will ask for a yes or no on reboot choose yes


Sweet.   (sarcasm intended)

I can't seem to get a command prompt for XP in order to do a chkdsk.

---

### Post by jagdefalke on 2011-03-21
Ok, update and quick question..  :)

I used another XP disk and did a fixboot and fixmbr and it just made things worse...  (figures) but I was still able to access everything through the boot disks so I backed up a few things and wiped the whole drive.
While I was doing something else my fiance partitioned the drive (110gb) and reinstalled XP.   So right now XP is on a 45gb partition, and when I look at it with disk utility through the Ubuntu boot disk it shows an extended partition with another 43gb and a 22gb.     My impression is that I need to break the 22 gb into about 12gb mounted as "/" and 10gb for swap, and the 45gb as /home. 
Is that right?
And also: is there anything I should be doing with these partitions ahead of time through disk utility BEFORE I reinstall Ubuntu, or can I do everything I need through advanced install off the boot disk?

---

### Post by jagdefalke on 2011-03-21
Ok, so it occurred to me right after I logged off last night that being as I've got a 512 ram the swap would be more like 1-2gb and root would be more like 20gb.     I still want to make sure I do it right the first time.. this time.

---

### Post by Hippytaff on 2011-03-21
My setup is -

'root' : Min - 20G
'swap' 1G should be plenty - the general rules used to be 2 X Ram. So 1Gb Ram = 2Gb Swap, though some say this is a needless waste of memory. I matched my 1Gb Ram with 1Gb Swap.
'home': as much as you think - though I used everything left after setting root and swap.

:-)

---

### Post by jagdefalke on 2011-03-21
Thanx!

So I used GParted and adjusted the partitions the sizes I think they should be, but I'm not sure the paths are right.

Here's how they are now:
sda1    ntfs    (the one xp is in)
sda2    extended
  sda5    ext4  (the one /home will be in)
  sda7    ext4  (the one for /)
  sda6    swap

it seems to me 5, 6, and 7 are in the wrong order..   or is it my imagination and it doesn't matter?
And if it is wrong, do the partitions needed to be moved somehow or deleted and recreated?     Can the path name be changed?

---

### Post by Hippytaff on 2011-03-21
There are arguments about order and speed etc etc...Mine is / then /home then /swap.

But I doesn't really matter I don't think

---

### Post by jagdefalke on 2011-03-21
> **Hippytaff said:**
> There are arguments about order and speed etc etc...Mine is / then /home then /swap.

But I doesn't really matter I don't think

Which was what I wanted to do, and I'm not sure how it came out this way but I want to change it.     So I'm wondering if I need to delete all the partitions in the extension and start over, or if I can fix it some other way.

---

### Post by Hippytaff on 2011-03-22
You can move partitions around, but you need to do it from a live CD/USB and things can get messy and broken. I personally woud start again, but it's up to you...just back up everything that you can't live without

---

