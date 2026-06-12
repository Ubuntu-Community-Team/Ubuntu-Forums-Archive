---
title: "Grub ERROR 15"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by MATUBA on 2010-01-03
Hi!
After following some advises to make my old computer ran faster , the old Abacus went dead, and the only way to access the hd is through the live cd, Esc won't work and neither the recovery mode,  please I will appreciate any help thanks!!
There is the info
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000675f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4679    37584036   83  Linux
/dev/sda2            4680        4866     1502077+   5  Extended
/dev/sda5            4680        4866     1502046   82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo blkid
/dev/sda1: UUID="a49c55ad-4926-4b41-89be-55addf305766" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="a1e4d55a-73d0-48a0-a734-bb223d5ee6d4" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 
/dev/ramzswap0: TYPE="swap"

---

### Post by kansasnoob on 2010-01-03
Please post the output of the Boot Info Script as described here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

That may seem like overkill on a single boot system but then we'll know what version of Ubuntu and grub we're dealing with along with the appropriate boot files, ie: menu.lst or grub.cfg :)

Also more info about exactly what changes you made to try and speed things up might be helpful.

---

### Post by MATUBA on 2010-01-03
Thanks for your help!!!
============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 1.97
    Boot sector info:  Grub 1.97 is installed in the boot sector of sda1 and 
                       looks at sector 51384399 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sda and 
                       looks on partition #1 for /boot/grub.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders, total 78177792 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0000675f

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    75,168,134    75,168,072  83 Linux
/dev/sda2          75,168,135    78,172,289     3,004,155   5 Extended
/dev/sda5          75,168,198    78,172,289     3,004,092  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

sda1: UUID="a49c55ad-4926-4b41-89be-55addf305766" TYPE="ext3" 
sda5: UUID="a1e4d55a-73d0-48a0-a734-bb223d5ee6d4" TYPE="swap" 

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
/dev/sda1 on /mnt type ext3 (rw)
/dev on /mnt/dev type none (rw,bind)


=========================== sda1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=a49c55ad-4926-4b41-89be-55addf305766 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.10, kernel 2.6.31-17-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=a49c55ad-4926-4b41-89be-55addf305766 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-17-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=a49c55ad-4926-4b41-89be-55addf305766 ro  single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.28-17-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=a49c55ad-4926-4b41-89be-55addf305766 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-17-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-17-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=a49c55ad-4926-4b41-89be-55addf305766 ro  single
initrd		/boot/initrd.img-2.6.28-17-generic

title		Ubuntu 9.10, kernel 2.6.27-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-16-generic root=UUID=a49c55ad-4926-4b41-89be-55addf305766 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.27-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-16-generic root=UUID=a49c55ad-4926-4b41-89be-55addf305766 ro  single
initrd		/boot/initrd.img-2.6.27-16-generic

title		Ubuntu 9.10, kernel 2.6.24-26-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=a49c55ad-4926-4b41-89be-55addf305766 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-26-generic
quiet

title		Ubuntu 9.10, kernel 2.6.24-26-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=a49c55ad-4926-4b41-89be-55addf305766 ro  single
initrd		/boot/initrd.img-2.6.24-26-generic

title		Ubuntu 9.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a49c55ad-4926-4b41-89be-55addf305766 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a49c55ad-4926-4b41-89be-55addf305766 ro  single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 9.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/10_linux ###
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
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=a49c55ad-4926-4b41-89be-55addf305766 /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/hda5
UUID=a1e4d55a-73d0-48a0-a734-bb223d5ee6d4 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/fd1        /media/floppy1  auto    rw,user,noauto,exec 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/core.img
    .0GB: boot/grub/grub.cfg
    .0GB: boot/grub/menu.lst
    .0GB: boot/grub/stage2

---

### Post by kansasnoob on 2010-01-03
You have mixed grub files/directories.

Which grub do you want to use? Legacy grub or grub2?

I rather recommend grub2 unless it just doesn't work for you for some reason.

As soon as I know I'll type the commands you can run from the Live CD to get you going.

---

### Post by MATUBA on 2010-01-03
grub2 sounds good to me

---

### Post by kansasnoob on 2010-01-03
OK from the terminal running the Live CD we'll mount and chroot sda1:

```
sudo mount /dev/sda1 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```

```
dpkg-divert --local --rename --add /sbin/initctl
```

```
ln -s /bin/true /sbin/initctl
```

```
mv /boot/grub /boot/grub_backup
```

```
mkdir /boot/grub
```

```
apt-get --purge remove grub
```

Note: it may say "not installed so not removed", that's OK.

```
apt-get update
```

```
apt-get install --reinstall grub-pc
```

```
update-grub
```

```
grub-install /dev/sda
```

If that shows any errors:

```
grub-install --recheck /dev/sda
```

Then exit the chroot and unmount:

```
exit
```

```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

Don't worry about errors from that last command.

Then just reboot.

---

### Post by MATUBA on 2010-01-03
not going after this point:
root@ubuntu:/# apt-get update && apt-get install --reinstall grub-pc
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US                     
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates Release.gpg                     
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/main Translation-en_US          
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release.gpg                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Translation-en_US      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Translation-en_US      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Translation-en_US             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates Release                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Translation-en_US            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Translation-en_US        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg                               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Translation-en_US                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Translation-en_US                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Translation-en_US              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security Release.gpg                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Translation-en_US           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Translation-en_US           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release                                
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/main Packages                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Translation-en_US       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed Release.gpg                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed/universe Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed/main Translation-en_US           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed/restricted Translation-en_US     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security Release                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages                      
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/restricted Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed Release                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages          
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/main Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Packages
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Sources
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/main Packages
  404  Not Found [IP: 91.189.88.40 80]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Sources
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/restricted Packages
  404  Not Found [IP: 91.189.88.40 80]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed/restricted Packages
W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.40 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by MATUBA on 2010-01-03
root@ubuntu:/# update-grub
The program 'update-grub' can be found in the following packages:
 * grub
 * grub-pc
 * grub-coreboot
 * grub-efi-amd64
 * grub-efi-ia32
 * grub-ieee1275
Try: apt-get install <selected package>
update-grub: command not found

---

### Post by MATUBA on 2010-01-03
Should I start all over again?

---

### Post by kansasnoob on 2010-01-03
Why do you have Gutsy and Dapper repos in your Karmic?

Regardless go back to post #6, well look here to better understand the commands in my mount & chroot:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

If you have not exited the chroot just drop the update from that one command "apt-get update && apt-get install --reinstall grub-pc" like:

```
apt-get install --reinstall grub-pc
```

```
update-grub
```

```
grub-install /dev/sda
```

Understand?

It couldn't update the package list because your sources.list is an absolute mess! It may fail to install grub-pc though, we'll have to see.

---

### Post by kansasnoob on 2010-01-03
I separated the update & install --reinstall commands in post #6 so if you run into trouble just reboot and try that again.

If it doesn't work we'll have to try the same thing, only installing legacy grub, and if that doesn't work we'll have to try and straighten out your sources.list.

You never did say what you did to try and speed things up :confused:

And I'm dieing to know why you have Dapper and Gutsy repos in a Karmic sources.list.

---

