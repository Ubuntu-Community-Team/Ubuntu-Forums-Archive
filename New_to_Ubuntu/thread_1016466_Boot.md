---
title: "Boot"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by Eddie002Fast on 2008-12-19
I used too have Linux Ubuntu on my hard drive and it showed it in a list of operating systems! with my new install i dont see an operating system list when i boot up my comp only grub loading screen then straight to the load screen then desktop is there a way i can fix this? I miss the operating system list when i boot up my comp!

---

### Post by bumanie on 2008-12-19
Please post the output of > sudo fdisk -l so that we can see what OSes are installed and to which partitions.

---

### Post by keplerspeed on 2008-12-19
You say you have a new install? was this a linux install or a windoes install? If its a linux install we can edit your /boot/grub/menu.lst or if it was a windows install we can setup grub, since windoes eats grub.

---

### Post by Eddie002Fast on 2008-12-20
Linux Ubuntu 8.10 was the new OS I installed on my hard drive. i had Linux Ubuntu 8.04 on there before and it showed a list of Operating systems when i booted up my comp. It would show for example 

Linux Kernel version ubuntu 8.04
Linux kernel version ubuntu 8.04 (safe mode I think)
other operating systems

thats what my list used too look like when I had Linux Ubuntu 8.04 onstalled then i did a fresh install of Linux Ubuntu 8.10 and now it just says

grub loading 3...2....1....

