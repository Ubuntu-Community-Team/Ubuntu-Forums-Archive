---
title: "Kernel Panic....9.1 wont boot....uninstalled VB and tried to reinstall"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by jotto! on 2009-11-12
OK, so after getting a lot of help to get VirtualBox working, I decided I wanted USB support so DL the PUEL version.
I clicked on uninstall for the OSE version expecting to get some options to save my configuration but nothing....just seemed to uninstall.

Went to install vitualbox PUEL and got an error, conflicting with existing installation.

Thought I might need to re-boot to complete removal, clicked on restart and now all I get is something like
[ 0.924148 ] Kernel Panic not syncing : VFS unable to mount root fs on unknown block (0,0) 

Any ideas? I just have a flashing cursor and cant type anything in.....

---

### Post by jotto! on 2009-11-13
TTT
Still no boot and Im at a complete loss....do I need to try and boot from an ubuntu CD/DVD and type some commands in to see whats going on?

---

### Post by aquavitae on 2009-11-13
Try booting off a live cd and post the output from ```
sudo fdisk -l
```
Also see if you can post the contents of /boot/grub/menu.lst.

Just to claify, did you install and uninstall VB from the package manager?  Or did you download it from the website?

---

### Post by jotto! on 2009-11-13
Hope Ive got this correct....
Think I installed VB by package manager but not sure!


Disk /dev/sda: 300.1 GB, 300090728448 bytes

255 heads, 63 sectors/track, 36483 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x00930092



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *           1       36482   293041633+   7  HPFS/NTFS



Disk /dev/sdb: 160.0 GB, 160041885696 bytes

will go back for the other one!

255 heads, 63 sectors/track, 19457 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0xf7fdf7fd



   Device Boot      Start         End      Blocks   Id  System

/dev/sdb1   *           1       19456   156280288+   7  HPFS/NTFS

ubuntu@ubuntu:~$

---

### Post by jotto! on 2009-11-13
Ok, looked in file system, boot, grub folder and all I could find was a file named grubenv
When I opend it, it looked like this

#Grub Enviroment Block
#####################################################

And that was it....

---

### Post by jotto! on 2009-11-13
OK so couldnt find menu.lst but did find grub...
does this help?


# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"

---

### Post by aquavitae on 2009-11-16
Are you sure you're looking at /boot on the right drive?  Once you've booted off the live cd, open a terminal and type the following
```

sudo mkdir -p /mnt/temp
sudo mount -o default,users,ro /dev/sda1 /mnt/temp
ls /mnt/temp

```
If you get a permission denied error try "sudo ls /mnt/temp".  It should give you a list of system folders (i.e. bin boot etc home media ...)  If so, see if you can browse (in a file browser) to /mnt/temp/boot/grub/menu.lst.

---

