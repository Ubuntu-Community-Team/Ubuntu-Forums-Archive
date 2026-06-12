---
title: "GRUB + kernel = generic?."
date: 2009-09-06
forum: New to Ubuntu
---

### Post by sunrex on 2009-09-06
I'm trying to boot into my custom kernel (well, custom in options).

I am using grub 0.97, since that is what ubuntu installed.

Upon removing ALL other entries from the menu.lst, and putting in my custom kernel - it still boots into a generic kernel...

Is there a different option I need to change?.

My original menu.lst:

```
## ## End Default Options ##  
 
title    Ubuntu 9.04, kernel 2.6.28-15-generic
uuid     60dd6148-0971-449c-b2a6-fbeea43a929a
kernel   /vmlinuz-2.6.28-15-generic root=UUID=3a313810-2850-45cd-a928-39704a5e3ccf ro quiet splash
initrd   /initrd.img-2.6.28-15-generic
quiet
 
title    Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid     60dd6148-0971-449c-b2a6-fbeea43a929a
kernel   /vmlinuz-2.6.28-15-generic root=UUID=3a313810-2850-45cd-a928-39704a5e3ccf ro single
initrd   /initrd.img-2.6.28-15-generic
 
title    Ubuntu 9.04, kernel 2.6.28-11-generic
uuid     60dd6148-0971-449c-b2a6-fbeea43a929a
kernel   /vmlinuz-2.6.28-11-generic root=UUID=3a313810-2850-45cd-a928-39704a5e3ccf ro quiet splash
initrd   /initrd.img-2.6.28-11-generic
quiet
 
title    Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid     60dd6148-0971-449c-b2a6-fbeea43a929a
kernel   /vmlinuz-2.6.28-11-generic root=UUID=3a313810-2850-45cd-a928-39704a5e3ccf ro single
initrd   /initrd.img-2.6.28-11-generic
 
title    Ubuntu 9.04, memtest86+
uuid     60dd6148-0971-449c-b2a6-fbeea43a929a
kernel   /memtest86+.bin
quiet
 
### END DEBIAN AUTOMAGIC KERNELS LIST
```

My current menu.lst:

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
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=3a313810-2850-45cd-a928-39704a5e3ccf ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=60dd6148-0971-449c-b2a6-fbeea43a929a

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
# defoptions=quiet splash vga=775

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
title           Debian GNU/Linux, RT Kernel
uuid		60dd6148-0971-449c-b2a6-fbeea43a929a
kernel          /vmlinuz-2.6.26.8-rt16 root=UUID=3a313810-2850-45cd-a928-39704a5e3ccf
initrd          /initrd.img-2.6.26.8-rt16
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

My boot folder:

```
root@DDC-ONE:/# ls -l /boot
total 37931
-rw-r--r-- 1 root root  529118 2009-04-16 20:41 abi-2.6.28-11-generic
-rw-r--r-- 1 root root  528185 2009-08-18 13:23 abi-2.6.28-15-generic
-rw-r--r-- 1 root root   87564 2009-09-05 13:44 config-2.6.26.8-rt16
-rw-r--r-- 1 root root   96795 2009-04-16 20:41 config-2.6.28-11-generic
-rw-r--r-- 1 root root   96768 2009-08-18 13:23 config-2.6.28-15-generic
drwxr-xr-x 3 root root    1024 2009-09-05 17:41 grub
-rw-r--r-- 1 root root 7644947 2009-09-05 13:45 initrd.img-2.6.26.8-rt16
-rw-r--r-- 1 root root 7884315 2009-09-05 17:41 initrd.img-2.6.28-11-generic
-rw-r--r-- 1 root root 7896913 2009-09-05 17:41 initrd.img-2.6.28-15-generic
drwx------ 2 root root   12288 2009-08-28 06:39 lost+found
-rw-r--r-- 1 root root  128796 2009-03-27 10:15 memtest86+.bin
-rw-r--r-- 1 root root 1222882 2009-09-05 13:44 System.map-2.6.26.8-rt16
-rw-r--r-- 1 root root 1456232 2009-04-16 20:41 System.map-2.6.28-11-generic
-rw-r--r-- 1 root root 1450109 2009-08-18 13:23 System.map-2.6.28-15-generic
-rw-r--r-- 1 root root    1074 2009-04-16 20:43 vmcoreinfo-2.6.28-11-generic
-rw-r--r-- 1 root root    1074 2009-08-18 13:25 vmcoreinfo-2.6.28-15-generic
-rw-r--r-- 1 root root 2800704 2009-09-05 13:44 vmlinuz-2.6.26.8-rt16
-rw-r--r-- 1 root root 3501776 2009-04-16 20:41 vmlinuz-2.6.28-11-generic
-rw-r--r-- 1 root root 3491024 2009-08-18 13:23 vmlinuz-2.6.28-15-generic
root@DDC-ONE:/#
```

