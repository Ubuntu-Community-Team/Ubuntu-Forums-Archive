---
title: "Not opening Ubuntu on Dell Dimension 8250"
date: 2010-01-15
forum: New to Ubuntu
---

### Post by obliviousdream on 2010-01-15
I just bought this computer, and changed the Hard Drive to a larger one (It started with a 30 GB, upgraded to a 350 GB by the same company) 

Anyway, the disk works, the installation work (I know because it opens GRUB, and when I reinstalled it, the partitioner noticed it.) But when I try to boot into it, it gives me an error.

The error is: error: no such device: 60ff5674-d927-49be-803f-a5cb1e2d6cc6

Anyway, does anyone know what's wrong? I'm so confused...

---

### Post by audiomick on 2010-01-15
I think that grub is looking for the UUID of the old HD, or at least the wrong UUID.

Do you know if it is Grub or Grub 2?
there is info for repairing Grub here
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

and Grub2 here
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

grub has a version number under 1.0, it is 0.96 or so.
Grub2 has a version number over 1.0, like 1.97 or so.

---

### Post by obliviousdream on 2010-01-15
It would have to be Grub2 because I'm using Karmic.

So, If I fix it, it'll work? I'll try. 

But why would it try and look for the other UUID? I never tried to install it on the other one.

I can't figure it out from the page you linked me to...There's a lot of info, and I don't know what to do with it...

---

### Post by audiomick on 2010-01-15
> **obliviousdream said:**
> 
But why would it try and look for the other UUID? I never tried to install it on the other one.

Don't know enough about it to say...
Try the instructions from the documentation. If it doesn't work, post again. There is a lot of traffic on the subject. Someone will be able to help.;)

---

### Post by obliviousdream on 2010-01-15
Okay, that sounds like what's wrong (The UUID is just wrong...) However, I'm having some trouble finding the new one, and also I don't know how to change it. Any help?

Okay, the UUID that it's searching for is the same as the one installed. So...I have no idea how to fix it. It's saying that my dev/sda1 is that UUID, and it's type is EXT4

---

### Post by audiomick on 2010-01-15
Seems like your making at least a tiny bit of progress.

There is a very helpful thing here
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
that I would recommend you go through.

The boot info script generates a text file full of info about what is installed where. Maybe you will be able to see the problem yourself, otherwise post it back here.

---

### Post by obliviousdream on 2010-01-15
Yeah...I don't understand any of it. It's really confusing. I'll post it up for you guys to see.

```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
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

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0003144c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   617,618,924   617,618,862  83 Linux
/dev/sda2         617,618,925   625,137,344     7,518,420   5 Extended
/dev/sda5         617,618,988   625,137,344     7,518,357  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2003 MB, 2003795968 bytes
32 heads, 63 sectors/track, 1941 cylinders, total 3913664 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7a661ec4

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63     3,913,055     3,912,993   6 FAT16


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="60ff5674-d927-49be-803f-a5cb1e2d6cc6" TYPE="ext4" 
/dev/sda5: UUID="de8f8d4e-e812-4723-b38a-21846f14f2a0" TYPE="swap" 
/dev/sdb1: SEC_TYPE="msdos" LABEL="" UUID="68AA-50EE" TYPE="vfat" 

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
/dev/sdb1 on /media/68AA-50EE type vfat (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


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
search --no-floppy --fs-uuid --set 60ff5674-d927-49be-803f-a5cb1e2d6cc6
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
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 60ff5674-d927-49be-803f-a5cb1e2d6cc6
	linux	/boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 60ff5674-d927-49be-803f-a5cb1e2d6cc6
	linux	/boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 ro single 
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=60ff5674-d927-49be-803f-a5cb1e2d6cc6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=de8f8d4e-e812-4723-b38a-21846f14f2a0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/core.img
    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: initrd.img
    .0GB: vmlinuz
```

---

### Post by audiomick on 2010-01-15
Ok. I don't understand all of it either, but as far as I can tell, it looks right. There is a Grub there, it knows where the system is, and is looking for it at the right place.:confused: I think, anyway.

That brings me to other thoughts. On my desktop (this machine), I had several bouts of start problems, which resulted in behaviour that looked like the computer couldn't read the HD. I solved that (after the shop had updated the BIOS and then changed the whole motherboard...) by checking that all the cables were plugged in right, and turning off all the fast start options in BIOS. My HDs are Samsung, and they seem to need a few extra seconds to spin up and get themselves together. Do you think that something along those lines might be possible?

---

### Post by obliviousdream on 2010-01-15
Maybe, except I've disabled fast start, and usually when the computer can't read the hard drive, I can't use LiveCDs. And it can obviously read it, because I've installed Ubuntu on it already...

So I'm confused. I'm going to see if maybe it's GRUB2 just not liking me, and install Linux Mint 7.   

And if that doesn't work, I just don't know what to do.

---

### Post by audiomick on 2010-01-15
Ok, if the fast start stuff is off, it should probably work. On the other hand I have also seen recommendations to put a "wait" in the boot sequence. (but I don't remember how, sorry)

Being able to use the Live CD is possibly not an indication. By the time the CD is up and running, the HD has had lots of time to spin up and get ready to go.

Try re-installing Grub with the instructions from the Grub2 documentation. Maybe that will help...

---

