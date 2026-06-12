---
title: "Grub problems with triple boot - no vista (windows 7) anymore"
date: 2009-10-15
forum: New to Ubuntu
---

### Post by dan1973 on 2009-10-15
Hello, 

Please help, in a bit of a state, 

Had a nice triple boot system going on ubuntu 9.04, ubuntu 9,10 (trying out) and Windows 7 - for the rest of the family.

The usual problem of playing around and trying to tweak things just a little bit has got me into bother and i need help quickly before the wife finds out!

She was complaining about how the grub loader selects Ubuntu as default and how she is always missing the 'selection time'

'No problem' i say and change the default in the menu list.
While i was there, I chopped and pasted things around to alter the display order, saved and rebooted.

Now, both Ubuntus boot but windows 7 under the vista loader gives an 'Error 11: Unrecognized device string'

I can't seem to find out what's wrong. 

Please see this menu list
[HTML]
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
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# kopt=root=UUID=778a8cf3-6bfa-4377-947e-a0a8c827d978 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=778a8cf3-6bfa-4377-947e-a0a8c827d978

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


### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Operating systems:
root





# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista (loader)
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 9.04, kernel 2.6.28-15-generic (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=d66f9301-0f58-4256-936c-df607a517e67 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=d66f9301-0f58-4256-936c-df607a517e67 ro single 
initrd		/boot/initrd.img-2.6.28-15-generic
savedefault
boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 9.04, memtest86+ (on /dev/sda3)
root		(hd0,2)
kernel		/boot/memtest86+.bin  
savedefault
boot

#This is my testing area
# Think this is on /dev/sda6
title		Ubuntu karmic (development branch), kernel 2.6.31-14-generic
uuid		778a8cf3-6bfa-4377-947e-a0a8c827d978
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=778a8cf3-6bfa-4377-947e-a0a8c827d978 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu karmic (development branch), kernel 2.6.31-14-generic (recovery mode)
uuid		778a8cf3-6bfa-4377-947e-a0a8c827d978
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=778a8cf3-6bfa-4377-947e-a0a8c827d978 ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu karmic (development branch), memtest86+
uuid		778a8cf3-6bfa-4377-947e-a0a8c827d978
kernel		/boot/memtest86+.bin
quiet
[/HTML]

thought this may also be helpful:

[HTML]dan@dan-laptop:~$ sudo fdisk -l
[sudo] password for dan: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x34fe34fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         638     5124703+  12  Compaq diagnostics
/dev/sda2             639        7583    55785712+   7  HPFS/NTFS
/dev/sda3            7584       12786    41793097+  83  Linux
/dev/sda4           12787       14593    14514727+   5  Extended
/dev/sda5           14072       14593     4192933+  82  Linux swap / Solaris
/dev/sda6   *       12787       14010     9831717   83  Linux
/dev/sda7           14011       14071      489951   82  Linux swap / Solaris
[/HTML]

Please could someone help me get the dreaded windows back before it is missed! - not by me.

---

### Post by LewRockwell on 2009-10-15
does your grub menu show more than one instance of windows?

(looks like it should given your menu.lst file content)

you're probably attempting to boot whichever one doesn't work anymore

you could always resort to your back-up copy of your menu.lst file from before you made your changes

.

---

### Post by dan1973 on 2009-10-15
Hi, the other Windows partition is an enclosed Acer partition from the original windows XP which was on the system.

It has always been sitting there without doing any harm.

Where do I find my backup list - sounds like a good idea at the moment!

---

### Post by PrePenguin on 2009-10-15
> **dan1973 said:**
> Hi, the other Windows partition is an enclosed Acer partition from the original windows XP which was on the system.
 
It has always been sitting there without doing any harm.
 
Where do I find my backup list - sounds like a good idea at the moment!
 
 
 
Yep thats your recovery partition however if you burn a recovery Disk you can delete that hidden partition or just leave it there choice is yours.

---

### Post by dan1973 on 2009-10-15
Don't mind it sitting there at the moment - may try to move it at a later point - once i manage to get windows 7 back!

---

### Post by jmundinger on 2009-10-15
I'm a noobie in this Linux stuff, too.  But, my initial take on your boot menu is that grub is looking for windows xp and windows vista.  If I understand correctly, you took both of those off in favor of running windows 7.  What would happen if you edited "windows vista" to read "windows 7"?

---

### Post by louieb on 2009-10-15
Does it boot the 9.04 or 9.10? Are your sure where your Vista boot file are?
Please follow the [Boot Info Script How to]("http://ubuntuforums.org/showthread.php?p=8104352") and put the results.txt in your next post. If all you did was mess around with /boot/grub/menu.lst it should be easy enought to get straighten out.

BTW: Starting duplicate threads for the same problem will probably confuse you and those trying to help. It is discouraged.

---

### Post by dan1973 on 2009-10-15
Not sure, my windows 7 installation has always booted up via the 'vista' heading in grub.

---

### Post by dan1973 on 2009-10-15
Here is the output as requested - nifty little program that.
[HTML]============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTLDR /NTDETECT.COM /ntdetect.com

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu karmic (development 
                       branch)
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x34fe34fd

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    10,249,469    10,249,407  12 Compaq diagnostics
/dev/sda2          10,249,470   121,820,894   111,571,425   7 HPFS/NTFS
/dev/sda3         121,820,895   205,407,089    83,586,195  83 Linux
/dev/sda4         205,407,090   234,436,544    29,029,455   5 Extended
/dev/sda5         226,050,678   234,436,544     8,385,867  82 Linux swap / Solaris
/dev/sda6    *    205,407,216   225,070,649    19,663,434  83 Linux
/dev/sda7         225,070,713   226,050,614       979,902  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="PQSERVICE" UUID="16D9-B5D2" TYPE="vfat" 
/dev/sda2: UUID="9A4CE1F54CE1CC57" TYPE="ntfs" 
/dev/sda3: UUID="d66f9301-0f58-4256-936c-df607a517e67" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="eb3cd45e-b9be-49f7-8c10-c22e6d38d764" TYPE="swap" 
/dev/sda6: UUID="778a8cf3-6bfa-4377-947e-a0a8c827d978" TYPE="ext3" 
/dev/sda7: TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/dan/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dan)


