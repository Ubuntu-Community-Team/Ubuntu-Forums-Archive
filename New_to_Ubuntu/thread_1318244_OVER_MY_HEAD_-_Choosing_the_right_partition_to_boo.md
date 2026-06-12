---
title: "OVER MY HEAD - Choosing the right partition to boot from, Grub?"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by zzyzx1 on 2009-11-07
Will try and keep short and on point. Ive been using Ubuntu and decided to load Mint and give it a try. Simple install, but i chose the "load along side Ubuntu" option and on a separate partition. So i used the partition tool to resize the hd into 2 equal parts and loaded Mint on the new partition "along side" next to Ubuntu.

I was hoping to reboot and find some kind of friendly splash asking me which OS to boot into, Mint or Ubuntu but it just goes right into Ubuntu. So i checked GParted to make sure that my new part was flagged for boot and it was not, so i changed it, still wont boot from Mint.

So now Im looking at Grub. I don't know much about Grub so I am RTFM and looking for any assistance to help me figure this out. The result I am looking for is a choice at boot up. Ubuntu or Mint.

Thank you!

---

### Post by utnubuuser on 2009-11-07
post which versions of ubuntu/mint you're running. - 9.10 uses grub 2, and the procedure is different.

might be as easy as running > sudo update-grub

---

### Post by zzyzx1 on 2009-11-07
> **utnubuuser said:**
> post which versions of ubuntu/mint you're running. - 9.10 uses grub 2, and the procedure is different.

might be as easy as running

-desktop:~$ update-grub
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
Searching for GRUB installation directory ... found: /boot/grub
/dev/sda1: error opening volume
/dev/sda1: error opening volume
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
cp: cannot remove `/boot/grub/menu.lst~': Permission denied

---

### Post by oldos2er on 2009-11-07
Try **sudo update-grub**

---

### Post by zzyzx1 on 2009-11-07
Ubuntu 9.04 and Mint 7

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
timeout        3

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
# kopt=root=UUID=c1fac2bc-2156-482f-9249-79b3854acfc0 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=c1fac2bc-2156-482f-9249-79b3854acfc0

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

title        Ubuntu 9.04, kernel 2.6.28-16-generic
uuid        c1fac2bc-2156-482f-9249-79b3854acfc0
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=c1fac2bc-2156-482f-9249-79b3854acfc0 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid        c1fac2bc-2156-482f-9249-79b3854acfc0
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=c1fac2bc-2156-482f-9249-79b3854acfc0 ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        c1fac2bc-2156-482f-9249-79b3854acfc0
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=c1fac2bc-2156-482f-9249-79b3854acfc0 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        c1fac2bc-2156-482f-9249-79b3854acfc0
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=c1fac2bc-2156-482f-9249-79b3854acfc0 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-14-generic
uuid        c1fac2bc-2156-482f-9249-79b3854acfc0
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=c1fac2bc-2156-482f-9249-79b3854acfc0 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid        c1fac2bc-2156-482f-9249-79b3854acfc0
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=c1fac2bc-2156-482f-9249-79b3854acfc0 ro  single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        c1fac2bc-2156-482f-9249-79b3854acfc0
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=c1fac2bc-2156-482f-9249-79b3854acfc0 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        c1fac2bc-2156-482f-9249-79b3854acfc0
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=c1fac2bc-2156-482f-9249-79b3854acfc0 ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        c1fac2bc-2156-482f-9249-79b3854acfc0
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=c1fac2bc-2156-482f-9249-79b3854acfc0 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        c1fac2bc-2156-482f-9249-79b3854acfc0
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=c1fac2bc-2156-482f-9249-79b3854acfc0 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        c1fac2bc-2156-482f-9249-79b3854acfc0
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by kansasnoob on 2009-11-07
The most helpful thing would be to see Mint's /boot/grub/menu.lst so if you'd go to Places or Places > Computer and figure out which file system is Mint (shouldn't be hard with only two OS's) then click on it and you'll be asked for your password.

Do not try to make any modification in that file system.

If you're in the right place you'll see a boot folder so double click that and you'll see a grub folder. Again double click that and you will hopefully see a menu.lst.

Copy and paste that menu.lst here.

Remember to right click and unmount the file system icon on the desktop when you're done.

---

### Post by zzyzx1 on 2009-11-07
> **kansasnoob said:**
> The most helpful thing would be to see Mint's /boot/grub/menu.lst so if you'd go to Places or Places > Computer and figure out which file system is Mint 

Here it is. I think the problem is that the Mint partition is not mounting upon boot. I copied the Mint info from this Mint munu.lst and pated into Ubuntu menu.lst and chose Mint OS on reboot. it was pretty ugly and then it crashed.

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default        0

## Graphical boot menu location
gfxmenu=/boot/gfxmenu/linuxmint.message

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/sda6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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
##      altoptions=(single-user) single
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

title        Linux Mint 7 Gloria, kernel 2.6.28-11-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-11-generic root=/dev/sda6 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Linux Mint 7 Gloria, kernel 2.6.28-11-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-11-generic root=/dev/sda6 ro single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Linux Mint 7 Gloria, memtest86+
root        (hd0,5)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title        Ubuntu 9.04, kernel 2.6.28-16-generic (on /dev/sda1)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=c1fac2bc-2156-482f-9249-79b3854acfc0 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title        Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode) (on /dev/sda1)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=c1fac2bc-2156-482f-9249-79b3854acfc0 ro single 
initrd        /boot/initrd.img-2.6.28-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title        Ubuntu 9.04, kernel 2.6.28-15-generic (on /dev/sda1)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=c1fac2bc-2156-482f-9249-79b3854acfc0 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode) (on /dev/sda1)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=c1fac2bc-2156-482f-9249-79b3854acfc0 ro single 
initrd        /boot/initrd.img-2.6.28-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title        Ubuntu 9.04, kernel 2.6.28-14-generic (on /dev/sda1)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=c1fac2bc-2156-482f-9249-79b3854acfc0 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode) (on /dev/sda1)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=c1fac2bc-2156-482f-9249-79b3854acfc0 ro single 
initrd        /boot/initrd.img-2.6.28-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title        Ubuntu 9.04, kernel 2.6.28-13-generic (on /dev/sda1)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=c1fac2bc-2156-482f-9249-79b3854acfc0 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode) (on /dev/sda1)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=c1fac2bc-2156-482f-9249-79b3854acfc0 ro single 
initrd        /boot/initrd.img-2.6.28-13-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda1)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=c1fac2bc-2156-482f-9249-79b3854acfc0 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda1)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=c1fac2bc-2156-482f-9249-79b3854acfc0 ro single 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title        Ubuntu 9.04, memtest86+ (on /dev/sda1)
root        (hd0,0)
kernel        /boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title        Microsoft Windows XP Home Edition
rootnoverify    (hd1,1)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

---

### Post by kansasnoob on 2009-11-07
> Here it is. I think the problem is that the Mint partition is not mounting upon boot. I copied the Mint info from this Mint munu.lst and pated into Ubuntu menu.lst and chose Mint OS on reboot. it was pretty ugly and then it crashed.

So you just couldn't wait a few minutes?

Can you still boot Ubuntu?

---

### Post by zzyzx1 on 2009-11-07
> **kansasnoob said:**
> So you just couldn't wait a few minutes?

Can you still boot Ubuntu?

Ubuntu boots just fine. I just cant get that Mint partition to be recognized/understood by Grub. (I guess)

I ven tried pointing to the UUID of Mint instedd of root=/dev/sda6, sda6 is not understood upon boot.

---

### Post by kansasnoob on 2009-11-07
First of all this was the wrong thing to do:

> So i checked GParted to make sure that my new part was flagged for boot and it was not, so i changed it, still wont boot from Mint.


I'm running a muti-boot and look:

> lance@lance-desktop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000bffde

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2677    21502971    7  HPFS/NTFS
/dev/sda2            3764       19457   126062055    5  Extended
/dev/sda3            2678        3763     8723295   83  Linux
/dev/sda5            3764        4799     8321638+  83  Linux
/dev/sda6            4800        9284    36025731   83  Linux
/dev/sda7            9285       10301     8169021   83  Linux
/dev/sda8           10302       14879    36772753+  83  Linux
/dev/sda9           14880       15032     1228941   82  Linux swap / Solaris
/dev/sda10          15033       17103    16635276   83  Linux
/dev/sda11          17104       17819     5751238+  83  Linux
/dev/sda12          17820       19457    13157203+  83  Linux


Only Windows partitions require a boot flag! 

So you need to correct that and possibly run a file system check on that partition.

You also didn't say anything about having Windows on a separate drive but Mint's menu.lst shows this:

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title Microsoft Windows XP Home Edition
rootnoverify (hd1,1)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

Anyway if you can get that Mint partition straightened out go to terminal and run:

```
sudo grub
```

Then:

```
find /boot/grub/stage1
```

I'd expect the output to be:

> (hd0,0)
(hd0,5)

BTW those are zeros.

So run:

```
root (hd0,5)

