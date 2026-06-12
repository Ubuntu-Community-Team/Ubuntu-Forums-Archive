---
title: "Help with Grub2"
date: 2010-05-29
forum: New to Ubuntu
---

### Post by Keith Myers on 2010-05-29
Just installed my first experience with Linux, Ubuntu 10.04 LTS. I had a dilemma with where to put it on my two hard drives. I think I goofed. I had doubts of whether I could protect my OS/2 Boot Manager and emergency recovery OS/2 partition on my first HDD. I finally decided to delete the partitions entirely in order to give Ubuntu the entire hard drive to play in. I figured I would just use the Grub 2 boot loader to get access to my eComStation operating system on the other drive. Well, the short reply is that I have spent the last two days trying to get Grub2 to see my other operating system and get it into the grub.cfg file. I have made a executable script to add it in via the update-grub command, I have tried to enter it via the 40_custom script, I have tried to modify the 30_os-prober script; in short I have tried every method and suggestion in dozens of forum posts and google searches that I can find and nothing works. I gather the os-prober can find other linux distros and has no troubles with Macs or Windows, but I have found nothing on how to get it to see OS/2. Also, I have been unable to reload the Boot Manager because I don't have any partitions on either drive at the beginning of the disks and within the 1024 cylinder limits. Now I am limited to setting the first boot disk in the computer BIOS to determine which OS I boot into. It works but is cumbersome and I really would like to get back to using a boot manager of some sort to simply select the OS I want to boot into.

Does anyone have a simple and easy method for Grub2 to see my eComStation operating system?  Thanks in advance.

Cheers,  Keith
:(

---

### Post by drs305 on 2010-05-29
Keith,

First, welcome to the Ubuntu forums.  :-)

Sorry to hear about your experiences but hopefully we'll get someone knowledgeable with your system to come up with the solution (if it's not something the rest of us can figure out).

A good start would be for us to see what is on your system. If you would run the following script and post the results here. You can run it from the LiveCD if necessary.

Use the "#" icon in the post's menu to generate *code* tags and copy the information within the tags. It helps present the results in a more compact format.

