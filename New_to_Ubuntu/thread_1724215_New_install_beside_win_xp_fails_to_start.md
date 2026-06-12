---
title: "New install beside win xp fails to start"
date: 2011-04-08
forum: New to Ubuntu
---

### Post by tracktop on 2011-04-08
Hi All
New here and got a problem - yep I'm unique - not.
Also know next to zip about linux

So please help if you can with where to start next without breaking it any more..

I have a win XP machine
tried cd boot version and seemed to work ok and worth a further look but rebooting lost any addons / changes etc.
SO
added a separate addition hard drive ( now has 3 )
XP is 32 bit
Using wubi installed ubuntu 10.10 desktop 64 bit ( I have amd64 processor?) to the new drive with 2 primary partitions on. ( installed to 2nd primary partition ( drive F: in win) 
updated 300+mb after auto install, rebooted as requested.
get to choose win or ubuntu OK
windows still works fine after selected - so far
choose ubuntu and get a fair way through the startup then got
the /dev/sda2 does not exist dropping to shell error
looked around for a solution but all other occurrences of this fault seem to be unable to get win working or start ubuntu and solutions seem to be grub??? related 
mine seems to get well past that
Thought it might be a partition problem so in win deleted both partitions and reformatted
the new drive with on partition.
Reran the wubi again and it seemed to reinstall OK. - didn't do the update this time
also didn't get to choose which file to use to reinstall from so there must be bits left ther on the Win drive.???????
win still works - so far :-)
but now when starting ubuntu after a number of screens and lots of text scrolling past fast then I get. 
alert /host/ubuntu/disk/root.disk does not exist

There were a couple of warnings during the install but they vanished off the screen before I could note what they were. - something not being found

Thanks in advance

---

### Post by Rubi1200 on 2011-04-08
Hi and welcome to the forums :-)

The best way for us to help you is if you post the results of the following diagnostic script:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by tracktop on 2011-04-09
Hi Rubi

Thanks for the welcome and the help and good instructions.
code below as requested.

 so much info to look at and thing to learn




