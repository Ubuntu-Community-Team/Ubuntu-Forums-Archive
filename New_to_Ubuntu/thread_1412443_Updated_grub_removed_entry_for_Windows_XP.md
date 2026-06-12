---
title: "Updated grub removed entry for Windows XP"
date: 2010-02-21
forum: New to Ubuntu
---

### Post by M8744 on 2010-02-21
Hi I am a Beginner. Someone previously configured my PC for dual booting Ubuntu 9.10 and Windows XP. Everything was fine until last week, when I apparently installed an updated bootloader progam as prompted by the Update Manager that now prevents me from having the option to boot to Windows XP. However, the entry for Windows XP is still at the bottom of the grub file (root (hd0,0) followed by chainloader +1). Is there an EASY way to get back to where I was, or will this be substantially difficult (i.e., reinstalling Linux)? Please advise.

---

### Post by kansasnoob on 2010-02-21
Please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

That way we'll hopefully be able to see what's going on.

---

### Post by AndresM on 2010-02-21
Hi, I'm a beginner as well. But today I  wanted to have windows as default starting point so installed Start-up Manager from the synaptics package manager. Maybe it will help.

---

### Post by petermit on 2010-02-21
Same problem... here is the results from the boot script:

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

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

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1bfc1bfc

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   144,568,934   144,568,872   7 HPFS/NTFS
/dev/sda2         144,568,935   156,296,384    11,727,450   5 Extended
/dev/sda5         144,568,998   146,528,864     1,959,867  82 Linux swap / Solaris
/dev/sda6         146,528,928   156,296,384     9,767,457  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        06F00AA7F00A9D55                       ntfs       WinXP                         
/dev/sda5        9fec1367-9115-42a0-b4ae-acc56d09ada6   swap                                     
/dev/sda6        cb32a826-5c61-4e80-aed7-281b21a298d9   ext3                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext3       (rw,relatime,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect


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
# kopt=root=UUID=cb32a826-5c61-4e80-aed7-281b21a298d9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=cb32a826-5c61-4e80-aed7-281b21a298d9

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

title		Ubuntu 9.10, kernel 2.6.31-20-generic
uuid		cb32a826-5c61-4e80-aed7-281b21a298d9
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=cb32a826-5c61-4e80-aed7-281b21a298d9 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-20-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid		cb32a826-5c61-4e80-aed7-281b21a298d9
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=cb32a826-5c61-4e80-aed7-281b21a298d9 ro  single
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 9.10, memtest86+
uuid		cb32a826-5c61-4e80-aed7-281b21a298d9
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

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
UUID=cb32a826-5c61-4e80-aed7-281b21a298d9 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=9fec1367-9115-42a0-b4ae-acc56d09ada6 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


  78.8GB: boot/grub/menu.lst
  78.8GB: boot/grub/stage2
  78.8GB: boot/initrd.img-2.6.31-20-generic
  78.9GB: boot/vmlinuz-2.6.31-20-generic
  78.8GB: initrd.img
  78.9GB: vmlinuz

---

### Post by kansasnoob on 2010-02-21
@petermit,

I don't know why updates "ate" your Windows entry but it's gone so you'll need to add Windows to the menu.lst:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```

```
gksudo gedit /boot/grub/menu.lst
```

Then at the very bottom of the menu.lst below this:

### END DEBIAN AUTOMAGIC KERNELS LIST

add this:

```
# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry added for a non-linux OS on /dev/sda1
title		Microsoft Windows XP
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1
```

Then be sure to click on Save and File > Quit.

---

### Post by petermit on 2010-02-22
@kansasnoob

Well thank you very much, everything worked and i finally managed to boot WindowsXP... I ve been using Ubuntu for almost a year now, and every time i had a problem i was able to fix it with some forum reading (such this one). But this time i was getting nowhere whetever i was trying.... Basically i was trying to add Windows with (hd0,1), so that must was the thing....

Anyway, problem solved, thank you very much...

---

### Post by M8744 on 2010-02-22
Here are my RESULTS.txt:
```

```                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

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

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0f4738c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   466,672,184   466,672,122   7 HPFS/NTFS
/dev/sda2         466,672,185   625,137,344   158,465,160   f W95 Ext d (LBA)
/dev/sda5         466,672,248   618,598,889   151,926,642  83 Linux
/dev/sda6         618,598,953   625,137,344     6,538,392  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        FEF4E67FF4E63A13                       ntfs                                     
/dev/sda5        6a343049-e781-464c-a719-bf6ed9dfe801   ext3                                     
/dev/sda6        95cf0422-0b4a-4486-b6c3-3281f719416b   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sda1        /mnt/windows             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=6a343049-e781-464c-a719-bf6ed9dfe801 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=6a343049-e781-464c-a719-bf6ed9dfe801

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

title        Ubuntu 9.10, kernel 2.6.31-19-generic
uuid        6a343049-e781-464c-a719-bf6ed9dfe801
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=6a343049-e781-464c-a719-bf6ed9dfe801 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-19-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid        6a343049-e781-464c-a719-bf6ed9dfe801
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=6a343049-e781-464c-a719-bf6ed9dfe801 ro  single
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, kernel 2.6.31-16-generic
uuid        6a343049-e781-464c-a719-bf6ed9dfe801
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=6a343049-e781-464c-a719-bf6ed9dfe801 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-16-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid        6a343049-e781-464c-a719-bf6ed9dfe801
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=6a343049-e781-464c-a719-bf6ed9dfe801 ro  single
initrd        /boot/initrd.img-2.6.31-16-generic

title        Ubuntu 9.10, kernel 2.6.31-15-generic
uuid        6a343049-e781-464c-a719-bf6ed9dfe801
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=6a343049-e781-464c-a719-bf6ed9dfe801 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-15-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid        6a343049-e781-464c-a719-bf6ed9dfe801
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=6a343049-e781-464c-a719-bf6ed9dfe801 ro  single
initrd        /boot/initrd.img-2.6.31-15-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        6a343049-e781-464c-a719-bf6ed9dfe801
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=6a343049-e781-464c-a719-bf6ed9dfe801 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        6a343049-e781-464c-a719-bf6ed9dfe801
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=6a343049-e781-464c-a719-bf6ed9dfe801 ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.28-15-generic
uuid        6a343049-e781-464c-a719-bf6ed9dfe801
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=6a343049-e781-464c-a719-bf6ed9dfe801 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-15-generic (recovery mode)
uuid        6a343049-e781-464c-a719-bf6ed9dfe801
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=6a343049-e781-464c-a719-bf6ed9dfe801 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.10, memtest86+
uuid        6a343049-e781-464c-a719-bf6ed9dfe801
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1




=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=6a343049-e781-464c-a719-bf6ed9dfe801 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=95cf0422-0b4a-4486-b6c3-3281f719416b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda1 /mnt/windows ntfs-3g defaults 0 0


=================== sda5: Location of files loaded by Grub: ===================


 259.0GB: boot/grub/menu.lst
 259.1GB: boot/grub/stage2
 259.1GB: boot/initrd.img-2.6.28-15-generic
 259.1GB: boot/initrd.img-2.6.31-14-generic
 259.1GB: boot/initrd.img-2.6.31-15-generic
 259.1GB: boot/initrd.img-2.6.31-16-generic
 259.1GB: boot/initrd.img-2.6.31-19-generic
 259.1GB: boot/vmlinuz-2.6.28-15-generic
 259.0GB: boot/vmlinuz-2.6.31-14-generic
 259.1GB: boot/vmlinuz-2.6.31-15-generic
 259.1GB: boot/vmlinuz-2.6.31-16-generic
 259.0GB: boot/vmlinuz-2.6.31-19-generic
 259.1GB: initrd.img
 259.1GB: initrd.img.old
 259.0GB: vmlinuz
 259.1GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde

---

### Post by kansasnoob on 2010-02-25
I'll bet your list of Ubuntu kernels is just so long it "pushed" Windows off the bottom of the visible list. The easiest way to deal with that is to install Startup Manager:

```
sudo apt-get install startupmanager
```

It'll then show up in System > Administration. If you click on the Advanced tab you'll see that you can check a box to limit the number of kernels and also toggle up or down to set the number.

I like to check that and set the number to 2 because it's always best to have one older kernel to boot in case something goes haywire with the newest one.

You can also select whether or not to display the recovery mode or the memtest options. IMHO it's best to leave the Recovery options shown, but how often do you use the memtest?

---

