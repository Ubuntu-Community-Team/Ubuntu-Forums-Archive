---
title: "booting problem"
date: 2010-10-04
forum: New to Ubuntu
---

### Post by DavidVader on 2010-10-04
Hi. So here's the deal. I installed Ubuntu along with Windows 7. I used it with pleasure. But then I had to reinstall W7 because it ****ed up. After reinstalling W7 my grub broke down, but when I used a tutorial to fix this, now when turning on my computer it automatically boots Ubuntu without even noticing W7. Please, help me find a way to bring back my grub, or another way to choose between my OS-es before booting. Thank you.

---

### Post by Clever_Username on 2010-10-04
I would think a "sudo update grub" might be in order here. But I would suggest you wait for one of the more experienced guys on here to respond before doing it. I'm still kind of new.

---

### Post by andrewthomas on 2010-10-04
What tutorial did you use?

This one?

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by da burger on 2010-10-04
I would also guess that sudo update-grub would get you sorted, besides even if it doesn't it's a harmless command that could work. If that fails I would recommend that you run meierfra's boot script and post the RESULTS.txt file here so we have a better idea of exactly what's wrong.

EDIT: I would forget to explain exactly what the boot script was :) [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by DavidVader on 2010-10-04
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #4 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848    45,062,143    44,855,296   7 HPFS/NTFS
/dev/sda3          97,675,261   976,773,119   879,097,859   f W95 Ext d (LBA)
/dev/sda5          97,675,263   971,530,874   873,855,612   7 HPFS/NTFS
/dev/sda6         971,532,288   976,773,119     5,240,832  82 Linux swap / Solaris
/dev/sda4          45,062,144    97,673,215    52,611,072  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="System Reserved" UUID="287E459B7E4562A4" TYPE="ntfs" 
/dev/sda2: UUID="9C567E84567E5F48" TYPE="ntfs" 
/dev/sda4: UUID="fa407b97-1791-4e07-936f-d2c3fe209e39" TYPE="ext4" 
/dev/sda5: LABEL="My Files" UUID="2C84683984680822" TYPE="ntfs" 
/dev/sda6: UUID="60e68aa2-9b42-4465-8978-b2bf8e71b35a" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda4 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/david/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=david)


=========================== sda4/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

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
# kopt=root=UUID=fa407b97-1791-4e07-936f-d2c3fe209e39 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=fa407b97-1791-4e07-936f-d2c3fe209e39

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

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-25-generic
uuid		fa407b97-1791-4e07-936f-d2c3fe209e39
kernel		/boot/vmlinuz-2.6.32-25-generic root=UUID=fa407b97-1791-4e07-936f-d2c3fe209e39 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-25-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-25-generic (recovery mode)
uuid		fa407b97-1791-4e07-936f-d2c3fe209e39
kernel		/boot/vmlinuz-2.6.32-25-generic root=UUID=fa407b97-1791-4e07-936f-d2c3fe209e39 ro  single
initrd		/boot/initrd.img-2.6.32-25-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic
uuid		fa407b97-1791-4e07-936f-d2c3fe209e39
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=fa407b97-1791-4e07-936f-d2c3fe209e39 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-24-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic (recovery mode)
uuid		fa407b97-1791-4e07-936f-d2c3fe209e39
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=fa407b97-1791-4e07-936f-d2c3fe209e39 ro  single
initrd		/boot/initrd.img-2.6.32-24-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-21-generic
uuid		fa407b97-1791-4e07-936f-d2c3fe209e39
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=fa407b97-1791-4e07-936f-d2c3fe209e39 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-21-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-21-generic (recovery mode)
uuid		fa407b97-1791-4e07-936f-d2c3fe209e39
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=fa407b97-1791-4e07-936f-d2c3fe209e39 ro  single
initrd		/boot/initrd.img-2.6.32-21-generic

title		Chainload into GRUB 2
root		fa407b97-1791-4e07-936f-d2c3fe209e39
kernel		/boot/grub/core.img

