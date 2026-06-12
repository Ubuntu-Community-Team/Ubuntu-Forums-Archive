---
title: "Another Windows 7/Ubuntu Lucid dual boot problem"
date: 2010-09-17
forum: New to Ubuntu
---

### Post by Troll_the_Great on 2010-09-17
Hello all!

Like the title says, I have problems trying to dual boot those systems.
I installed Windows 7 first, and the installation had no problems, the system was 100% operational. Then I installed Lucid, and again there were no problems during the installation or with the system. At startup, the Grub is OK, and I can choose between the 2 OS (I mean I can see them listed). If I choose to boot Ubuntu, I have no issues, the system boots OK. But if I choose Windows, as soon as I highlighted and hit "ENTER" the computer just restarts. I don't see any errors, or the Windows logo, the computer restarts as soon as I try to boot the system.
I have as ASUS laptop, 1 GB RAM, and 4 partitions: one for Windows, two for Ubuntu (a boot and a home partition) and a swap partition.
Can you help me?
Thanks in advance!

---

### Post by jtarin on 2010-09-17
Removed

---

### Post by jtarin on 2010-09-17
Removed

---

### Post by jtarin on 2010-09-17
Removed

---

### Post by wilee-nilee on 2010-09-17
Thread starter post the bootscript in my signature, in code tags, as described.

Edit: Also OP did you resize the windows partition with it's disc manager, then reboot before installing to make sure it works? If you did not and used the Ubuntu install to do the re-partitioning, take a look at W7 in gparted in Ubuntu and see if it is flagged and if so what does it say. Gparted can be used to resize W7 partitions but the round to cylinders must not be checked on.

You may have to install gparted if you haven't already.
```
sudo apt-get install gparted
```

---

### Post by Troll_the_Great on 2010-09-18
> **wilee-nilee said:**
> Thread starter post the bootscript in my signature, in code tags, as described.

Edit: Also OP did you resize the windows partition with it's disc manager, then reboot before installing to make sure it works? If you did not and used the Ubuntu install to do the re-partitioning, take a look at W7 in gparted in Ubuntu and see if it is flagged and if so what does it say. Gparted can be used to resize W7 partitions but the round to cylinders must not be checked on.

The partition were already prepared before I install anything, so that's not an issue. Here is my bootscript and a screenshot with gparted.
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
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

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    61,432,559    61,432,497   7 HPFS/NTFS
/dev/sda2          61,432,621   625,121,279   563,688,659   f W95 Ext d (LBA)
/dev/sda5          61,432,623   102,398,309    40,965,687  83 Linux
/dev/sda6         102,398,373   110,591,459     8,193,087  82 Linux swap / Solaris
/dev/sda7         110,591,523   625,121,279   514,529,757  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        A05CC3005CC2D068                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        99df9a18-2f72-4cdd-bc6d-cc3ea02789ed   ext4                                     
/dev/sda6        ef10163a-5f5f-49ed-9624-f631efe6321b   swap                                     
/dev/sda7        becc60e4-1287-4461-ba1f-e967acedb4e9   ext3                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sda7        /home                    ext3       (rw)
/dev/sda1        /media/A05CC3005CC2D068  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
search --no-floppy --fs-uuid --set 99df9a18-2f72-4cdd-bc6d-cc3ea02789ed
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
search --no-floppy --fs-uuid --set 99df9a18-2f72-4cdd-bc6d-cc3ea02789ed
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
	search --no-floppy --fs-uuid --set 99df9a18-2f72-4cdd-bc6d-cc3ea02789ed
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=99df9a18-2f72-4cdd-bc6d-cc3ea02789ed ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 99df9a18-2f72-4cdd-bc6d-cc3ea02789ed
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=99df9a18-2f72-4cdd-bc6d-cc3ea02789ed ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 99df9a18-2f72-4cdd-bc6d-cc3ea02789ed
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=99df9a18-2f72-4cdd-bc6d-cc3ea02789ed ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 99df9a18-2f72-4cdd-bc6d-cc3ea02789ed
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=99df9a18-2f72-4cdd-bc6d-cc3ea02789ed ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 99df9a18-2f72-4cdd-bc6d-cc3ea02789ed
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 99df9a18-2f72-4cdd-bc6d-cc3ea02789ed
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set a05cc3005cc2d068
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
UUID=99df9a18-2f72-4cdd-bc6d-cc3ea02789ed /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=becc60e4-1287-4461-ba1f-e967acedb4e9 /home           ext3    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=ef10163a-5f5f-49ed-9624-f631efe6321b none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  42.4GB: boot/grub/core.img
  42.4GB: boot/grub/grub.cfg
  43.4GB: boot/initrd.img-2.6.32-21-generic
  43.0GB: boot/initrd.img-2.6.32-24-generic
  43.1GB: boot/vmlinuz-2.6.32-21-generic
  43.5GB: boot/vmlinuz-2.6.32-24-generic
  43.0GB: initrd.img
  43.4GB: initrd.img.old
  43.5GB: vmlinuz
  43.1GB: vmlinuz.old
