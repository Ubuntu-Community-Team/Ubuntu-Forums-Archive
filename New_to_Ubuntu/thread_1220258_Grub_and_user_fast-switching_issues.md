---
title: "Grub and user fast-switching issues"
date: 2009-07-22
forum: New to Ubuntu
---

### Post by Winlinos on 2009-07-22
```

find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
error 15: file not found
press any key to continue...

```After pressing key, I get this 

```

/ubuntu/disks/boot/grub/menu.lst
/ubuntu/install/boot/grub/menu.lst
/menu.lst
/boot/grub/menu.lst
/grub/menu.;st
command line
reboot
halt

```I had to choose the 4th line to get into the grub menu list itself to select the OS to boot. I tried editing one of those lines to no avail.

That's not something I'd like to do; booting straight into the OS if possible. Once I change the initial boot menu (Windows Xp and ubuntu) then hit the roadbock at the first code message above. 

Secondly, vital issue to be resolve if possible. 

When two users logs on into the system (fast-switching), after a few turns, one logs off... suddenly crash ending up non responsive black screen!

Help me with those please, thanks!

---

### Post by rraj.be on 2009-07-22
Could you post me the menu.lst contents?
```

sudo gedit /boot/grub/menu.lst
```

---

### Post by Winlinos on 2009-07-22
> **rraj.be said:**
> Could you post me the menu.lst contents?
```

sudo gedit /boot/grub/menu.lst
```
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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=f96c5440-644c-4350-83db-081f9196d9ed ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,4)

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

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic
root        (hd2,4)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=f96c5440-644c-4350-83db-081f9196d9ed ro quiet splash
initrd        /boot/initrd.img-2.6.24-24-generic
quiet

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (recovery mode)
root        (hd2,4)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=f96c5440-644c-4350-83db-081f9196d9ed ro single
initrd        /boot/initrd.img-2.6.24-24-generic

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-16-generic
root        (hd2,4)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=f96c5440-644c-4350-83db-081f9196d9ed ro quiet splash
initrd        /boot/initrd.img-2.6.24-16-generic
quiet

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-16-generic (recovery mode)
root        (hd2,4)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=f96c5440-644c-4350-83db-081f9196d9ed ro single
initrd        /boot/initrd.img-2.6.24-16-generic

title        Ubuntu 8.04.3 LTS, memtest86+
root        (hd2,4)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title        Microsoft Windows XP Professional
root        (hd1,1)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

```
Not sure what section you wanted to see so I went ahead with the whole.

---

### Post by oldfred on 2009-07-22
You have an extra other operating systems & root with no entry just above the windows entry. Comment out these two lines and see if this helps. 
Otherwise we will need to see your disk layout. 
sudo fdisk -l 
where -l is the letter el not one 1 or eye I.

---

### Post by Winlinos on 2009-07-23
[quote=oldfred]You have an extra other operating systems & root with no entry just above the windows entry. Comment out these two lines and see if this helps. 
Otherwise we will need to see your disk layout. 
sudo fdisk -l 
where -l is the letter el not one 1 or eye I.[/quote]

```
Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd40dd40d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14946   120053713+  42  SFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
240 heads, 63 sectors/track, 32301 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x2f7c2f7c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       10515    79489024   42  SFS
/dev/sdb2           10515       32301   164705512   42  SFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000106e2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       15035   120768606    5  Extended
/dev/sdc2           15036       29950   119804737+   7  HPFS/NTFS
/dev/sdc3           29951       44483   116736322+   7  HPFS/NTFS
/dev/sdc4           44484       60801   131074335    7  HPFS/NTFS
/dev/sdc5               1       14062   112952952   83  Linux
/dev/sdc6           14063       15035     7815591   82  Linux swap / Solaris

Disk /dev/sdd: 512 MB, 512753664 bytes
16 heads, 32 sectors/track, 1956 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0xcfe2a146

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        1956      500720    b  W95 FAT32

```

---

### Post by oldfred on 2009-07-24
Did you delete the blank root? 

I am not familiar with the sfs file system and do not know if that adds confusion for GRUB. Have you checked that the versions match. This says that is a common problem for Grub error 15.
[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_]("http://members.iinet.net.au/%7Eherman546/p15.html#How_to_make_a_separate_Grub_Partition_")

It also looks like you have done some editing for Grub to find all the additional misnamed/mislocated menu.lsts.  Unless all but line 4 belong to another operating system you can delete them.

---

### Post by egalvan on 2009-07-24
> **oldfred said:**
> You have an **extra other operating systems & root with no entry **
just above the windows entry. Comment out these two lines and see if this helps. 


It's NOT an "extra operating system etc"...
it's just what it says it is...


```
# **This is a divider, added to separate the menu items **below from the Debian
# ones.
title        Other operating systems:
root

```


It's a **divider**, and the **title** is "Other operating systems".

This is it's proper syntax.

And deleting it will not help.

BTW, I renamed mine to 

# This is a divider, added to separate the menu items below from the Debian
# ones.
title       ** non-*nix op-sys:**
root

---

### Post by Winlinos on 2009-08-12
```
find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
error 15: file not found
press any key to continue...
```I still have this problem and it yet needs to be resolved. The way I see it that it's pointing to the wrong directory to boot into directly. but it stops there. 

So if I could just put this...
```
find --set-root --ignore-floppies /boot/grub/menu.lst


```and I would be able to boot without stopping. So could antyone help me with that? Where to fix it? where to delete these lines? 

Thanks!

---

### Post by Winlinos on 2009-08-14
Bump

---

### Post by LewRockwell on 2009-08-14
> **egalvan said:**
> It's NOT an "extra operating system etc"...
it's just what it says it is...


```
# **This is a divider, added to separate the menu items **below from the Debian
# ones.
title        Other operating systems:
root

```


It's a **divider**, and the **title** is "Other operating systems".

This is it's proper syntax.

And deleting it will not help.

BTW, I renamed mine to 

# This is a divider, added to separate the menu items below from the Debian
# ones.
title       ** non-*nix op-sys:**
root

I made some of mine look like:
```
# This is a divider, added to separate the menu items below from the Debian
# ones.


title **THIS SPACE RESERVED FOR ANOTHER COOL NIX DISTRO!**
root
```

.

---

### Post by LewRockwell on 2009-08-14
> **Winlinos said:**
> ```

find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
error 15: file not found
press any key to continue...

```After pressing key, I get this 

```

/ubuntu/disks/boot/grub/menu.lst
/ubuntu/install/boot/grub/menu.lst
/menu.lst
/boot/grub/menu.lst
/grub/menu.;st
command line
reboot
halt

```I had to choose the 4th line to get into the grub menu list itself to select the OS to boot. I tried editing one of those lines to no avail.

That's not something I'd like to do; booting straight into the OS if possible. Once I change the initial boot menu (Windows Xp and ubuntu) then hit the roadblock at the first code message above.

SuperGrubDisk should correct the portion of your Grub that resides in the MBR

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

.

---

### Post by LewRockwell on 2009-08-14
> **Winlinos said:**
> When two users logs on into the system (fast-switching), after a few turns, one logs off... suddenly crash ending up non responsive black screen!

[http://www.dslreports.com/forum/r19324272-Ubuntu-switch-user-problem](http://www.dslreports.com/forum/r19324272-Ubuntu-switch-user-problem)

.

---