=========================== sda3/boot/grub/menu.lst: ===========================

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
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# kopt=root=UUID=d66f9301-0f58-4256-936c-df607a517e67 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d66f9301-0f58-4256-936c-df607a517e67

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

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		d66f9301-0f58-4256-936c-df607a517e67
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=d66f9301-0f58-4256-936c-df607a517e67 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		d66f9301-0f58-4256-936c-df607a517e67
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=d66f9301-0f58-4256-936c-df607a517e67 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		d66f9301-0f58-4256-936c-df607a517e67
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=d66f9301-0f58-4256-936c-df607a517e67 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		d66f9301-0f58-4256-936c-df607a517e67
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=d66f9301-0f58-4256-936c-df607a517e67 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		d66f9301-0f58-4256-936c-df607a517e67
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista (loader)
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=d66f9301-0f58-4256-936c-df607a517e67 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=eb3cd45e-b9be-49f7-8c10-c22e6d38d764 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


  62.3GB: boot/grub/menu.lst
  62.3GB: boot/grub/stage2
  62.3GB: boot/initrd.img-2.6.28-11-generic
  62.3GB: boot/initrd.img-2.6.28-15-generic
  62.3GB: boot/vmlinuz-2.6.28-11-generic
  62.3GB: boot/vmlinuz-2.6.28-15-generic
  62.3GB: initrd.img
  62.3GB: initrd.img.old
  62.3GB: vmlinuz
  62.3GB: vmlinuz.old

