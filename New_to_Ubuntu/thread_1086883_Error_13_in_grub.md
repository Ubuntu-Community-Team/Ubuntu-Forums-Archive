---
title: "Error 13 in grub"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by bibimig on 2009-03-04
I have three diferent hard drives, and i dont know what's the problem with my grub.lst.

my fdisk -l

Disco /dev/sda: 200.0 GB, 200049647616 bytes
255 cabezas, 63 sectores/pista, 24321 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x05a79a88

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1       24320   195350368+   7  HPFS/NTFS

Disco /dev/sdb: 500.1 GB, 500107862016 bytes
255 cabezas, 63 sectores/pista, 60801 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xf27ff3cc

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1   *           1       59322   476503933+  83  Linux
/dev/sdb2           59323       60801    11880067+   5  Extendida
/dev/sdb5           59323       60801    11880036   82  Linux swap / Solaris

Disco /dev/sdc: 122.9 GB, 122942324736 bytes
164 cabezas, 1 sectores/pista, 1464156 cilindros
Unidades = cilindros de 164 * 512 = 83968 bytes
Identificador de disco: 0x95e2608e

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdc1   *           1     1464144   120059807+   7  HPFS/NTFS

my menu lst

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
# kopt=root=UUID=98afe77c-7539-49f4-8213-7a51f501bef5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=98afe77c-7539-49f4-8213-7a51f501bef5

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		98afe77c-7539-49f4-8213-7a51f501bef5
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=98afe77c-7539-49f4-8213-7a51f501bef5 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		98afe77c-7539-49f4-8213-7a51f501bef5
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=98afe77c-7539-49f4-8213-7a51f501bef5 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		98afe77c-7539-49f4-8213-7a51f501bef5
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=98afe77c-7539-49f4-8213-7a51f501bef5 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		98afe77c-7539-49f4-8213-7a51f501bef5
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=98afe77c-7539-49f4-8213-7a51f501bef5 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		98afe77c-7539-49f4-8213-7a51f501bef5
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=98afe77c-7539-49f4-8213-7a51f501bef5 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		98afe77c-7539-49f4-8213-7a51f501bef5
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=98afe77c-7539-49f4-8213-7a51f501bef5 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		98afe77c-7539-49f4-8213-7a51f501bef5
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
root		(hd0,0)  **I think the fail is here**
savedefault
makeactive
chainloader	+1

---

### Post by ubername on 2009-03-04
What is the problem: how do you get error 13?

---

### Post by ubername on 2009-03-04
Having looked at your menu.lst, you should try root (hd1,0) or root (hd2,0) for your windows entry or, depending on how your other drives are set up, change the last number in the brackets to indicate which partition of the hard drive you have your other OS installed

---

### Post by bibimig on 2009-03-05
Thank you for the answer, i tried (hd1,0) and (hd2,0) before, but that didn't solve my problem, i can't boot the windows partition, that is on this hd:

 Disco /dev/sda: 200.0 GB, 200049647616 bytes
255 cabezas, 63 sectores/pista, 24321 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x05a79a88.

and this hd is only for data storing:

Disco /dev/sdc: 122.9 GB, 122942324736 bytes
164 cabezas, 1 sectores/pista, 1464156 cilindros
Unidades = cilindros de 164 * 512 = 83968 bytes
Identificador de disco: 0x95e2608e

and the other hd of 500 gb is for the ubuntu system, that works right,  and boot fine.

Thanks a lot, and excuse my english level is very poor.

---

