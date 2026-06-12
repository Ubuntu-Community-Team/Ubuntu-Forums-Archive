---
title: "how do i change boot sequence with dual OS (winxp/ubuntu8.10)..."
date: 2009-01-23
forum: New to Ubuntu
---

### Post by ebineesey on 2009-01-23
SOLVE UPDATE:
Thanks very much for all the help everybody. 



i don't know how to access windows now that i installed ubuntu.

any help?

i know it's probably pretty simple.

also, i'd like to change the default boot to windows, because there are multiple users who are still using windows on this machine-- and now i don't even know how to get back to it...

all on one HDD, different partitions.
see [http://ubuntuforums.org/showthread.php?t=1048866](http://ubuntuforums.org/showthread.php?t=1048866) for more info about the install.

---

### Post by pluckypigeon on 2009-01-23
> **ebineesey said:**
> i don't know how to access windows now that i installed ubuntu.

any help?

i know it's probably pretty simple.

also, i'd like to change the default boot to windows, because there are multiple users who are still using windows on this machine-- and now i don't even know how to get back to it...

all on one HDD, different partitions.
see [http://ubuntuforums.org/showthread.php?t=1048866](http://ubuntuforums.org/showthread.php?t=1048866) for more info about the install.

Can I see your** /boot/grub/menu.lst** file?

---

### Post by ebineesey on 2009-01-23
sure but you need to coach me..... i'm new to this

---

### Post by pluckypigeon on 2009-01-23
> **ebineesey said:**
> sure but you need to coach me..... i'm new to this

cool.

open a terminal.

type:

**gedit /boot/grub/menu.lst **

(i'm assuming you are using ubuntu with gnome)

this will open up your grub menu in gedit. have a look to see if anything is wrong with it.

if you need to edit it you must use "gksudo gedit" instead, gksudo will give you super user privileges 

anyway... if you aren't sure paste it in this thread.

---

### Post by ebineesey on 2009-01-23
ok here it is:

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
# kopt=root=UUID=324b1ce6-f8e6-42bf-8f3c-0105e419955d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=324b1ce6-f8e6-42bf-8f3c-0105e419955d

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
uuid		324b1ce6-f8e6-42bf-8f3c-0105e419955d
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=324b1ce6-f8e6-42bf-8f3c-0105e419955d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		324b1ce6-f8e6-42bf-8f3c-0105e419955d
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=324b1ce6-f8e6-42bf-8f3c-0105e419955d ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		324b1ce6-f8e6-42bf-8f3c-0105e419955d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=324b1ce6-f8e6-42bf-8f3c-0105e419955d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		324b1ce6-f8e6-42bf-8f3c-0105e419955d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=324b1ce6-f8e6-42bf-8f3c-0105e419955d ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		324b1ce6-f8e6-42bf-8f3c-0105e419955d
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by pluckypigeon on 2009-01-23
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1


this is where the clue is

---

### Post by pluckypigeon on 2009-01-23
replace hd0,0 with your windows partition

hd0,0 is == hda1
hd0,1 is == hda2
 and so forth

e.g

vista on hda2 =

title Windows Vista
root (hd0,1)
makeactive
chainloader +1

---

### Post by ebineesey on 2009-01-23
OK-- sorry to be such a newbie, but i'm kinda lost here...

i have this:
cat /etc/fstab
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x56f056f0

Device Boot Start End Blocks Id System
/dev/sda1 * 1 12748 102398278+ 7 HPFS/NTFS
/dev/sda2 12749 60801 385985722+ 5 Extended
/dev/sda5 59829 60801 7815622+ 82 Linux swap / Solaris
/dev/sda6 47670 59827 97659103+ 83 Linux
/dev/sda7 12749 47668 280494837 83 Linux

Partition table entries are not in disk order

i don't see any hda like you said, they are sda... does that matter?

---

### Post by pluckypigeon on 2009-01-23
> **ebineesey said:**
> OK-- sorry to be such a newbie, but i'm kinda lost here...

i have this:
cat /etc/fstab
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x56f056f0

Device Boot Start End Blocks Id System
/dev/sda1 * 1 12748 102398278+ 7 HPFS/NTFS
/dev/sda2 12749 60801 385985722+ 5 Extended
/dev/sda5 59829 60801 7815622+ 82 Linux swap / Solaris
/dev/sda6 47670 59827 97659103+ 83 Linux
/dev/sda7 12749 47668 280494837 83 Linux

Partition table entries are not in disk order

i don't see any hda like you said, they are sda... does that matter?

No that doesn't matter. 

If it's /dev/sda1 then that should be (hd0,0)

---

### Post by ebineesey on 2009-01-24
i hate that i don't know what's going on here...

can you just spell it out for me from the start?

To load windows, instead of ubuntu, by default (ie, when the computer is initially turned on), i do the following:

step 1: .........


(thank you)

---

### Post by gyaneshwar on 2009-01-24
I would add some more things:

1) Start Terminal from Applications-accessories menu
2) Type in terminal

   sudo /boot/grub/menu.lst
   type your password

3) on the last line add hash

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu
so that always you can see what are your booting