=========================== sda6/boot/grub/menu.lst: ===========================

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
default		3

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# kopt=root=UUID=778a8cf3-6bfa-4377-947e-a0a8c827d978 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=778a8cf3-6bfa-4377-947e-a0a8c827d978

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
#This is my testing area
# Think this is on /dev/sda6
title		Ubuntu karmic (development branch), kernel 2.6.31-14-generic
uuid		778a8cf3-6bfa-4377-947e-a0a8c827d978
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=778a8cf3-6bfa-4377-947e-a0a8c827d978 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu karmic (development branch), kernel 2.6.31-14-generic (recovery mode)
uuid		778a8cf3-6bfa-4377-947e-a0a8c827d978
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=778a8cf3-6bfa-4377-947e-a0a8c827d978 ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu karmic (development branch), memtest86+
uuid		778a8cf3-6bfa-4377-947e-a0a8c827d978
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista (loader)
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 9.04, kernel 2.6.28-15-generic (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=d66f9301-0f58-4256-936c-df607a517e67 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=d66f9301-0f58-4256-936c-df607a517e67 ro single 
initrd		/boot/initrd.img-2.6.28-15-generic
savedefault
boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 9.04, memtest86+ (on /dev/sda3)
root		(hd0,2)
kernel		/boot/memtest86+.bin  
savedefault
boot





=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=778a8cf3-6bfa-4377-947e-a0a8c827d978 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=eb3cd45e-b9be-49f7-8c10-c22e6d38d764 none            swap    sw              0       0
/dev/sda7       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 105.1GB: boot/grub/menu.lst
 105.1GB: boot/grub/stage2
 105.1GB: boot/initrd.img-2.6.26-2-amd64
 105.1GB: boot/initrd.img-2.6.26-2-amd64.bak
 105.1GB: boot/initrd.img-2.6.28-11-generic
 105.1GB: boot/initrd.img-2.6.31-14-generic
 105.1GB: boot/vmlinuz-2.6.26-2-amd64
 105.1GB: boot/vmlinuz-2.6.28-11-generic
 105.1GB: boot/vmlinuz-2.6.31-14-generic
 105.1GB: initrd.img
 105.1GB: initrd.img.old
 105.1GB: vmlinuz
 105.1GB: vmlinuz.old[/HTML]

Sorry about the multiple threads, it was an accident.

Yes, all i did was remove some grub entries that i didn't need anymore - older linux kernels and then re-arranged the order.

---

### Post by dan1973 on 2009-10-15
Thanks all for your input.

Have discovered where the problem was. Found out that the 'divider' in the boot list counts as an entry when counting which entry is to be booted as default.

Simple but annoying. Of course it was giving an unrecognized device string message if it was trying to boot up a divider!

Sorry for my stupidity,

---

### Post by louieb on 2009-10-15
lol just saw our last post - still may want to do something about the boot flag - but guess now it really does not matter. Lou

Don't see any show stoppers in your menu.list. however there is one thing **odd  2 partitions with the boot flag on.** There should be at most 1.  Now Linux does not care if the boot flag is set or not. Windows does care it wants the boot flag on the partition with its boot files.  Heard that was changed with Win 7 but...

What partition program(s) are  using?   I know Gparted will only allow the boot flag to be set on one partition only. 

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x34fe34fd

Partition [COLOR=Red] Boot[/COLOR]         Start           End          Size  Id System

/dev/sda1    *             63    10,249,469    10,249,407  12 Compaq diagnostics
/dev/sda2          10,249,470   121,820,894   111,571,425   7 HPFS/NTFS
/dev/sda3         121,820,895   205,407,089    83,586,195  83 Linux
/dev/sda4         205,407,090   234,436,544    29,029,455   5 Extended
/dev/sda5         226,050,678   234,436,544     8,385,867  82 Linux swap / Solaris
/dev/sda6    *    205,407,216   225,070,649    19,663,434  83 Linux
/dev/sda7         225,070,713   226,050,614       979,902  82 Linux swap / Solaris
```What partition program(s) are  using?   I know Gparted will only allow the boot flag to be set on one partition only. Anyway see what you can do to get the boot flag off sda6 and sda1 and put it on sda2. Then your entry that looks like this should work. 
```
title        Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1
```

---

### Post by oldfred on 2009-10-15
Did your boot into windows give you choices? Win7 likes to combine its boot with all the other versions of windows on the system. Then if you delete the old version of windows,  Win7 will then not boot.

I do not see anything preventing booting. You do have the boot flag on sda1 which is your recovery partition, but the makeactive command should reset that when you try to boot windows on sda2.

Grub is booting into your Karmic version. Your last swap on sda7 is not used and does not have a UUID. Both fstabs show swap mounted sda5.

With WinXP the script prints out boot.ini, I do not see one, but I do not know if Win7 also eliminated that.

Someone else may see more.

---

### Post by oldfred on 2009-10-15
Everyone always seems to put the windows stanza at the bottom below the end of the automagic area. But you can also put it above the automagic area and it will be first. This is in the middle somewhere in menu.lst

# Put static boot stanzas [COLOR=Red]before and/or after[/COLOR] AUTOMAGIC KERNEL LIST
[COLOR=DarkRed]Put windows stanza here[/COLOR]
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

---

### Post by dan1973 on 2009-10-16
> **oldfred said:**
> Did your boot into windows give you choices? Win7 likes to combine its boot with all the other versions of windows on the system. Then if you delete the old version of windows,  Win7 will then not boot.

I do not see anything preventing booting. You do have the boot flag on sda1 which is your recovery partition, but the makeactive command should reset that when you try to boot windows on sda2.

[COLOR="Red"]Grub is booting into your Karmic version. Your last swap on sda7 is not used and does not have a UUID. Both fstabs show swap mounted sda5[/COLOR].

With WinXP the script prints out boot.ini, I do not see one, but I do not know if Win7 also eliminated that.

Someone else may see more.

So does this mean that both my Ubuntu versions only need and use the one swap partition?

What should i do with sda7?

---

### Post by dan1973 on 2009-10-16
> **oldfred said:**
> Everyone always seems to put the windows stanza at the bottom below the end of the automagic area. But you can also put it above the automagic area and it will be first. This is in the middle somewhere in menu.lst


Have now done it as you say. Windows now at the top - good for the wife and kids (both can be easily confused) - as can I when it comes to the machine, but i am trying in earnest.

The folowing seems to be working for me now.
[HTML]
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
timeout		5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# kopt=root=UUID=778a8cf3-6bfa-4377-947e-a0a8c827d978 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=778a8cf3-6bfa-4377-947e-a0a8c827d978

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
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows 7 (loader)
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root



# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 9.04, kernel 2.6.28-15-generic (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=d66f9301-0f58-4256-936c-df607a517e67 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=d66f9301-0f58-4256-936c-df607a517e67 ro single 
initrd		/boot/initrd.img-2.6.28-15-generic
savedefault
boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 9.04, memtest86+ (on /dev/sda3)
root		(hd0,2)
kernel		/boot/memtest86+.bin  
savedefault
boot

#This is my testing area
# Think this is on /dev/sda6
title		Ubuntu karmic (development branch), kernel 2.6.31-14-generic
uuid		778a8cf3-6bfa-4377-947e-a0a8c827d978
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=778a8cf3-6bfa-4377-947e-a0a8c827d978 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu karmic (development branch), kernel 2.6.31-14-generic (recovery mode)
uuid		778a8cf3-6bfa-4377-947e-a0a8c827d978
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=778a8cf3-6bfa-4377-947e-a0a8c827d978 ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu karmic (development branch), memtest86+
uuid		778a8cf3-6bfa-4377-947e-a0a8c827d978
kernel		/boot/memtest86+.bin
quiet

[/HTML]

---

### Post by oldfred on 2009-10-16
While your menu.lst may work now, it does not follow the standard format and your windows7 entry will get overwritten the next time a kernel is updated and everything in the automagic area is updated. Also you moved the Ubuntu outside the automagic area, after a kernal update you will have duplicate entries for Ubuntu some in automagic and some outside. When it says update-grub script it means it will be run with any kernel change, addition, or deletion, so some updates will cause your windows stanza to be deleted.

# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian [COLOR=DarkRed]update-grub script[/COLOR] except for the default options below
[COLOR=Red]
your current windows stanza will be deleted on kernel update[/COLOR]
### END DEBIAN AUTOMAGIC KERNELS LIST
[COLOR=Red]
Your current ubuntu stanzas[/COLOR] will not be updated and new ones will be added above inside teh automagic area.

My suggestion to fix this is make a backup of menu.lst. Run the script to total write a new menu.lst and copy the windows entry back from the backup to above the automagic area.

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
sudo update-grub
sudo gedit /boot/grub/menu.lst

---

### Post by dan1973 on 2009-10-17
> **oldfred said:**
> While your menu.lst may work now, it does not follow the standard format and your windows7 entry will get overwritten the next time a kernel is updated and everything in the automagic area is updated. Also you moved the Ubuntu outside the automagic area, after a kernal update you will have duplicate entries for Ubuntu some in automagic and some outside. When it says update-grub script it means it will be run with any kernel change, addition, or deletion, so some updates will cause your windows stanza to be deleted.

# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian [COLOR=DarkRed]update-grub script[/COLOR] except for the default options below
[COLOR=Red]
your current windows stanza will be deleted on kernel update[/COLOR]
### END DEBIAN AUTOMAGIC KERNELS LIST
[COLOR=Red]
Your current ubuntu stanzas[/COLOR] will not be updated and new ones will be added above inside teh automagic area.

My suggestion to fix this is make a backup of menu.lst. Run the script to total write a new menu.lst and copy the windows entry back from the backup to above the automagic area.

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
sudo update-grub
sudo gedit /boot/grub/menu.lst

OK, so this is sounding a little serious now - like something which should be fixed once and for all.

Questions before proceeding:-

1) How do I know which area is this 'automagic area'?

2) The So called Windows XP boot partition is a 'hidden' backup feature from this PC - years old and useless to me. The only reason it's still there is because i forgot to format the whole hard disk before placing my OSs. Is it best to format this partition? Then resize my main jaunty partition? 

3) Is the Above risky?

4) Do I need 2 swap partitions, one for each Ubuntu, or can I delete one as suggested earlier in the thread?

---

### Post by oldfred on 2009-10-17
The automagic area is everything between these lines:
### BEGIN AUTOMAGIC KERNELS LIST
[COLOR=DarkRed]Everything here is rewritten.[/COLOR]
### END DEBIAN AUTOMAGIC KERNELS LIST

There are a lot of comments and options at the top of menu.lst then the start of automagic with what may look like more comments but are settings used by the grub-update to include when it is rewriting. Most people manually add additional stanzas at the bottom below the bottom automagic line.

If you remove the hidden XP partition you may renumber partitons. Or it may just leave the other partitions with current numbers. I am not sure and I think it depends on how you do it. For now I would not change it.

You only need one swap partition, although most linux will use both if necessary. sda7 is not mounted per your fstab so you should be able to delete without any issue.

Backup your menu.lst and run the grub-update to create the new menu.lst, then you can easily edit the corrected menu.lst.

---

### Post by dan1973 on 2009-10-17
O.K have done as suggested. Hopefully the following should be safe for now.

It works well, booting into Windows by default and Ubuntu by choice - rather like many computer users.

Must say a big thank you for all the patience and help.:)  

I will remove sda7 at some later point. The XP partition can stay for now, especially if it may cause troubles - save it for later.
[HTML]
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
default		7

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# kopt=root=UUID=778a8cf3-6bfa-4377-947e-a0a8c827d978 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=778a8cf3-6bfa-4377-947e-a0a8c827d978

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

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 9.04, kernel 2.6.28-15-generic (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=d66f9301-0f58-4256-936c-df607a517e67 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=d66f9301-0f58-4256-936c-df607a517e67 ro single 
initrd		/boot/initrd.img-2.6.28-15-generic
savedefault
boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 9.04, memtest86+ (on /dev/sda3)
root		(hd0,2)
kernel		/boot/memtest86+.bin  
savedefault
boot

#This is my testing area
# Think this is on /dev/sda6
title		Ubuntu karmic (development branch), kernel 2.6.31-14-generic
uuid		778a8cf3-6bfa-4377-947e-a0a8c827d978
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=778a8cf3-6bfa-4377-947e-a0a8c827d978 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu karmic (development branch), kernel 2.6.31-14-generic (recovery mode)
uuid		778a8cf3-6bfa-4377-947e-a0a8c827d978
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=778a8cf3-6bfa-4377-947e-a0a8c827d978 ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu karmic (development branch), memtest86+
uuid		778a8cf3-6bfa-4377-947e-a0a8c827d978
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows 7 (loader)
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1[/HTML]

---

### Post by oldfred on 2009-10-17
Since you are using the count to control which stanza to boot you need to also be aware that a kernel update adds entries and changes the count of the windows below. So each kernal update will require a change to the count

If you change the all entry to a number it will only show that many. We recommend 2 since sometimes a new kerel does not work and you want to be able to select the old one. The line with the single # is what is used for updating. So with all it will show all your kernels and change the line for windows each time.

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
[COLOR=DarkRed]# howmany=all[/COLOR]

---

### Post by dan1973 on 2009-10-18
Is this now correct, is it the case that I don't need to remove the hash sign?

Do you have any more grub suggestions - am finding this most educational!
[HTML]# menu.lst - See: grub(8), info grub, update-grub(8)
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
default		7

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# kopt=root=UUID=778a8cf3-6bfa-4377-947e-a0a8c827d978 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=778a8cf3-6bfa-4377-947e-a0a8c827d978

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
# howmany=2

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

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 9.04, kernel 2.6.28-15-generic (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=d66f9301-0f58-4256-936c-df607a517e67 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=d66f9301-0f58-4256-936c-df607a517e67 ro single 
initrd		/boot/initrd.img-2.6.28-15-generic
savedefault
boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 9.04, memtest86+ (on /dev/sda3)
root		(hd0,2)
kernel		/boot/memtest86+.bin  
savedefault
boot

#This is my testing area
# Think this is on /dev/sda6
title		Ubuntu karmic (development branch), kernel 2.6.31-14-generic
uuid		778a8cf3-6bfa-4377-947e-a0a8c827d978
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=778a8cf3-6bfa-4377-947e-a0a8c827d978 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu karmic (development branch), kernel 2.6.31-14-generic (recovery mode)
uuid		778a8cf3-6bfa-4377-947e-a0a8c827d978
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=778a8cf3-6bfa-4377-947e-a0a8c827d978 ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu karmic (development branch), memtest86+
uuid		778a8cf3-6bfa-4377-947e-a0a8c827d978
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows 7 (loader)
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1[/HTML]

---

### Post by oldfred on 2009-10-18
The only issues I see are your Karmic stanzas are inside the automagic and will be deleted on a kernel update. With 2 kernel shown fri future updates and you only have 1 now, your entry to default to windows will have to change. The single # in the automagic area is an entry it reads for settings of the automagic update. Normally your are correct that # is comments. Just make sure you have a backup, so you can copy entries from the backup when the next kernel update occurs. It will normally make a backup anyway but I like to make sure.

Glad I can help, part of the fun of Ubuntu is learning all the ways things work.

The only problem with learning how menu.lst works is that the default for new installs of Karmic is grub2 which is a lot different but if you understand some of the troubles you are having grub.cfg is automatically created as a separate file kinda like the automagic area. All the comments and anything you want to add are in totally separate files which are automatically merged into grub.cfg and grub2 is much better at finding other installed systems.

---

### Post by dan1973 on 2009-10-19
Greetings from Finland!

A few more questions, 

Do i understand your last post correctly, I should have only my 9.04 within the automagic section and move Karmic out?

That when I do this, I will need to change my default boot-up number to whichever windows is?

I don't quite understand the following:> [COLOR="Red"]With 2 kernel shown fri future updates and you only have 1 now[/COLOR]

I still have 2 different kernels on the machine? Do you mean that the '2' will allow 2 different kernels per Ubuntu version?

If I leave this set as 2, when the kernel is updated does it mean that the old version will show on the boot selection, whereas if I change it to '1' only the most recent is visible (with recovery mode)?

Many thanks for your continued patience,

---

### Post by hopelessone on 2009-10-19
Hi,

*future note* install VirtualBox for all OS's other than Ubuntu..

---

### Post by oldfred on 2009-10-19
As long as you keep windows at the bottom the count will not change. I think it counts title entries as I have seen where the count was to the separater entry with the blank root and of course it does not boot and was difficult to figure out why it would not boot as every entry looked good. This was why I suggested having the windows entry above the automagic area so  its count will always be 1 and it is on top. 

Kernal update will add two new lines - standard and recovery. Since you currently only have one kernel your entry will change when the first one is updated. After that it will never change the count. You do want to allow 2 kernels just in case the new one does not work on your configuration. Of course if you do not remove the kernels you can go back with the liveCD and edit menu again, but that is a hassle.

Just move this above your line that says testing area. It should not change any counts:
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root

---

### Post by dan1973 on 2009-10-19
Think I am with it now, please see following:

once again, many thanks.
[HTML]# menu.lst - See: grub(8), info grub, update-grub(8)
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
default		7

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# kopt=root=UUID=778a8cf3-6bfa-4377-947e-a0a8c827d978 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=778a8cf3-6bfa-4377-947e-a0a8c827d978

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
# howmany=2

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

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 9.04, kernel 2.6.28-15-generic (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=d66f9301-0f58-4256-936c-df607a517e67 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
savedefault
boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=d66f9301-0f58-4256-936c-df607a517e67 ro single 
initrd		/boot/initrd.img-2.6.28-15-generic
savedefault
boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 9.04, memtest86+ (on /dev/sda3)
root		(hd0,2)
kernel		/boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

#This is my testing area
# Think this is on /dev/sda6
title		Ubuntu karmic (development branch), kernel 2.6.31-14-generic
uuid		778a8cf3-6bfa-4377-947e-a0a8c827d978
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=778a8cf3-6bfa-4377-947e-a0a8c827d978 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu karmic (development branch), kernel 2.6.31-14-generic (recovery mode)
uuid		778a8cf3-6bfa-4377-947e-a0a8c827d978
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=778a8cf3-6bfa-4377-947e-a0a8c827d978 ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu karmic (development branch), memtest86+
uuid		778a8cf3-6bfa-4377-947e-a0a8c827d978
kernel		/boot/memtest86+.bin
quiet

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows 7 (loader)
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

[/HTML]

---

### Post by oldfred on 2009-10-19
Looks good to me, real question is does it work the way you want? Just one more time, after the first kernel update you will have to make the change to the number for windows to be the default. After that no other changes should be required.

Now that you are experienced with editing menu.lst, there is a gui start up manager that you can download that makes some of the minor edits to menu.lst.

---

