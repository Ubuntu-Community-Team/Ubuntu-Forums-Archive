---
title: "hard disc partition"
date: 2009-11-26
forum: New to Ubuntu
---

### Post by sauravbhaumik on 2009-11-26
In a 320gb hard disc, I had a FAT partition, another ntfs partition with windows xp installed, and an Ext3 partition with ubuntu 9.10 installed, with the rest space unallocated. In that last unallocated space, I created a partition, and installed Mandriva in it. I had modified the ubuntu boot screen so that Mandriva came in the boot option also. Intending to install Open SUSE separately, I booted from Open SUSE installation Dvd and it said that it could not create a new partition, while I chose to install it in the partition where Mandriva was installed. However, after installation of OpenSUSE, no live CD of linux (Ubuntu, Fedora, Open SUSE and Mandriva) could create a new partition or even detect the partition table. 

I could not understand the significance, nor can I guess what went wrong with the hard disc. I attach the boot info script result: 
```
============================= Boot Info Summary: ==============================

 => Grub1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda4 starts 
                       at sector 2048. But according to the info from fdisk, 
                       sda4 starts at sector 379236352.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    63,488,879    63,488,817   c W95 FAT32 (LBA)
/dev/sda2    *     63,488,880   123,379,199    59,890,320  83 Linux
/dev/sda3         123,379,326   625,139,711   501,760,386   f W95 Ext d (LBA)
Invalid MBR Signature found
/dev/sda5     ? 4,418,346,621 4,418,346,620                   Unknown
/dev/sda6     ? 4,418,346,621 4,418,346,620                   Unknown
/dev/sda4         379,236,352   625,139,711   245,903,360   7 HPFS/NTFS

/dev/sda3 overlaps with /dev/sda4
/dev/sda5 ends after the last sector of /dev/sda
the logical partition /dev/sda5 is not contained in the extended partition /dev/sda3
/dev/sda6 ends after the last sector of /dev/sda
the logical partition /dev/sda6 is not contained in the extended partition /dev/sda3

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="WINDOWS" UUID="6029-8182" TYPE="vfat" 
/dev/sda2: UUID="4f0aaacb-4857-4f28-94b9-f29c568729a5" TYPE="ext3" 
/dev/sda4: UUID="C49ED3E49ED3CCD4" LABEL="Data" TYPE="ntfs" 
/dev/sda5: UUID="c6f7d865-4b4c-4a6d-92f0-13539f5ce894" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/saurav/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=saurav)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


================================ sda1/BOOT.INI: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda2/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,2)
search --no-floppy --fs-uuid --set 4f0aaacb-4857-4f28-94b9-f29c568729a5
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 4f0aaacb-4857-4f28-94b9-f29c568729a5
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=4f0aaacb-4857-4f28-94b9-f29c568729a5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 4f0aaacb-4857-4f28-94b9-f29c568729a5
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=4f0aaacb-4857-4f28-94b9-f29c568729a5 ro single 
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 4f0aaacb-4857-4f28-94b9-f29c568729a5
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=4f0aaacb-4857-4f28-94b9-f29c568729a5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 4f0aaacb-4857-4f28-94b9-f29c568729a5
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=4f0aaacb-4857-4f28-94b9-f29c568729a5 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod fat
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 6029-8182
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=4f0aaacb-4857-4f28-94b9-f29c568729a5 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=c6f7d865-4b4c-4a6d-92f0-13539f5ce894 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


  32.5GB: boot/grub/grub.cfg
  32.5GB: boot/grub/stage2
  32.5GB: boot/initrd.img-2.6.31-14-generic
  32.5GB: boot/initrd.img-2.6.31-15-generic
  32.5GB: boot/vmlinuz-2.6.31-14-generic
  32.5GB: boot/vmlinuz-2.6.31-15-generic
  32.5GB: initrd.img
  32.5GB: initrd.img.old
  32.5GB: vmlinuz
  32.5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda6



=============================== StdErr Messages: ===============================

hexdump: /dev/sda6: No such file or directory
hexdump: /dev/sda6: No such file or directory
```