[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

---

### Post by Keith Myers on 2010-05-30
OK, this is the output of the boot.info script.  It properly identifies my eComStation hard drive as /dev/sdb1.  I tried every variation of defining this hard drive I could think of and had no luck getting it into the Grub2 bootloader.  Hopeful that someone knows the magic incantation to see the drive.
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       hpfs
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 18.4 GB, 18389272576 bytes
255 heads, 63 sectors/track, 2235 cylinders, total 35916548 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    34,324,479    34,322,432  83 Linux
/dev/sda2          34,326,526    35,915,775     1,589,250   5 Extended
/dev/sda5          34,326,528    35,915,775     1,589,248  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders, total 58633344 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    16,450,559    16,450,497   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        ef502876-5e4a-45e4-9e49-10082b4c970f   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        59eba0d6-cf60-4410-81d6-f31170f3c1c0   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        288F-4814                              hpfs       ECOMSTATION                   
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set default="6"
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
search --no-floppy --fs-uuid --set ef502876-5e4a-45e4-9e49-10082b4c970f
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
search --no-floppy --fs-uuid --set ef502876-5e4a-45e4-9e49-10082b4c970f
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set ef502876-5e4a-45e4-9e49-10082b4c970f
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=ef502876-5e4a-45e4-9e49-10082b4c970f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set ef502876-5e4a-45e4-9e49-10082b4c970f
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=ef502876-5e4a-45e4-9e49-10082b4c970f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set ef502876-5e4a-45e4-9e49-10082b4c970f
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=ef502876-5e4a-45e4-9e49-10082b4c970f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set ef502876-5e4a-45e4-9e49-10082b4c970f
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=ef502876-5e4a-45e4-9e49-10082b4c970f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set ef502876-5e4a-45e4-9e49-10082b4c970f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set ef502876-5e4a-45e4-9e49-10082b4c970f
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=ef502876-5e4a-45e4-9e49-10082b4c970f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=59eba0d6-cf60-4410-81d6-f31170f3c1c0 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   2.3GB: boot/grub/core.img
   3.1GB: boot/grub/grub.cfg
   3.2GB: boot/initrd.img-2.6.32-21-generic
   3.2GB: boot/initrd.img-2.6.32-22-generic
   3.1GB: boot/vmlinuz-2.6.32-21-generic
   2.7GB: boot/vmlinuz-2.6.32-22-generic
   3.2GB: initrd.img
   3.2GB: initrd.img.old
   2.7GB: vmlinuz
   3.1GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 4e 90 49 42 4d 20 34  2e 35 30 00 02 40 01 00  |.N.IBM 4.50..@..|
00000010  00 00 02 00 00 f8 ec 03  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  c1 03 fb 00 80 82 28 14  48 8f 28 45 43 4f 4d 53  |......(.H.(ECOMS|
00000030  54 41 54 49 4f 4e 48 50  46 53 20 20 20 20 00 00  |TATIONHPFS    ..|
00000040  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000050  fa 33 c0 8e d0 bc 00 7c  fb b8 c0 07 8e d8 a1 24  |.3.....|.......$|
00000060  00 a3 4d 00 cd 12 2d 4c  00 25 f0 ff c1 e0 06 a3  |..M...-L.%......|
00000070  4b 00 68 00 30 0f a1 64  66 81 3e 00 00 49 31 33  |K.h.0..df.>..I13|
00000080  58 75 05 c6 06 4f 00 01  c7 06 3e 00 00 00 c7 06  |Xu...O....>.....|
00000090  40 00 00 00 c7 06 45 00  14 00 a1 4b 00 8e c0 2b  |@.....E....K...+|
000000a0  db e8 23 00 ff 36 4b 00  68 82 02 a1 4d 00 26 a3  |..#..6K.h...M.&.|
000000b0  4d 00 26 a2 24 00 66 a1  1c 00 26 66 a3 1c 00 a0  |M.&.$.f...&f....|
000000c0  4f 00 26 a2 4f 00 cb 50  53 51 52 06 a1 3e 00 8b  |O.&.O..PSQR..>..|
000000d0  16 40 00 03 06 1c 00 13  16 1e 00 80 3e 4f 00 01  |.@..........>O..|
000000e0  74 6c 50 a1 1a 00 f6 26  18 00 8b c8 58 f7 f1 a3  |tlP....&....X...|
000000f0  42 00 8b c2 f6 36 18 00  fe c4 88 26 44 00 a2 25  |B....6.....&D..%|
00000100  00 a1 18 00 2a 06 44 00  40 3b 06 45 00 76 03 a1  |....*.D.@;.E.v..|
00000110  45 00 50 b4 02 8b 16 42  00 b1 06 d2 e6 0a 36 44  |E.P....B......6D|
00000120  00 8b ca 86 e9 8b 16 24  00 cd 13 58 72 5d 01 06  |.......$...Xr]..|
00000130  3e 00 83 16 40 00 00 29  06 45 00 76 0b c1 e0 05  |>...@..).E.v....|
00000140  8c c2 03 d0 8e c2 eb 84  07 5a 59 5b 58 c3 57 8b  |.........ZY[X.W.|
00000150  3e 24 00 8b 0e 45 00 8d  36 72 02 c7 04 10 00 89  |>$...E..6r......|
00000160  5c 04 8c 44 06 89 4c 02  89 44 08 89 54 0a 66 c7  |\..D..L..D..T.f.|
00000170  44 0c 00 00 00 00 b4 42  8b d7 cd 13 5f 72 ad eb  |D......B...._r..|
00000180  c7 be 7e 08 eb 08 be 02  02 eb 03 be ab 01 e8 09  |..~.............|
00000190  00 be 3e 02 e8 03 00 fb  eb fe ac 3c 00 74 09 b4  |..>........<.t..|
000001a0  0e bb 07 00 cd 10 eb f2  c3 1d 00 41 20 64 69 73  |...........A dis|
000001b0  6b 20 72 65 61 64 20 65  72 72 6f 72 20 6f 63 63  |k read error occ|
000001c0  75 72 72 65 64 2e 0d 0a  00 07 4f 53 32 4b 52 4e  |urred.....OS2KRN|
000001d0  4c 06 4f 53 32 4c 44 52  07 4f 53 32 42 4f 4f 54  |L.OS2LDR.OS2BOOT|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

Thanks in advance,  Keith:)

---

### Post by Keith Myers on 2010-05-31
Anyone want to take a crack at my problem? :confused:

---

### Post by drs305 on 2010-05-31
> **Keith Myers said:**
> Anyone want to take a crack at my problem? :confused:

I'll at least bump the thread with this one. I don't have any experience with the eComStation and haven't seen the 'unknown bootloader' message before. So my response is very generic and assumes your sdb partition is not in disarray.

I think the next step would be to make a custom entry and see if you can get Grub2 to chainload into your other OS. If the other OS's bootloader is working you can just try passing control to it and see what happens.

Open /etc/grub.d/40_custom for editing as root:
```
gksu gedit /etc/grub.d/40_custom
```
The original lines are in blue. The bold black line is added only to provide feedback in the terminal as 'update-grub' is run. Below the existing lines blue lines is the new section:
> 
[COLOR="Blue"]#!/bin/sh[/COLOR]
**echo "Adding 40_custom." >&2**
[COLOR="Blue"]exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.[/COLOR]

menuentry "eComStation" {
insmod ntfs
set root=(hd1,1)
chainloader +1
}

Save the file, then upate-grub:
```
sudo update-grub
```

As you run the update, watch the terminal for any error messages.

This would be the absolutely most basic entry that might work. You may need to load other modules as well but I'm just not familiar with the OS.

---

### Post by oldfred on 2010-05-31
I do not know OS/2, except a lifetime ago I did boot warp when it was a box of diskettes to load.

It looks like OS/2 keeps part of its boot files in that boot partition just like win7 keeps essential boot files in the 100mb boot partition. Or it is like in Ubuntu creating a separate /boot partition. But it seems to be more like windows with data in the PBR or with grub installed to the partition boot sector.

When you deleted the OS/2 boot partition you removed the files needed to boot. The script does not see OS/2 data as it is not in the list of things it looks for.

More discussion of boot partition.
[http://ps-2.kev009.com:8081/tavi/os2pages/boot.html](http://ps-2.kev009.com:8081/tavi/os2pages/boot.html)
 The boot sector is generally updated by using the SYSINSTX command. 


It looks like OS2 is like windows in that boot info is put into a  partitions boot sector or PBR. And that then continues booting. I do not know if you can put that into the OS/2 partition's boot sector and use drs305's chainload entry or not.

  ****

If the SYSINSTX command installs to the OS/2 partition then drs305 chainboot entry should then work. 

OR you need to recreate the /boot partition (you may not need the recovery files to allow booting) and copy the files back. It needs to be a primary partition and set with the boot flag so it is active. I do not know if you can put it on your OS/2 drive's  partition but now it has valuable data and would be higher risk. You can create the OS/2 /boot partition with gparted on your first disk and reinstall Ubuntu with less risk of data loss.

I do not like going from one drive to another for booting as both drives must be working for either system to boot. I prefer to have each drive have a stand alone system and use Ubuntu's grub to allow booting into the other drive's systems.

---

### Post by Keith Myers on 2010-05-31
Hi oldfred and thanks for taking a look at this.  I believe that OS/2 simply puts its boot files into the main partition or logical volume that you install it into.  There are several hidden files along with the main configuration file config.sys that is always visible and mainly sets up how OS/2 is configured.  No separate boot partition.  What I was referring to in the OP was that I had installed OS/2's Boot Manager which is a separate boot loader and was using that to either boot into eComStation or my maintenance partition made with BOOTOS2.  The Boot Manager was in its separate 7MB partition in the beginning of the SCSI disk.  I stupidly deleted it because I was unsure of what Ubuntu was trying to do to it when I first started the installation and it proclaimed that it was going to do rude things to the SCSI drive which is where I installed Ubuntu.  I thought I would just use the Grub2 boot loader to get back to using a boot manager to make my OS choice.  I can easily make another BOOTOS2 volume on the IDE disk where eComStation resides in a 8GB primary partition.  I have 20GB of unused disk space on that disk.  I have no problem simply selecting that disk as the first boot choice in the BIOS and boot normally into eComStation.  When I want to boot into Ubuntu, I just change my selection to the SCSI disk.  I just want to avoid the extra time to configure the BIOS and subsequent reboots to get back to using some sort of boot loader.  Unfortunately, I can't reinstall Boot Manager anywhere unless I delete partitions and start over to give Boot Manager the first part of some disk.  I may just do that to Ubuntu and start all over again if I can't make Grub 2 work.

I know about SYSINTX in OS/2 as that is the normal way to make a OS/2 boot entry.  I'm not sure if it relevant as I stated above, eComStation is fine and boots normally. It's looking likely I will follow your suggestion and blow away the Ubuntu installation and go back to installing Boot Manager on the SCSI disk and then make the BOOTOS2 maintenance partition and then somehow get Ubuntu to install without screwing things up.  If the Ubuntu hadn't sent me all kinds of dire messages about re-partitioning the entire disk and not seemingly acknowledging my OS/2 operating systems I wouldn't have deleted the OS/2 partitions on the disk and let the Ubuntu installation have the rest of the disk.  I got really confused when it asked me to create the /SWAP partition.  I didn't know anything about that and I decided if I just let it do an automatic installation and have the entire disk to work with, the least amount of things would go wrong.  I really would have like to keep OS/2 on its own separate disk and Ubuntu on its own separate disk but in order to do that I would have to somehow backup my entire 8GB eComStation and then repartition that disk so that I could give Boot Manager the beginning of the disk.

Thanks for the suggestions.

Cheers,  Keith:)

> **oldfred said:**
> I do not know OS/2, except a lifetime ago I did boot warp when it was a box of diskettes to load.

It looks like OS/2 keeps part of its boot files in that boot partition just like win7 keeps essential boot files in the 100mb boot partition. Or it is like in Ubuntu creating a separate /boot partition. But it seems to be more like windows with data in the PBR or with grub installed to the partition boot sector.

When you deleted the OS/2 boot partition you removed the files needed to boot. The script does not see OS/2 data as it is not in the list of things it looks for.

More discussion of boot partition.
[http://ps-2.kev009.com:8081/tavi/os2pages/boot.html](http://ps-2.kev009.com:8081/tavi/os2pages/boot.html)
 The boot sector is generally updated by using the SYSINSTX command. 


It looks like OS2 is like windows in that boot info is put into a  partitions boot sector or PBR. And that then continues booting. I do not know if you can put that into the OS/2 partition's boot sector and use drs305's chainload entry or not.

  

If the SYSINSTX command installs to the OS/2 partition then drs305 chainboot entry should then work. 

OR you need to recreate the /boot partition (you may not need the recovery files to allow booting) and copy the files back. It needs to be a primary partition and set with the boot flag so it is active. I do not know if you can put it on your OS/2 drive's  partition but now it has valuable data and would be higher risk. You can create the OS/2 /boot partition with gparted on your first disk and reinstall Ubuntu with less risk of data loss.

I do not like going from one drive to another for booting as both drives must be working for either system to boot. I prefer to have each drive have a stand alone system and use Ubuntu's grub to allow booting into the other drive's systems.

---

### Post by oldfred on 2010-05-31
From what I read the boot manager is like windows in that it has to be a primary partition, not necessarily the first partition. I think it is like window only because they both have the same history.
Early versions of OS/2 were designed by Microsoft and IBM/s updates probably did not change booting that much.

The ancient MBR partition scheme is still used and windows, and it looks like OS/2 (and lilo) all use a simple boot loader in the MBR that just looks for an active (boot flag) primary partition and then jumps to the PBR or partition boot sector to continue booting.

If you can boot then drs305 chainload entry should work at that just jumps to the PBR like the simple MBR boot loaders do.

---

### Post by Keith Myers on 2010-05-31
Hi dr305 and thanks for the help. I have tried several times to put entries into 40_custom.  The entries go into the config.cfg file at the bottom where it reads 40_custom, its just that nothing ever shows up in the actual Grub2 boot menu.  The one thing different I notice in you script is that you are using the insmod ntfs definition.  This is where I was different. My entry was an insmod hpfs entry.  I have since noticed in other posts and with the output of the boot.info script that basically, linux seems to consider ntfs and hpfs to be more or less the same type of file system.  I was the understanding that they are distinct and different types of file systems.  I certainly can't read any kind of ntfs file system within OS/2.  I never felt it necessary to try to install any of the buggy nfts readable addons to eComStation.  I am very happy sticking with eComStation.  All of my word processing and financial information is contained within OS/2 programs with no easy way to get that data into a different operating system.  I was just trying to get to a point with an operating system that would get me current multimedia access to Internet content and such.  I have no love for Windows.  I dumped it back in the Windows 3.0 era and went with OS/2 and never entertained any notion of using Windows ever again.

I will try your version of the file type definition but have my doubts.  I think that there is a lot more information that is going to be required for Grub2 to recognize my eComStation installation.  I was hoping that some knowledgeable linux user was also familiar with OS/2.  I have spent days researching everywhere in th OS/2 universe for the information to get Grub2 to acknowledge OS/2 with no success. Most of the information is to easily get Boot Manager or one of the many other OS/2 boot managers to add a linux installation to those boot loaders.  Or how to deal with Windows corruption of any kind of OS/2 operating system or boot loader and ways to get OS/2 working after a Windows installation trashes it.  I have found some tantalizing information that the old LILO boot loader had no troubles seeing OS/2 since they were basically concurrent in history.  I don't know whether that is an option for me.  Do you know whether that is something I should attempt? Or would the more recent first version of Grub be more likely to have success.  Is this something I should consider with the latest Ubuntu 10.04 LTS?

Cheers,  Keith:)

> **drs305 said:**
> I'll at least bump the thread with this one. I don't have any experience with the eComStation and haven't seen the 'unknown bootloader' message before. So my response is very generic and assumes your sdb partition is not in disarray.

I think the next step would be to make a custom entry and see if you can get Grub2 to chainload into your other OS. If the other OS's bootloader is working you can just try passing control to it and see what happens.

Open /etc/grub.d/40_custom for editing as root:
```
gksu gedit /etc/grub.d/40_custom
```The original lines are in blue. The bold black line is added only to provide feedback in the terminal as 'update-grub' is run. Below the existing lines blue lines is the new section:

Save the file, then upate-grub:
```
sudo update-grub
```As you run the update, watch the terminal for any error messages.

This would be the absolutely most basic entry that might work. You may need to load other modules as well but I'm just not familiar with the OS.

---

### Post by Keith Myers on 2010-05-31
Hi oldfred and dr305.  I just put the menuentry for eComStation in 40_custom, this time with a cut and paste from dr305 code suggestion with the insmod ntfs variation, and ran the update-grub command.  In the command window, all it lists are the standard linux distros and memtest86 entries.  Is it supposed to also see my eComStation entry also and echo that back to the terminal?  I haven't tried to reboot yet to check whether Grub2 actually has an entry now.  This is the same behavior I have seen every time I've tried to update Grub2 and never see any mention of eComStation anywhere in the grub.cfg file.  So, off I go once again to see if anything has changed.

Keith:)