```

To use Mint's grub or "root (hd0,0)" to use Ubuntu's grub.

Then run:

```
setup (hd0)
```

And you should see an output like this:

> Checking if "/boot/grub/stage1" exists... **yes**
 Checking if "/boot/grub/stage2" exists... **yes**
 Checking if "/boot/grub/e2fs_stage1_5" exists... **yes**
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...* 15 sectors are embedded.
 **succeeded**
 Running "install /boot/grub/stage1 d (hd0) (hd0)1+15 p (hd0,1)/boot/grub/stage
 2 /boot/grub/menu.lst"... **succeeded**

If that shows it succeeded just run:

```
quit
```

And hopefully now you'll be able to boot Mint, Ubuntu, or Windows.

---

### Post by zzyzx1 on 2009-11-07
> **kansasnoob said:**
> First of all this was the wrong thing to do:

You may be right, but thats not what just fixed it. I changed all references from hd0,5 to the UUID of the Mint partition (including root=UUID=xxx) in the Ubuntu menu.lst and all is well now!

I would LOVE to here some feedback as to how I fixed this, since i was going on a hunch rather than advice... and I am a total noob at this...

I will go over your recommendations, i sure i need some housekeeping done...

Thank you.

---

### Post by Joe Ker1086 on 2009-11-07
Another helpful tool if you want to set up multiple bootable partitions is GAG, It is a graphical user interface for booting that installs at the beginning of your hard drive. I have been told it even does a good job at finding partitions that have been rendered unbootable. I know you fixed the problem but I hope this helps in the future. It can be downloaded at [gag.sourceforge.net]("gag.sourceforge.net")

---

