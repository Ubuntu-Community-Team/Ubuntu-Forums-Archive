---
title: "Ubuntu went bye bye? What happened?"
date: 2009-09-24
forum: New to Ubuntu
---

### Post by ubuntnoob512 on 2009-09-24
Well, I had Ubuntu on my computer and I wanted to install windows XP.

Everybody told me to do this terminal command and copy something to do with grub and put it on a flash drive or email it to myself.

Well I did that, and I installed XP like normal and Ubuntu as people said might happen, Ubuntu disappeared.

In windows, all I see is an 80GB Harddive named C: but I had a 10 GB Linux swap and a 20GB Partion for Linux. 

How do I reinstall "Grub"?

Any help will help.

---

### Post by tchoklat on 2009-09-24
this is a gr8 how to:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

### Post by tchoklat on 2009-09-24
if you installed XP correctly what you want is on this page of the article:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5)

---

### Post by ubuntnoob512 on 2009-09-24
thanks, i will try that walk through

---

### Post by tchoklat on 2009-09-24
specially here:

Load Ubuntu live CD and enter terminal.
To enter the GRUB configuration mode, type in "sudo grub" and press Enter. Then type in the following commands in sequence: 
- root (hd0,0) 
- setup (hd0) 
- quit 
- exit

---

### Post by tchoklat on 2009-09-24
good luck ....

---

### Post by ubuntnoob512 on 2009-09-24
When I try to boot windows Xp afete going throught the instructions, it says: 

error 23: Error while parsing number

press any key to continue...

---

### Post by ubuntnoob512 on 2009-09-24
It still will boot Ubuntu just fine.

Just not XP

---

### Post by mikewhatever on 2009-09-24
If your hdd is 80GB and all you can see is the C partition of the same size, then you must have formatted the Ubuntu partitions. Why don't you boot from the Ubuntu installation cd and post the output of **sudo fdisk -l**.

---

### Post by ubuntnoob512 on 2009-09-24
Wait what?

---

### Post by ubuntnoob512 on 2009-09-24
No that is just in windows that i see that, according to windows there are no other partions besides that one.

---

### Post by pedro3005 on 2009-09-24
That's because Windows can't see EXT3 partitions.

---

### Post by kansasnoob on 2009-09-24
Boot your Ubuntu Live CD and go to Applications > Accessories > Terminal and post the output of this command:

```
sudo fdisk -l
```

BTW, thats a lower case L!

---

### Post by 73ckn797 on 2009-09-24
> **pedro3005 said:**
> That's because Windows can't see EXT3 partitions.


This link has a program that will allow Windows to read ext2 & 3 file systems.
[http://www.fs-driver.org/](http://www.fs-driver.org/)

You would likely have to reboot Windows after installing. Like that is surprising?

---

### Post by pedro3005 on 2009-09-24
Once Windows updated Internet Explorer for me then asked to restart.

---

### Post by kansasnoob on 2009-09-24
> **pedro3005 said:**
> Once Windows updated Internet Explorer for me then asked to restart.

What in the world does that have to do with the OP's problem?

---

### Post by pedro3005 on 2009-09-24
Nothing really. I was just adding to: "You would likely have to reboot Windows after installing. Like that is surprising?", which also didn't have much to do with the problem either.

---

### Post by 73ckn797 on 2009-09-25
Having to restart Windows after an installation is a given, that is why I commented as I did. It also will apply to installing the "ext2" program. There are also some times when a restart is necessary in Ubuntu, though not as often.

---

### Post by Elfy on 2009-09-25
> **ubuntnoob512 said:**
> When I try to boot windows Xp afete going throught the instructions, it says: 

error 23: Error while parsing number

press any key to continue...

This error should be just 
> 
23 : Error while parsing number
    This error is returned if GRUB was expecting to read a number and encountered bad data. 

Boot your ubuntu - open a terminal and run these please

```
cat /boot/grub/menu.lst
sudo fdisk -l
```

---

### Post by ubuntnoob512 on 2009-09-25
After putting commands into termonal:

aaron@aaron-laptop:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=3f0f4124-68ec-4f6d-bb79-960d6ee20e6c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3f0f4124-68ec-4f6d-bb79-960d6ee20e6c

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

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        3f0f4124-68ec-4f6d-bb79-960d6ee20e6c
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=3f0f4124-68ec-4f6d-bb79-960d6ee20e6c ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        3f0f4124-68ec-4f6d-bb79-960d6ee20e6c
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=3f0f4124-68ec-4f6d-bb79-960d6ee20e6c ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        3f0f4124-68ec-4f6d-bb79-960d6ee20e6c
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=3f0f4124-68ec-4f6d-bb79-960d6ee20e6c ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        3f0f4124-68ec-4f6d-bb79-960d6ee20e6c
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=3f0f4124-68ec-4f6d-bb79-960d6ee20e6c ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        3f0f4124-68ec-4f6d-bb79-960d6ee20e6c
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
title Windows Xp
root (hdo,1)
makeactive
chainloader +1
aaron@aaron-laptop:~$ sudo fdisk -l
[sudo] password for aaron: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfe5cfe5c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2295    18434556   83  Linux
/dev/sda2   *        2296       13995    93980250    7  HPFS/NTFS
/dev/sda3           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris
aaron@aaron-laptop:~$ 


I will install the thing you told me to install.

If you haven't figured out already, the only OS I can get into is Ubuntu.

---

### Post by ubuntnoob512 on 2009-09-25
> **73ckn797 said:**
> This link has a program that will allow Windows to read ext2 & 3 file systems.
[http://www.fs-driver.org/](http://www.fs-driver.org/)

You would likely have to reboot Windows after installing. Like that is surprising?



---  


Well, quite frankly, now I cant get into Windows so I cant in stall that "reverse Wine program".

It will be helpful once I get into windows but at the moment, all the programs I have on Linux that aren't clones of ones in Windows are all games.

---

### Post by Elfy on 2009-09-25
This is likely your problem 

root (hdo,1)

Open the file for editing - in a terminal run

```
gksudo gedit /boot/grub/menu.lst
```

Go to the line at the very bottom for your windows install and change the o in that line to a 0

It should read

root (hd0,1)

Edit - no need to install the driver to read the buntu files in windows at the moment.

---

### Post by ubuntnoob512 on 2009-09-25
Wow, how did you know that was the problem. You were right.


I changed it to a 0 and then I saved it.

i will restart now to see if it worked

---

### Post by ubuntnoob512 on 2009-09-25
Wow, thank you

hallelujah

It worked.

The first time I thought it didden't work because I t booted into Ubuntu but the second time I had about 1 second to press Esc to show the boot menu.

Thanks so much.

---

### Post by ubuntnoob512 on 2009-09-25
The only problem with windows right now is I have to search and install Drivers. Gr. I will start with my graphics driver. It is the most annoying problem right now.

---

### Post by Elfy on 2009-09-25
Glad it was that simple in the end, I've had plenty of grub errors myslef so I keep this handy

[http://members.iinet.net.au/~herman546/p15.html#Common_Booting_Errors_and_Some_Possible](http://members.iinet.net.au/~herman546/p15.html#Common_Booting_Errors_and_Some_Possible)
> 
1 second to press Esc to show the boot menu.

You can change this behaviour - open the file to edit again (same one)

Put a # in front of

> hiddenmenu

You can change the time the menu stays before it runs the default by changing 

> timeout 3

Have fun.

---

### Post by ubuntnoob512 on 2009-09-25
thanks a   lot, if I ever have a question I now know where to go.

---