---

### Post by drs305 on 2010-05-31
Since I added the extra second line in the 40_custom file you should see a message "Adding 40_Custom" in the terminal as update-grub is run.

Whether the menuentry works or not is irrelevant as far as putting it into grub.cfg via "update-grub" is concerned. If there is no scripting format error, the script should be imported.

If you aren't seeing the item being added (and especially if there is no resulting menu in grub.cfg), check to make sure the /etc/grub.d/40_custom file is executable:
```
sudo chmod +x /etc/grub.d/40_custom
```

As far as the modules to load, I have no idea which modules would be needed to recognize your system. You can insert more than one in the custom file. I used ntfs but it of course may not be the one necessary.

---

### Post by Keith Myers on 2010-05-31
Well, no luck and no change in Grub2 boot loader.  Still no entry for eComStation. I'm also getting a boot error message now (error205) failed to load directory /dev/NULL or something like that. Ubuntu still loads, its just my initial installation just went straight to the Ubuntu splash screen.  Nothing disastrous probably.  I am amazed at how fast Ubuntu loads,  it just flies.  I have a usable desktop in under 10 seconds after the SCSI controller card lists its devices and the screen blanks. Anyone else have any ideas?  I have seen some entries in the grub.cfg online examples that seem to use a UUID entry for a specific hard drive in peoples systems.  Is this something I should try?  I saw a UUID entry in the output of my boot.info script for my eComStation boot drive /dev/sdb1.  Not sure of the syntax I should use to make this kind of entry.  Anyone want to take a stab at another code snippet for me to cut and paste?

