---
title: "Can't boot Vista from Grub"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by shadowroses on 2009-01-17
Hi all.
I am new to Ubuntu and can't seem to get Vista to boot from Grub, despite many hours of research.  Any help would be much appreciated.

This is my output from fdisk -l...
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37763   303331266    7  HPFS/NTFS
/dev/sda3           37764       38913     9237375    7  HPFS/NTFS
```

And this is my menu.lst.
```
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
# kopt=root=UUID=06023FE6023FD8FF loop=/ubuntu/disks/root.disk ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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

title		Ubuntu 8.04.1, kernel 2.6.24-23-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=06023FE6023FD8FF loop=/ubuntu/disks/root.disk ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.1, kernel 2.6.24-23-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=06023FE6023FD8FF loop=/ubuntu/disks/root.disk ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=06023FE6023FD8FF loop=/ubuntu/disks/root.disk ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=06023FE6023FD8FF loop=/ubuntu/disks/root.disk ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=06023FE6023FD8FF loop=/ubuntu/disks/root.disk ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=06023FE6023FD8FF loop=/ubuntu/disks/root.disk ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=06023FE6023FD8FF loop=/ubuntu/disks/root.disk ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=06023FE6023FD8FF loop=/ubuntu/disks/root.disk ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
chainloader	+1
```

Thanks in advance.

---

### Post by seagullplayer77 on 2009-01-17
For the sake of comparison, here's my menu.lst file

```
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
timeout		4

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
# kopt=root=UUID=d969d5a3-1d3b-4c67-b3db-f3aa077573bd ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title		Ubuntu 8.04.1, kernel 2.6.24-23-rt
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-23-rt root=UUID=d969d5a3-1d3b-4c67-b3db-f3aa077573bd ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-rt
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-23-rt (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-23-rt root=UUID=d969d5a3-1d3b-4c67-b3db-f3aa077573bd ro single
initrd		/boot/initrd.img-2.6.24-23-rt

title		Ubuntu 8.04.1, kernel 2.6.24-22-rt
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-22-rt root=UUID=d969d5a3-1d3b-4c67-b3db-f3aa077573bd ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-rt
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-rt (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-22-rt root=UUID=d969d5a3-1d3b-4c67-b3db-f3aa077573bd ro single
initrd		/boot/initrd.img-2.6.24-22-rt

title		Ubuntu 8.04.1, kernel 2.6.24-21-rt
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-21-rt root=UUID=d969d5a3-1d3b-4c67-b3db-f3aa077573bd ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-rt
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-rt (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-21-rt root=UUID=d969d5a3-1d3b-4c67-b3db-f3aa077573bd ro single
initrd		/boot/initrd.img-2.6.24-21-rt

title		Ubuntu 8.04.1, kernel 2.6.24-19-rt
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=d969d5a3-1d3b-4c67-b3db-f3aa077573bd ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-rt
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-rt (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=d969d5a3-1d3b-4c67-b3db-f3aa077573bd ro single
initrd		/boot/initrd.img-2.6.24-19-rt

title		Ubuntu 8.04.1, kernel 2.6.24-18-rt
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-18-rt root=UUID=d969d5a3-1d3b-4c67-b3db-f3aa077573bd ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-rt
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-18-rt (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-18-rt root=UUID=d969d5a3-1d3b-4c67-b3db-f3aa077573bd ro single
initrd		/boot/initrd.img-2.6.24-18-rt

title		Ubuntu 8.04.1, kernel 2.6.24-17-rt
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-17-rt root=UUID=d969d5a3-1d3b-4c67-b3db-f3aa077573bd ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-rt
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-17-rt (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-17-rt root=UUID=d969d5a3-1d3b-4c67-b3db-f3aa077573bd ro single
initrd		/boot/initrd.img-2.6.24-17-rt

title		Ubuntu 8.04.1, kernel 2.6.24-16-rt
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-rt root=UUID=d969d5a3-1d3b-4c67-b3db-f3aa077573bd ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-rt
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-rt (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-rt root=UUID=d969d5a3-1d3b-4c67-b3db-f3aa077573bd ro single
initrd		/boot/initrd.img-2.6.24-16-rt

title		Ubuntu 8.04.1, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

Just looking at yours and mine, it seems that the only significant difference is that I have "makeactive" in the entries for my Vista OS, while you don't. You could try adding that one line of code and that might help. I know that I can boot Vista from Grub on my machine without a hitch.

---

### Post by shadowroses on 2009-01-17
Thanks, seagullplayer77, but I've tried that... It just loops back to Grub.  :/ I appreciate the suggestion though.

---

### Post by Hendrixski on 2009-01-17
:-(  It seems that Vista causes nothing but problems.

I installed Ubuntu for a friend with Vista and Vista was able to load... after it did like tons of esoteric crap, like checking drives and scanning things and...  I tell you what, it's black magic man.

We use just Ubuntu in my office, no dual booting.  So that's what I recommend to everybody.

---

### Post by northern lights on 2009-01-17
What error do you get when selecting the first Vista entry from GRUB?

If Vista is installed on sda1 (as it both appears to be and should),```
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
chainloader	+1
```
the above should work.

---

### Post by caljohnsmith on 2009-01-17
It sounds like you may of accidentally installed Grub to the boot sector of your Vista partition at some point if booting Vista loops you back to Grub. In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your booting problem might be.

---

### Post by shadowroses on 2009-01-17
Northern lights, that is exactly what the entry is, and it loops back... It displays something first, but it doesn't stay up long enough for me to read it.

Caljohnsmith, I tried to do that and got the result "bash: /home/kim/Desktop/boot_info_script*.sh: No such file or directory" in the terminal.

---

### Post by northern lights on 2009-01-17
> **shadowroses said:**
> Northern lights, that is exactly what the entry is
I know. I was simply mentioning that it should work. Which leads me to believe that this is not a GRUB issue, but rather one of the Vista loader.

> **shadowroses said:**
> Caljohnsmith, I tried to do that and got the result "bash: /home/kim/Desktop/boot_info_script*.sh: No such file or directory" in the terminal.
You need to download the script first (see link above). If you downloaded it, but not to your desktop, alter the location in the execution command or move it there.

---

### Post by caljohnsmith on 2009-01-17
OK, I'm guessing the problem is that Grub is installed to your Vista boot sector, so how about instead booting your Vista Install CD, go to the command line and do:
```
bootrec /fixboot
```
If you don't have a Vista Install CD, you can instead download a Vista Recovery CD from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"). Then reboot, try to boot Vista from Grub again using the (hd0,0) entry you have been using, and let me know exactly what happens. If it doesn't work, we'll need to see the output of the Boot Info Script in order to help you further.

---

### Post by shadowroses on 2009-01-17
Ah, okay, thank you for clarifying that, northern lights.

Caljohnsmith, I had actually tried doing that at an earlier time and nothing happened.
Here's the output of the Boot Info Script...
```
============================= Boot Info Summary: ==============================

 => Drive sdb does not have a valid partition table.
 => Drive sdc does not have a valid partition table.
 => Drive sdd does not have a valid partition table.
 => Drive sde does not have a valid partition table.
 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /ubuntu/disks/boot/grub/menu.lst /bootmgr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /Boot /ubuntu/disks 
                       /ubuntu/disks/boot/ /ubuntu/disks/boot/grub 
                       /ubuntu/disks/boot/grub

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   606662594   303331266    7  HPFS/NTFS
/dev/sda3       606662595   625137344     9237375    7  HPFS/NTFS

sfdisk -V /dev/sda:

partition 3: start: (c,h,s) expected (1023,254,63) found (1022,254,63)
partition 3: end: (c,h,s) expected (1023,254,63) found (1022,254,63)
/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

sfdisk -V /dev/sdb:

/dev/sdb: No medium found

sfdisk: cannot open /dev/sdb for reading

Drive sdc: _____________________________________________________________________

fdisk -lu /dev/sdc:

sfdisk -V /dev/sdc:

/dev/sdc: No medium found

sfdisk: cannot open /dev/sdc for reading

Drive sdd: _____________________________________________________________________

fdisk -lu /dev/sdd:

sfdisk -V /dev/sdd:

/dev/sdd: No medium found

sfdisk: cannot open /dev/sdd for reading

Drive sde: _____________________________________________________________________

fdisk -lu /dev/sde:

sfdisk -V /dev/sde:

/dev/sde: No medium found

sfdisk: cannot open /dev/sde for reading

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="06023FE6023FD8FF" LABEL="HP" TYPE="ntfs" 
/dev/sda3: UUID="2C88743C8874071C" LABEL="FACTORY_IMAGE" TYPE="ntfs" 
/dev/loop0: UUID="baf01b3e-2ccd-458c-baab-61f534bcd1a5" TYPE="ext3" 

=============================== "mount" output: ===============================

/host/ubuntu/disks/root.disk on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw)
/host/ubuntu/disks/boot on /boot type none (rw,bind)
/dev/sda1 on /media/HP type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/sandy/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=sandy)
gvfs-fuse-daemon on /home/kim/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=kim)

==================== sda1/ubuntu/disks/boot/grub/menu.lst: ====================

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
# kopt=root=UUID=06023FE6023FD8FF loop=/ubuntu/disks/root.disk ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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

title		Ubuntu 8.04.1, kernel 2.6.24-23-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=06023FE6023FD8FF loop=/ubuntu/disks/root.disk ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.1, kernel 2.6.24-23-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=06023FE6023FD8FF loop=/ubuntu/disks/root.disk ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=06023FE6023FD8FF loop=/ubuntu/disks/root.disk ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=06023FE6023FD8FF loop=/ubuntu/disks/root.disk ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=06023FE6023FD8FF loop=/ubuntu/disks/root.disk ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=06023FE6023FD8FF loop=/ubuntu/disks/root.disk ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=06023FE6023FD8FF loop=/ubuntu/disks/root.disk ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=06023FE6023FD8FF loop=/ubuntu/disks/root.disk ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
chainloader	+1


================================== sda1/Boot: ==================================

total 748
drwxrwxrwx 1 root root   4096 2009-01-16 17:41 .
drwxrwxrwx 1 root root  12288 2009-01-16 17:52 ..
-rwxrwxrwx 1 root root  32768 2008-12-25 15:08 BCD
-rwxrwxrwx 1 root root 262144 2008-12-25 15:08 BCD.LOG
-rwxrwxrwx 2 root root      0 2007-09-15 12:30 BCD.LOG1
-rwxrwxrwx 2 root root      0 2007-09-15 12:30 BCD.LOG2
-rwxrwxrwx 1 root root  65536 2007-09-15 12:30 bootstat.dat
drwxrwxrwx 1 root root      0 2007-09-15 12:30 cs-CZ
drwxrwxrwx 1 root root      0 2007-09-15 12:30 da-DK
drwxrwxrwx 1 root root      0 2007-09-15 12:30 de-DE
drwxrwxrwx 1 root root      0 2007-09-15 12:30 el-GR
drwxrwxrwx 1 root root      0 2007-09-15 12:30 en-US
drwxrwxrwx 1 root root      0 2007-09-15 12:30 es-ES
drwxrwxrwx 1 root root      0 2007-09-15 12:30 fi-FI
drwxrwxrwx 1 root root      0 2007-09-15 12:30 Fonts
drwxrwxrwx 1 root root      0 2007-09-15 12:30 fr-FR
drwxrwxrwx 1 root root      0 2007-09-15 12:30 hu-HU
drwxrwxrwx 1 root root      0 2007-09-15 12:30 it-IT
drwxrwxrwx 1 root root      0 2007-09-15 12:30 ja-JP
drwxrwxrwx 1 root root      0 2007-09-15 12:30 ko-KR
-rwxrwxrwx 1 root root 386664 2006-11-02 04:51 memtest.exe
drwxrwxrwx 1 root root      0 2007-09-15 12:30 nb-NO
drwxrwxrwx 1 root root      0 2007-09-15 12:30 nl-NL
drwxrwxrwx 1 root root      0 2007-09-15 12:30 pl-PL
drwxrwxrwx 1 root root      0 2007-09-15 12:30 pt-BR
drwxrwxrwx 1 root root      0 2007-09-15 12:30 pt-PT
drwxrwxrwx 1 root root      0 2007-09-15 12:30 ru-RU
drwxrwxrwx 1 root root      0 2007-09-15 12:30 sv-SE
drwxrwxrwx 1 root root      0 2007-09-15 12:30 tr-TR
drwxrwxrwx 1 root root      0 2007-09-15 12:30 zh-CN
drwxrwxrwx 1 root root      0 2007-09-15 12:30 zh-HK
drwxrwxrwx 1 root root      0 2007-09-15 12:30 zh-TW

============================== sda1/ubuntu/disks: ==============================

total 14648448
drwxrwxrwx 1 root root           0 2008-07-28 22:21 .
drwxrwxrwx 1 root root        4096 2008-07-28 21:52 ..
drwxrwxrwx 1 root root        4096 2009-01-16 18:26 boot
-rwxrwxrwx 2 root root 14000000000 2009-01-17 16:17 root.disk
drwxrwxrwx 1 root root           0 2008-07-28 21:52 shared
-rwxrwxrwx 2 root root  1000000000 2008-07-28 18:27 swap.disk

=========================== sda1/ubuntu/disks/boot/: ===========================

total 76536
drwxrwxrwx 1 root root    4096 2009-01-16 18:26 .
drwxrwxrwx 1 root root       0 2008-07-28 22:21 ..
-rwxrwxrwx 1 root root  420224 2008-08-20 18:15 abi-2.6.24-19-generic
-rwxrwxrwx 1 root root  420395 2008-10-21 21:49 abi-2.6.24-21-generic
-rwxrwxrwx 1 root root  420395 2008-11-24 17:19 abi-2.6.24-22-generic
-rwxrwxrwx 1 root root  420395 2008-11-27 15:56 abi-2.6.24-23-generic
-rwxrwxrwx 1 root root   74164 2008-08-20 18:15 config-2.6.24-19-generic
-rwxrwxrwx 1 root root   74177 2008-10-21 21:49 config-2.6.24-21-generic
-rwxrwxrwx 1 root root   74177 2008-11-24 17:19 config-2.6.24-22-generic
-rwxrwxrwx 1 root root   74166 2008-11-27 15:56 config-2.6.24-23-generic
drwxrwxrwx 1 root root       0 2009-01-16 18:55 grub
-rwxrwxrwx 1 root root 8000129 2008-08-26 14:55 initrd.img-2.6.24-19-generic
-rwxrwxrwx 1 root root 8000193 2008-08-19 12:18 initrd.img-2.6.24-19-generic.bak
-rwxrwxrwx 1 root root 8000842 2008-11-10 15:44 initrd.img-2.6.24-21-generic
-rwxrwxrwx 1 root root 8000779 2008-10-28 15:34 initrd.img-2.6.24-21-generic.bak
-rwxrwxrwx 1 root root 7997072 2008-12-12 16:20 initrd.img-2.6.24-22-generic
-rwxrwxrwx 1 root root 7997390 2008-11-28 11:55 initrd.img-2.6.24-22-generic.bak
-rwxrwxrwx 1 root root 7998584 2009-01-16 13:54 initrd.img-2.6.24-23-generic
-rwxrwxrwx 1 root root 7998636 2009-01-12 16:24 initrd.img-2.6.24-23-generic.bak
-rwxrwxrwx 1 root root  103204 2007-09-28 07:03 memtest86+.bin
-rwxrwxrwx 1 root root 1152364 2008-08-20 18:15 System.map-2.6.24-19-generic
-rwxrwxrwx 1 root root 1153201 2008-10-21 21:49 System.map-2.6.24-21-generic
-rwxrwxrwx 1 root root 1153201 2008-11-24 17:19 System.map-2.6.24-22-generic
-rwxrwxrwx 1 root root 1153225 2008-11-27 15:56 System.map-2.6.24-23-generic
-rwxrwxrwx 1 root root 1903096 2008-08-20 18:15 vmlinuz-2.6.24-19-generic
-rwxrwxrwx 1 root root 1905688 2008-10-21 21:49 vmlinuz-2.6.24-21-generic
-rwxrwxrwx 1 root root 1905656 2008-11-24 17:19 vmlinuz-2.6.24-22-generic
-rwxrwxrwx 1 root root 1907096 2008-11-27 15:56 vmlinuz-2.6.24-23-generic

========================= sda1/ubuntu/disks/boot/grub: =========================

total 29
drwxrwxrwx 1 root root    0 2009-01-16 18:55 .
drwxrwxrwx 1 root root 4096 2009-01-16 18:26 ..
-rwxrwxrwx 1 root root  191 2008-07-28 14:32 default
-rwxrwxrwx 1 root root   45 2008-07-28 14:32 device.map
-rwxrwxrwx 1 root root 6180 2009-01-16 18:55 menu.lst
-rwxrwxrwx 1 root root 6188 2009-01-16 18:52 menu.lst~
-rwxrwxrwx 1 root root 6169 2009-01-12 16:24 menu.lst~~

========================= sda1/ubuntu/disks/boot/grub: =========================

total 29
drwxrwxrwx 1 root root    0 2009-01-16 18:55 .
drwxrwxrwx 1 root root 4096 2009-01-16 18:26 ..
-rwxrwxrwx 1 root root  191 2008-07-28 14:32 default
-rwxrwxrwx 1 root root   45 2008-07-28 14:32 device.map
-rwxrwxrwx 1 root root 6180 2009-01-16 18:55 menu.lst
-rwxrwxrwx 1 root root 6188 2009-01-16 18:52 menu.lst~
-rwxrwxrwx 1 root root 6169 2009-01-12 16:24 menu.lst~~

================================== sda3/boot: ==================================

total 3596
drwxrwxrwx 1 root root    4096 2007-09-15 19:59 .
drwxrwxrwx 1 root root    4096 2008-11-04 15:31 ..
-rwxrwxrwx 1 root root   28672 2007-09-15 19:59 bcd
-rwxrwxrwx 1 root root   21504 2007-09-15 19:59 bcd.LOG
-rwxrwxrwx 2 root root  262144 2006-08-29 05:47 bcd.LOG1
-rwxrwxrwx 2 root root       0 2006-08-29 05:47 bcd.LOG2
-rwxrwxrwx 1 root root 3170304 2006-09-18 09:45 boot.sdi
drwxrwxrwx 1 root root       0 2007-09-15 19:59 cs-CZ
drwxrwxrwx 1 root root       0 2007-09-15 19:59 da-DK
drwxrwxrwx 1 root root       0 2007-09-15 19:59 de-DE
-rwxrwxrwx 1 root root    1322 2006-10-13 11:00 Desktop.ini
drwxrwxrwx 1 root root       0 2007-09-15 19:59 el-GR
drwxrwxrwx 1 root root       0 2007-09-15 19:59 en-US
drwxrwxrwx 1 root root       0 2007-09-15 19:59 es-ES
drwxrwxrwx 1 root root       0 2007-09-15 19:59 fi-FI
drwxrwxrwx 1 root root       0 2007-09-15 19:46 fonts
drwxrwxrwx 1 root root       0 2007-09-15 19:59 fr-FR
drwxrwxrwx 1 root root       0 2007-09-15 19:59 hu-HU
drwxrwxrwx 1 root root       0 2007-09-15 19:59 it-IT
drwxrwxrwx 1 root root       0 2007-09-15 19:59 ja-JP
drwxrwxrwx 1 root root       0 2007-09-15 19:59 ko-KR
drwxrwxrwx 1 root root       0 2007-09-15 19:59 nb-NO
drwxrwxrwx 1 root root       0 2007-09-15 19:59 nl-NL
drwxrwxrwx 1 root root       0 2007-09-15 19:59 pl-PL
-rwxrwxrwx 1 root root  181648 2004-11-22 10:28 Protect.ed
drwxrwxrwx 1 root root       0 2007-09-15 19:59 pt-BR
drwxrwxrwx 1 root root       0 2007-09-15 19:59 pt-PT
drwxrwxrwx 1 root root       0 2007-09-15 19:59 ru-RU
drwxrwxrwx 1 root root       0 2007-09-15 19:59 sv-SE
drwxrwxrwx 1 root root       0 2007-09-15 19:59 tr-TR
drwxrwxrwx 1 root root       0 2007-09-15 19:59 zh-CN
drwxrwxrwx 1 root root       0 2007-09-15 19:59 zh-HK
drwxrwxrwx 1 root root       0 2007-09-15 19:59 zh-TW

=============================== StdErr Messages: ===============================

/dev/sdb: No medium found

sfdisk: cannot open /dev/sdb for reading
/dev/sdc: No medium found

sfdisk: cannot open /dev/sdc for reading
/dev/sdd: No medium found

sfdisk: cannot open /dev/sdd for reading
/dev/sde: No medium found

sfdisk: cannot open /dev/sde for reading
```

---

### Post by caljohnsmith on 2009-01-17
OK, how about booting your Vista CD, go to the command line, and do:
```
diskpart
```
And at the diskpart prompt do:
```
list volume
exit
```
And find which is the drive letter for your Vista partition, most likely "C". Then do:
```
bcdedit /store C:\boot\bcd /set {default} osdevice boot
bcdedit /store C:\boot\bcd /set {default} device boot
bcdedit /store C:\boot\bcd /set {bootmgr} device boot
bcdedit /store C:\boot\bcd /set {memdiag} device boot
```
And replace C above if the Vista drive letter is different. If the commands complete successfully, try to boot Vista again and let me know exactly what happens. We can work from there if you want.

---

### Post by shadowroses on 2009-01-17
When I did
```
bcdedit /store C:\boot\bcd /set {default} osdevice boot
```
I got the result "The element data type specified is not recognized, or does not apply to the specified entry."
The rest executed successfully.

---

### Post by caljohnsmith on 2009-01-17
Does your Vista CD have some sort of "Vista Repair" or "Startup Repair" type option you can use? You could try that. If that doesn't work, you could copy over a new bootmgr file and Boot folder to your Vista installation from the Vista CD. See step 2 of [this tutorial]("http://ubuntuforums.org/showpost.php?p=5726832") for the details, and let me know how that goes.

---

### Post by shadowroses on 2009-01-18
I did the Startup Repair and all tests completed successfully with no errors, so I'll try copying a new bootmgr file and Boot folder.

---

### Post by shadowroses on 2009-01-18
I have Vista booting properly now, so thank you! The only problem is I can no longer access Ubuntu.... Seems to be a never-ending cycle.  The partition is still there and intact, but Vista doesn't seem to recognize it.

---

### Post by caljohnsmith on 2009-01-18
Glad to hear that at least Vista is booting OK now, so to get Ubuntu booting too, how about downloading [EasyBCD]("http://neosmart.net/dl.php?id=1") in Vista; you can use that to add the C:\wubildr.mbr file to your Vista boot menu, and that should boot Ubuntu again. How about giving that a shot and let me know how it goes.

---

### Post by shadowroses on 2009-01-19
I added the entry, and when I tried to boot into Ubuntu, it brought me to a grub command line.

---

### Post by caljohnsmith on 2009-01-19
So did you add the C:\wubildr.mbr file or the C:\ubuntu\winboot\wubildr.mbr file to Vista's boot menu? Whichever one you added, try adding the other one instead and let me know if that works or not.

---

### Post by shadowroses on 2009-01-21
I wasn't given the option to add a specific file, unless I missed a setting somewhere.

---

