---
title: "Noob looking for GRUB help"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by ChemShock on 2009-05-10
I went from wubi to doing a fresh Jaunty dual boot with XP install. Now since I cant use XP to configure the GRUB, how do I do the following tasks 'cause everything looks Greek to me.

1. Have XP appear on the same list as Ubuntu, Recovery Mode, and Memtest.

2. The XP I want is "Microsoft Windows XP Home Edition" not the default generic Windows(default) title.

3. It would be nice to also change the timers. Not needed but it be nice.

If you can help me that be great! On a separate note, is a power-on password a bit of an overkill when it come to security for a college student?

---

### Post by taurus on 2009-05-10
Boot into Ubuntu.  Then, open a terminal and edit /boot/grub/menu.lst.

Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```
Change the **timeout 3** to whatever seconds you want.  Then scroll down to the bottom and change the **title** for windows to whatever you want to call it.

Save it and reboot.

---

### Post by ChemShock on 2009-05-10
I got the timeout. Now I'm lost on setting up Windows on the same list as Ubuntu. Also, rid the windows(default) option.

Is it all possible?

---

### Post by 73ckn797 on 2009-05-10
Post the results of ```
gksudo gedit /boot/grub/menu.lst
``` and maybe we can help a little more.

---

### Post by ChemShock on 2009-05-11
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
timeout		15

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
# kopt=root=UUID=5e2074f2-dc7e-4301-be3f-a22e06061956 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5e2074f2-dc7e-4301-be3f-a22e06061956

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
uuid		5e2074f2-dc7e-4301-be3f-a22e06061956
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=5e2074f2-dc7e-4301-be3f-a22e06061956 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		5e2074f2-dc7e-4301-be3f-a22e06061956
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=5e2074f2-dc7e-4301-be3f-a22e06061956 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		5e2074f2-dc7e-4301-be3f-a22e06061956
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

```

Here's everything.

---

### Post by cholericfun on 2009-05-11
> **ChemShock said:**
> ```
# menu.lst - See: grub(8), info grub, 
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP      <<<<----------JUST CHANGE THIS LINE TO WHATEVER
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

```



all you want is change the title to Windows XP
or you may call it hulahulablabla here for that matter...

---

### Post by ChemShock on 2009-05-11
So changing what you said did help. Now on the boot loader screen it goes to another screen (its been doing since I posted) two different windows options. What's labeled as default doesn't work but the other does.

I want ubuntu, recovery for ubuntu, memtest, and windows all be on one screen.

Is it possible?

---

### Post by Don1500 on 2009-05-11
"I want ubuntu, recovery for ubuntu, memtest, and windows all be on one screen.
Is it possible?" ----- Yes, this is the way it is normally set up.


Repost the menu.lst file. It only shows one instance of Windows, did you add another?
(BTW I hope you made a copy of Menu.lst under another name so you can go back if you screw it up.)

I See.... you must have a WINDOWS dual boot option that gives you two instances of windows. Why? I don't know what you had before you installed Jaunty so I don't know why. When you boot Grub you have only one option for Windows XP. When you activate that you go to a separate Windows "Grub" (This has nothing to do with Jaunty) and you get two choices.

Also if you want to go back to just windows to find out what happened you can get "The Ultimate Boot Disk" (Do a search) and reinstall the windows MBR. Or, if you have your origninal Windows disk, use FixMBR. You can later reinstall grub to work with the Linux/windows dual boot.

---

### Post by ChemShock on 2009-05-11
I might have two versions of windows because I did have wubi on here at one point, deleted it so I can then do a dual boot. Like I said, once I hit enter on Wnidows XP (which I know how to change) it leads me to another screen that says:

1. Microsoft Windows XP Home Edition
2. Windows(default) << (Which doesn't work cause its missing a file)

---

### Post by Don1500 on 2009-05-11
I haven't worked with windows dual boot systems but I'm sure somebody here has. Maybe they can give you the help you need.

---

### Post by 73ckn797 on 2009-05-12
Maybe you ought to boot with the Windows XP disk, go to recovery and type fixmbr. You then could reinstall grub from the Ubuntu LiveCD (instructions in community documentation). It is one way to fix things.

---

### Post by gkestrel on 2009-05-15
Hi
 Do you mean that when you choose the windows option in grub, that you then get a second menu with two windows listed, one that works and one that does not due to a missing file. If so the second menu you see is the windows boot menu you normally only see when you have two copies of windows installed. You can check this out by booting into windows, open the systems properties page by pressing the windows key and the pause break keys together (or by opening control panel and choosing system), choose the advanced tab, at the bottom you will see startup and recovery - choose settings, nexty click the edit button next to the line that says 

to edit the startup options manually click edit

notepad will open with the boot.ini file loaded make shure that notepad is maximised to full screen so that no entries are word wrapped. you will see something like this:

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Default" /noexecute=optin /fastdetect

if there are two operating systems listed, you will need to highlight the line for the Windows(default) that you told us about and delete it(in the example above it would be all the second line of the listed operating systems)

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Default" /noexecute=optin /fastdetect

save the file and exit notepad, click ok and ok again to exit systems properties. Now reboot again again choose windows in the grub menu, windows should now load straight away. Hope that helps you out.

---

### Post by ChemShock on 2009-05-20
Ok, I figured this out and I hope this helps anyone going from wubi to a full dual boot.

When you uninstall Wubi from the Windows OS, it keeps settings the program changes. Meaning Windows was still using Wubi's boot.ini file. So after I realized this, All is takes is:

1. Bring up the boot.ini file.
> There's several ways to do this:
     >From Ubuntu, access the hard drive and manually find it.
     >If you still have access to Windows, right-click on my         computer, Properties, hardware tab(?), then button that says "Click Me to edit boot options, then bring up the actual text of the command to edit.
     >Follow Microsoft's instruction on how to edit boot.ini.(see attached)

2. Once the boot.ini file can be accessed replace it with the default boot.ini
>If you lost it like me, either copy it from another comp that's just running "Windows XP", or assuming whatever version you want, or Microsoft did post a sample under their support section. (see attached) Then just change what version you are using.

3. Save and Restart.

This fixed my "extra screen of Windows options" problem. So now, Windows now boots from the same list as Ubuntu and if for whatever reason I can't access Ubuntu; theoretically, Windows is unaffected.

Also, as a side note, this is a way easier and less complicated fix than the others proposed.

[http://support.microsoft.com/kb/289022]("http://support.microsoft.com/kb/289022")

My fix looks like this:

```
[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn

c:\wubildr.mbr="Ubuntu"
```

to

```
[boot loader]
timeout=10
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home" /fastdetect 
```

---

### Post by ChemShock on 2009-05-20
Now to be back to being a noob, how do I mark this as resolved?

---

### Post by 73ckn797 on 2009-05-20
Go back to your first post in this thread and edit the title by inserting [SOLVED] with the brackets at the beginning of the title.

---

