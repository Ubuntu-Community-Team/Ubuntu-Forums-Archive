---
title: "grub error"
date: 2009-12-23
forum: New to Ubuntu
---

### Post by libihero on 2009-12-23
i deleted a partition, and it gave me an error that went something along the lines of there being no grub and "grub recovery>" with a prompt.
i did a temporary fix by installing an ubuntu partition, but how can i completely fix it?

---

### Post by oldfred on 2009-12-24
If you have a working Ubuntu you can download and run this script in that and run it from the location downloaded to, lyou will have to make it executable if you do that.

From a LiveCD:
Download this script to your Desktop from 
[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)
sudo bash ~/Desktop/boot_info_script*.sh
This creates the file RESULTS.txt on your Desktop. Post the content of RESULTS.txt (use the code tags: #)

---

### Post by tacantara on 2009-12-24
> **libihero said:**
> i deleted a partition, and it gave me an error that went something along the lines of there being no grub and "grub recovery>" with a prompt.
i did a temporary fix by installing an ubuntu partition, but how can i completely fix it?


I did the same thing the other night.  This thread helped me reinstall the GRUB bootloader:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by libihero on 2009-12-24
is there a way that i can make my largest partition the main grub partition so i can delete the smaller one i made without removing grub?

---

### Post by oldfred on 2009-12-24
It depends on which grub is in control, the last install is usually the version of grub in the MBR that the system uses to boot. The boot info script will tell us what is where.

---

### Post by libihero on 2009-12-24
how can i give it to u? and is there a way to reinstall it on the version i want to be the default?

---

### Post by oldfred on 2009-12-25
Boot Info Script 0.42 courtesy of forum member meierfra 
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/) 
Instructions:  louieb's 
 [http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
 
or as example if on desktop or  downloads directory from liveCD download: 
sudo bash ~/Desktop/boot_info_script*.sh
sudo bash ~/Downloads/boot_info_script*.sh 
This will create a RESULTS.txt file in the same directory.(Ver41 put mine in my home dir). Paste the entire contents of that file back here, it can be big. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text, to make it easier to view.

---

### Post by mapes12 on 2009-12-25
I'm not sure which version of Ubu you have on your system. If it's the latest 9.10 then this may help you out: [https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by libihero on 2009-12-29
when i tried to reinstall grub from a livecd
```
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
grub-probe: error: Cannot find a GRUB drive for /dev/sda1.  Check your device.map.

Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.

```

here is my boot info script
```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /grub.
sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x11f2341e

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   364,723,694   364,723,632  83 Linux
/dev/sda3         364,723,695   372,724,064     8,000,370  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="e6e0b425-ef3c-4ab8-9714-79c1d4a2ec9a" TYPE="ext4" 
/dev/sda3: UUID="e6e734d8-9cb1-4810-87c1-7fb896041693" TYPE="swap" 

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
/dev/sda1 on /mnt type ext4 (rw)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root=(hd0,1)
search --no-floppy --fs-uuid --set e6e0b425-ef3c-4ab8-9714-79c1d4a2ec9a
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
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set e6e0b425-ef3c-4ab8-9714-79c1d4a2ec9a
insmod tga
if background_image /boot/grub/Allah.tga ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/black
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set e6e0b425-ef3c-4ab8-9714-79c1d4a2ec9a
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=e6e0b425-ef3c-4ab8-9714-79c1d4a2ec9a ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (on /dev/sda2)" {
	insmod ntfs
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 3c4e589a4e584f30
	chainloader +1
}
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=e6e0b425-ef3c-4ab8-9714-79c1d4a2ec9a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e6e734d8-9cb1-4810-87c1-7fb896041693 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-16-generic
    .0GB: boot/vmlinuz-2.6.31-16-generic
    .0GB: initrd.img
    .0GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb 

```

---

### Post by oldfred on 2009-12-29
This has pretty much the same instructions as the link mapes12 gave you. You have to do the full chroot into your system from the live CD. The grub2 in your MBR points to a partition sda5 you have deleted. You need to use sda1 as that is where your install is.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

sudo mkdir /media/sda1
sudo mount /dev/sda1 /media/sda1
sudo grub-install --root-directory=/media/sda1 /dev/sda

---

### Post by libihero on 2009-12-29
i tried and this is exactly what happens:
```
ubuntu@ubuntu:~$ sudo mkdir /media/sda1
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /media/sda1
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/sda1 /dev/sda
grub-probe: error: Cannot find a GRUB drive for /dev/sda1.  Check your device.map.

Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.

```

---

### Post by oldfred on 2009-12-30
If you have only one drive the device map should not be wrong, but since it says check it.

/boot/grub/device.map

It should just be this:
(hd0)    /dev/sda

---

### Post by libihero on 2010-01-02
my device.map file is completely empty
should i put (hd0) /dev/sda into it?

---