then it goes too the loading screen and then my desktop bypassing the List of operating systems :(

---

### Post by BDNiner on 2008-12-20
Since it was a fresh install of Ubuntu did you install over all the data on your Hard Disk. Can you post the output of Bumanie's command so that we can see if there are other partitions on your system with operating systems on them.

---

### Post by caljohnsmith on 2008-12-20
Have you tried pressing "ESC" on start up to see if that gives you the Grub menu? If not, please also post:
```
cat /boot/grub/menu.lst
```

---

### Post by Eddie002Fast on 2008-12-20
Linux Ubuntu 8.10 only (during partition set-up i did 100% (entire disk) )

---

### Post by hexanol on 2008-12-20
Well, if you installed your new operating system on the entire disk, that means there's only one operating system now. Still, I guess the GRUB menu list should show since even if you have only one operating system installed on your computer, you should still see the GRUB menu list showing different kernel image to pick from (and memtest86+). Please post the result of "sudo fdisk -l" and "cat /boot/grub/menu.lst".

---

### Post by BDNiner on 2008-12-20
oh ok, then the other OSes have been erased from the harddisk.

---

### Post by Eddie002Fast on 2008-12-20
Before

Linux Kernel (version) Ubuntu 8.04
Linux Kernel (version) Ubuntu 8.04 (another mode)
other operating systems

and memtest too i remember

After

grub loading 3...2...1...

Ubuntu load screen then Desktop :(

---

### Post by caljohnsmith on 2008-12-20
So have you tried pressing ESC yet on start up to see if that gives you the Grub menu?

---

### Post by Eddie002Fast on 2008-12-20
sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18696   150175588+  83  Linux
/dev/sda2           18697       19452     6072570    5  Extended
/dev/sda5           18697       19452     6072538+  82  Linux swap / Solaris

cat /boot/grub/menu.lst

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
# kopt=root=UUID=725895da-56e2-4db7-8404-7f86f32f4e14 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=725895da-56e2-4db7-8404-7f86f32f4e14 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=725895da-56e2-4db7-8404-7f86f32f4e14 ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=725895da-56e2-4db7-8404-7f86f32f4e14 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=725895da-56e2-4db7-8404-7f86f32f4e14 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

Somethings wrong I can feel it LOL :D

---

### Post by caljohnsmith on 2008-12-20
OK, how about doing:
```
gksudo gedit /boot/grub/menu.lst
```
And put a pound sign # in front of the "hiddenmenu" line like:
```
# hiddenmenu
```
Reboot, and you should get the Grub menu. Let us know how it goes.

---

### Post by 3rdalbum on 2008-12-20
No, there's nothing wrong. When you install Ubuntu as a dual-boot, you get the list of operating systems. When you install Ubuntu as the only operating system, you don't get the list.

If you really want the list, just remove the word "hiddenmenu" from /boot/grub/menu.lst, and put the "timeout" number higher (like 10 seconds).

---

### Post by Eddie002Fast on 2008-12-20
OMG! LOL! THX! You were right! ESC Key!!! :D

Grub Loading 3...2...1...

in the middle of that I hit the ESC Key and it took me too my operating system list along with memtest and other operating systems option on there yay!!!

Thanx a ton guys!

:D :) :popcorn::guitar::KS

---

### Post by Eddie002Fast on 2008-12-20
ok I tried the ESC button then it showed the Grub list of OSes and memtest then i rebooted and i had too hit ESC again......it used too just take me too the grub list everytime without having too hit ESC Key

The list looks like this EXACTLY:

ubuntu 8.04.1, Kernel 2.6.24-22-generic
ubuntu 8.04.1, Kernel 2.6.24-22-generic (recovery mode)
ubuntu 8.04.1, Kernel 2.6.22-14-generic
ubuntu 8.04.1, Kernel 2.6.22-14-generic (recovery mode)
ubuntu 8.04.1, memtest+

:D

---

### Post by Eddie002Fast on 2008-12-20
> **caljohnsmith said:**
> OK, how about doing:
```
gksudo gedit /boot/grub/menu.lst
```
And put a pound sign # in front of the "hiddenmenu" line like:
```
# hiddenmenu
```
Reboot, and you should get the Grub menu. Let us know how it goes.

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
# kopt=root=UUID=725895da-56e2-4db7-8404-7f86f32f4e14 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=725895da-56e2-4db7-8404-7f86f32f4e14 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=725895da-56e2-4db7-8404-7f86f32f4e14 ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=725895da-56e2-4db7-8404-7f86f32f4e14 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=725895da-56e2-4db7-8404-7f86f32f4e14 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by Eddie002Fast on 2008-12-20
caljohnsmith which hiddenmenu line do i put the # in front of i dont wanna mess it up hehe thx in advance :D

---

### Post by hexanol on 2008-12-20
The one not already starting with a '#'.
All lines starting with a '#' are comments and thus ignored. If you put a '#' in front of a line starting already with a '#', it won't do anything.

---

### Post by Eddie002Fast on 2008-12-20
w00t thx guys ok now my grub list shows everytime but now the timer is way too fast how do I change that......or can I remove the timer all together? 

Thx! :D

---

### Post by Eddie002Fast on 2008-12-20
How do I change my Grub Menu timer settings? To be honost if I could i would love too not have a timer and have that screen stay there till i chose which 1 i wanted too load :D

---

### Post by caljohnsmith on 2008-12-20
I've never tried it before, but you could try commenting out the "timeout" line near the top of the menu.lst by putting a pound sign in front of it:
```
# timeout 3
```
See if that works, and if not, just change the timeout to say 1000 or a big number.

---

### Post by hexanol on 2008-12-20
Look for the 'timeout' options in your menu.lst file (in your case, that's just before the 'hiddenmenu' options). Change the value to something bigger than 3 seconds.

For more information, you can also look at the [grub manual]("http://www.gnu.org/software/grub/manual/grub.html"). It has a lot of informations but can be a bit hard to understand depending on your knowledge.

---

### Post by Eddie002Fast on 2008-12-20
ok problem solved!

gksudo gedit /boot/grub/menu.lst

hiddenmenu (changed to #hiddenmenu)

timer 3  (changed to #timer 3)

the timer setting is in secs and 0-whatever would be the timer but if you put # in front of it and leave the default secs (3) then it will not use the timer......Take all the time you need LOL! :D

---