```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No known boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr /wubildr

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   488,392,064   488,392,002   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   156,295,439   156,295,377   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 300.1 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   586,051,199   586,051,137   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       af97ec70-fcc5-4da5-b0e5-a92099ff8b72   ext4                                     
/dev/sda1        00F05434F05431E0                       ntfs       ubuntu                        
/dev/sda: PTTYPE="dos" 
/dev/sdb1        380C93750C932D3E                       ntfs       XpvrDrive                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        92E8174FE81730C9                       ntfs                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/92E8174FE81730C9  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


======================== sda1/Wubi/boot/grub/grub.cfg: ========================

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
}

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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.35-22-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 00f05434f05431e0
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, Linux 2.6.35-22-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 00f05434f05431e0
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sdc1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 92e8174fe81730c9
    drivemap -s (hd0) ${root}
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

============================= sda1/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sda1/Wubi: Location of files loaded by Grub: =================


   4.6GB: boot/grub/grub.cfg
   4.8GB: boot/initrd.img-2.6.35-22-generic
  13.7GB: boot/vmlinuz-2.6.35-22-generic
   4.8GB: initrd.img
  13.7GB: vmlinuz

================================ sdc1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect /usepmtimer 
C:\wubildr.mbr = "Ubuntu" 
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdb

00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 f0 00 00 00 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  4f ec ef 03 00 00 00 00  |........O.......|
00000030  00 00 0c 00 00 00 00 00  c4 fe 3e 00 00 00 00 00  |..........>.....|
00000040  f6 00 00 00 01 00 00 00  e1 25 ae 74 33 ae 74 c6  |.........%.t3.t.|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb b8 c0 07  |.....3.....|....|
00000060  8e d8 e8 16 00 b8 00 0d  8e c0 33 db c6 06 0e 00  |..........3.....|
00000070  10 e8 53 00 68 00 0d 68  6a 02 cb 8a 16 24 00 b4  |..S.h..hj....$..|
00000080  08 cd 13 73 05 b9 ff ff  8a f1 66 0f b6 c6 40 66  |...s......f...@f|
00000090  0f b6 d1 80 e2 3f f7 e2  86 cd c0 ed 06 41 66 0f  |.....?.......Af.|
000000a0  b7 c9 66 f7 e1 66 a3 20  00 c3 b4 41 bb aa 55 8a  |..f..f. ...A..U.|
000000b0  16 24 00 cd 13 72 0f 81  fb 55 aa 75 09 f6 c1 01  |.$...r...U.u....|
000000c0  74 04 fe 06 14 00 c3 66  60 1e 06 66 a1 10 00 66  |t......f`..f...f|
000000d0  03 06 1c 00 66 3b 06 20  00 0f 82 3a 00 1e 66 6a  |....f;. ...:..fj|
000000e0  00 66 50 06 53 66 68 10  00 01 00 80 3e 14 00 00  |.fP.Sfh.....>...|
000000f0  0f 85 0c 00 e8 b3 ff 80  3e 14 00 00 0f 84 61 00  |........>.....a.|
00000100  b4 42 8a 16 24 00 16 1f  8b f4 cd 13 66 58 5b 07  |.B..$.......fX[.|
00000110  66 58 66 58 1f eb 2d 66  33 d2 66 0f b7 0e 18 00  |fXfX..-f3.f.....|
00000120  66 f7 f1 fe c2 8a ca 66  8b d0 66 c1 ea 10 f7 36  |f......f..f....6|
00000130  1a 00 86 d6 8a 16 24 00  8a e8 c0 e4 06 0a cc b8  |......$.........|
00000140  01 02 cd 13 0f 82 19 00  8c c0 05 20 00 8e c0 66  |........... ...f|
00000150  ff 06 10 00 ff 0e 0e 00  0f 85 6f ff 07 1f 66 61  |..........o...fa|
00000160  c3 a0 f8 01 e8 09 00 a0  fb 01 e8 03 00 fb eb fe  |................|
00000170  b4 01 8b f0 ac 3c 00 74  09 b4 0e bb 07 00 cd 10  |.....<.t........|
00000180  eb f2 c3 0d 0a 41 20 64  69 73 6b 20 72 65 61 64  |.....A disk read|
00000190  20 65 72 72 6f 72 20 6f  63 63 75 72 72 65 64 00  | error occurred.|
000001a0  0d 0a 4e 54 4c 44 52 20  69 73 20 6d 69 73 73 69  |..NTLDR is missi|
000001b0  6e 67 00 0d 0a 4e 54 4c  01 00 00 00 73 20 00 01  |ng...NTL....s ..|
000001c0  01 00 07 ef ff ff 3f 00  00 00 d1 e0 50 09 00 00  |......?.....P...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by tracktop on 2011-04-10
mmmmmmmm
been wading through looking for solutions and.
from what I can see especially reading "[B]Wubi megathread"
[/B]I still a few problems.
easiest fix from what I can see would be to us XP fixmbr, fixboot  to repair my win drive and start again differently.
BUT these commands don't work on a AMD64 processor machine. Tried, and as all the win docs and searches reveal, it appears to be true. So no easy fix for my mbr :-(
The other listed fixes seem to be a side step and have the potential of destroying my XP boot that still works, and I would like to keep it that working, as you may well imagine

At this stage I am wondering if Ubuntu is really worth the switch????

Especially considering the Ubuntu home page??? was promoting switching and using the wubi as a valid load option when this forum shows there have been major issues with using it for some time. 

I am still a bit confused as I seem to read that wubi is meant for a ubuntu install on the same partition as windows using a file as the ub system???? but my ubuntu is on a separate drive and partition???? yet I used wubi to do my install.

---

### Post by Rubi1200 on 2011-04-10
Hi,
sorry for the delayed response; been pretty busy lately.

Before you make any more changes, I want forum member bcbc, an expert on Wubi installs, to take a look at the script results and offer advice.

Please be patient and wait for one of us to post again.

Thanks.

---

### Post by tracktop on 2011-04-10
Thanks - no changes done - just trying to learn and understand more :-)
Tis a busy place here.

---

### Post by bcbc on 2011-04-10
1. fixmbr and fixboot are only useful if your windows is not booting. The first repairs the bootloader, and the second repairs boot sector on the windows partition.
If you are able to boot windows, which it sounds like you are... this is not required.

