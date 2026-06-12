---
title: "Grub not Updating"
date: 2010-01-25
forum: New to Ubuntu
---

### Post by EnigmaticCoder on 2010-01-25
I'm trying to change the default menu entry of Grub as well as the splash image, but it's not working. I was able to do it a few months ago (change the default entry and splash image), but I can't seem to get it to work today. I commented out the GRUB_DEFAULT = 4 line in /etc/default/grub and added GRUB_DEFAULT = 0, but it still chooses the fifth entry when I boot. As for the image, when I run update-grub, it says no image is found, but uses my previous splash image. Anyone know what I should do to fix these problems?

---

### Post by drs305 on 2010-01-25
You aren't adding spaces in "GRUB_DEFAULT=0" are you? And it appears you have run "sudo update-grub" to actually update the menu.

Please download and run the boot info script and post the content between the "code" brackets (press the # icon in the post menu):
[http://ubuntuforums.org/showthread.php?t=1291280]("http://ubuntuforums.org/showthread.php?t=1291280")

You could also try placing the exact title from grub.cfg between the GRUB_DEFAULT= quotes but I'd wait until we see what boot_info turns up.

---

### Post by EnigmaticCoder on 2010-01-25
Yep, I'm running update-grub, and there are no spaces.

Here's the output from that script:

```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub.
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

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   268,410,239   268,410,177   7 HPFS/NTFS
/dev/sda2         268,414,020   488,392,064   219,978,045   5 Extended
/dev/sda5         268,414,083   482,383,754   213,969,672  83 Linux
/dev/sda6         482,383,818   488,392,064     6,008,247  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="5ABC1981BC195939" TYPE="ntfs" 
/dev/sda5: UUID="98fdfda3-2f9c-4eb7-9367-c4a1421f86bd" TYPE="ext4" 
/dev/sda6: UUID="882e7114-18bd-42d4-a93f-ebfc4d6819e5" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext4 (rw,errors=remount-ro)
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
gvfs-fuse-daemon on /home/john/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=john)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn

=========================== sda5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=98fdfda3-2f9c-4eb7-9367-c4a1421f86bd ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=98fdfda3-2f9c-4eb7-9367-c4a1421f86bd

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
uuid		98fdfda3-2f9c-4eb7-9367-c4a1421f86bd
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=98fdfda3-2f9c-4eb7-9367-c4a1421f86bd ro quiet splash 
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid		98fdfda3-2f9c-4eb7-9367-c4a1421f86bd
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=98fdfda3-2f9c-4eb7-9367-c4a1421f86bd ro  single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.31-16-generic
uuid		98fdfda3-2f9c-4eb7-9367-c4a1421f86bd
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=98fdfda3-2f9c-4eb7-9367-c4a1421f86bd ro quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid		98fdfda3-2f9c-4eb7-9367-c4a1421f86bd
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=98fdfda3-2f9c-4eb7-9367-c4a1421f86bd ro  single
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.31-15-generic
uuid		98fdfda3-2f9c-4eb7-9367-c4a1421f86bd
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=98fdfda3-2f9c-4eb7-9367-c4a1421f86bd ro quiet splash 
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid		98fdfda3-2f9c-4eb7-9367-c4a1421f86bd
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=98fdfda3-2f9c-4eb7-9367-c4a1421f86bd ro  single
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		98fdfda3-2f9c-4eb7-9367-c4a1421f86bd
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=98fdfda3-2f9c-4eb7-9367-c4a1421f86bd ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		98fdfda3-2f9c-4eb7-9367-c4a1421f86bd
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=98fdfda3-2f9c-4eb7-9367-c4a1421f86bd ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Chainload into GRUB 2
root		98fdfda3-2f9c-4eb7-9367-c4a1421f86bd
kernel		/boot/grub/core.img

title		Ubuntu 9.10, memtest86+
uuid		98fdfda3-2f9c-4eb7-9367-c4a1421f86bd
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set default="4"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set 98fdfda3-2f9c-4eb7-9367-c4a1421f86bd
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
set root=(hd0,5)
search --no-floppy --fs-uuid --set 98fdfda3-2f9c-4eb7-9367-c4a1421f86bd
insmod png
if background_image /boot/grub/grubsplash.png ; then
  set color_normal=white/black
  set color_highlight=magenta/white
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/white
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 98fdfda3-2f9c-4eb7-9367-c4a1421f86bd
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=98fdfda3-2f9c-4eb7-9367-c4a1421f86bd ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 98fdfda3-2f9c-4eb7-9367-c4a1421f86bd
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=98fdfda3-2f9c-4eb7-9367-c4a1421f86bd ro single 
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
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 5abc1981bc195939
	drivemap -s (hd0) ${root}
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=98fdfda3-2f9c-4eb7-9367-c4a1421f86bd /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=882e7114-18bd-42d4-a93f-ebfc4d6819e5 none            swap    sw              0       0
/dev/scd1       /media/cdrom2   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 137.4GB: boot/grub/core.img
 137.4GB: boot/grub/grub.cfg
 137.4GB: boot/grub/menu.lst
 137.4GB: boot/initrd.img-2.6.31-14-generic
 137.4GB: boot/initrd.img-2.6.31-15-generic
 137.4GB: boot/initrd.img-2.6.31-16-generic
 137.4GB: boot/initrd.img-2.6.31-17-generic
 137.4GB: boot/vmlinuz-2.6.31-14-generic
 137.4GB: boot/vmlinuz-2.6.31-15-generic
 137.4GB: boot/vmlinuz-2.6.31-16-generic
 137.4GB: boot/vmlinuz-2.6.31-17-generic
 137.4GB: initrd.img
 137.4GB: initrd.img.old
 137.4GB: vmlinuz
 137.4GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

---

### Post by drs305 on 2010-01-25
In the grub.cfg file you posted the default is still set to #4, which would boot Windows:
> 
set default="4"


It appears that any files you are editing are either not the correct ones or are not being executed. Here are a few reasons why this could happen:
1. Editing the wrong file. While in Ubuntu (not on LiveCD):
```
gksu gedit /etc/default/grub
```
Make the change, save the file, then "sudo update-grub". I'd get rid of the commented line and have only one "GRUB_DEFAULT=0" line. You can ensure the script files are executable with the following command.
```

sudo chmod +x /etc/grub.d/*_*

```

2. Make sure the files are executable (check /etc/grub.d/05_debian_theme). For the splash image, is the file grubsplash.png in /boot/grub? That is what it is currently using. You should watch the terminal while update-grub is running and make sure you see the confirmation that the correct image was found.
 
3. Check /boot/grub/grubenv to make sure it isn't holding a "saved" value:
```
cat /boot/grub/grubenv
```
It normally will have one title line with the second line being # symbols, with no "saved" in it. If it has an erroneous entry, run:
```
sudo grub-editenv /boot/grub/grubenv create
```

---

### Post by EnigmaticCoder on 2010-01-25
It seems I'm editing the correct file. I've posted it below, just in case something looks wrong. I also ran this line: sudo chmod +x /etc/grub.d/*_*, but it didn't help.

Also I'm not sure what you mean by "Make sure the files are executable (check /etc/grub.d/05_debian_theme)." Do I have to run ch_mod on some of those files?


Also, "For the splash image, is the file grubsplash.png in /boot/grub?" I'm trying to use MatrixGrubSplashImage.png. It is in /boot/grub as is grubsplash.png.

"You should watch the terminal while update-grub is running and make sure you see the confirmation that the correct image was found." The terminal says that no image is found and skips it.

In regard to the grub environment variables, they are correct. One line followed by a bunch of hash marks.

Any other ideas?

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
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
```

---

### Post by drs305 on 2010-01-25
> **EnigmaticCoder said:**
> It seems I'm editing the correct file. I've posted it below, just in case something looks wrong. I also ran this line: sudo chmod +x /etc/grub.d/*_*, but it didn't help.
The file looks correct. However the key is what is reflected in the RESULTS.txt file. After the first run, it still shows the default setting is "4". You can run "sudo update-grub" again, then run the boot_info script and once again look at the line in RESULTS to see what the value is in *set default="4"*  >  Also I'm not sure what you mean by "Make sure the files are executable (check /etc/grub.d/05_debian_theme)." Do I have to run ch_mod on some of those files? No, that was what the "chmod +x" command did. The files/scripts in /etc/grub.d/ are not considered if the executable bit is removed. This has advantages, such as if the user doesn't want grub searching for other OS's, memtest86+, etc. By running the chmod command it made sure all the scripts should be executed when update-grub is run.  >  I'm trying to use MatrixSplashImage.png. It is in /boot/grub as is grubsplash.png. If you don't see the file being found in the terminal when update-grub is run, it's not being located and included. If you post the line from "/etc/grub.d/05_debian_theme" which lists the image file you are trying to use we can be sure it is in the correct format. The name should be *grubsplash.* Include the period (.) but not the extension, which is included in the brackets {}.  >  Any other ideas?
 I'm a bit paranoid, so I'd move the /boot/grub/menu.lst somewhere else after I confirmed you were seeing the Grub 2 menu on boot. The menu should show 1.96 or later at the top of the menu screen.   You could also add a menuentry to 40_custom, then run update-grub and see if it gets included in the menu. You can confirm it was included by checking the /boot/grub/grub.cfg file or looking for it in the menu when you reboot. Naming it something like "Test Menu" or something other than a kernel name would make it easy to pick out.

---

### Post by EnigmaticCoder on 2010-01-25
Here's the line from 05_debian_theme. I renamed the MatrixGrubSplashImage.png to grubsplash.png, but now no splash image is shown at startup:

for i in {/boot/grub,/usr/share/images/desktop-base}/grubsplash.{png,tga} ; do

About the version, on startup it said 1.97~beta4

About adding a custom entry, what line should I put in 40_custom?

---

### Post by drs305 on 2010-01-25
> **EnigmaticCoder said:**
> Here's the line from 05_debian_theme. I renamed the MatrixGrubSplashImage.png to grubsplash.png, but now no splash image is shown at startup:

for i in {/boot/grub,/usr/share/images/desktop-base}/grubsplash.{png,tga} ; do

About the version, on startup it said 1.97~beta4

About adding a custom entry, what line should I put in 40_custom?

You would copy a menuentry item just as it appears in */boot/grub/grub.cfg* and place it after the commented lines already existing in 40_custom. Here is an example from your grub.cfg:
> menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 98fdfda3-2f9c-4eb7-9367-c4a1421f86bd
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=98fdfda3-2f9c-4eb7-9367-c4a1421f86bd ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}


The next thing I would do is run "sudo update-grub" and then check the timestamp of /boot/grub/grub.cfg and see if it changes.
```
sudo update-grub && ls -la /boot/grub/grub.cfg

``` 

The image coding looks correct as long as your file is in one of the two folders mentioned.

---

### Post by EnigmaticCoder on 2010-01-25
I ran this 

sudo update-grub && ls -la /boot/grub/grub.cfg

And the timestamp was

-r--r--r-- 1 root root 2963 2009-11-13 12:10 /boot/grub/grub.cfg

So apparently, it's not updating for some reason.

---

### Post by drs305 on 2010-01-25
> **EnigmaticCoder said:**
> I ran this 

sudo update-grub && ls -la /boot/grub/grub.cfg

And the timestamp was

-r--r--r-- 1 root root 2963 2009-11-13 12:10 /boot/grub/grub.cfg

So apparently, it's not updating for some reason.

I would try completely removing Grub 2 and reinstalling it. You can make copies of the /etc/grub.d and /boot/grub folders and the /etc/default/grub file if you want just so you have the information if you decide to reference it later. Then I would remove and reinstall assuming you have a stable internet connection. Do not reboot until you have accomplished all the steps:

```

sudo apt-get purge grub-common grub-pc 
sudo apt-get install grub-common grub-pc 

```
Use the tab and space keys if asked to make selections, and ENTER once OK is highlighted.

Once everything is finished, open up the /boot/grub/grub.cfg file and make sure there is a menuentry there for your (hd0,5) linux installation.

---

### Post by meierfra. on 2010-01-25
Before removing and reinstalling Grub2, try

```
sudo update-grub2
```

---

### Post by EnigmaticCoder on 2010-01-25
I tried doing update-grub2, but it asked to install certain packages, so I skipped it. Then I tried reinstalling grub and it game me a bunch of error messages:

error: cannot open `/dev/sdb' while attempting to get disk size

The same error message over and over. It did the same when running sudo update-grub. I'm leery about rebooting now...

Here's the full output:

```
john@EnigmaticLinux:/etc$ sudo update-grub
error: cannot open `/dev/sdb' while attempting to get disk size
error: cannot open `/dev/sdb' while attempting to get disk size
Generating grub.cfg ...
error: cannot open `/dev/sdb' while attempting to get disk size
error: cannot open `/dev/sdb' while attempting to get disk size
error: cannot open `/dev/sdb' while attempting to get disk size
error: cannot open `/dev/sdb' while attempting to get disk size
Found Debian background: grubsplash.png
error: cannot open `/dev/sdb' while attempting to get disk size
error: cannot open `/dev/sdb' while attempting to get disk size
error: cannot open `/dev/sdb' while attempting to get disk size
error: cannot open `/dev/sdb' while attempting to get disk size
Found Debian background: MatrixGrubSplashImage.png
error: cannot open `/dev/sdb' while attempting to get disk size
error: cannot open `/dev/sdb' while attempting to get disk size
error: cannot open `/dev/sdb' while attempting to get disk size
error: cannot open `/dev/sdb' while attempting to get disk size
error: cannot open `/dev/sdb' while attempting to get disk size
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
error: cannot open `/dev/sdb' while attempting to get disk size
error: cannot open `/dev/sdb' while attempting to get disk size
error: cannot open `/dev/sdb' while attempting to get disk size
error: cannot open `/dev/sdb' while attempting to get disk size
error: cannot open `/dev/sdb' while attempting to get disk size
error: cannot open `/dev/sdb' while attempting to get disk size
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
error: cannot open `/dev/sdb' while attempting to get disk size
error: cannot open `/dev/sdb' while attempting to get disk size
error: cannot open `/dev/sdb' while attempting to get disk size
error: cannot open `/dev/sdb' while attempting to get disk size
error: cannot open `/dev/sdb' while attempting to get disk size
error: cannot open `/dev/sdb' while attempting to get disk size
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
error: cannot open `/dev/sdb' while attempting to get disk size
error: cannot open `/dev/sdb' while attempting to get disk size
error: cannot open `/dev/sdb' while attempting to get disk size
error: cannot open `/dev/sdb' while attempting to get disk size
error: cannot open `/dev/sdb' while attempting to get disk size
error: cannot open `/dev/sdb' while attempting to get disk size
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
error: cannot open `/dev/sdb' while attempting to get disk size
error: cannot open `/dev/sdb' while attempting to get disk size
error: cannot open `/dev/sdb' while attempting to get disk size
error: cannot open `/dev/sdb' while attempting to get disk size
error: cannot open `/dev/sdb' while attempting to get disk size
error: cannot open `/dev/sdb' while attempting to get disk size
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Home Edition on /dev/sda1
error: cannot open `/dev/sdb' while attempting to get disk size
error: cannot open `/dev/sdb' while attempting to get disk size
error: cannot open `/dev/sdb' while attempting to get disk size
done

```

---

### Post by meierfra. on 2010-01-25
Do you have any external media plugged in? Check you device map

```
gksudo gedit /boot/grub/device.map
```

If it has an entry for "/dev/sdb" remove that line. Then run "sudo update-grub"   again.

---

### Post by EnigmaticCoder on 2010-01-25
I didn't have any external media, so I removed the line and now update-grub works without error. I'm going to reboot!

---

### Post by EnigmaticCoder on 2010-01-25
Now I'm getting this:

```
john@EnigmaticLinux:/boot/grub$ sudo update-grub
Generating grub.cfg ...
Found Debian background: grubsplash.png
No path or device is specified.
Try ``grub-probe --help'' for more information.
No path or device is specified.
Try ``grub-probe --help'' for more information.

```

EDIT: And also, the splash image still doesn't work, and it still says version 1.97~beta4

---

### Post by EnigmaticCoder on 2010-01-25
I reinstalled it again. When I reinstalled it, I got that blue configuration screen, which didn't happen before. Now the grub probe | no path or device error is gone, but I still can't get the splash image to work.

EDIT: Here's that script output again:

```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub.
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

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   268,410,239   268,410,177   7 HPFS/NTFS
/dev/sda2         268,414,020   488,392,064   219,978,045   5 Extended
/dev/sda5         268,414,083   482,383,754   213,969,672  83 Linux
/dev/sda6         482,383,818   488,392,064     6,008,247  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="5ABC1981BC195939" TYPE="ntfs" 
/dev/sda5: UUID="98fdfda3-2f9c-4eb7-9367-c4a1421f86bd" TYPE="ext4" 
/dev/sda6: UUID="882e7114-18bd-42d4-a93f-ebfc4d6819e5" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext4 (rw,errors=remount-ro)
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
gvfs-fuse-daemon on /home/john/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=john)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn

=========================== sda5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=98fdfda3-2f9c-4eb7-9367-c4a1421f86bd ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=98fdfda3-2f9c-4eb7-9367-c4a1421f86bd

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
uuid		98fdfda3-2f9c-4eb7-9367-c4a1421f86bd
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=98fdfda3-2f9c-4eb7-9367-c4a1421f86bd ro quiet splash
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid		98fdfda3-2f9c-4eb7-9367-c4a1421f86bd
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=98fdfda3-2f9c-4eb7-9367-c4a1421f86bd ro single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.31-16-generic
uuid		98fdfda3-2f9c-4eb7-9367-c4a1421f86bd
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=98fdfda3-2f9c-4eb7-9367-c4a1421f86bd ro quiet splash
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid		98fdfda3-2f9c-4eb7-9367-c4a1421f86bd
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=98fdfda3-2f9c-4eb7-9367-c4a1421f86bd ro single
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.31-15-generic
uuid		98fdfda3-2f9c-4eb7-9367-c4a1421f86bd
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=98fdfda3-2f9c-4eb7-9367-c4a1421f86bd ro quiet splash
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid		98fdfda3-2f9c-4eb7-9367-c4a1421f86bd
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=98fdfda3-2f9c-4eb7-9367-c4a1421f86bd ro single
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		98fdfda3-2f9c-4eb7-9367-c4a1421f86bd
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=98fdfda3-2f9c-4eb7-9367-c4a1421f86bd ro quiet splash
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		98fdfda3-2f9c-4eb7-9367-c4a1421f86bd
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=98fdfda3-2f9c-4eb7-9367-c4a1421f86bd ro single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, memtest86+
uuid		98fdfda3-2f9c-4eb7-9367-c4a1421f86bd
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root=(hd0,5)
search --no-floppy --fs-uuid --set 98fdfda3-2f9c-4eb7-9367-c4a1421f86bd
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
set root=(hd0,5)
search --no-floppy --fs-uuid --set 98fdfda3-2f9c-4eb7-9367-c4a1421f86bd
insmod png
if background_image /boot/grub/grubsplash.png ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/white
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 98fdfda3-2f9c-4eb7-9367-c4a1421f86bd
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=98fdfda3-2f9c-4eb7-9367-c4a1421f86bd ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 98fdfda3-2f9c-4eb7-9367-c4a1421f86bd
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=98fdfda3-2f9c-4eb7-9367-c4a1421f86bd ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 98fdfda3-2f9c-4eb7-9367-c4a1421f86bd
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=98fdfda3-2f9c-4eb7-9367-c4a1421f86bd ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 98fdfda3-2f9c-4eb7-9367-c4a1421f86bd
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=98fdfda3-2f9c-4eb7-9367-c4a1421f86bd ro single 
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 98fdfda3-2f9c-4eb7-9367-c4a1421f86bd
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=98fdfda3-2f9c-4eb7-9367-c4a1421f86bd ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 98fdfda3-2f9c-4eb7-9367-c4a1421f86bd
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=98fdfda3-2f9c-4eb7-9367-c4a1421f86bd ro single 
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 98fdfda3-2f9c-4eb7-9367-c4a1421f86bd
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=98fdfda3-2f9c-4eb7-9367-c4a1421f86bd ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 98fdfda3-2f9c-4eb7-9367-c4a1421f86bd
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=98fdfda3-2f9c-4eb7-9367-c4a1421f86bd ro single 
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
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 5abc1981bc195939
	drivemap -s (hd0) ${root}
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=98fdfda3-2f9c-4eb7-9367-c4a1421f86bd /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=882e7114-18bd-42d4-a93f-ebfc4d6819e5 none            swap    sw              0       0
/dev/scd1       /media/cdrom2   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 137.4GB: boot/grub/core.img
 137.4GB: boot/grub/grub.cfg
 137.4GB: boot/grub/menu.lst
 137.4GB: boot/initrd.img-2.6.31-14-generic
 137.4GB: boot/initrd.img-2.6.31-15-generic
 137.4GB: boot/initrd.img-2.6.31-16-generic
 137.4GB: boot/initrd.img-2.6.31-17-generic
 137.4GB: boot/vmlinuz-2.6.31-14-generic
 137.4GB: boot/vmlinuz-2.6.31-15-generic
 137.4GB: boot/vmlinuz-2.6.31-16-generic
 137.4GB: boot/vmlinuz-2.6.31-17-generic
 137.4GB: initrd.img
 137.4GB: initrd.img.old
 137.4GB: vmlinuz
 137.4GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
=============================== StdErr Messages: ===============================

umount: /tmp/BootInfo/sda1: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
```

---

### Post by EnigmaticCoder on 2010-01-25
Alright, I got the splash image to work. There seemed to be a problem with the specific picture I was using. Marking thread as solved. Cheers.

---

