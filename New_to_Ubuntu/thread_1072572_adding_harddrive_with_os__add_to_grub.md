---
title: "adding harddrive with os / add to grub?"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by chaddiesel on 2009-02-17
I have my system running a dual boot ubuntu 7.10/windows xp on one drive. I want to add a harddrive to the system with windows 7 on it to the boot list in grub. 

My main harddrive(dual boot) is SATA and the extra harddrive(windows 7) is PATA or IDE with a converter to SATA. 

I think I'm unsure what to set the jumpers to on the extra harddrive. And, I have no idea how to set up another boot partition thats located physically on another harddrive.

---

### Post by caljohnsmith on 2009-02-17
I would set your Windows 7 PATA drive as "master", and also you don't need to set up a separate boot partition from what it sounds like. Just install Windows 7 to the PATA drive, and then you can boot it from Grub using an entry in your menu.lst like:
```
title Windows 7
rootnoverify (hd1)
map (hd1) (hd0)
map (hd0) (hd1)
chainloader +1

```
That should work if you have only the two drives, but if you have more drives, you might have to use (hd2) or higher. Let me know how that goes or if you run into problems.

---

### Post by chaddiesel on 2009-02-17
Thanks for the quick reply. I have changed the grub file before. What is the location again? :o

---

### Post by caljohnsmith on 2009-02-17
To modify your Grub menu.lst, if you open a terminal (Applications > Accessories > Terminal), just do:
```
gksudo gedit /boot/grub/menu.lst
```
Let me know how it goes.

---

### Post by chaddiesel on 2009-02-17
I tried making an edit and the extra boot option it doesn't do anything but go right back to grub. Seems like grub doesn't know where to find it.

here's the file.....

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
# kopt=root=UUID=02b0b594-955a-4b3d-9b76-afb552cd1c13 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title		Ubuntu 7.10, kernel 2.6.22-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-16-generic root=UUID=02b0b594-955a-4b3d-9b76-afb552cd1c13 ro quiet splash
initrd		/boot/initrd.img-2.6.22-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-16-generic root=UUID=02b0b594-955a-4b3d-9b76-afb552cd1c13 ro single
initrd		/boot/initrd.img-2.6.22-16-generic

title		Ubuntu 7.10, kernel 2.6.22-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=02b0b594-955a-4b3d-9b76-afb552cd1c13 ro quiet splash
initrd		/boot/initrd.img-2.6.22-15-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=02b0b594-955a-4b3d-9b76-afb552cd1c13 ro single
initrd		/boot/initrd.img-2.6.22-15-generic

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=02b0b594-955a-4b3d-9b76-afb552cd1c13 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=02b0b594-955a-4b3d-9b76-afb552cd1c13 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title		Windows 7
root		(hd1,0)
makeactive
chainloader	+1
```

...........you can see how I made the edit on the bottom, tried to duplicate what the XP code looked like minus the "savedefault".

---

### Post by chaddiesel on 2009-02-18
On another note. The extra harddisk doesn't automatically mount. It will mount but it needs to be double-clicked. 

My harddisk that is dual booted has the windows partition mounted at /dev/sda1. The new harddisk mounts after being found, but mounts as /dev/disk..... similar to an external drive.

---

### Post by caljohnsmith on 2009-02-18
The Windows 7 entry in the menu.lst you posted is not the entry that I recommended in post #2. Did you try that entry yet, and if so, what exactly happened?

---

### Post by chaddiesel on 2009-02-18
I'll give it a shot. I'm at work right now. I saw that other windows set up and thought it might need to look identical to it.

Thanks for all this help. :D

---

### Post by chaddiesel on 2009-02-18
ok here is what I get.....

```
 BOOTMGR is missing
 press Ctrl+Alt+Del to restart.
```

and here is my file..... 

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
# kopt=root=UUID=02b0b594-955a-4b3d-9b76-afb552cd1c13 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title		Ubuntu 7.10, kernel 2.6.22-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-16-generic root=UUID=02b0b594-955a-4b3d-9b76-afb552cd1c13 ro quiet splash
initrd		/boot/initrd.img-2.6.22-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-16-generic root=UUID=02b0b594-955a-4b3d-9b76-afb552cd1c13 ro single
initrd		/boot/initrd.img-2.6.22-16-generic

title		Ubuntu 7.10, kernel 2.6.22-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=02b0b594-955a-4b3d-9b76-afb552cd1c13 ro quiet splash
initrd		/boot/initrd.img-2.6.22-15-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=02b0b594-955a-4b3d-9b76-afb552cd1c13 ro single
initrd		/boot/initrd.img-2.6.22-15-generic

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=02b0b594-955a-4b3d-9b76-afb552cd1c13 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=02b0b594-955a-4b3d-9b76-afb552cd1c13 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title Windows 7
rootnoverify (hd1)
map (hd1) (hd0)
map (hd0) (hd1)
chainloader +1

```

---

### Post by chaddiesel on 2009-02-18
i went and changed the rootnoverify and made it root noverify and I get 