2. If you have a whole drive dedicated to Ubuntu, then why do you want to run Wubi? Wubi is mostly for people to try Ubuntu without partitioning - which in your case doesn't seem to be an issue. I am curious as to why the new drive shows up first in the bios order.

3. Regarding the Wubi - I can't see anything wrong. But I suspect that there was some sort of corruption to the initial ram disk required to boot. I don't think there's an issue finding the root.disk as otherwise you wouldn't have got that far.

4. So, if you want Wubi, I'd just reinstall.

PS I didn't really understand what you meant about this:
> Reran the wubi again and it seemed to reinstall OK. - didn't do the update this time
also didn't get to choose which file to use to reinstall from so there must be bits left ther on the Win drive.???????
If you formatted the drive, there is definitely nothing of substance left over. Maybe just the bits on your Windows drive.

---

### Post by tracktop on 2011-04-10
Hi and thanks for looking at my problem :grin:

1.  Yes window boots and works fine - I get a menu asking if I want to boot  windows or Ubuntu with windows being the 1st selection and countdown  for auto selection.

2. I thought from my initial reading that  Wubi looked like the simplest, easy, foolproof way to have dual a boot  system. Yes I have a drive to dedicate to Ubuntu. 
I have a legacy win/office/database program that I need to use at times so need to keep win as well.
Windows  boot drive is primary Sata, other 2 drives are IDE - 2nd windows drive  does not have a widows system on it and is purely storage. 
Bios 1st  page lists in order IDE master (sda1?), slave(sdb1) then IDE CD/DVD  master and slave, then Sata 1 ( sdc1) 2,3, 4 ??????????
Bios Drive Boot order is selected as sdc1,sda1,sdb1

3. Ram disk required to boot ????  

4.  Wubi required, not necessarily. I would just like a boot menu to select  windows or Ubuntu. Prefer if they were on separate drives, the less  dependent on each the better.

Install process and order as I recall :-)

 formatted a new drive and made 2 partitions 150gb (1) and 100gb (2)
ran wubi and selected partition 2 as I thought I would use the smaller partition and keep the larger one as a backup area.
After  install Ubuntu seem to work fine ( no reboot yet ) so did the updates  as system suggested. I have an nvidia video card (reading there seems to  be some issues there maybe?)  so also loaded suggested recommended  drive.
Rebooted and system would not fully start Ubuntu when selected. Win OK.

Started  looking for answers and read ( or interpreted rightly or wrongly )  somewhere, something about Ubuntu needing to be installed on the 1st  partition for some reason or other. So thought mmmmm mines on the 2nd  one - maybe need to fix that.
So deleted both partitions, reformatted the drive, made it 1 partition then reran Wubi again.  
This time I did not get a choice about where to install it as I did the 1st time, ( it seemed more like a reinstall process than an fresh install ) but it  seemed to install OK and then start Ubuntu. Thought the problem may have  been caused by the updating so shut down and rebooted.
Same ( or similar) issue as after the 1st try.

So I guess I have done a 2nd Wubi install already - with a format and partition change in between 

Should I try to run Wubi again or do you have some other suggestions considering I really want Ubuntu on it's own drive?

Also
If I disconnect the Ubuntu ( new) drive ( sda1) and restart the computer, it starts into the Win/Ubuntu menu. 
Selecting Win works fine.
Selecting Ubuntu brings up an immediate error - I'll need to check what it is if it is important or helps ? 

Thanks again

 


> **bcbc said:**
> 1.  fixmbr and fixboot are only useful if your windows is not booting. The  first repairs the bootloader, and the second repairs boot sector on the  windows partition.
If you are able to boot windows, which it sounds like you are... this is not required.

2. If you have a whole drive dedicated to Ubuntu, then why do you want  to run Wubi? Wubi is mostly for people to try Ubuntu without  partitioning - which in your case doesn't seem to be an issue. I am  curious as to why the new drive shows up first in the bios order.

3. Regarding the Wubi - I can't see anything wrong. But I suspect that  there was some sort of corruption to the initial ram disk required to  boot. I don't think there's an issue finding the root.disk as otherwise  you wouldn't have got that far.

4. So, if you want Wubi, I'd just reinstall.

PS I didn't really understand what you meant about this:

If you formatted the drive, there is definitely nothing of substance  left over. Maybe just the bits on your Windows drive.

---