Cheers,  Keith:)

---

### Post by Keith Myers on 2010-05-31
Hi drs305, I never have seen the "adding custom entries" at any time in the terminal when I do the the update-grub command.  I checked the 40_custom script's properties and it is marked as an executable shell script.  I then cut and pasted your chmod script into the terminal to be sure the 40_custom file was executable and then tried update-grub.  Still never an echo of the "Adding 40_Custom" to the terminal display.  This what the terminal display has in it:```

```
 keith@keith-desktop:~$ sudo update-grub
[sudo] password for keith: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
done
keith@keith-desktop:~$ sudo chmod +x /etc/grub.d/40_custom
keith@keith-desktop:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
done
keith@keith-desktop:~$ 

```

```

I do see the entry in the grub.cfg file, it just doens't seem to do anything.  This is what is in the grub.cfg file:
```

```
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
set default="6"
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
search --no-floppy --fs-uuid --set ef502876-5e4a-45e4-9e49-10082b4c970f
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
search --no-floppy --fs-uuid --set ef502876-5e4a-45e4-9e49-10082b4c970f
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set ef502876-5e4a-45e4-9e49-10082b4c970f
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=ef502876-5e4a-45e4-9e49-10082b4c970f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set ef502876-5e4a-45e4-9e49-10082b4c970f
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=ef502876-5e4a-45e4-9e49-10082b4c970f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set ef502876-5e4a-45e4-9e49-10082b4c970f
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=ef502876-5e4a-45e4-9e49-10082b4c970f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set ef502876-5e4a-45e4-9e49-10082b4c970f
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=ef502876-5e4a-45e4-9e49-10082b4c970f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set ef502876-5e4a-45e4-9e49-10082b4c970f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set ef502876-5e4a-45e4-9e49-10082b4c970f
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
menuentry "eComStation"{
insmod ntfs
set root=(hd1,1)
chainloader +1
} 
### END /etc/grub.d/40_custom ###
```

