---
title: "MBR issue!"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by sauravbhaumik on 2009-11-17
Hello,
I had dual boot Ubuntu 9.10 and windows XP. Installed opensuse as a third boot. After installing opensuse, I lost my ubuntu boot screen, and I tried to repair my boot screen by modifying the mbr using supergrub disc (that's only how I can login to my ubuntu), but I couldn't restore ubuntu grub to mbr because there is no /boot/grub/stage1. 

I tried to install ubuntu afresh, but you see, the partition manager which comes during installation doesn't find the already existing partitions, so the only suggestion it gives is to format the whole hard disc. But I have valuable things in my hard disc. 

I tried to format the partition where opensuse is, but still I can't, because the disc utility gives an error while formatting that partition. 

Kindly help me out! I am in great distress!

Regards,
Saurav

---

### Post by snkiz on 2009-11-17
Witch version of grub are you using in Ubuntu? The new one doesn't use /boot/grub/stage1. You say you can use super grub to get Ubuntu loaded? Have you tried to reinstall grub from within Ubuntu?

---

### Post by kansasnoob on 2009-11-17
> **sauravbhaumik said:**
> Hello,
I had dual boot Ubuntu 9.10 and windows XP. Installed opensuse as a third boot. After installing opensuse, I lost my ubuntu boot screen, and I tried to repair my boot screen by modifying the mbr using supergrub disc (that's only how I can login to my ubuntu), but I couldn't restore ubuntu grub to mbr because there is no /boot/grub/stage1. 

I tried to install ubuntu afresh, but you see, the partition manager which comes during installation doesn't find the already existing partitions, so the only suggestion it gives is to format the whole hard disc. But I have valuable things in my hard disc. 

I tried to format the partition where opensuse is, but still I can't, because the disc utility gives an error while formatting that partition. 

Kindly help me out! I am in great distress!

Regards,
Saurav

If you can either boot into Ubuntu or run the Ubuntu Live CD (choosing Try Ubuntu without changes to disc) run the Boot Info Script and post the results as described here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by sauravbhaumik on 2009-11-17
> **snkiz said:**
> Witch version of grub are you using in Ubuntu? The new one doesn't use /boot/grub/stage1. You say you can use super grub to get Ubuntu loaded? Have you tried to reinstall grub from within Ubuntu?

Which grub to reinstall? I mean, I suppose the grub that ubuntu 9.10 uses by default, doesn't use /boot/grub/stage1. Still super grub disk can load ubuntu. However, even if I reinstall grub, how can I restore my ubuntu grub to mbr? I find another great trouble: after installation of the opensuse, no live cd can find the partitioning of my hard disc. So I can't install my ubuntu afresh!

Kindly instruct.

---

### Post by sauravbhaumik on 2009-11-17
Hello,
My mbr issue is solved, I just reinstalled the grub and rebooted and have found my old ubuntu boot screen.
However, a greater anxiety is there because Ubuntu live cd installation can't find my partition table and says that no operating system is there in my hard disc. What to do?
Edit: Gparted says that the whole hard disc is unallocated.

---

### Post by snkiz on 2009-11-17
It doesn't see any of your partitions? that is troublesome. However I'd suggest you never use the auto partitioning in ANY distro, its too easy to mess up. Does gparted on the live disk show the correct partitions?

---

### Post by kansasnoob on 2009-11-17
> **sauravbhaumik said:**
> Hello,
My mbr issue is solved, I just reinstalled the grub and rebooted and have found my old ubuntu boot screen.
However, a greater anxiety is there because Ubuntu live cd installation can't find my partition table and says that no operating system is there in my hard disc. What to do?
Edit: Gparted says that the whole hard disc is unallocated.

That Boot Info Script would tell us a lot!

---

### Post by snkiz on 2009-11-17
> **kansasnoob said:**
> That Boot Info Script would tell us a lot!
Definitely do that something is not right there.

---

### Post by sauravbhaumik on 2009-11-17
Hello, something worse happened. I deleted that suspicious partition by windows cd and after that my ubuntu grub again started not to be detected. Here is the result:
```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

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

/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="WINDOWS" UUID="6029-8182" TYPE="vfat" 
/dev/sda2: UUID="4f0aaacb-4857-4f28-94b9-f29c568729a5" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: UUID="C49ED3E49ED3CCD4" LABEL="Data" TYPE="ntfs" 
/dev/sda5: UUID="c6f7d865-4b4c-4a6d-92f0-13539f5ce894" TYPE="swap" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


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
set root=(hd0,3)
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
  32.5GB: boot/initrd.img-2.6.31-14-generic
  32.5GB: boot/vmlinuz-2.6.31-14-generic
  32.5GB: initrd.img
  32.5GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda6



=============================== StdErr Messages: ===============================

hexdump: /dev/sda6: No such file or directory
hexdump: /dev/sda6: No such file or directory
```

---

### Post by kansasnoob on 2009-11-17
Did you delete a partition before or after running that script?

If you can boot Ubuntu again (even if using Super Grub Disk) then just go to terminal and run:

```
sudo grub-install /dev/sda
```

If that returns any errors run:

```
sudo grub-install --recheck /dev/sda
```

Then:

```
sudo update-grub
```

Hopefully that will get both Ubuntu and Windows booting. If so see what shape you're in as far as being able to access data, etc.

---

### Post by sauravbhaumik on 2009-11-17
> **kansasnoob said:**
> Did you delete a partition before or after running that script?

If you can boot Ubuntu again (even if using Super Grub Disk) then just go to terminal and run:

```
sudo grub-install /dev/sda
```

If that returns any errors run:

```
sudo grub-install --recheck /dev/sda
```

Then:

```
sudo update-grub
```

Hopefully that will get both Ubuntu and Windows booting. If so see what shape you're in as far as being able to access data, etc.
sudo grub-install /dev/sda returns error: ```
cannot seek `/dev/sda'
grub-probe: error: cannot find a device for /boot/grub.

No path or device is specified.
Try ``grub-probe --help'' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.

```

With the recheck option it says: ```
sudo grub-install --recheck /dev/sda
error: cannot seek `/dev/sda'
grub-probe: error: cannot find a device for /boot/grub.

No path or device is specified.
Try ``grub-probe --help'' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
ubuntu@ubuntu:~$ 
```

---

### Post by snkiz on 2009-11-17
I'm sorry this is out of my league to fix but I'd say from reading that your partition table is fragged. No matter what you do to get you system booting THAT is a ticking timebomb. I humbly suggest you backup and start over.

> /dev/sda3 overlaps with /dev/sda4
/dev/sda5 ends after the last sector of /dev/sda
the logical partition /dev/sda5 is not contained in the extended partition /dev/sda3
/dev/sda6 ends after the last sector of /dev/sda
the logical partition /dev/sda6 is not contained in the extended partition /dev/sda3


---

### Post by kansasnoob on 2009-11-17
> **sauravbhaumik said:**
> sudo grub-install /dev/sda returns error: ```
cannot seek `/dev/sda'
grub-probe: error: cannot find a device for /boot/grub.

No path or device is specified.
Try ``grub-probe --help'' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.

```

With the recheck option it says: ```
sudo grub-install --recheck /dev/sda
error: cannot seek `/dev/sda'
grub-probe: error: cannot find a device for /boot/grub.

No path or device is specified.
Try ``grub-probe --help'' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
ubuntu@ubuntu:~$ 
```

Were you booted into Ubuntu when you did that?

Or running the Live CD?

If booted into Ubuntu post the output of:

```
df -H
```

and:

```
sudo parted /dev/sda print
```

---

### Post by sauravbhaumik on 2009-11-17
> **kansasnoob said:**
> Were you booted into Ubuntu when you did that?

Or running the Live CD?

If booted into Ubuntu post the output of:

```
df -H
```

and:

```
sudo parted /dev/sda print
```
Yes, I was doing that from the live cd; while being booted in my ubuntu, the output is ```
saurav@reflexion:~$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda2               31G    15G    14G  52% /
udev                   1.6G   254k   1.6G   1% /dev
none                   1.6G   1.2M   1.6G   1% /dev/shm
none                   1.6G   197k   1.6G   1% /var/run
none                   1.6G      0   1.6G   0% /var/lock
none                   1.6G      0   1.6G   0% /lib/init/rw
/dev/sr0               4.6M   4.6M      0 100% /media/cdrom0
/dev/sda1               33G    12G    22G  36% /media/WINDOWS
/dev/sda4              126G    47G    80G  38% /media/Data

```

and the second one:```
saurav@reflexion:~$ sudo parted /dev/sda print
Error: Invalid argument during seek for read on /dev/sda                  
Retry/Ignore/Cancel? 
```

---

