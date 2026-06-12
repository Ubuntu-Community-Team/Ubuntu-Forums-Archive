---
title: "Dual boot crash on windows side only/need help"
date: 2011-05-07
forum: New to Ubuntu
---

### Post by AbsolutMayhem on 2011-05-07
Hi. I have a dual boot system grub2, vista/ubuntu 10.04, on two separate hard drives.

I had vista, but that disk has crashed. (And yes, I need windows because it is more compatible with my work files, and my kids have games that run on it.)

I originally installed vista, then ubuntu. I tried booting to the Vista side this morning, got an error that boot/disk is corrupt. I am sill able to boot to the  ubuntu disk- so SO glad I had the foresight to install both OS's. I was able to access all my work files on the vista disk, and copy them to the ubuntu disk (thank God!). I plan on copying over all my personal files from that disk if I can so I won't lose everything.  Since I was able to boot to linux, I assume the grub file, which is on the vista disk, is ok.

I have three questions:

Is there a way to check the vista disk to see what happened, and correct it?

And if I need to reinstall the OS, how do I do it if it is being installed 2nd? I ask b/c I know windows "likes" to be installed first, and b/c the grub file is on the first drive.

And, I figure I might as well just install windows 7 if the Vista OS is gone anyway. But will that make the whole process dual boot process nore difficult?

Any help would be much appreciated. I'm pretty good at the tech stuff if I have explicit instructions.

---

### Post by wilee-nilee on 2011-05-07
> **AbsolutMayhem said:**
> Hi. I have a dual boot system grub2, vista/ubuntu 10.04, on two separate hard drives.

I had vista, but that disk has crashed. (And yes, I need windows because it is more compatible with my work files, and my kids have games that run on it.)

I originally installed vista, then ubuntu. I tried booting to the Vista side this morning, got an error that boot/disk is corrupt. I am sill able to boot to the  ubuntu disk- so SO glad I had the foresight to install both OS's. I was able to access all my work files on the vista disk, and copy them to the ubuntu disk (thank God!). I plan on copying over all my personal files from that disk if I can so I won't lose everything.  Since I was able to boot to linux, I assume the grub file, which is on the vista disk, is ok.

I have three questions:

Is there a way to check the vista disk to see what happened, and correct it?

And if I need to reinstall the OS, how do I do it if it is being installed 2nd? I ask b/c I know windows "likes" to be installed first, and b/c the grub file is on the first drive.

And, I figure I might as well just install windows 7 if the Vista OS is gone anyway. But will that make the whole process dual boot process nore difficult?

Any help would be much appreciated. I'm pretty good at the tech stuff if I have explicit instructions.

So from a booted live Ubuntu cd, thumbdrive, or Ubnutu installation lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

This will give us a better look at the whole setup.

---

### Post by AbsolutMayhem on 2011-05-07
WHen I clicked on the #, the only option was to close window..nowhere to paste data.
Here it is:

Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
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
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    22,651,649    22,651,587   7 HPFS/NTFS
/dev/sda2    *     22,652,928   976,771,071   954,118,144   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   958,636,031   958,633,984  83 Linux
/dev/sdb2         958,638,078   976,773,119    18,135,042   5 Extended
/dev/sdb5         958,638,080   976,773,119    18,135,040  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        00980C6B980C6190                       ntfs                                     
/dev/sda2        6A767E9C767E6929                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        5e7abdcb-b8bc-409d-8c7c-c2dd73f44ab2   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        a1613209-3115-4225-bd41-2f21f9dabd77   swap                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)
/dev/sda2        /media/6A767E9C767E6929  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
set default="Windows Vista (loader) (on /dev/sda2)"
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 5e7abdcb-b8bc-409d-8c7c-c2dd73f44ab2
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 5e7abdcb-b8bc-409d-8c7c-c2dd73f44ab2
set locale_dir=($root)/boot/grub/locale
set lang=
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=1200
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-31-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 5e7abdcb-b8bc-409d-8c7c-c2dd73f44ab2
	linux	/boot/vmlinuz-2.6.32-31-generic root=UUID=5e7abdcb-b8bc-409d-8c7c-c2dd73f44ab2 ro  splash  quiet splash
	initrd	/boot/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 5e7abdcb-b8bc-409d-8c7c-c2dd73f44ab2
	echo	'Loading Linux 2.6.32-31-generic ...'
	linux	/boot/vmlinuz-2.6.32-31-generic root=UUID=5e7abdcb-b8bc-409d-8c7c-c2dd73f44ab2 ro single  splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-31-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 5e7abdcb-b8bc-409d-8c7c-c2dd73f44ab2
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 5e7abdcb-b8bc-409d-8c7c-c2dd73f44ab2
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 6a767e9c767e6929
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=5e7abdcb-b8bc-409d-8c7c-c2dd73f44ab2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=a1613209-3115-4225-bd41-2f21f9dabd77 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


   4.4GB: boot/grub/core.img
 182.7GB: boot/grub/grub.cfg
  20.0GB: boot/initrd.img-2.6.32-31-generic
   7.7GB: boot/vmlinuz-2.6.32-31-generic
  20.0GB: initrd.img
   7.7GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf

---

### Post by wilee-nilee on 2011-05-07
You have grub in the sda mbr looking at sda1, where a ntfs partition is.

Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in
partition #1 for /boot/grub.