Could you be so kind as to explain what actually happened? 

Best regards,
Saurav

---

### Post by Daveth on 2009-11-26
it looks to me like you have a very messy hard drive now, with lots of untidy partitions and bootloaders. Would it not be easier, if you want to run this many operating systems, to run them as a virtual machines, assuming your PC can take it???

---

### Post by sauravbhaumik on 2009-11-27
> **Daveth said:**
> Would it not be easier, if you want to run this many operating systems, to run them as a virtual machines, assuming your PC can take it???
Actually, now, I only have two operating systems, since I deleted manually the files of the partition where I had put my other operating systems; and in future, at a time, it would be sufficient for me to have only three operating systems, one ubuntu, one windows, and another linux which I would try. And I could not understand your advice as to running them as virtual machines. Kindly elaborate.

However, for this moment, what I am mostly after is a way to bypass formatting the whole hard drive and to have my partition table readable. What would you advise, sir?

---

### Post by Some Penguin on 2009-11-28
Ouch.  If you really have a mangled partition table -- and the listing suggests you do -- you probably want to clone the drive (in case initial attempts to fix it only make it worse...) and then look into something like [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk) (which is available on various live CDs, it seems).

---

### Post by Baelus on 2009-11-28
From what I can see there are 3 primary partitions and 1 extended partition.

1) sda1 XP
2) sda2 ubuntu
3) sda3 extended (which contains the swap partition and extra space)
4) sda4 vista

If that's the case, opensuse will probably be trying to create another primary partition to boot from. A maximum of 3 primary partitions and 1 extended is allowed (as far as I know). From what I understand, an OS can only boot from a primary partition.

That said, not being able to even detect the partition table leads me to believe something more serious is going on. :(

---

### Post by Baelus on 2009-11-28
Never mind. From the errors shown here it looks like your drive is fubar.

> 
...Invalid MBR Signature found...

/dev/sda3 overlaps with /dev/sda4
/dev/sda5 ends after the last sector of /dev/sda
the logical partition /dev/sda5 is not contained in the extended partition /dev/sda3
/dev/sda6 ends after the last sector of /dev/sda
the logical partition /dev/sda6 is not contained in the extended partition /dev/sda3

If it can be fixed it's going to take some work.

---

### Post by sauravbhaumik on 2009-11-28
> **Some Penguin said:**
> Ouch.  If you really have a mangled partition table -- and the listing suggests you do -- you probably want to clone the drive (in case initial attempts to fix it only make it worse...) and then look into something like [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk) (which is available on various live CDs, it seems).

What has to be done with testdisk? It gives many options like analyse, change disk geometry, modify options etc. Which one to go after?

---

### Post by Some Penguin on 2009-11-28
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

Going by that, you'll probably want to use 'Analyze'.

---

### Post by a!man_96 on 2009-11-28
I think you should consider cleaning your hard drive..

---

### Post by sauravbhaumik on 2009-12-02
Even after I tried to fix the partition table by using testdisk, the problem is not totally solved, the part of boot info result that I put down here will give the detail; but I can't understand how I will solve the issue with /dev/sda4, which is said to be an extended partition. Kindly advise.
```
============================= Boot Info Summary: ==============================

 => Grub1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda5 and 
                       looks at sector 128711825 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #7 for 
                       /boot/grub/menu.lst.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x10000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    63,488,879    63,488,817   c W95 FAT32 (LBA)
/dev/sda2          63,488,880   123,379,199    59,890,320  83 Linux
/dev/sda3         123,379,326   125,467,629     2,088,304  82 Linux swap / Solaris
/dev/sda4         125,467,650   625,153,409   499,685,760   f W95 Ext d (LBA)
/dev/sda5         125,467,713   187,783,784    62,316,072  83 Linux
/dev/sda6         379,236,352   625,139,711   245,903,360   7 HPFS/NTFS

/dev/sda4 ends after the last sector of /dev/sda

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="WINDOWS" UUID="6029-8182" TYPE="vfat" 
/dev/sda2: UUID="4f0aaacb-4857-4f28-94b9-f29c568729a5" TYPE="ext3" 
/dev/sda3: UUID="c6f7d865-4b4c-4a6d-92f0-13539f5ce894" TYPE="swap" 
/dev/sda5: UUID="fc9f4d02-a796-459d-9ddc-3f7e7049a42a" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="C49ED3E49ED3CCD4" LABEL="Data" TYPE="ntfs" 

```

---

### Post by sauravbhaumik on 2010-01-19
Can anyone give me a clue as to this problem?

---

### Post by PenguinInside on 2010-01-19
> **Baelus said:**
> From what I can see there are 3 primary partitions and 1 extended partition.

1) sda1 XP
2) sda2 ubuntu
3) sda3 extended (which contains the swap partition and extra space)
4) sda4 vista

