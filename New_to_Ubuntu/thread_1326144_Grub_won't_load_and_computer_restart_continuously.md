---
title: "Grub won't load and computer restart continuously"
date: 2009-11-14
forum: New to Ubuntu
---

### Post by IsolatedSheep on 2009-11-14
Hey guys,

As mentioned by the title, when I start my computer, there's no option for dual boot (i'm using 9.10 and XP) but only "Grub loading" then the computer restarts and this continues until I remove the power supply.

Here's my spec:
* laptop amd64 turion X2
* ATI Radeon HD3200
* 3 GB ddr2

Before the problem starts, I was on XP. I downloaded autodesk 3ds max and installed it on my XP and run it for testing and no problem. Then there's this Windows update which I don't know exacly what the update is. I shutdown my computer and Windows intalling the update to my computer. When I reboot my computer, the problem occur.

I tried to check grub.conf, but i couldn't find it in /boot/grub/. I'm currently running ubuntu from the liveCD. So, please help me solve this. Thanks in advance.

---

### Post by ikt on 2009-11-14
on the live cd try running ```
sudo update-grub
```, and rebooting

---

### Post by IsolatedSheep on 2009-11-14
It says this
```

Searching for GRUB installation directory ... 
No GRUB directory found. To create a template run 'mkdir /boot/grub' first.
To install grub, install it manually or try the 'grub-install' command.
### Warning, grub-install is used to change your MBR. ###

```

Can I create a certain folder anywhere and install grub there then replace the old folder in my 9.10 root (/boot/grub/) with the new one?

---

### Post by IsolatedSheep on 2009-11-14
*update*

I tried to reinstall grub into the MBR (/dev/sda) but it gives me an error. Here's the code:
```
ubuntu@ubuntu:~$ sudo grub-install /dev/sda
Could not find device for /boot: Not found or not a block device.
```what does this mean?

---

### Post by ranch hand on 2009-11-14
I think you better boot to your live CD and run this script;

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

And pot the results for us.

---

### Post by IsolatedSheep on 2009-11-14
here's the content of RESULT.txt
```

============================= Boot Info Summary: ==============================

 => Grub1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #8 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   /menu.lst

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x74557455

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   102,398,309   102,398,247   7 HPFS/NTFS
/dev/sda2         102,398,310   488,392,064   385,993,755   f W95 Ext d (LBA)
/dev/sda5         102,398,373   236,782,034   134,383,662   7 HPFS/NTFS
/dev/sda6         286,712,118   467,459,369   180,747,252   7 HPFS/NTFS
/dev/sda7         467,459,433   468,873,089     1,413,657  82 Linux swap / Solaris
/dev/sda8         468,873,153   488,392,064    19,518,912  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="26A4E13DA4E1105B" LABEL="System" TYPE="ntfs" 
/dev/sda5: UUID="A69C733A9C730459" LABEL="Misc" TYPE="ntfs" 
/dev/sda6: UUID="A8C88161C8812E9E" LABEL="Downloads" TYPE="ntfs" 
/dev/sda7: TYPE="swap" 
/dev/sda8: UUID="3d7c0a0b-4cb4-41a1-ad75-75826020c340" TYPE="ext4" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda8 on /media/disk type ext4 (rw,nosuid,nodev,uhelper=hal)
/dev/sda6 on /media/Downloads type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5 on /media/Misc type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1 on /media/System type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

================================ sda5/menu.lst: ================================

title Windows
rootnoverify (hd0,0)
chainloader (hd0,0)+1 

=================== sda5: Location of files loaded by Grub: ===================


  52.4GB: menu.lst

=========================== sda8/boot/grub/grub.cfg: ===========================

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
set root=(hd0,8)
search --no-floppy --fs-uuid --set 3d7c0a0b-4cb4-41a1-ad75-75826020c340
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
    set root=(hd0,8)
    search --no-floppy --fs-uuid --set 3d7c0a0b-4cb4-41a1-ad75-75826020c340
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=3d7c0a0b-4cb4-41a1-ad75-75826020c340 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,8)
    search --no-floppy --fs-uuid --set 3d7c0a0b-4cb4-41a1-ad75-75826020c340
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=3d7c0a0b-4cb4-41a1-ad75-75826020c340 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 26a4e13da4e1105b
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda8 during installation
UUID=3d7c0a0b-4cb4-41a1-ad75-75826020c340 /               ext4    errors=remount-ro 0       1
/dev/sda7       none            swap    sw              0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda8: Location of files loaded by Grub: ===================


 242.8GB: boot/grub/grub.cfg
 242.2GB: boot/grub/stage2
 247.0GB: boot/initrd.img-2.6.31-14-generic
 240.5GB: boot/vmlinuz-2.6.31-14-generic
 247.0GB: initrd.img
 240.5GB: vmlinuz

```

---

### Post by Paqman on 2009-11-14
> **ikt said:**
> on the live cd try running ```
sudo update-grub
```, and rebooting

That won't work, because it'll run on the live session, not the system installed onto the hard drive. If you want to run commands on the installed system, you have to [chroot]("http://ubuntuforums.org/showthread.php?t=1156240") into it.

---

### Post by ranch hand on 2009-11-14
I believe this is just a case of Win JerryLewis Pro not playing nicely with others.

Follow these instructions;

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

You will come to the "edit file" part.  Looking at your info I think you can ignore that.

---

### Post by IsolatedSheep on 2009-11-14
i got this error when i try to chroot:
```

ubuntu@ubuntu:~$ sudo mount /dev/sda8 /mnt
mount: /dev/sda8 already mounted or /mnt busy
mount: according to mtab, /dev/sda1 is already mounted on /mnt
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo chroot /mnt
[COLOR=Red]chroot: cannot run command `/bin/bash': Exec format error[/COLOR]

```

p/s: I forgot to mention, I'm using LiveCD for 9.04 but the one installed in my computer is 9.10. I have a USB installer for 9.10, but it's just an installer.

---

### Post by oldfred on 2009-11-14
Ubuntu 9.04 used old grub and 9.10 uses grub2 (1.97 beta4 currently). You do not want to mix these unless you really want to revert to old grub - lot more complicated. To reinstall new grub you have to use the 9.10 liveCD or can you boot your installer USB key?

---

### Post by ranch hand on 2009-11-14
It really shouldn't matter what CD you use.  The 9.04 is good because it is compatible with ext4.

I am not sure why you are having a problem with this.

Why don't you close down your box and restart with the disk and see if that helps.

---

### Post by IsolatedSheep on 2009-11-14
@oldfred: I can boot to the USB installer but I'm not sure how to solve this from the installer. Because it's plainly an installer, no internet connection (if I'm not mistaken).

@ranch hand: still can't chroot. Would this means anything? :
```

ubuntu@ubuntu:~$ ls -l /bin/sh
lrwxrwxrwx 1 root root 4 2009-04-20 13:59 /bin/sh -> dash
ubuntu@ubuntu:~$ ls -l /media/disk/bin/sh
lrwxrwxrwx 1 root root 4 2009-11-07 23:54 /media/disk/bin/sh -> dash

```

---

### Post by ranch hand on 2009-11-14
Probably.  Unfortunately not to me.

I take it, then, that you are getting the same errors for your commands as before?

---

### Post by IsolatedSheep on 2009-11-15
I've downloaded livecd for 9.10 and do the chroot and solved the problem. :D
Looks like grub2 is not compatible for grub. Maybe something in the bash for 9.10 is set for grub2. :/

*EDIT*
Forgot something, thanks guys ^_^

---

