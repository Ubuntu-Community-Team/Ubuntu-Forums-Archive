---
title: "Bootchart not making a bootchart...?"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by jondgls on 2009-04-24
I have searched everywhere for a solution to my problem without success. Basically I installed bootchart from Synaptic Package Manager, rebooted and went to the /var/log/bootchart folder and it was empty.

I tried re-installing bootchart. No luck.
I tried installing using apt-get in terminal. No luck.

I have no idea why bootchart is not creating a bootchart. I have Ubuntu 8.10 Intrepid 64bit with AMD infrastructure.

Any help is appreciated because I have exhausted Google and this forum for a solution.

Thank you,
JonDgls

---

### Post by aheckler on 2009-04-24
Can you post the output of 
```
cat /boot/grub/menu.lst
```

---

### Post by jondgls on 2009-04-24
Here is the output of 
```
cat /boot/grub/menu.lst
```

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
# kopt=root=UUID=7deac4bf-f97e-47dc-986c-703396a57db5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7deac4bf-f97e-47dc-986c-703396a57db5

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

title		Ubuntu 8.10, kernel 2.6.27-12-generic
uuid		7deac4bf-f97e-47dc-986c-703396a57db5
kernel		/boot/vmlinuz-2.6.27-12-generic root=UUID=7deac4bf-f97e-47dc-986c-703396a57db5 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-12-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-12-generic (recovery mode)
uuid		7deac4bf-f97e-47dc-986c-703396a57db5
kernel		/boot/vmlinuz-2.6.27-12-generic root=UUID=7deac4bf-f97e-47dc-986c-703396a57db5 ro  single
initrd		/boot/initrd.img-2.6.27-12-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		7deac4bf-f97e-47dc-986c-703396a57db5
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7deac4bf-f97e-47dc-986c-703396a57db5 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		7deac4bf-f97e-47dc-986c-703396a57db5
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7deac4bf-f97e-47dc-986c-703396a57db5 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		7deac4bf-f97e-47dc-986c-703396a57db5
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by aheckler on 2009-04-24
Open up your menu.lst with gEdit, like so:
```
gksudo gedit /boot/grub/menu.lst
```

Find the line that looks like this
```
kernel		/boot/vmlinuz-2.6.27-12-generic root=UUID=7deac4bf-f97e-47dc-986c-703396a57db5 ro quiet splash
```

Make sure you have the right line!

Then add "init=/sbin/bootchartd" to the end of it, so it looks like this:
```
kernel		/boot/vmlinuz-2.6.27-12-generic root=UUID=7deac4bf-f97e-47dc-986c-703396a57db5 ro quiet splash **init=/sbin/bootchartd**
```

The entry for your default kernel should then look like this:
```
title		Ubuntu 8.10, kernel 2.6.27-12-generic
uuid		7deac4bf-f97e-47dc-986c-703396a57db5
kernel		/boot/vmlinuz-2.6.27-12-generic root=UUID=7deac4bf-f97e-47dc-986c-703396a57db5 ro quiet splash init=/sbin/bootchartd
initrd		/boot/initrd.img-2.6.27-12-generic
quiet
```

Save and close the file. Try rebooting and see if Bootchart worked.

---

### Post by jondgls on 2009-04-24
@ aheckler:

Edited menu.lst as stated. Ubuntu booted normally without errors however still no files in /var/log/bootchart.

Double checked menu.lst after reboot. The change was made correctly and was saved.

JonDgls

---

### Post by Alterax on 2009-04-24
> **jondgls said:**
> @ aheckler:

Edited menu.lst as stated. Ubuntu booted normally without errors however still no files in /var/log/bootchart.

Double checked menu.lst after reboot. The change was made correctly and was saved.

JonDgls

Hmmm...did you run sudo update-grub once you updated menu.lst?  If you hadn't, then the changes you made to menu.lst weren't merged into grub...which would explain why bootchart didn't run.

---

### Post by jondgls on 2009-04-24
@ Alterax:

