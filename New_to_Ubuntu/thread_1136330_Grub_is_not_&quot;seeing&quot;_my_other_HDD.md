---
title: "Grub is not &quot;seeing&quot; my other HDD??"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by R@inm@n on 2009-04-24
I have two HDD's in this computer, one with Windows XP and the other with Linux Jaunty Jackalope.
Before I installed JJ, Grub used to give me the option of booting either WinXP or Linux.
Now, it doesn't give me the option, it doesn't see the other HDD with Windows on it at all.

What is the solution to this please?

Thanks,

R.

---

### Post by R@inm@n on 2009-04-25
Hmmm...no answers? No solution?


  R.

---

### Post by adult swim on 2009-04-25
what do these commands output?
```
sudo fdisk -l

cat /boot/grub/menu.lst
```

---

### Post by R@inm@n on 2009-04-25
rainman@Toxic:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1dce1dcd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19083   153284166   83  Linux
/dev/sda2           19084       19457     3004155    f  W95 Ext'd (LBA)
/dev/sda5           19084       19457     3004123+  82  Linux swap / Solaris
rainman@Toxic:~$ 


And:

rainman@Toxic:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=63345bad-64ce-4784-ab75-19555b81ebfb ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=63345bad-64ce-4784-ab75-19555b81ebfb

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		63345bad-64ce-4784-ab75-19555b81ebfb
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=63345bad-64ce-4784-ab75-19555b81ebfb ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		63345bad-64ce-4784-ab75-19555b81ebfb
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=63345bad-64ce-4784-ab75-19555b81ebfb ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		63345bad-64ce-4784-ab75-19555b81ebfb
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
rainman@Toxic:~$ 


OK?   


R.

---

### Post by adult swim on 2009-04-25
is your other disk plugged into to the computer?

---

### Post by R@inm@n on 2009-04-25
Yes, of course.


R.

---

### Post by Seks on 2009-04-25
I have the same problem, a disk with XP is plugged in and the only way to access or even see that it exists is to set it to boot from the bios

---

### Post by R@inm@n on 2009-04-25
I can boot into either HDD if I disconnect the power to the one I don't want to boot. In other words, if I want to boot into Ubuntu, I disconnect the power from the Win XP HDD by pulling the 12v plug.
 
When I was running Ubuntu 8.04 the grub menu would give me the option of which OS to boot up, but Jaunty isn't doing that.

It's a pita to have to disconnect the power from the HDD's when I want to boot to either OS, and i'm sure that it is a relatively easy fix to get Grub to give me the options automatically at computer startup, but as a Linux n00b I just don't know how to do it.

Any help would be appreciated ...  

Thanks,


R.

---

### Post by adult swim on 2009-04-25
i dont really know anything about it but do you have the master/slave situation set up right?

---

### Post by R@inm@n on 2009-04-25
Yes, all correctly set...and it used to work fine on 8.04 Hardy Heron.  I think that it's a Grub problem, imo.

A setting in Grub that I need to 'tweak' but I don't know which setting...so that grub gives me the option to boot either OS.


 R.

---

### Post by adult swim on 2009-04-25
well to boot the second hard drive, you could run this
```
gksu gedit /boot/grub/menu.lst
``` and paste this in the text editor that pops up```
title Windows
rootnoverify	(hd1,0)
map	(hd0) (hd1)
map	(hd1) (hd0)
chainloader	+1
``` then save and close the file

however, i dont know that this will work because above, when you posted the results of the fdisk -l command, it only shows one hard drive connected to the computer

---

### Post by R@inm@n on 2009-04-26
No, you are correct, it did not work.
I now have a "Window" at the top of the list, but selecting it gives me an error.


R.

---

### Post by R@inm@n on 2009-04-27
I think i'll go back to Hardy...this latest release is too full of bugs.

Thanks for the help....


  R.

---

### Post by R@inm@n on 2009-05-01
I re-installed Jaunty, thinking that a new install *may* fix any problems that I had with my first attempt.
No change, Grub still can't 'see' my slave HDD with Win XP Pro on it.
I have to go into the bios and change the HDD boot sequence to get the correct OS to boot up, which is a pita, but nevertheless it will have to do until I can get the Grub menu sorted out properly.
I've seen quite a few other posts like mine in the forums, it seems like Jaunty Grub is glitched...:(

Anyways, thanks for the help, i'll just have to get used to changing the boot sequence every time I want to change operating systems...


R.

---

### Post by Miljet on 2009-05-01
I think that the first problem is to figure why your system is not seeing your second disk. Are you running SATA or IDE disks? If IDE, you might check the jumpers to see if they are set to master/slave or autoselect. I haven't played with any SATA drives, but think they did away with jumpers.

Another thing I would try is to swap the data cables on the drives to see if that changes the output of "sudo fdisk -l." Once you get that output to show both drives, it will be a simple matter to reinstall or correct GRUB.

---

### Post by R@inm@n on 2009-05-02
SOLVED.  

It's ok, I solved this myself by re-installing Jaunty from a DVD [3rd time] and got Grub working and now I have the option to boot into Ubuntu or Win XP.

It took some working out, but I did it...finally.:)


  R.

---

