---
title: "need help 2 hard drives dual booting"
date: 2010-01-22
forum: New to Ubuntu
---

### Post by gigaferz on 2010-01-22
Hello! 

I had a dual set up in my hd ubuntu -vista, then ubuntu - 7.

But my hd always gave problems. I had to disconnect it and connect it again to a different plug when i had that problem (in any os)

So I decided to buy another hd. so I installed 7 on it. then my old hd gave me problems so i unplugged it.

Then I needed something from it and i connected it again, and windows saw it as not formatted, so i formatted the windows partition in my old hd. but it does have ubuntu on it, so i want to know how to restore it to dual boot. 

This is my actual set up:

custom@custom:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4692f002

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13      121602   976657408    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000429cd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29959   240640000    7  HPFS/NTFS
/dev/sdb2           29960       31174     9759487+  83  Linux
/dev/sdb3           31175       31296      979965   82  Linux swap / Solaris
/dev/sdb4           31297       60801   236998912+  83  Linux

so you know i have it like this:sdb1 ntfs (formatted windows)
 sdb2 / dir for ubuntu
sdb3 swap
sdb4 /home

how should i install grub to dual boot? 
can i install it to sdb2? (/ partition) or does it has to be a windows partition or hd?

does any of this makes anysense?

yes im trying to avoid rewriting the mbr on my new hd.

And in my bios i have it to boot first from cd then old drive then new drive.

so just some advice please... also can i use a jaunty live cd to install grub to a koala installation?

thank you guys

yes ive read waay to many threads but honestly i do not have the time to go tru them. so im not lazy im just always sleppy

---

### Post by oldfred on 2010-01-22
So we can see your entire configuration, down load this script and run it. You can download it to a working install also but it may be in the downloads directory.