If that's the case, opensuse will probably be trying to create another primary partition to boot from. A maximum of 3 primary partitions and 1 extended is allowed (as far as I know). From what I understand, an OS can only boot from a primary partition.

:(

Actually, that's only true for inferior boot loaders (such as Windows).

Linux can boot from extended partitions.

I'm running from sda6 right now.

sda1-3 are primary partitions. sda4 is the extended partition. And then sda5 onward are the logical partitions.

---

### Post by PenguinInside on 2010-01-19
> **sauravbhaumik said:**
> Can anyone give me a clue as to this problem?

Look, sauravbhaumik, I would avoid being overly clever and trying to fix the problem by making configuration changes, etc.

First of all, can you read the data by booting from a live CD?

If yes, then consolidate your data in one place, make a backup, and simplify your partitions (with gparted).
Click here from Firefox to install: [apt://gparted]("apt://gparted")

Then either re-grub or re-install an OS.

Note: Be sure to leave a separate home partition. If you don't know what that means, post in this thread for a reply.

---

### Post by sauravbhaumik on 2010-01-19
> **PenguinInside said:**
> Look, sauravbhaumik, I would avoid being overly clever and trying to fix the problem by making configuration changes, etc.

First of all, can you read the data by booting from a live CD?

If yes, then consolidate your data in one place, make a backup, and simplify your partitions (with gparted).
Click here from Firefox to install: [apt://gparted]("apt://gparted")

Then either re-grub or re-install an OS.

Note: Be sure to leave a separate home partition. If you don't know what that means, post in this thread for a reply.

Gparted can't read my hard disc, though I can boot ubuntu and windows from hard drive. And installing an OS will require a clean up of the hard disc, for the same reason I guess.

---

### Post by oldfred on 2010-01-19
There is nothing wrong with your partition table. You can have a max of 4 primary partitions or 3 primary and one extended. The extended is just a container for many logical partitions. Windows and some other operating systems need a primary partition to boot from. Linux can be installed totally into logical partition. 

If you need another primary you can delete swap and create a new swap in the extended partition. Deleting swap will change its UUID and require you to edit your fstab to allow Ubuntu to boot. To do any editing of partitions is a slow process as you have to move all the data and verify it and it has to be done from the liveCD. This assumes you do have space available. Each partition needs about 20% free space or you will have difficulty moving it.

[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by sauravbhaumik on 2010-01-19
> **oldfred said:**
> There is nothing wrong with your partition table. You can have a max of 4 primary partitions or 3 primary and one extended. The extended is just a container for many logical partitions. Windows and some other operating systems need a primary partition to boot from. Linux can be installed totally into logical partition. 

If you need another primary you can delete swap and create a new swap in the extended partition. Deleting swap will change its UUID and require you to edit your fstab to allow Ubuntu to boot. To do any editing of partitions is a slow process as you have to move all the data and verify it and it has to be done from the liveCD. This assumes you do have space available. Each partition needs about 20% free space or you will have difficulty moving it.


But gparted can't find my partitions, how can I delete the swap, even? And from system>administration>disk utility, no partition can be deleted or even modified, since if you try to delete, say some partition from disk utility, it will give the error message```
Error erasing: helper exited with exit code 1: In part_del_partition: device_file=/dev/sda, offset=64239469056
Entering MS-DOS parser (offset=0, size=320072933376)
MSDOS_MAGIC found
looking at part 0 (offset 32256, size 32506274304, type 0x0c)
new part entry
looking at part 1 (offset 32506306560, size 30663843840, type 0x83)
new part entry
looking at part 2 (offset 63170214912, size 1069211648, type 0x82)
new part entry
looking at part 3 (offset 64239436800, size 255839109120, type 0x0f)
Entering MS-DOS extended parser (offset=64239436800, size=255839109120)
readfrom = 64239436800
MSDOS_MAGIC found
readfrom = 194168959488
MSDOS_MAGIC found
Exiting MS-DOS extended parser
Exiting MS-DOS parser
MSDOS partition table detected
got it
Error: Can't have a partition outside the disk!
ped_disk_new() failed

```

---

### Post by oldfred on 2010-01-19
You can only change partitions that are not mounted. You have to use a liveCD to edit them. But it should show your partitions. The boot_info script showed your partitions and they looked fine then. Did you make further changes?

copy & paste this into a terminal:

sudo fdisk -lu

---

### Post by mikechant on 2010-01-20
Oldfred said:
> There is nothing wrong with your partition table.

There *is* something seriously wrong with the partition table still:
```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x10000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    63,488,879    63,488,817   c W95 FAT32 (LBA)
/dev/sda2          63,488,880   123,379,199    59,890,320  83 Linux
/dev/sda3         123,379,326   125,467,629     2,088,304  82 Linux swap / Solaris
/dev/sda4         125,467,650   625,153,409   499,685,760   f W95 Ext d (LBA)
/dev/sda5         125,467,713   187,783,784    62,316,072  83 Linux
/dev/sda6         379,236,352   625,139,711   245,903,360   7 HPFS/NTFS

**/dev/sda4 ends after the last sector of /dev/sda**
```

The last line above tells us what is wrong, so the end point of sda4 needs to be set to equal the end point of sda6.

The first post in this thread:
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)
describes among other things how to use 'sfdisk' to dump the partition table to an editable text file, update it and reload it. It looks as if this method could be used to correct your error.

---

### Post by Baelus on 2010-01-20
Just throwing this out there:

[http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page")

From the introduction about SystemRescueCd:

SystemRescueCd is a Linux system rescue disk available as a bootable CD-ROM or USB stick for administrating or repairing your system and data after a crash. It aims to provide an easy way to carry out admin tasks on your computer, such as creating and editing the partitions of the hard disk. It comes with a lot of linux software such as system tools (parted, partimage, fstools, ...) and basic tools (editors, midnight commander, network tools). It requires no installation since you just have to boot on the CD-ROM.

Download Page:

[http://www.sysresccd.org/Download]("http://www.sysresccd.org/Download")

If you use it you may have to read up on how to use the different tools, but I've had success with it in the past.

---

### Post by meierfra. on 2010-01-20
> describes among other things how to use 'sfdisk' to dump the partition table to an editable text file, update it and reload it. It looks as if this method could be used to correct your error.

That should work. But testdisk should be able to fix the problem a little easier:

Start testdisk as before and do the "Quick Search".  After the Quick search you should have a  "[Extd Part]" tab on the bottom of the  screen. Select it and hit "enter".  Then make sure that all your partitions are still selected correctly and  choose "write".

Hopefully, that's all it takes to fix your problem. But I have seen some cases, where testdisk does not give you the "Extd Part" tab. If that happens, just come back here and  I will give detailed instruction  how to use "sfdisk".

---

### Post by sauravbhaumik on 2010-01-23
> **meierfra. said:**
> That should work. But testdisk should be able to fix the problem a little easier:

Start testdisk as before and do the "Quick Search".  After the Quick search you should have a  "[Extd Part]" tab on the bottom of the  screen. Select it and hit "enter".  Then make sure that all your partitions are still selected correctly and  choose "write".

Hopefully, that's all it takes to fix your problem. But I have seen some cases, where testdisk does not give you the "Extd Part" tab. If that happens, just come back here and  I will give detailed instruction  how to use "sfdisk".

I attach the screen shot I get after quick search. I didn't see anything like "[Extd Part]". Could you kindly look at the screen shot?
[http://ubuntuforums.org/attachment.php?attachmentid=144686&stc=1&d=1264270051](http://ubuntuforums.org/attachment.php?attachmentid=144686&stc=1&d=1264270051)
Edit: I had done some modification of the hard disk with my windows. Now, all of my hard disk should be partitioned in either ntfs, fat or ext3. But gparted can't still locate my hard disc partitions. After partition, the hard disc looks like
```
============================= Boot Info Summary: ==============================

 => Grub1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x10000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    63,488,879    63,488,817   c W95 FAT32 (LBA)
/dev/sda2          63,488,880   123,379,199    59,890,320  83 Linux
/dev/sda3         123,379,326   125,467,629     2,088,304  82 Linux swap / Solaris
/dev/sda4         125,467,650   625,153,409   499,685,760   f W95 Ext d (LBA)
/dev/sda5         125,467,713   187,783,784    62,316,072   b W95 FAT32
/dev/sda6         187,783,848   379,230,389   191,446,542   7 HPFS/NTFS
/dev/sda7         379,236,352   625,139,711   245,903,360   7 HPFS/NTFS

/dev/sda4 ends after the last sector of /dev/sda

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="WINDOWS" UUID="6029-8182" TYPE="vfat" 
/dev/sda2: UUID="4f0aaacb-4857-4f28-94b9-f29c568729a5" TYPE="ext3" 
/dev/sda3: UUID="c6f7d865-4b4c-4a6d-92f0-13539f5ce894" TYPE="swap" 
/dev/sda5: LABEL="DATA2" UUID="EC42-43AB" TYPE="vfat" 
/dev/sda6: UUID="B63831373830F7C7" LABEL="Storage" TYPE="ntfs" 
/dev/sda7: UUID="C49ED3E49ED3CCD4" LABEL="Data" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/saurav/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=saurav)
/dev/sda5 on /media/DATA2 type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


================================ sda1/BOOT.INI: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda2/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,2)
search --no-floppy --fs-uuid --set 4f0aaacb-4857-4f28-94b9-f29c568729a5
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 4f0aaacb-4857-4f28-94b9-f29c568729a5
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=4f0aaacb-4857-4f28-94b9-f29c568729a5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 4f0aaacb-4857-4f28-94b9-f29c568729a5
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=4f0aaacb-4857-4f28-94b9-f29c568729a5 ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod fat
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 6029-8182
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=4f0aaacb-4857-4f28-94b9-f29c568729a5 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=c6f7d865-4b4c-4a6d-92f0-13539f5ce894 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


  32.5GB: boot/grub/grub.cfg
  32.5GB: boot/grub/stage2
  32.5GB: boot/initrd.img-2.6.31-14-generic
  32.5GB: boot/initrd.img-2.6.31-15-generic
  32.5GB: boot/initrd.img-2.6.31-16-generic
  32.5GB: boot/initrd.img-2.6.31-17-generic
  32.5GB: boot/vmlinuz-2.6.31-14-generic
  32.5GB: boot/vmlinuz-2.6.31-15-generic
  32.5GB: boot/vmlinuz-2.6.31-16-generic
  32.5GB: boot/vmlinuz-2.6.31-17-generic
  32.5GB: initrd.img
  32.5GB: initrd.img.old
  32.5GB: vmlinuz
  32.5GB: vmlinuz.old
```

---

### Post by meierfra. on 2010-01-23
You need to press "Enter" at the Quick Search.  (Sorry, I should have mentioned that)

---

### Post by sauravbhaumik on 2010-01-23
> **meierfra. said:**
> You need to press "Enter" at the Quick Search.  (Sorry, I should have mentioned that)

No no, it is only after pressing "Enter" at the quick search that I got the screen. I attached the screen shot. 

Let me tell you what I did : sudo testdisk> create> proceed> choosing intel> choosing "analyse"> pressing "Enter" at quick search. Then it gives a list of partitions. No Extd Part is there. Now what should I do? You might like to have a look at the screen shot I attached in my earlier post.

---

### Post by meierfra. on 2010-01-23
> You might like to have a look at the screen shot I attached in my earlier post.


I did.   After you get the list of partitions you need to press "enter" one more  time.  At the new screen you should get the following options :
 
[Quit  ]  [Deeper Search]  [ Write  ]  [Extd Part]


You might not get the [Extd Part], but  the other three will be there.

---

### Post by sauravbhaumik on 2010-01-23
> **meierfra. said:**
> I did.   After you get the list of partitions you need to press "enter" one more  time.  At the new screen you should get the following options :
 
[Quit  ]  [Deeper Search]  [ Write  ]  [Extd Part]


You might not get the [Extd Part], but  the other three will there.

Yes, there is no Extd Part option, but the other three are there.

---

### Post by meierfra. on 2010-01-23
OK, that one is the correct screen.  So you will have to use "sfdisk" to fix the problem.  I don't have time  right now, but I'll post the instructions as soon as I can.

---

### Post by meierfra. on 2010-01-24
Open a terminal in Ubuntu and copy and paste the following line to the terminal:

```
echo ,499669696 |sudo sfdisk -N4 -uS -f --no-reread -O ~/Desktop/PT.save /dev/sda
```


This will change  the size of your extended partition to 499,669,696 sectors and your extended partition will  end at the last full cylinder of the hard drive.

It also creates the file PT.save on your Desktop. It is a backup of your current partition table. Save it to some place outside the hard drive.  (flash drive, online storage ..). If something goes wrong, you can use the file to  restore your partition table.

That's it. Although you might have to reboot for gparted to recognize the new partition table.

---

### Post by sauravbhaumik on 2010-01-24
> **meierfra. said:**
> Open a terminal in Ubuntu and copy and paste the following line to the terminal:

```
echo ,499669696 |sudo sfdisk -N4 -uS -f --no-reread -O ~/Desktop/PT.save /dev/sda
```


This will change  the size of your extended partition to 499,669,696 sectors and your extended partition will  end at the last full cylinder of the hard drive.

It also creates the file PT.save on your Desktop. It is a backup of your current partition table. Save it to some place outside the hard drive.  (flash drive, online storage ..). If something goes wrong, you can use the file to  restore your partition table.

That's it. Although you might have to reboot for gparted to recognize the new partition table.

I did that, but even after it reread, the gparted doesn't recognize it. However, I didn't find any change that it makes - the size remains the same I think. I am attaching the terminal output for your information, sir.```
saurav@reflexion:~$ echo ,499669696 |sudo sfdisk -N4 -uS -f --no-reread -O ~/Desktop/PT.save /dev/sda
[sudo] password for saurav: 

Disk /dev/sda: 38913 cylinders, 255 heads, 63 sectors/track
Old situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *        63  63488879   63488817   c  W95 FAT32 (LBA)
/dev/sda2      63488880 123379199   59890320  83  Linux
/dev/sda3     123379326 125467629    2088304  82  Linux swap / Solaris
/dev/sda4     125467650 625137345  499669696   f  W95 Ext'd (LBA)
/dev/sda5     125467713 187783784   62316072   b  W95 FAT32
/dev/sda6     187783848 379230389  191446542   7  HPFS/NTFS
/dev/sda7     379236352 625139711  245903360   7  HPFS/NTFS
Warning: given size (499669696) exceeds max allowable size (499669695)
New situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *        63  63488879   63488817   c  W95 FAT32 (LBA)
/dev/sda2      63488880 123379199   59890320  83  Linux
/dev/sda3     123379326 125467629    2088304  82  Linux swap / Solaris
/dev/sda4     125467650 625137345  499669696   f  W95 Ext'd (LBA)
/dev/sda5     125467713 187783784   62316072   b  W95 FAT32
/dev/sda6     187783848 379230389  191446542   7  HPFS/NTFS
/dev/sda7     379236352 625139711  245903360   7  HPFS/NTFS
Warning: partition 4 extends past end of disk
Successfully wrote the new partition table

Re-reading the partition table ...
BLKRRPART: Device or resource busy
The command to re-read the partition table failed.
Run partprobe(8), kpartx(8) or reboot your system now,
before using mkfs

If you created or changed a DOS partition, /dev/foo7, say, then use dd(1)
to zero the first 512 bytes:  dd if=/dev/zero of=/dev/foo7 bs=512 count=1
(See fdisk(8).)
saurav@reflexion:~$ 

```
I restarted, but no effect. I did it second time (of which the above is the output). Still gparted can't recognize.

---

### Post by sauravbhaumik on 2010-01-24
The boot script info says that the sda7 ends after sda4.```
============================= Boot Info Summary: ==============================

 => Grub1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x10000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    63,488,879    63,488,817   c W95 FAT32 (LBA)
/dev/sda2          63,488,880   123,379,199    59,890,320  83 Linux
/dev/sda3         123,379,326   125,467,629     2,088,304  82 Linux swap / Solaris
/dev/sda4         125,467,650   625,137,345   499,669,696   f W95 Ext d (LBA)
/dev/sda5         125,467,713   187,783,784    62,316,072   b W95 FAT32
/dev/sda6         187,783,848   379,230,389   191,446,542   7 HPFS/NTFS
/dev/sda7         379,236,352   625,139,711   245,903,360   7 HPFS/NTFS

the logical partition /dev/sda7 is not contained in the extended partition /dev/sda4

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="WINDOWS" UUID="6029-8182" TYPE="vfat" 
/dev/sda2: UUID="4f0aaacb-4857-4f28-94b9-f29c568729a5" TYPE="ext3" 
/dev/sda3: UUID="c6f7d865-4b4c-4a6d-92f0-13539f5ce894" TYPE="swap" 
/dev/sda5: LABEL="DATA2" UUID="EC42-43AB" TYPE="vfat" 
/dev/sda6: UUID="B63831373830F7C7" LABEL="Storage" TYPE="ntfs" 
/dev/sda7: UUID="C49ED3E49ED3CCD4" LABEL="Data" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/saurav/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=saurav)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


================================ sda1/BOOT.INI: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda2/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,2)
search --no-floppy --fs-uuid --set 4f0aaacb-4857-4f28-94b9-f29c568729a5
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 4f0aaacb-4857-4f28-94b9-f29c568729a5
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=4f0aaacb-4857-4f28-94b9-f29c568729a5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 4f0aaacb-4857-4f28-94b9-f29c568729a5
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=4f0aaacb-4857-4f28-94b9-f29c568729a5 ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod fat
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 6029-8182
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=4f0aaacb-4857-4f28-94b9-f29c568729a5 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=c6f7d865-4b4c-4a6d-92f0-13539f5ce894 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


  32.5GB: boot/grub/grub.cfg
  32.5GB: boot/grub/stage2
  32.5GB: boot/initrd.img-2.6.31-14-generic
  32.5GB: boot/initrd.img-2.6.31-15-generic
  32.5GB: boot/initrd.img-2.6.31-16-generic
  32.5GB: boot/initrd.img-2.6.31-17-generic
  32.5GB: boot/vmlinuz-2.6.31-14-generic
  32.5GB: boot/vmlinuz-2.6.31-15-generic
  32.5GB: boot/vmlinuz-2.6.31-16-generic
  32.5GB: boot/vmlinuz-2.6.31-17-generic
  32.5GB: initrd.img
  32.5GB: initrd.img.old
  32.5GB: vmlinuz
  32.5GB: vmlinuz.old
