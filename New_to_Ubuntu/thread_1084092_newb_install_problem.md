---
title: "newb install problem"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by sjmcyyc1960 on 2009-03-01
I have looked everywhere for a solution to this...I have been trying to install ubuntu 8.10 inside windows vista, but when I do the install upon first reboot I do not get Ubuntu as a boot option, the pute boots straight to Vista. During my many attempts at installing I noticed that ubuntu lists my sata drive (D in windows) as my first drive and my ide drive (c in windows). This does not seem right, so anyway i tried to install it straight from the cd instead of inside  Windows and now I have a different problem. In my bios if I set the boot drive as the ide, I get the choice of Vista or Ubuntu, but ubuntu does not work. If I set the sata drive as my boot, Ubuntu comes up as the default and the vista options does not work. Also when I boot into Ubuntu I am unable to mount any Vista drives. Any ideas anyone? 

Just as a side note I intalled Ubuntu on another computer set up the same way with an ide and sata drive and had no problem at all. Iused the same Ubuntu install disk so I know the disk is OK.

Thanks in advance

Sean

---

### Post by Bodsda on 2009-03-01
from ubuntu can you please provide us with the output of the following commands

```
sudo fdisk -l
```
and
```
cat /boot/grub/menu.lst
```

This information should help us solve the problem

Thanks

Bodsda

---

### Post by sjmcyyc1960 on 2009-03-01
here is the fdisk -l:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00033121

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       55694   447362023+   7  HPFS/NTFS
/dev/sda2           55695       60801    41021977+   5  Extended
/dev/sda5           55695       60314    37110118+  83  Linux
/dev/sda6           60315       60801     3911796   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
240 heads, 63 sectors/track, 41345 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xc773c773

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       40737   307971688+   7  HPFS/NTFS
/dev/sdb2           40738       41345     4596480    f  W95 Ext'd (LBA)

here is the boot/grub/menu.lst

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
# kopt=root=UUID=1cfd939b-56a1-4294-9c8a-70520a40f66a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1cfd939b-56a1-4294-9c8a-70520a40f66a

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		1cfd939b-56a1-4294-9c8a-70520a40f66a
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1cfd939b-56a1-4294-9c8a-70520a40f66a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		1cfd939b-56a1-4294-9c8a-70520a40f66a
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1cfd939b-56a1-4294-9c8a-70520a40f66a ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		1cfd939b-56a1-4294-9c8a-70520a40f66a
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


Thanks for your help
Sean

---

### Post by Bodsda on 2009-03-01
Is the windows boot files (stupidly known as the system files) located on the 320gb hard drive or the 500gb hard drive?

---

### Post by sjmcyyc1960 on 2009-03-01
located on the 320gb drive

Sean

---

### Post by sjmcyyc1960 on 2009-03-01
Any ideas anyone?

Thanks
Sean

---

### Post by presence1960 on 2009-03-01
You have plenty of hard drive space why not just create a partition(s) for Linux and do a dual boot instead of installing Linux inside Windows. That's just my opinion, I would not build a house on sinking ground (Windows Vista).

---

### Post by sjmcyyc1960 on 2009-03-01
I have installed ubuntu both ways, when installed inside windows computer boots straight to vista.

I did the partition thing and installed that way, which is how it is now but I have to change the drive boot oreder in the bios to get either vista or ubuntu. That's my problem now.

Thanks

---

### Post by presence1960 on 2009-03-01
Does this mean you got rid of the install inside windows? If so run in terminal those  two commands Bodsda gave in post #2 and let's see what you have now. It should just be a matter of setting the disk with grub on it to boot first in BIOS then a little editing of the menu.lst file. I have things to do with my daughter, I will be back later. But go ahead and redo those commands as there are plenty who are willing and able to help you in here.

---

### Post by sjmcyyc1960 on 2009-03-01
the commands I ran were after the one inside windows was unintalled.

Thanks for your help!

Sean

---

### Post by presence1960 on 2009-03-01
What is the NTFS partition #1 on the 500Gb drive? It has an asterisk indicating it is bootable. You stated your Windows boot files are on the 320 Gb drive. I am assuming Windows is installed on the 320 Gb drive which is supported by the asterisk on that dive also. It appears you have 2 bootable windows - one on each drive. Here is what my fdisk -l looks like:
> 
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000d179

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20972826   83  Linux
/dev/sda2            2612       27963   203639940   83  Linux
/dev/sda3           29411       30401     7960207+  82  Linux swap / Solaris
/dev/sda4           27964       29410    11623027+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa7a57e45

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7833    62918541    7  HPFS/NTFS
/dev/sdb2            7834       19457    93369780   83  Linux

My windows is set up on sdb1 and is bootable, Linux Mint is installed on sda1 and Kubuntu on sda4. sda2 is /home for both. I had gotten rid of windows but my DSL had problems and the techs needed windows to solve the problem so now I have windows again :(

---

### Post by sjmcyyc1960 on 2009-03-02
So how do I get the Ubuntu installation to see my 320gb as my main drive and set up a proper dual boot.

Thanks Again

---

### Post by presence1960 on 2009-03-02
> **sjmcyyc1960 said:**
> So how do I get the Ubuntu installation to see my 320gb as my main drive and set up a proper dual boot.

Thanks Again

You can go into BIOS and set the 320Gb drive as first hard disk boot. Then to restore GRUB you can pop in a live CD and reboot off the Cd. Follow this:
```

1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Go SuperUser (that is, type "sudo -s"). Enter root passwords as 
   necessary.
4. Type "grub"
5. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
6. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
7. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition nr is, to install GRUB to a 
   partition.
8. Quit grub by typing "quit".
9. Reboot and remove the bootable CD.
```

Or you can try Super Grub disk.

---

### Post by sjmcyyc1960 on 2009-03-02
Thanks, I'll give that a try.

---

### Post by sjmcyyc1960 on 2009-03-02
Could not get ir to work. I cannot boot from Ubuntu cd when I boot from 320gb drive, it just runs in live version and does not see the installation on my 500gb drive. For some reason when I install ubuntu it sees my 500gb as my main drive, this has me stumped for sure. I uninstalled unbuntu from the computer and started from scratch by trying to install inside windows again and once again it just boots straight to windows and does not finish the Ubuntu install so i cannot get into it at all. It is extra frustrating because I just installed this a week ago on another computer with no trouble at all (except the video driver problem), yet I cannot get it to go in at all on this other computer.

There has to be something I can change so when ubuntu is installing it sees my 320gb drive as the boot drive.

---

### Post by sjmcyyc1960 on 2009-03-02
Any ideas anyone?

---

### Post by sjmcyyc1960 on 2009-03-02
Anybody...before I have no hair left:lolflag:

---

### Post by sjmcyyc1960 on 2009-03-03
Still waiting ...and hoping.

Thanks
Sean

---

### Post by Khaldoun Dabain on 2009-03-03
I purchased a Mini with ubuntu for my daughter there are about 100 updates that she needs to down load, but she is not setup as a superuser. how can i change this for her. I donot know any thing about ubuntu
please help:(:

---