title		Ubuntu 10.04.1 LTS, memtest86+
uuid		fa407b97-1791-4e07-936f-d2c3fe209e39
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda4/boot/grub/grub.cfg: ===========================

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
set root='(hd0,4)'
search --no-floppy --fs-uuid --set fa407b97-1791-4e07-936f-d2c3fe209e39
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
set root='(hd0,4)'
search --no-floppy --fs-uuid --set fa407b97-1791-4e07-936f-d2c3fe209e39
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
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set fa407b97-1791-4e07-936f-d2c3fe209e39
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=fa407b97-1791-4e07-936f-d2c3fe209e39 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set fa407b97-1791-4e07-936f-d2c3fe209e39
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=fa407b97-1791-4e07-936f-d2c3fe209e39 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set fa407b97-1791-4e07-936f-d2c3fe209e39
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=fa407b97-1791-4e07-936f-d2c3fe209e39 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set fa407b97-1791-4e07-936f-d2c3fe209e39
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=fa407b97-1791-4e07-936f-d2c3fe209e39 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set fa407b97-1791-4e07-936f-d2c3fe209e39
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set fa407b97-1791-4e07-936f-d2c3fe209e39
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 287e459b7e4562a4
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=fa407b97-1791-4e07-936f-d2c3fe209e39 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=60e68aa2-9b42-4465-8978-b2bf8e71b35a none            swap    sw              0       0

=================== sda4: Location of files loaded by Grub: ===================


  23.0GB: boot/grub/grub.cfg
  23.0GB: boot/grub/menu.lst
  23.0GB: boot/grub/stage2
  23.0GB: boot/initrd.img-2.6.32-21-generic
  23.0GB: boot/initrd.img-2.6.32-24-generic
  23.0GB: boot/initrd.img-2.6.32-25-generic
  23.0GB: boot/vmlinuz-2.6.32-21-generic
  23.0GB: boot/vmlinuz-2.6.32-24-generic
  23.0GB: boot/vmlinuz-2.6.32-25-generic
  23.0GB: initrd.img
  23.0GB: initrd.img.old
  23.0GB: vmlinuz
  23.0GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  fd fd fd fd fd fd fd fd  fd fd fd fd fd fd fd fd  |................|
*
000001b0  fd fd fd fd fd fd fd fd  fd fd fd fd fd fd 00 fe  |................|
000001c0  ff ff 07 fe ff ff 02 00  00 00 7c fa 15 34 00 fe  |..........|..4..|
000001d0  ff ff 05 fe ff ff 7e fa  15 34 85 fd 4f 00 00 00  |......~..4..O...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by da burger on 2010-10-04
Okay a few things:

1) First things first, in future post command output in [CODE] tags (press the # button at the top of the reply box). It's not too much of a problem but it does make the stuff a little easier to use.

2) Do you know why you have GRUB legacy installed?

3) As a temporary solution try selecting the "chainload GRUB2" then an option to boot windows should appear. You may have to press escape to get this menu to appear. If you could, please post back to tell us if this works as it affects how I'd like to continue

4) I think the solution will be to install GRUB2 to the MBR of the disk and just getting rid of GRUB legacy. I'll tell you how to do that after you check out the thing I mentioned in point 3.

Hope we'll be able to fix this problem :)
Angus

---

### Post by oldfred on 2010-10-04
Old grub required the escape key to get the menu when only one system was installed or found. Grub legacy also was not good at finding win7 and we usually had to manually insert a boot stanza for it. Much better to install grub2 since you seem to have parts already. 

Follow da burger's test of booting thru grub legacy to grub2 to insure it works.

If you want to read ahead:

 HOWTO: Purge and Reinstall Grub 2 from the Live CD - drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by drs305 on 2010-10-04
> **da burger said:**
> 

4) I think the solution will be to install GRUB2 to the MBR of the disk and just getting rid of GRUB legacy.
Angus

+1

If you want to purge Grub/Grub2 and reinstall Grub2 see the G2-Chroot link in my signature line. It's pretty straightforward and should solve your problem.

---

### Post by DavidVader on 2010-10-04
Problem Solved. I logged into my Ubuntu and just installed grub2 from the terminal. Thanks to everyone, really appreciate it!

---

### Post by amjjawad on 2010-10-04
> **DavidVader said:**
> Problem Solved. I logged into my Ubuntu and just installed grub2 from the terminal. Thanks to everyone, really appreciate it!

GRUB2 is the magic word :D

Don't forget to mark this thread as SOLVED ;)

---