=============================== StdErr Messages: ===============================

umount: /tmp/BootInfo/sda7: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
```

---

### Post by sauravbhaumik on 2010-01-24
Should it be 499674798 instead of 499669696 in the command?
/dev/sda is total 625142448 sectors. and /dev/sda starts at 125,467,650 sector. difference 499674798.

---

### Post by sauravbhaumik on 2010-01-24
The following made gparted recognize my partition table ```
echo ,499674798 |sudo sfdisk -N4 -uS -f --no-reread -O ~/Desktop/PT.save /dev/sda

```

Could you tell me what actually happened behind the commands?

---

### Post by meierfra. on 2010-01-24
> 
The following made gparted recognize my partition table
```

echo ,499674798 |sudo sfdisk -N4 -uS -f --no-reread -O ~/Desktop/PT.save
``` /dev/sda

Could you tell me what actually happened behind the commands? 


Your partition table contains the following information for each of your partition:

start_point  size   system_id boot_flag (and some more)

sfdisk lets you change those  values.  sfdisk accepts input of the format

63,2000,83,-,...

This will tell sfdisk to use "63" as start point, "2000" as the size, "83" as the system id. and to not  set the boot flag.

If you leave out some  values, sfdisk will use the current value.
So if you use

 ,2000

as the input, sfdisk will only change the size of the partition.

```
echo  ",499674798" | sfdisk  .....
```

   tells sfdisk to use ",49967498" as its input. So "sfdisk" will change the size of the partition to 49967498.

Now lets go though the remaining arguments:

 -N4    : Edit partition 4

-uS     : All sizes use "sectors" as the unit.

-f      : Use force, that is write the partition table even if sfdisk does not like the new partition table.  You need this option for example if one of your partition does not end on a cylindrical bound.

---no-reread :  Do not check whether the  partition is mounted or busy.

/dev/sda   : Edit the partition table of the /dev/sda.  

> 499674798 instead of 499669696 

I want the extended partition to end at a cylindrical bound. Your hard drive has 38913 cylinders.  Each cylinder has 255 heads and each head as 63 sectors  So your last cylinder ends at sector 

38913 *255*63=625,137,345

I derived  the size of the partition from that number:

625,137,345-125,467,650+1=499,669,696

But I was a little bit sloppy. Partition tables start counting at zero, so the cylinder actually ends at sector 625,137,344.

Also I forgot to check that /dev/sda7 ended after the last cylinder, namely  at 625,139,711.  


Cylindrical bounds are pretty much irrelevant. It used to be that lots of programs assumed that partitions are on cylindrical bounds. But  these days everybody calculates in terms of sectors rather than cylinders. Only that various partition programs (like fdisk) still generate warning if a partition does not end on a cylindrical bound. 

Actually, cylindrical bounds caused your problem in the first place:

Your hard drive has 625,142,448 sectors.
Now 
38913 cylinders= 625,137,345 sectors
38914 cylinders= 625,153,410 sectors

You original partition table  assumed that you have 38914 cylinders and the extended partition ended at sector 625,153,409. But that was beyond the actual size of your hard drive.

Testdisk was not able to fix the problem.  It tries to  keep partitions on cylindrical bounds and since /dev/sda7 ends after cylinder 38913, testdisk did not gave you  an option to shrink the extended partition.

But I just notice that testdisk as an "Allow partial last cylinder : No" option. So maybe if one changes that to "Allow partial last cylinder : Yes", one can use testdisk to fix the problem.

---

### Post by sauravbhaumik on 2010-01-27
> **meierfra. said:**
> Your partition table contains the following information for each of your partition..........fix the problem.

I read this article, sir, and what I understand now is that the number of sectors that my hard disk has is not cylinder bound. Instead, if one cylinder is "c" sectors, and my hard drive has "n" sectors then there is "m" such that *(m-1)c<n<mc*; and that makes gparted believe that my HD ends at (m-1)c sectors, and if some partition ends somewhere beyond this, gparted will act as if there was an error. Have I understood correctly?

Thank you very much, sir.

---

### Post by meierfra. on 2010-01-27
> I read this article, sir, and what I understand now is that the number of sectors that my hard disk has is not cylinder bound. 
Correct.

> Instead, if one cylinder is "c" sectors, and my hard drive has "n" sectors then there is "m" such that (m-1)c<n<mc;
Correct.

> that makes gparted believe that my HD ends at (m-1)c sectors, and if some partition ends somewhere beyond this, gparted will act as if there was an error.

No quite. Actually  currently /dev/sda7 ends beyond (m-1)c sectors and Gparted does not complain.

Correct version:

What ever program wrote your partition table table, believed that your HD ends at mc sectors and set your extended partition to end at mc sectors. So your  partition table  contained a minor error. Gparted noticed this   and  acted as  if there was an serious error.

---