```

---

### Post by wilee-nilee on 2010-09-18
I could be missing something in the bootscript but it looks okay. 

When you installed did you have a open space, or pre-formatted partitions for Ubuntu or did you have Ubuntu resize the Windows partition?

---

### Post by Hobgoblin on 2010-09-18
Doesn't Win7 usually have a small partition as well as the one holding the O/S (about 100MB?).  I don't see it.

---

### Post by wilee-nilee on 2010-09-18
> **Hobgoblin said:**
> Doesn't Win7 usually have a small partition as well as the one holding the O/S (about 100MB?).  I don't see it.

Not if you preformat the partitions this was a upgrade at some point there are XP boot= /boot.ini /ntldr /NTDETECT.COM mixed in the boot partition, all the correct files are the in the script, as far as I can tell. I think that W7 was resized, and not checked to be working before installing, but that is just conjecture.

---

### Post by Troll_the_Great on 2010-09-18
> **wilee-nilee said:**
> I could be missing something in the bootscript but it looks okay. 

When you installed did you have a open space, or pre-formatted partitions for Ubuntu or did you have Ubuntu resize the Windows partition?

No, Ubuntu did not resize the windows partition, the partition were already there.
First, I had dual boot between XP and Ubuntu, and then I decided to switch to Windows 7 and Ubuntu. So, I installed Windows 7 in the partition where I had XP, and then I installed Ubuntu in his old partition (formating it in the process).So no resizing or messing with partitions.
When I dual booted with XP, I didn't have any problems, that's why I'm confused now...

PS: By the way, the Windows 7 installation was working before I installed Ubuntu, I checked it.

---

### Post by Rubi1200 on 2010-09-18
I was just wondering if your extended partition may be the cause of the problems?

> f W95 Ext d (LBA)

My bootscript marks the extended partition as > 5 Extended

See here for possible issues with your extended partition:
[http://www.win.tue.nl/~aeb/partitions/partition_types-1.html](http://www.win.tue.nl/~aeb/partitions/partition_types-1.html)

---

### Post by wilee-nilee on 2010-09-18
> **Rubi1200 said:**
> I was just wondering if your extended partition may be the cause of the problems?



My bootscript marks the extended partition as 

See here for possible issues with your extended partition:
[http://www.win.tue.nl/~aeb/partitions/partition_types-1.html](http://www.win.tue.nl/~aeb/partitions/partition_types-1.html)

I missed that thanks for seeing it;) I have to crash so carry on.

---

### Post by wilee-nilee on 2010-09-18
Looking at the gparted screen shot I see that the LBA is a flag that can be removed, but it would have to be done while the partition is not mounted I assume. I would try that. I'm not sure if this is the problem, but since it is a flag it can be put back. Here is a picture of the flag gui. Right clicking the extended and choosing manage flags brings the gui up.
[ATTACH]169828[/ATTACH]

I think it is more then just the flag though, as sda2 goes. This is not an area I am real familiar with.

---

### Post by Troll_the_Great on 2010-09-18
> **wilee-nilee said:**
> Looking at the gparted screen shot I see that the LBA is a flag that can be removed, but it would have to be done while the partition is not mounted I assume. I would try that. I'm not sure if this is the problem, but since it is a flag it can be put back. Here is a picture of the flag gui. Right clicking the extended and choosing manage flags brings the gui up.
[ATTACH]169828[/ATTACH]

I think it is more then just the flag though, as sda2 goes. This is not an area I am real familiar with.

No use. I removed the flag, but the same thing happens: the computer just restarts when I choose to boot into windows...

---

### Post by jtarin on 2010-09-18
> **Rubi1200 said:**
> I was just wondering if your extended partition may be the cause of the problems?



My bootscript marks the extended partition as 

See here for possible issues with your extended partition:
[http://www.win.tue.nl/~aeb/partitions/partition_types-1.html](http://www.win.tue.nl/~aeb/partitions/partition_types-1.html)It could possibly, but for one thing.....he can boot Linux....that has nothing to do with his inability to boot Win7.

---

### Post by phillipdhall on 2010-09-18
This is probably a dumb question...
 
I noticed that his Win 7 partition is mounted as /media in Ubuntu. Is there a chance that the Ubuntu installation would have done 'something' to that partition?
 
Phil

---

### Post by jtarin on 2010-09-18
> **phillipdhall said:**
> This is probably a dumb question...
 
I noticed that his Win 7 partition is mounted as /media in Ubuntu. Is there a chance that the Ubuntu installation would have done 'something' to that partition?
 
Phil
It's a normal mountpoint directory.

---

### Post by Troll_the_Great on 2010-09-18
Thanks everybody for your cooperation (especially jtarin), the problem is solved!
I fixed the MBR with the Windows 7 installation disk, reinstalled GRUB on the Ubuntu partition, booted into windows and installed EasyBCD and then added the Ubuntu entry.
Thanks again jtarin!
All the best!

---

### Post by jtarin on 2010-09-18
> **Troll_the_Great said:**
> Thanks everybody for your cooperation (especially jtarin), the problem is solved!
I fixed the MBR with the Windows 7 installation disk, reinstalled GRUB on the Ubuntu partition, booted into windows and installed EasyBCD and then added the Ubuntu entry.
Thanks again jtarin!
All the best!Your more than welcome...I'm glad to see you up and running. Anytime you need help...just ask.;)

---

### Post by wilee-nilee on 2010-09-18
Glad you have it going.;) Thanks to jtarin for getting it going, we do need people who know the easybcd stuff as it is a great alternative.

Personally though I always try to get the native bootloader working, and I want to see the whole setup (bootscript) before suggesting a fix generally.

---

### Post by zazootheparrot on 2010-10-14
Hello there,

I have an ubuntu 10.04 Lucid Lynx running on a Sony Vaio VGN-SZ740.  During the past week I've had a problem with the operating system  booting. It happened after I did the usual update of the system using  the update manager.
It's worth mentioning that I have a Linux/ Windows 7 dual boot but they  all worked fine before. Here's what I see in the GRUB page when I start  my computer:
```
GNU GRUB version 1.98-ubuntu 7
Ubuntu, with linux 2.6.32-25-generic
Ubuntu, with linux 2.6.21-25-generic (recovery mode)
Ubuntu, with linux 2.6.21-24-generic
Ubuntu, with linux 2.6.21-24-generic (recovery mode)
Ubuntu, with linux 2.6.21-23-generic
Ubuntu, with linux 2.6.21-23-generic (recovery mode)
Ubuntu, with linux 2.6.21-21-generic
Ubuntu, with linux 2.6.21-21-generic (recovery mode)
Memory test (memtest 86+)
Memory test (memtest console 115200)
Windows 7 loader (on/dev/sda1)
```After I choose the first one (as I always did), I get the following:
```
Ubuntu 10.04.1 LTS ava-laptop tty1
ava-laptop login .. [129.736043] tpm_tis 00:09: tpm_trasmit :tpm_send:  error 42 94967234
```and then it takes more that 3 minutes for ubuntu  to come up!!!

I would we grateful if anyone could could help me solve this issue,

Thank you in advance

---

### Post by jtarin on 2010-10-14
You couldn't always have chose the first one....it's the newest in the upgrade line.You originally chose "Ubuntu, with linux 2.6.21-21-generic" as the first in line then each successive upgrade you used a different kernel.
 Post under your own topic this thread has been marked solved.

---