My fdisk:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcbe95fc3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          12       96358+  83  Linux
/dev/sda2              13       60801   488287642+   5  Extended
/dev/sda5              13          24       96358+  82  Linux swap / Solaris
/dev/sda6              25        2456    19535008+  83  Linux
/dev/sda7            2457       60801   468656181   83  Linux
tyler@DDC-ONE:~$ 


```

I'm at a loss here.

---

### Post by hal10000 on 2009-09-06
your menu.lst looks ok so far. Did you try [COLOR="Red"]sudo update-grub[/COLOR], whic would bring you back the other menu entries, but at least you would have correct setting for you custom kernel too. You could then again comment out the other entries you don't need.

---

### Post by sunrex on 2009-09-06
> **hal10000 said:**
> your menu.lst looks ok so far. Did you try [COLOR="Red"]sudo update-grub[/COLOR], whic would bring you back the other menu entries, but at least you would have correct setting for you custom kernel too. You could then again comment out the other entries you don't need.

I did, but nothing changed with menu.lst.

---

### Post by jeppewinther on 2009-09-06
Are you pulling up the menu to choose which kernel to boot?
What options are you given there?

You're given 3 seconds to press ESC to access it with your current configuration, you can alter the value of "timeout" and comment out "hiddenmenu" to make it easier to spot.

---

### Post by sunrex on 2009-09-06
> **jeppewinther said:**
> Are you pulling up the menu to choose which kernel to boot?
What options are you given there?

You're given 3 seconds to press ESC to access it with your current configuration, you can alter the value of "timeout" and comment out "hiddenmenu" to make it easier to spot.

I can't, I'm using a VNC server to connect.

---

### Post by hal10000 on 2009-09-06
Did you try to get it directly from the grub commandline prompt?
You have to press the ESC key when at boot time your grub menu appears to get to the grub prompt .

**I assume you have separate /boot partition, it's in /dev/sda1, and your system root ([COLOR="Red"][B] / **[/COLOR]) is in /dev/sda6, am i right?[/B]
If so, then on the grub prompt you have to type in this order: (you will get a success message after each ENTER)

1.) [COLOR="Red"]root (hd0,0)[/COLOR] Press the ENTER key. 
2.) [COLOR="Red"]kernel /[/COLOR] [TAB] [TAB] (i guess you need to press the TAB key two times after typing the slash /). Then there should appear a list of all bootable kernel images that are available,where hopefully your custom kernel is among them. Type in the correct kernel image name and append [COLOR="Red"]root=/dev/sda6 ro[/COLOR] Then press ENTER.
3.) Next is to type [COLOR="Red"]initrd /[/COLOR] [TAB] TAB]. You will again see a list of valid initrd files. Type in the correct one and press ENTER
4.) Type [COLOR="Red"]boot [/COLOR] and press ENTER

On success you will now boot your custom kernel.

Good luck

---