Your Ubuntu is sdb1, always put the grub bootloader in the mbr of the HD where Ubuntu is installed. So go to the bios move the sdb as read first, boot a live cd equal to the Ubuntu install open a terminal and run these two commands.
```
sudo mount /dev/sdb1 /mnt
```
then
```
sudo grub-install --root-directory=/mnt /dev/sdb
```
Reboot to the grub menu login to the install, and run this command.
```
sudo update-grub
```
Here is a link to where I got the commands.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

You can reset the mbr of the sda with a MS bootloader as well using a recovery or Vista install disk.
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
BootRec.exe /fixmbr 
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

There is also a Linux bootloader called lilo that can be put in the sda mbr ask if needed, personally I like to se a MS bootloader put back, both work though.

I'm presuming as well here that sdb is not limited to being a slave drive.

Also even if this fixes your problem look in my signature there is a manual method for wrapping the text in code tags, if you can wrap them it will be easier for others to read it and help others.;)

---

### Post by AbsolutMayhem on 2011-05-07
Thanks for getting back to me so quickly. THIS is why I like Ubuntu so much better than windows.

Just so I'm clear:

The bootloader on my machine is on the wrong disk, so I have to move it, correct? (The guys at Best Buy set up my original configuration- so I blame them).

So here's how I'm reading your instructions- 

I go into bios at startup, and change boot order to the ubuntu disk (sdb). (I think right now it's set to boot from CD drive first.)

I then reboot, with the live CD in place.(Will that work if I change the boot order away from the CD boot first? Or do I go into bios with the live CD in place?)

Then I go into ubuntu from the live disk (*not* from sdb), & open a terminal to put in the 1st two lines of code you gave me.

Then I reboot without the live cd, go into ubuntu, open a terminal, and update grub. 

I reboot again, putting in the windows recovery disk, and use the repair function.

Re: the slave drive thing, I don't know. When I bought his pc I asked the Best Buy guys to make my machine bootable from eiher drive, as I've had window crashes before and lost eveything, and I wanted to avoid that with this pc. Is there a way to figure out if sdb is a slave? And if it is, does that in any way change my 'how to'?

Thanks again for the quick reply. (You can see what I mean about needing explicit instructions from my post here.)

---

### Post by wilee-nilee on 2011-05-07
> **AbsolutMayhem said:**
> Thanks for getting back to me so quickly. THIS is why I like Ubuntu so much better than windows.

Just so I'm clear:

The bootloader on my machine is on the wrong disk, so I have to move it, correct? (The guys at Best Buy set up my original configuration- so I blame them).

So here's how I'm reading your instructions- 

I go into bios at startup, and change boot order to the ubuntu disk (sdb). (I think right now it's set to boot from CD drive first.)

I then reboot, with the live CD in place.(Will that work if I change the boot order away from the CD boot first? Or do I go into bios with the live CD in place?)

Then I go into ubuntu from the live disk (*not* from sdb), & open a terminal to put in the 1st two lines of code you gave me.

Then I reboot without the live cd, go into ubuntu, open a terminal, and update grub. 

I reboot again, putting in the windows recovery disk, and use the repair function.

Re: the slave drive thing, I don't know. When I bought his pc I asked the Best Buy guys to make my machine bootable from eiher drive, as I've had window crashes before and lost eveything, and I wanted to avoid that with this pc. Is there a way to figure out if sdb is a slave? And if it is, does that in any way change my 'how to'?

Thanks again for the quick reply. (You can see what I mean about needing explicit instructions from my post here.)

You have it :) the sdb should just be before the sda the cd can be before them for booting a cd.

Grub will be your bootloader this way, but by putting the MS bootloader back in the sda it will boot just windows if you have the sda before the sdb in the bios.

So just for information there is a post bios menu to choose what you want to boot from ie, cd, sda, sdb, floppy...etc. This is reached with a key prompt like going to the bios, mine is f12, usually the booting of a live ubuntu cd will tell you at the bottom what key does this.

Actually if you can boot to the Ubuntu you would run these two command for the same outcome.
```
sudo grub-install /dev/sdb
```
then
```
sudo update-grub
```

I was not sure if you were getting in to the Ubuntu, the script as it looks says you aren't, but stranger things have happened.

---

### Post by AbsolutMayhem on 2011-05-07
Yes, I can get into ubuntu fine. Makes things a lot easier.

I ran the two script lines in ubuntu (grub-install to sdb, then update grub)

So now I just have to change the boot order (cd is #1, sdb #2, sda last), then run the windows recovery disk, right?

Thanks again.

---

### Post by wilee-nilee on 2011-05-07
> **AbsolutMayhem said:**
> Yes, I can get into ubuntu fine. Makes things a lot easier.

I ran the two script lines in ubuntu (grub-install to sdb, then update grub)

So now I just have to change the boot order (cd is #1, sdb #2, sda last), then run the windows recovery disk, right?

Thanks again.

That is it, now you know the secret that will make your life easier. Once a person understands the mbr and how to load it, there's no stopping you from installing as many OS's as you want, with knowing the use of extended type partitions for linux.

I assume when you ran the update-grub you saw the same lines you see in the grub menu including Vista.

---