4) Change time of booting to something reasonable

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 3

Like 10 seconds - so that you just need to explain to people to move cursor to Windows and press enter (during this 10 sec)

5) Copy following lines to the end of your file (menu.lst)

# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1

6) remove #

title Windows 95/98/NT/2000
root (hd0,0)
makeactive
chainloader +1

number hd0,0 is correct for your hard

7) if you want to have that computer always boot into windoz so that you have to press to come to ubuntu edit following line

# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default 0

This number 0 should be the number in which line your windows is starting. For eg. if you paste 6) at the end of file than your
line is 
default 5

Hope this helps

---

### Post by leonardo_neo on 2009-01-24
> **ebineesey said:**
> i hate that i don't know what's going on here...

can you just spell it out for me from the start?

To load windows, instead of ubuntu, by default (ie, when the computer is initially turned on), i do the following:

step 1: .........


(thank you)

Well as far as I understand your question, I assume that you want to set windows as default OS on boot up? 

Well, since you are a newbie, I guess you should install a GUI for this purpose. 

Startup manager is a good tool for that. 

Go to Add/Remove Application. On top drop down box, select "All available application" in next to show. Then in search box type 'starup'.......You will see an application called "StartUp-Manager". Check the box next to that and then click apply changes. This way you will install this application.

Then find this application in your software list. Most probably you will find this in 'system'.

Open it, it will give a very easy GUI. There you will see an option for default operating system. Select windows there, and that's it, you are done! 

Here is the screenshot images of startup manager

[http://web.telia.com/~u88005282/sum/screenshots.html](http://web.telia.com/~u88005282/sum/screenshots.html)

I hope this helps you. 

Best of luck :)

---

### Post by 73ckn797 on 2009-01-24
If everything else does not work, try this:

Go to Applications/Accessories/terminal.
Open Terminal from there.
enter:
```
gksudo gedit /boot/grub/menu.lst
```

You will have to enter your user password.

When the "menu.lst" opens look at the first section , at the top of the file info.
You should see something as follows:
```

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0
```

replace the last number "0" to "saved". Without the quotes.

Then look at the last section (at the bottom of the "menu.lst") and you will need to add the following:
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows
root        (hd0,0)
savedefault
makeactive
chainloader    +1
```

Just copy and paste this info into the grub menu.lst at the very end.

Save the file and when you re-boot into the grub menu it should default to Windows. It will also allow you time to choose Ubuntu. If you just restart the computer and walk away, Windows should load automatically.

---

### Post by leonardo_neo on 2009-01-24
One important thing which I forgot to mention, If you are using StartUp Manager, Please ***_do not_*** slect "time-out" time as 'zero'. Else you will probably not be able to boot Ubuntu again, if you select Windows as your default OS.

Always keep it more than 5 seconds, so that you have enough time to boot Ubuntu, in case you want that.

---

### Post by ebineesey on 2009-01-24
well that seemed promising (thank you) but heres the new problem...

windows isn't one of the options in the startup manager

i only see the following kinds of ubuntu:
(default first)

ubuntu 8.10, kernel 2.6.27-9-generic
ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
ubuntu 8.10, kernel 2.6.27-7-generic
ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
ubuntu 8.10, memtest86+
last used


any ideas?

---

### Post by 73ckn797 on 2009-01-24
> **ebineesey said:**
> well that seemed promising (thank you) but heres the new problem...

windows isn't one of the options in the startup manager

i only see the following kinds of ubuntu:
(default first)

ubuntu 8.10, kernel 2.6.27-9-generic
ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
ubuntu 8.10, kernel 2.6.27-7-generic
ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
ubuntu 8.10, memtest86+
last used


any ideas?


You may have posted this and not seen my recommendations.

---

### Post by ebineesey on 2009-01-24
true, i'm trying your thing right now

do i paste that last bit before or after this:


## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		324b1ce6-f8e6-42bf-8f3c-0105e419955d
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=324b1ce6-f8e6-42bf-8f3c-0105e419955d ro quiet splash vga=795 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		324b1ce6-f8e6-42bf-8f3c-0105e419955d
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=324b1ce6-f8e6-42bf-8f3c-0105e419955d ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		324b1ce6-f8e6-42bf-8f3c-0105e419955d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=324b1ce6-f8e6-42bf-8f3c-0105e419955d ro quiet splash vga=795 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		324b1ce6-f8e6-42bf-8f3c-0105e419955d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=324b1ce6-f8e6-42bf-8f3c-0105e419955d ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		324b1ce6-f8e6-42bf-8f3c-0105e419955d
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by 73ckn797 on 2009-01-24
> **ebineesey said:**
> true, i'm trying your thing right now

do i paste that last bit before or after this:


## ## End Default Options ##

title        Ubuntu 8.10, kernel 2.6.27-9-generic
uuid        324b1ce6-f8e6-42bf-8f3c-0105e419955d
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=324b1ce6-f8e6-42bf-8f3c-0105e419955d ro quiet splash vga=795 
initrd        /boot/initrd.img-2.6.27-9-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid        324b1ce6-f8e6-42bf-8f3c-0105e419955d
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=324b1ce6-f8e6-42bf-8f3c-0105e419955d ro  single
initrd        /boot/initrd.img-2.6.27-9-generic

title        Ubuntu 8.10, kernel 2.6.27-7-generic
uuid        324b1ce6-f8e6-42bf-8f3c-0105e419955d
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=324b1ce6-f8e6-42bf-8f3c-0105e419955d ro quiet splash vga=795 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid        324b1ce6-f8e6-42bf-8f3c-0105e419955d
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=324b1ce6-f8e6-42bf-8f3c-0105e419955d ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, memtest86+
uuid        324b1ce6-f8e6-42bf-8f3c-0105e419955d
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


After that section, as I stated, At the end of the menu.lst file.

---

### Post by ebineesey on 2009-01-24
it isn't working...
i tried editing it like you said but on restart it put me back here (not windows)


here's what the menu.lst looks like now:

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
default		saved

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

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
# kopt=root=UUID=324b1ce6-f8e6-42bf-8f3c-0105e419955d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=324b1ce6-f8e6-42bf-8f3c-0105e419955d

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
# defoptions=quiet splash vga=795

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
uuid		324b1ce6-f8e6-42bf-8f3c-0105e419955d
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=324b1ce6-f8e6-42bf-8f3c-0105e419955d ro quiet splash vga=795 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		324b1ce6-f8e6-42bf-8f3c-0105e419955d
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=324b1ce6-f8e6-42bf-8f3c-0105e419955d ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		324b1ce6-f8e6-42bf-8f3c-0105e419955d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=324b1ce6-f8e6-42bf-8f3c-0105e419955d ro quiet splash vga=795 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		324b1ce6-f8e6-42bf-8f3c-0105e419955d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=324b1ce6-f8e6-42bf-8f3c-0105e419955d ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		324b1ce6-f8e6-42bf-8f3c-0105e419955d
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows
root        (hd0,0)
savedefault
makeactive
chainloader    +1
```