Error 11 - Unknown Device String

Hit any key to restart

---

### Post by caljohnsmith on 2009-02-18
OK, looks like we're going to need to get more info about your setup, so how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post.

---

### Post by chaddiesel on 2009-02-19
I ran the script..... got some interesting results.

Didn't know that I had fat32 format on the drive. Take a look.

```
 
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 7.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /BOOTMGR /boot/bcd /BOOT/bcd /Boot/bcd 
                       /boot/BCD /BOOT/BCD /Boot/BCD

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0000b8a6

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   151,557,209   151,557,147   7 HPFS/NTFS
/dev/sda2         151,557,210   310,472,189   158,914,980  83 Linux
/dev/sda3         310,472,190   312,576,704     2,104,515  82 Linux swap / Solaris


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 164.6 GB, 164696555520 bytes
240 heads, 63 sectors/track, 21274 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xea2ced3d

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   268,430,084   268,430,022   c W95 FAT32 (LBA)
/dev/sdb2    *    268,431,360   321,669,119    53,237,760   7 HPFS/NTFS

/dev/sdb2 ends after the last cylinder of /dev/sdb

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="901C059D1C057F88" TYPE="ntfs" 
/dev/sda2: UUID="02b0b594-955a-4b3d-9b76-afb552cd1c13" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: UUID="70e18cdc-113a-4a27-8691-4623fc5dab43" TYPE="swap" 
/dev/sdb1: LABEL="STORAGE" UUID="8D98-4171" TYPE="vfat" 
/dev/sdb2: UUID="849CF9209CF90E04" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-16-generic/volatile type tmpfs (rw)
/dev/sda1 on /media/sda1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer


=========================== sda2/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=02b0b594-955a-4b3d-9b76-afb552cd1c13 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title		Ubuntu 7.10, kernel 2.6.22-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-16-generic root=UUID=02b0b594-955a-4b3d-9b76-afb552cd1c13 ro quiet splash
initrd		/boot/initrd.img-2.6.22-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-16-generic root=UUID=02b0b594-955a-4b3d-9b76-afb552cd1c13 ro single
initrd		/boot/initrd.img-2.6.22-16-generic

title		Ubuntu 7.10, kernel 2.6.22-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=02b0b594-955a-4b3d-9b76-afb552cd1c13 ro quiet splash
initrd		/boot/initrd.img-2.6.22-15-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=02b0b594-955a-4b3d-9b76-afb552cd1c13 ro single
initrd		/boot/initrd.img-2.6.22-15-generic

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=02b0b594-955a-4b3d-9b76-afb552cd1c13 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=02b0b594-955a-4b3d-9b76-afb552cd1c13 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title           Windows 7
root            noverify (hd1)
map             (hd1) (hd0)
map             (hd0) (hd1)
chainloader     +1


=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=02b0b594-955a-4b3d-9b76-afb552cd1c13 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=901C059D1C057F88 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=70e18cdc-113a-4a27-8691-4623fc5dab43 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

=================== sda2: Location of files loaded by Grub: ===================


 104.8GB: boot/grub/menu.lst
 104.9GB: boot/grub/stage2
 104.8GB: boot/initrd.img-2.6.22-14-generic
 104.8GB: boot/initrd.img-2.6.22-14-generic.bak
 104.8GB: boot/initrd.img-2.6.22-15-generic
 104.9GB: boot/initrd.img-2.6.22-15-generic.bak
 105.1GB: boot/initrd.img-2.6.22-16-generic
 104.9GB: boot/initrd.img-2.6.22-16-generic.bak
 104.9GB: boot/vmlinuz-2.6.22-14-generic
 104.9GB: boot/vmlinuz-2.6.22-15-generic
 104.8GB: boot/vmlinuz-2.6.22-16-generic
 105.1GB: initrd.img
 104.8GB: initrd.img.old
 104.8GB: vmlinuz
 104.9GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

hda hdb 
=============================== StdErr Messages: ===============================

umount: /tmp/BootInfo/sdb1: device is busy
umount: /tmp/BootInfo/sdb1: device is busy
```

---

### Post by caljohnsmith on 2009-02-19
OK, first of all change the Windows entry back to "rootnoverify", because it is all one word. Next try:
```
sudo sfdisk -A1 /dev/sdb

```
Reboot, and let me know exactly what happens when you boot Win 7 from Grub. We can work from there.

---

### Post by chaddiesel on 2009-02-19
IT WORKED!! Thanks for all of the help.:p

What was it that the sfdisk command actually did?

---

### Post by caljohnsmith on 2009-02-19
> **chaddiesel said:**
> IT WORKED!! Thanks for all of the help.:p

What was it that the sfdisk command actually did?
Glad that worked OK. The sfdisk command just changed the boot flag from sdb2 to sdb1, because Windows 7 put its boot files in sdb1 even though part of Windows 7 is installed in sdb2. Hope you enjoy your dual-boot setup.

---