updated menu.lst using:
```
sudo update-grub
```
then rebooted. Once again ubuntu booted normally without errors however still no files in /var/log/bootchart.

JonDgls

---

### Post by presence1960 on 2009-04-24
> **jondgls said:**
> I have searched everywhere for a solution to my problem without success. Basically I installed bootchart from Synaptic Package Manager, rebooted and went to the /var/log/bootchart folder and it was empty.

I tried re-installing bootchart. No luck.
I tried installing using apt-get in terminal. No luck.

I have no idea why bootchart is not creating a bootchart. I have Ubuntu 8.10 Intrepid 64bit with AMD infrastructure.

Any help is appreciated because I have exhausted Google and this forum for a solution.

Thank you,
JonDgls

install bootchart & pybootchartgui and next time you boot a .png file will be in the /var/log/bootchart directory. See if that works for you.

---

### Post by jondgls on 2009-04-24
@ presence1960:
> install bootchart & pybootchartgui and next time you boot a .png file will be in the /var/log/bootchart directory. See if that works for you.

Bootchart is already installed.
Output of:
```
sudo apt-get install pybootchartgui
```
is
```
XXXX@Office:~$ sudo apt-get install pybootchartgui
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package pybootchartgui
```

Found out pybootchartgui is not in the repo's yet. Downloaded pybootchartgui [here]("http://launchpadlibrarian.net/23750286/pybootchartgui_0%2Br102_all.deb") and installed.
No files in /var/log/bootchart after reboot.

Used the following command to create the bootchart:
```
pybootchartgui /var/log/bootchart
```
Output was:
```
Traceback (most recent call last):
  File "/usr/bin/pybootchartgui", line 7, in <module>
    sys.exit(main())
  File "/var/lib/python-support/python2.5/pybootchartgui/main.py", line 56, in main
    res = parsing.parse(args, options.prune)
  File "/var/lib/python-support/python2.5/pybootchartgui/parsing.py", line 196, in parse
    monitored_app = state.headers.get("profile.process")
AttributeError: 'NoneType' object has no attribute 'get'
```
 Still no bootchart or any files in /var/log/bootchart.


JonDgls

---

### Post by presence1960 on 2009-04-25
> **jondgls said:**
> @ presence1960:


Bootchart is already installed.
Output of:
```
sudo apt-get install pybootchartgui
```
is
```
XXXX@Office:~$ sudo apt-get install pybootchartgui
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package pybootchartgui
```

Found out pybootchartgui is not in the repo's yet. Downloaded pybootchartgui [here]("http://launchpadlibrarian.net/23750286/pybootchartgui_0%2Br102_all.deb") and installed.
No files in /var/log/bootchart after reboot.

Used the following command to create the bootchart:
```
pybootchartgui /var/log/bootchart
```
Output was:
```
Traceback (most recent call last):
  File "/usr/bin/pybootchartgui", line 7, in <module>
    sys.exit(main())
  File "/var/lib/python-support/python2.5/pybootchartgui/main.py", line 56, in main
    res = parsing.parse(args, options.prune)
  File "/var/lib/python-support/python2.5/pybootchartgui/parsing.py", line 196, in parse
    monitored_app = state.headers.get("profile.process")
AttributeError: 'NoneType' object has no attribute 'get'
```
 Still no bootchart or any files in /var/log/bootchart.


JonDgls

Must not be available in Intrepid...sorry. It is in Jaunty's repos.

---

### Post by jondgls on 2009-04-25
Any further suggestions on resolving this issue or are there other resources / forums that may assist?/

Thank you,
JonDgls

---

### Post by jondgls on 2009-04-26
When you install bootchart, you first need sun-java* installed and selected. To select sun-java use:
```
sudo update-alternatives --config java
```
Mine seemed fine so I left it on the default setting.

After that, because we are using an initrd system we need to regenerate initramfs for bootchart to work by using the following code:
```
sudo update-initramfs -u -k your_kernel_name
```
..where your_kernel_name is found by using:
```
uname -r
```

JonDgls

---