```

Does the grub.cfg look like its supposed to after modifying 40_custom and invoking the update-grub command?  Do you have an answer as to why I never have seen the "Adding 40_custom" echo in a terminal window?

Cheers,  Keith:)


> **drs305 said:**
> Since I added the extra second line in the 40_custom file you should see a message "Adding 40_Custom" in the terminal as update-grub is run.

Whether the menuentry works or not is irrelevant as far as putting it into grub.cfg via "update-grub" is concerned. If there is no scripting format error, the script should be imported.

If you aren't seeing the item being added (and especially if there is no resulting menu in grub.cfg), check to make sure the /etc/grub.d/40_custom file is executable:
```
sudo chmod +x /etc/grub.d/40_custom
```As far as the modules to load, I have no idea which modules would be needed to recognize your system. You can insert more than one in the custom file. I used ntfs but it of course may not be the one necessary.

---

### Post by Keith Myers on 2010-05-31
> **drs305 said:**
> Since I added the extra second line in the 40_custom file you should see a message "Adding 40_Custom" in the terminal as update-grub is run.

Whether the menuentry works or not is irrelevant as far as putting it into grub.cfg via "update-grub" is concerned. If there is no scripting format error, the script should be imported.

If you aren't seeing the item being added (and especially if there is no resulting menu in grub.cfg), check to make sure the /etc/grub.d/40_custom file is executable:
```
sudo chmod +x /etc/grub.d/40_custom
```As far as the modules to load, I have no idea which modules would be needed to recognize your system. You can insert more than one in the custom file. I used ntfs but it of course may not be the one necessary.


OK, I see why I don't see the "Adding 40_custom" message in the terminal.  I don't have the echo statement in my default 40_custom file and yours does.

Keith:)

---

### Post by oldfred on 2010-05-31
With grub legacy we would just do a root & chainload entry and if the chainload did not work it crashed.
With grub2 it tries to load a driver/module to check before jumping and can then recover most of the time. But if the ntfs is not reading the hpfs it may just error out.
You could try without the ntfs module (comment out with # insmod ntfs) realizing it may  crash and force total reboot. I did not see a hpfs module in grub.

---

### Post by Miljet on 2010-05-31
Hi Keith,

First the disclaimer, I know absolutely nothing about OS/2 or eComStation.

But the following comment you made > Most of the information is to easily get Boot Manager or one of the many other OS/2 boot managers to add a linux installation to those boot loaders.  reminded me that you can install Ubuntu without GRUB, or any boot loader for that matter. So perhaps you can set up your original boot loader, reinstall Ubuntu without any loader, and then add Ubuntu to your original boot loader. It may be easier that way, especially since you seem pretty familiar with your current loader.

---

### Post by Keith Myers on 2010-05-31
oldfred, well that is how I tried to do it originally without installing any modules.  Didn't work.  Didn't do anything.  Just keep seeing the same old Grub2 menu of the standard choices.  Never have been able to get any kind of eComStation entyr into the menu.

Keith

---

### Post by Keith Myers on 2010-05-31
Hi Miljet, thanks for jumping in and trying to help.  Well I just a couple of hours removing the original Ubuntu installation and get back to a naked drive. I tried too many times to install Boot Manager to the hard drive and always failed.  I can make partitions of whatever size I want and format them and whatever, but can't get Boot Manager installed.  I tried to do stuff with DFSee and no luck there.  I seem to recall when I last installed eComStation, I had a dickens of a time because, OS/2 at that time had many problems with LBA drives, partitions in excess of 1024 cylinders, etc. etc.  That is why I ended up with only a 8.3GB partition on a 30GB drive for the eComStation installation because that is the larges I could get and still stay under 1024 cylinders.  I can't for the life of me figure out why I can't get Boot Manager installed on the beginning of a naked drive.  I think that one of the problems is that in eComStation, they got rid of FDISK and went to Local Volume Manager and MinLVM.  You're supposed to be able to do everything that FDISK could and even more with Compatibility Volumes and ability to work with JFS file systems.  Every time I try to install Boot Manager, the LVM just complain that the operation is not allowed.  I can see now that I really screwed up big time when I deleted my Boot Manager bootloader and maintenance partitiion. I have been entertaining actually trying to install some sort of Windows onto the SCSI drive now and try to see whether their bootloader works and recognized my eComStation drive and OS, but now I have my doubts there too.  I may just have to keep resorting to using the BIOS to select the OS I boot into.  Or give up on this machine entirely and go buy something new with junk pre-installed.

Cheers, Keith

---

### Post by oldfred on 2010-05-31
I do not expect grub's osprober to find OS/2, but you did put drs305 entry into 40_custom to chainboot/chainload to the OS/2 partition where you used SYSINSTX to install to the partition boot sector. It may be different drive, partition depending on where you sysinstx the boot loader.

---

### Post by Keith Myers on 2010-06-01
[SIZE=3]oldfred, I can see what you are saying about SYSINSTX, but have my doubts whether it is really necessary.  My reasoning tells me that I must have eComStation bootloader on the IDE disk; how else would I be able to boot into eComStation when I select that disk as the 1st boot device in the computer BIOS?  At this time, it is literally the ONLY thing left on that disk since I deleted every maintenance partition and extended partition. I tried to do a newmbr a couple of times within the LVM programs and they just said it was not possible. 

Also, I believe that the results.txt developed by the boot.info script shows a valid master boot record on the eComStation disk.  It shows a good and healthy disk with a valid boot record in the Desktop Disk Utility. It's looking to me that the only thing that is going to help me is to get some version of Grub to recognize hpfs partitions with a module or whatever. Or get a customized 30_os-prober script that has the ability to see OS/2.

I really like what I have seen with Ubuntu. It boots really fast, I have access to a flash plugin now which I never did over in eComStation and unfortunately it seems the entire Internet is moving to that coding.  I am really bugged that I have lost access to satellite image animation on all my favorite sites since they moved to flash or a version of Java beyond what is available to me in eComStation 1.05.  I really would like to stick with this OS as it is current and growing.  I just wish there was a simpler way to switch between my old legacy OS and the newer ones.

Cheers,  Keith
:)
[/SIZE]

---

### Post by drs305 on 2010-06-01
Keith,

You may try talking with the grub developers over on their IRC channel. It's #grub on Freenode. The channel is mostly used by the devs to talk amongst each other, so you have to catch them at the right time - sometimes they are talkative and sometimes not. 

If anyone other than eComStation users would know which modules to use and how to load eComStation with Grub2 it would be those people.

---

### Post by oldfred on 2010-06-01
If the MBR is all that is required then you should be able to chainboot to that. Add this to 40_custom and run 
sudo update-grub

menuentry "eComStation" {
set root=(hd1)
chainloader +1
}

---

### Post by Keith Myers on 2010-06-03
[SIZE=3]Well first, I would like to thank all who tried to help me.  I give up.  I have made one step forward and two steps back.  I thought I was getting somewhere finally when I was able to reinstall the OS/2 Boot Manager into a small 100MB primary partition after the 10.04 and swap partitions at the beginning of the disk.  I could see it in the LVM manager and it let me add the bootable partitions to the Boot Manager menu.  I added in my eComStation 1.05 and Ubuntu 10.04 LTS installations and then rebooted.  Lo and behold I booted into the Boot Manager and there were my two selections.  First I checked to see if I could still boot my OS/2 system and it came up fine and dandy.  Did some further verification that all the partitions looked valid and active with DFSee and it reported no errors.  I then rebooted and selected Ubuntu from Boot Manager.  No joy.  Error 3: file system not found. Oh no!  I then booted into the LiveCD and looked at the disk with GParted and it had a blank 1 MB partition at the beginning of the disk.  The main Ubuntu and swap partitions were there and nothing reported wrong.  I figure I had somehow lost the Grub2 bootloader.  Probably that supposed blank 1MB partition at the beginning of the disk is where Boot Manager ACTUALLY went even though it showed up in the middle of the disk view in both DFSee and the LVM Manager.  So I attempted over 2 days to get it back onto the disk with no success.  No Grub found errors.  Error 15 errors.  Install-grub failed.  Tried the Grub-Legacy installation, no joy.  So I decided to just start from scratch and reinstall the OS onto the drive.  I think I am at over 20 installs now.  Everything looked good a couple of times, then bam, all kinds of script errors and all the configurations changes and files added to the Panels all are gone.  Sometimes, not even one icon populates the top and bottom panel.  So reinstall again, over and over.  Some times everything was hunky dory for a few hours and sometimes things went missing.  I finally deduced that it might have something to do with trying to preserve the Firefox and email settings, so I did a full install and thought everything was kosher up until the system crashed to a cursor and frozen mouse pointer.  So, said to hell with trying to keep Boot Manager on the drive and just told the install to take the whole drive again as I did in the first place.  Seems to be holding up mostly now, though, I did get the  messages for the missing icons on the panels again.  This time I acknowledged NOT to delete them and just rebooted and they miraculously reappeared again.  I can see that it was a mistake to downgrade my DSL service to the slowest speed in an attempt to save some money.  I figured I never download anything of any consequence normally except for email.  Wow, that sure is wrong with Linux installations.  EVERYTHING has to come down over the Internet and big pipelines I see reduce the stress and time involved.

So at this point, I give up with trying to have any kind of boot manager around.  I guess I will just go into the BIOS at every reboot to change the boot device to the hard drive containing the operating system I choose to run.

Thanks again for your time and patience.

Cheers,  Keith
:P
[/SIZE]

---

### Post by walt.smith1960 on 2010-06-03
Keith I admire your persistence. I'd have torn out what hair I have long ago. Here is a boot manager that may or may not help you.  I've had good luck with it once I figured out the incantations. It does recognize OS2 and other less common OSs.  The trick when using BootItNG is to install GRUB in the Linux partition, not in the MBR. When installing Ubuntu, screen 7 use the advanced button and place GRUB in sd-whatever.

[http://www.terabyteunlimited.com/bootit-next-generation.htm](http://www.terabyteunlimited.com/bootit-next-generation.htm)

---

### Post by oldfred on 2010-06-03
Did you try the chainboot entry?

I boot from sdc for Karmic and Lucid installed its boot loader into sda. I was using the BIOS to change like you are but to prove the chainboot entry works I set that up in my Karmic grub.cfg.

It did not work at first. Although both Karmic & Lucid see my 3 drives as sda, sdb, & sdc in the same order, something about booting to sdc made the sda drive hd1 not hd0. I assume since I booted with sdc that became hd0 for the chainboot entry.  Once I changed it to hd1, I chainbooted to the MBR of sda and booted Lucid in the same way my using BIOS to switch.

So with an initial boot into sdc this will boot the MBR of sda.

menuentry "Lucid Lynx on sda Chainboot" {
set root=(hd1)
chainloader +1
}

---

### Post by Keith Myers on 2010-06-03
Hi oldfred, yes I tried at least 10 variations of the chainboot entry.  Never saw a hint of OS/2 in any menus or reboots using Grub2.  I may not have commented directly on all the various posts that people have been kind to supply, but I tried every suggestion in many forms and followed all links to read about different success stories from users with similar problems.  Unfortunately nothing I ever read or stumbled across mentioned  anything to do with OS/2.  I think it has been too many years since OS/2 was ever in the awareness of the computing public and no one makes any kind of effort to include such an unpopular legacy OS.:)

Keith

---

### Post by Keith Myers on 2010-06-03
Hi Walt and thanks for jumping in here with your tidbit of info.  This solution looks promising as they seem to acknowledge OS/2 although they make a disclaimer about not being able to use all the normal features of the program because it can't deal with a LVM'd file system. I may try out the demo to see if it works for me.  I guess I will have to install Ubuntu again for the umpteenth time to get the GRUB partition out of the MBR area.  I have downloaded the Boot-It NG manual and have given it a quick read.    Thanks again, there may be hope after all.

Cheers,  Keith:P

---