---

### Post by MobiusCoffee on 2009-01-24
edit:

Sorry, my suggestion seems to of already been stated.

---

### Post by 73ckn797 on 2009-01-24
> **ebineesey said:**
> it isn't working...
i tried editing it like you said but on restart it put me back here (not windows)


here's what the menu.lst looks like now:

```
## ## End Default Options ##

title        Ubuntu 8.10, kernel 2.6.27-9-generic
uuid        324b1ce6-f8e6-42bf-8f3c-0105e419955d
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=324b1ce6-f8e6-42bf-8f3c-0105e419955d ro quiet splash vga=795 
initrd        /boot/initrd.img-2.6.27-9-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid        324b1ce6-f8e6-42bf-8f3c-0105e419955d
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=324b1ce6-f8e6-42bf-8f3c-0105e419955d ro  single
initrd        /boot/initrd.img-2.6.27-9-generic

title        Ubuntu 8.10, kernel 2.6.27-7-generic
uuid        324b1ce6-f8e6-42bf-8f3c-0105e419955d
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=324b1ce6-f8e6-42bf-8f3c-0105e419955d ro quiet splash vga=795 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid        324b1ce6-f8e6-42bf-8f3c-0105e419955d
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=324b1ce6-f8e6-42bf-8f3c-0105e419955d ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, memtest86+
uuid        324b1ce6-f8e6-42bf-8f3c-0105e419955d
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows
root        (hd0,0)
savedefault
makeactive
chainloader    +1
```


Try this:

Insert the following info after the first lines of each of the grub Ubuntu selections:


```
root        (hdo,5)
```

To look like the following:

```
title        Ubuntu 8.10, kernel 2.6.27-9-generic
root           (hd0,5)
uuid        324b1ce6-f8e6-42bf-8f3c-0105e419955d
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=324b1ce6-f8e6-42bf-8f3c-0105e419955d ro quiet splash vga=795 
initrd        /boot/initrd.img-2.6.27-9-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root           (hd0,5)
uuid        324b1ce6-f8e6-42bf-8f3c-0105e419955d
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=324b1ce6-f8e6-42bf-8f3c-0105e419955d ro  single
initrd        /boot/initrd.img-2.6.27-9-generic

title        Ubuntu 8.10, kernel 2.6.27-7-generic
root           (hd0,5)
uuid        324b1ce6-f8e6-42bf-8f3c-0105e419955d
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=324b1ce6-f8e6-42bf-8f3c-0105e419955d ro quiet splash vga=795 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root           (hd0,5)
uuid        324b1ce6-f8e6-42bf-8f3c-0105e419955d
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=324b1ce6-f8e6-42bf-8f3c-0105e419955d ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, memtest86+
root           (hd0,5)
uuid        324b1ce6-f8e6-42bf-8f3c-0105e419955d
kernel        /boot/memtest86+.bin
quiet
```
See what that will do for you. If it does not work change it to (hd0,6).

---

### Post by gyaneshwar on 2009-01-24
just change 
default saved
 to
default 5

---

