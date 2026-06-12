---
title: "[SOLVED] Vista wont boot after a dual boot install with ubuntu"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by gredawarha on 2008-12-08
Hello all

I have searched the forums but could not fins a solution that helped so apologies if this question has been asked before and answered.

My sister has a new laptop dell inspiron 1525 with vista installed.

I have installed intrepid so that she has a dual boot vista/ubuntu system.

Upon completion of the installation ubuntu works fine but when I select vista from the grub list nothing happens and then the pc reboots as I then see the dell BIOS screen.

Any ideas guys?

Any help is much appreciated.

thanks

---

### Post by mk1w86 on 2008-12-08
Could you post your /boot/grub/menu.lst file :-)

---

### Post by dragos_iliescu_2005 on 2008-12-08
I guess your problem is related with the boot configuration files. As I am not quit sure, pay all your attention to this matter. As far I understand, your vista is not "able" to find the correct partition to boot. Solution is to correct this configuration. You must edit the file /boot/grub/menu.lst to point the correct partition for vista to start.
But before doing that I believe you must to find more info on the subject. The risk is that ubuntu too will not boot.
Success.

---

### Post by gredawarha on 2008-12-08
menu.lst - See: grub(8), info grub, update-grub(8)
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
timeout		1

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
# kopt=root=UUID=058856b7-f5dd-42bf-91d6-fcbf0e91b344 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=058856b7-f5dd-42bf-91d6-fcbf0e91b344

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		058856b7-f5dd-42bf-91d6-fcbf0e91b344
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=058856b7-f5dd-42bf-91d6-fcbf0e91b344 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		058856b7-f5dd-42bf-91d6-fcbf0e91b344
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=058856b7-f5dd-42bf-91d6-fcbf0e91b344 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		058856b7-f5dd-42bf-91d6-fcbf0e91b344
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=058856b7-f5dd-42bf-91d6-fcbf0e91b344 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		058856b7-f5dd-42bf-91d6-fcbf0e91b344
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=058856b7-f5dd-42bf-91d6-fcbf0e91b344 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		058856b7-f5dd-42bf-91d6-fcbf0e91b344
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1

---

### Post by mk1w86 on 2008-12-08
Could you run 

```
sudo fdisk -l /dev/sda
```

and post the output so we can see your partitions.

---

### Post by gredawarha on 2008-12-08
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1319    10594836   82  Linux swap / Solaris
/dev/sda2           11519       14068    20482875   83  Linux
/dev/sda3   *        1320       11518    81923467+   7  HPFS/NTFS
/dev/sda4           14069       38913   199567462+   b  W95 FAT32

Partition table entries are not in disk order

---

### Post by mk1w86 on 2008-12-08
At the grub boot screen highlight the Vista entry and press e.  This will allow you to edit boot options without making permanent changes to your system so you can still boot Ubuntu if it does not work.

Then highlight the root (hd0,2) entry and press e again to edit this.  Try changing it to root (hd0,0) then press esc and then b to boot the entry.

If it doesn't work try (hd0,1) and see if it boots.


If Vista does boot you can make the changes permanant by editing your menu.lst file (You will need root privileges).

---

### Post by carml on 2008-12-08
Hi,me too I have a dual boot with Vista and Ubuntu 8.04.
I compared your file menu.list with mine and noticed some differences(maybe they relay on the difference between 8.04 and 8.10),but the last rows are similar.
In my humble opinion,you should ask the others if they have Ubuntu 8.10 too,so they can compare their menu.list with your and give suggestion... 
:-|.

---

### Post by gredawarha on 2008-12-08
Hi mk1w86

Followed your advice but still no joy any ideas?

---

### Post by mk1w86 on 2008-12-08
Do you get any error message at all or does the machine just reboot like you say in your first post?

I am asking because I have had problems with Windows in the past (mainly XP) where it will just reboot the machine if it cannot boot.  Grub normally gives an error message so if it is Windows then grub is OK and it is the Windows boot loader that has stopped working because all grub does is pass control to the windows loader it does not actually boot windows directly.

> In my humble opinion,you should ask the others if they have Ubuntu 8.10 too,so they can compare their menu.list with your and give suggestion...

I have only ever dual booted Vista with Ubuntu 8.04 but have dual booted 8.10 OK with XP.

---

### Post by caljohnsmith on 2008-12-08
Was Vista always on sda3 or did you move/resize Vista's partition at all? More importantly did you move the starting point of the original Vista partition? Using the original Vista entry you have in your Ubuntu menu.lst should be fine, so I think you have a Vista problem and not a Grub problem at this point.

---

### Post by gredawarha on 2008-12-08
When I select vista it just reboots, if I change the hd (0,2) to different numbers then I get:

Grub Error 13: "Invalid or unsupported executable format"

I have only shrunk the original vista partition to create room for my ubuntu.

I appreciate all the help and hopefully you guys can help me sort this out but I have to log off for know and will log in again tomorrow with any luck.  Thanks again for all the help and hopefully we can can resolve this

---

### Post by mk1w86 on 2008-12-08
It does now appear that grub is OK and it is Vista at fault.
The next thing to try is probably to recover the Vista boot loader.  There is a guide to doing that here:

[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

After recovering the Vista boot loader it will probably overwrite grub so you will have to reinstall that by booting the Ubuntu live CD and running the command:

```
sudo grub-install
```

:cool:

---

### Post by toucher5 on 2008-12-08
any time I have boot issues that involve boot loaders I use one of the following:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
or
[http://www.sysresccd.org](http://www.sysresccd.org)

For just the grub issue you should only need the first link. The second link gives you several tools for administering a Linux system.

Or you could always do the wubi-installer.org

---

### Post by caljohnsmith on 2008-12-08
> **gredawarha said:**
> 
I have only shrunk the original vista partition to create room for my ubuntu.

Yes, but did you shrink the end of the Vista partition to make room, or the beginning of the partition? It looks like what you did is delete the Vista recovery partition at the beginning of the disk and turn it into Ubuntu's swap partition. And by the way, a 10 GB swap partition is a bit of an overkill; the general rule of thumb I think is swap should be twice your RAM up to about 2 GB of swap space, and after that swap space should be equal to your RAM size. Do you have a Vista Install CD? If not, you can download a Vista Recovery CD from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"). I would boot that, go to the command line and do:
```
bootrec /rebuildbcd
chkdsk /r
```
And run the chkdsk as many times as it takes until it reports no errors. The first command is important in order to make Vista recognize your new partition changes, which can prevent Vista from booting. Then reboot, make sure you are using the original Vista entry that uses (hd0,2) in your Grub menu.lst, and then let me know exactly what happens when you boot Vista from Grub. If the above commands aren't enough to get Vista booting OK, we can work from there if you want.

---

### Post by gredawarha on 2008-12-09
Okay guys thanks for all your help, I ran the vista repair disc and now both ubuntu and vista boot fine.

Thanks

---

### Post by Nabo00o on 2011-02-24
Hi everybody sorry to reopen this old tread, but I got one problem.
Following caljohnsmith's link I made a bootable CD/RW and finally got to see the windows icon again.
However.... when I got inside the only choice I had was to install windows, there was no other option. I don't know if you are the correct people to ask this, but I have a feeling its because I too messed up windows bootup system (I deleted the recovery partition).

So how do I convince windows that it's actually there, and I only want to fix something on it, not install it? 

Appreciate any help I can get
Julian

---