From a LiveCD:
Download this script to your Desktop from 
[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)
sudo bash ~/Desktop/boot_info_script*.sh
This creates the file RESULTS.txt on your Desktop. Post the content of RESULTS.txt (use the code tags: #)

---

### Post by gigaferz on 2010-01-22
```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 1.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #2 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4692f002

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848 1,953,521,663 1,953,314,816   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000429cd

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   481,282,047   481,280,000   7 HPFS/NTFS
/dev/sdb2         481,291,335   500,810,309    19,518,975  83 Linux
/dev/sdb3         500,810,310   502,770,239     1,959,930  82 Linux swap / Solaris
/dev/sdb4         502,770,240   976,768,064   473,997,825  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="30F8D851F8D81746" LABEL="System Reserved" TYPE="ntfs" 
/dev/sda2: UUID="9668E13968E118AF" TYPE="ntfs" 
/dev/sdb1: UUID="9CD0A1B7D0A19852" TYPE="ntfs" 
/dev/sdb2: UUID="26c27f74-8c24-498b-98e8-8cd92e7e8efc" TYPE="ext4" 
/dev/sdb3: UUID="0a729e78-b45c-48c8-b91f-82234bb75b7b" TYPE="swap" 
/dev/sdb4: UUID="5b44ecde-e954-4934-9ad3-7cf6f3e63a8f" TYPE="ext3" 

=============================== "mount" output: ===============================

tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /media/cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/custom/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=custom)
/dev/sdb1 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb4 on /media/disk-1 type ext3 (rw,nosuid,nodev,uhelper=hal)


=========================== sdb2/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set 26c27f74-8c24-498b-98e8-8cd92e7e8efc
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 26c27f74-8c24-498b-98e8-8cd92e7e8efc
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=26c27f74-8c24-498b-98e8-8cd92e7e8efc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 26c27f74-8c24-498b-98e8-8cd92e7e8efc
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=26c27f74-8c24-498b-98e8-8cd92e7e8efc ro single 
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
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 247452297451fdcc
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=26c27f74-8c24-498b-98e8-8cd92e7e8efc /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda4 during installation
UUID=5b44ecde-e954-4934-9ad3-7cf6f3e63a8f /home           ext3    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=0a729e78-b45c-48c8-b91f-82234bb75b7b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb2: Location of files loaded by Grub: ===================


 248.9GB: boot/grub/core.img
 248.9GB: boot/grub/grub.cfg
 247.2GB: boot/initrd.img-2.6.31-14-generic
 248.8GB: boot/vmlinuz-2.6.31-14-generic
 247.2GB: initrd.img
 248.8GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf#code#
```

---

### Post by gigaferz on 2010-01-22
i need to sleep now, thnx, ill be back online in bout 9 hours, i appreciate any help

---

### Post by oldfred on 2010-01-22
I think you have things set up correctly. You want to leave the windows boot in the large drive and have ubuntu boot from the small drive. If you in BIOS set the 500GB drive to boot it should bring up Ubuntu. You still have windows in the large drive and if you ever have issues you can switch back and still boot. If the switching drives ends up not letting grub work you may have to reinstall grub so it sees the drive order correctly.

If after you switch boot order to have grub load and the windows does not work you may need to run update grub since windows will not be first even though it is still sda.

sudo update-grub

Only if you have to reinstall grub2 and you want to be sure to reinstall to the 500GB drive and not overwrite the windows boot loader in the large drive.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by gigaferz on 2010-01-22
```
custom@custom:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4692f002

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13      121602   976657408    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000429cd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29959   240640000    7  HPFS/NTFS
/dev/sdb2           29960       31174     9759487+  83  Linux
/dev/sdb3           31175       31296      979965   82  Linux swap / Solaris
/dev/sdb4           31297       60801   236998912+  83  Linux
custom@custom:~$ sudo mkdir /media/sdb4
custom@custom:~$ sudo mkdir /media/sdb2
custom@custom:~$ sudo mount /dev/sdb2 /media/sdb2
custom@custom:~$ sudo grub-install --root-directory=/media/sdb2 /dev/sdb
/dev/sdb does not have any corresponding BIOS drive.
custom@custom:~$ sudo grub-install --root-directory=/media/sdb2 /dev/sdb
/dev/sdb does not have any corresponding BIOS drive.
custom@custom:~$ sudo grub-install --root-directory=/media/sdb2 /dev/sdb1
/dev/sdb1 does not have any corresponding BIOS drive.

```

oops!, what happened?

---

### Post by flabdablet on 2010-01-22
These drives that are giving you trouble - they're not Samsungs, by any chance? Reason I ask is, I've seen some very weird interactions between some Samsung 500GB drives and a cheap ALi-based SATA controller, where the drives just go completely offline for no apparent reason and require power cycling (not just reset) to make them come back.

That aside: the grub-install commands you're issuing there look like you're trying to set your /dev/sdb up the way it's already set up - with GRUB installed, and looking in /dev/sdb2 for its boot files. So even if the command did succeed, doing it would not change the way your system behaves.

The only way you're going to make dual-booting happen without changing the MBR on your /dev/sda (which currently contains Windows-only boot code) is to make your BIOS avoid loading that MBR. Fiddling about with a GRUB that will never even be loaded is a waste of your precious waking hours.

Most modern BIOSes have a startup-time boot device selection option (F12 is often the hotkey that activates it) and if you use that, and boot from the second hard disk, you should see GRUB load from /dev/sdb.

If your BIOS doesn't have a startup boot menu built in, set it up to try booting from the floppy drive first, and use a Smart Boot Manager floppy to give you a convenient boot menu.

---

### Post by gigaferz on 2010-01-22
```
custom@custom:~$ sudo grub-install --recheck --root-directory=/media/sdb2 /dev/sdb
Probing devices to guess BIOS drives. This may take a long time.
grub-probe: error: Cannot open `/boot/grub/device.map'
[: 494: =: unexpected operator
Installing GRUB to /dev/sdb as (hd1)...
Installation finished. No error reported.
This is the contents of the device map /media/sdb2/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)	/dev/fd0
(hd0)	/dev/sda
(hd1)	/dev/sdb

didnt work so i tried this:

custom@custom:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4692f002

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13      121602   976657408    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000429cd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29959   240640000    7  HPFS/NTFS
/dev/sdb2           29960       31174     9759487+  83  Linux
/dev/sdb3           31175       31296      979965   82  Linux swap / Solaris
/dev/sdb4           31297       60801   236998912+  83  Linux
custom@custom:~$ sudo mkdir /media/sdb2
custom@custom:~$ sudo mount /dev/sdb2 /media/sdb2
custom@custom:~$ sudo grub-install --recheck --root-directory=/media/sdb2 /dev/sdb1
Probing devices to guess BIOS drives. This may take a long time.
grub-probe: error: Cannot open `/boot/grub/device.map'
[: 494: =: unexpected operator
Installing GRUB to /dev/sdb1 as (hd1,0)...
Installation finished. No error reported.
This is the contents of the device map /media/sdb2/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)	/dev/fd0
(hd0)	/dev/sda
(hd1)	/dev/sdb
custom@custom:~$ 

```

i did all this im gonna install grub to linux 10gb partition again because i didnt check the bios before so all i get now is a grub command prompt

---

### Post by oldfred on 2010-01-23
I think you were missing a slash. Your second one installed to the partition.

sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt[COLOR=Red]/[/COLOR] /dev/sdb

sudo grub-install --root-directory=/media/sdb2 /dev/sdb
/dev/sdb does not have any corresponding BIOS drive.

/media/sdb2  should be 
/media/sdb2/

---

### Post by HeadHunter00 on 2010-01-23
> **oldfred said:**
> I think you were missing a slash. Your second one installed to the partition.

sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt[COLOR=Red]/[/COLOR] /dev/sdb

sudo grub-install --root-directory=/media/sdb2 /dev/sdb
/dev/sdb does not have any corresponding BIOS drive.

/media/sdb2  should be 
/media/sdb2/
Surprisingly, it works for my friend, who had the same problem.

---

### Post by jnmjr on 2010-01-23
[B]Hi, this is the way I resolved my dual boot from separate hard drives.....

Grub2 is installed on the mbr of each drive, I boot from the Linux drive, use this command... sudo grub-install /dev/sda... followed by..... sudo update-grub....
repeat for SDB, this is what my set-up looks like,  very simple...
[/B]  
 jnmjr@My-Desktop:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8a4021bf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006329d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60049   482343561   83  Linux
/dev/sdb2           60050       60801     6040440    5  Extended
/dev/sdb5           60050       60801     6040408+  82  Linux swap / Solaris


jnmjr@My-Desktop:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found Microsoft Windows XP Professional on /dev/sda1

[B]Set your bios to boot from Linux drive....You are done!   
[/B]

---

### Post by gigaferz on 2010-01-23
i think im also missint the menu.lst file? and i did the --check option... but before that, im gonna try the slash and the update command, my bios already boots from linux drive but i think im missing the update. as i said it gets me to a grub cli

---

### Post by gigaferz on 2010-01-25
so, im a still getting to a grub shell.

I deleted boot from the linux system partition and from the empy windows partition.

I noticed with fdisk tha it shows you a * under the boot section so that is where im trying to install grub. but i guess is point less.

I know i was trying to install it to not boot enabled partitions, but then i guess is just fed up the mbr of the hd. but still, having the grub shell tells me im missing something.  anyways lets just close this thread or dele it or something..

---

### Post by jnmjr on 2010-01-25
> **gigaferz said:**
> so, im a still getting to a grub shell.

I deleted boot from the linux system partition and from the empy windows partition.

I noticed with fdisk tha it shows you a * under the boot section so that is where im trying to install grub. but i guess is point less.

I know i was trying to install it to not boot enabled partitions, but then i guess is just fed up the mbr of the hd. but still, having the grub shell tells me im missing something.  anyways lets just close this thread or dele it or something..

Look, your problem is solvable, I'm not much of a partition guy but from what I see from your posts is that you have NTFS partitions in both drives and you are trying to install grub2 there *.
I think you should make SDA drive into a single partition, that would be your Windows drive. SDB your Linux drive (delete NTFS partition from this drive). That said, you  have to boot into Win Repair Console booting from WinCD to repair your Win partition, you can also Fix-MBR and Boot.INI (type help at prompt to see list of commands)from there if you need to boot into Windows to do the re- partitioning of SDA. At this point, you won't see SDB because Windows has taken over booting. Supposing you have restored SDA to a single partition, you must now boot from LiveCD so you can delete Ntfs partition from SDB and re-install Grub2 using the commands I posted. This process is a bit time consuming but it should fix your problem... it should end up looking similar to mine. I don't know of any shortcuts to make it quicker so hope this helps.

---

### Post by presence1960 on 2010-01-25
> **gigaferz said:**
> ```
custom@custom:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4692f002

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13      121602   976657408    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000429cd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29959   240640000    7  HPFS/NTFS
/dev/sdb2           29960       31174     9759487+  83  Linux
/dev/sdb3           31175       31296      979965   82  Linux swap / Solaris
/dev/sdb4           31297       60801   236998912+  83  Linux
custom@custom:~$ sudo mkdir /media/sdb4
custom@custom:~$ sudo mkdir /media/sdb2
custom@custom:~$ sudo mount /dev/sdb2 /media/sdb2
custom@custom:~$ sudo grub-install --root-directory=/media/sdb2 /dev/sdb
/dev/sdb does not have any corresponding BIOS drive.
custom@custom:~$ sudo grub-install --root-directory=/media/sdb2 /dev/sdb
/dev/sdb does not have any corresponding BIOS drive.
custom@custom:~$ sudo grub-install --root-directory=/media/sdb2 /dev/sdb1
/dev/sdb1 does not have any corresponding BIOS drive.

```

oops!, what happened?

To reinstall GRUB2 (which does not use menu.lst BTW!) on sdb MBR boot from the 9.10 Live CD& choose "try ubuntu without any changes". When the desktop loads open terminal and run ```
sudo mount /dev/sdb2 /mnt
```
This will mount your ubuntu partition. next in terminal run ```
sudo grub-install --root-directory=/mnt/ /dev/sdb
```
This will put GRUB in MBR of sdb. Now reboot and go into BIOS and set sdb to boot first in the hard disk boot order. Save changes to CMOS & continue booting. Boot into Ubuntu and open a terminal and run ```
sudo update-grub
```

---

### Post by gigaferz on 2010-01-31
good morning every1, i didnt mean to sound female doggy i just know that sdb is defective, and yes the mbr could be unusable, ill check that out later 2 nite

---

### Post by gigaferz on 2010-01-31
I got something to say:
 at work, they have deep reach fork lifts, so they installed asus netbooks. i heard xp was crashing frequently, so guess what they decided to install?, ubuntu!

 Now one of the deep reach netbook is all messed up. It came with many errors and i did a fsck manually (ive done it before)(and i did it because it was asking for it,and no one knows but me, :P)  and after that, when rebooting i got a biosdisk not found  and a grubrescue> prompt. obviously the mbr is messed up am i right? only a winxp cd can fix it, right? and then a ubuntu livecd to put it back.

just wondering cos its been 4 days and i guess they dont know what is going on...

and and i was amazed when a little scanner gun worked with ubuntu and the program for inventory  works too tru wine.....

---