### Post by bcbc on 2011-04-10
That's OK... if you disconnect the drive with Ubuntu I know what it will say. It ends with 'grldr not found'.

So... wubi is the easiest way to try ubuntu for most windows users because it can be installed on their windows 'drive'. It's easy to try, and easy to uninstall. You can also install it on other 'drives' - it doesn't generally matter which one. There is no requirement for Ubuntu to be on the first partition (wubi or normal Ubuntu).

For a user who is able to add drives, and format partitions, the wubi advantage is diminished and the disadvantage is increased.
---------------

Regarding your current issue... the [initial ram disk]("http://en.wikipedia.org/wiki/Initrd") isn't always correctly created. I don't know the reasons but I've seen a number of users affected by this (not just wubi). Since it's a fresh install there is no point in trying to fix it - it's easier to reinstall.

If you want wubi again, then
1) uninstall
2) run chkdsk on the partition from windows (my computer, right click on 'drive', properties, tools, check disk for errors, check off the repair automatically
3) reinstall.

You can just as well install Wubi on drive C: - there is no real advantage to installing it on a different partition unless it's because there is no space available.

If you choose to install Ubuntu normally to /dev/sda1, then make sure you 
1) install grub2's bootloader to the /dev/sdc (the drive that bios boots first) 
or 2) change the bios boot order to boot /dev/sda first (probably preferable as it leaves /dev/sdc untouched)

---

### Post by tracktop on 2011-04-10
Thanks lots

looks like your last line is my best option - forget wubi, not much room left on sdc anyway

Install Ubuntu and boot off sda rather than the windows drive ( I like this option, wish I had gone this way first -  thanks)

The process to follow as I see it

reformat sda
set bias to boot off sda ( cd 1st of course )
run ubuntu from cd
select full install ???? rather than trial run
Follow the screen :-)


I have read where others have disconnected their windows drive to do this, to ensure that it remains uneffected but I assume if I do this in may stop any choice I may be given to set up a dual boot  - or is this not valid, ie need to be set later?


any other tips before I venture

Thanks

---

### Post by tracktop on 2011-04-10
Hi
I assume I am best using the 64bit edition? or is there not a lot of advantage between it and 32 bit version for general use.
Are there disadvantages with the 64bit edition - ie less drivers???

As I am just testing the waters and learning am I better starting with ver 10.10 or ver 11 beta or doesn't it matter too much.

---

### Post by bcbc on 2011-04-10
> **tracktop said:**
> Hi
I assume I am best using the 64bit edition? or is there not a lot of advantage between it and 32 bit version for general use.
Are there disadvantages with the 64bit edition - ie less drivers???

As I am just testing the waters and learning am I better starting with ver 10.10 or ver 11 beta or doesn't it matter too much.

I wouldn't go with the beta if you're new to Ubuntu. Either 10.04 or 10.10. I think 10.04 is probably better but that's a personal choice.

Re. 64-bit. I honestly don't know. I've heard that there are some flash issues with 64-bit, but other than that it should be good. On the other hand, I don't think you lose anything going 32-bit.

Since you have 300GB to play with you might consider some manual formatting... some people reckon it's good to split /home onto it's own partition. I usually don't bother - but since you have so much space you could also consider having a shared partition that windows can access as well - maybe ntfs. 

You don't have to preformat - you can do that all from the Ubuntu install CD. Or some people boot it first ("Try it" or "Try without installing") and then use GParted  (from the System Administration menu to setup their partitions) and then run the installer from the desktop.

You can disconnect the windows drive if you like, and then once it's reconnected, boot Ubuntu, and drop to a terminal (CTRL+ALT+t) and run "sudo update-grub" and it will find Windows and add it to the grub menu. That's probably the safest.

I usually stick to Wubi advice so I recommend looking around for other guides (measure twice, cut once). Note that there are a few differences in the installer (ubiquity) between 10.04 and 10.10 so make sure the guide matches the release you choose.

Here's one such guide: [http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

---

### Post by tracktop on 2011-04-10
Thanks very much
appreciate the effort and advice.

---

### Post by tracktop on 2011-04-29
And still thanks again for your efforts - without your help I probably would have dumped Ubuntu and stick with Windows.
Still finding a bit frustrating at times but getting there.

---

