---
title: "Apt-Get stopped working"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by transmition on 2009-01-10
Hello, it appears that apt-get no longer works for me, apt-get remove and apt-get install produce the same error. 

For example, if I try and uninstall irssi, this is what I get:

```

mason@mason-desktop:~$ sudo apt-get remove irssi
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  irssi
0 upgraded, 0 newly installed, 1 to remove and 32 not upgraded.
6 not fully installed or removed.
After this operation, 3064kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 117599 files and directories currently installed.)
Removing irssi ...
Setting up linux-image-2.6.24-22-generic (2.6.24-22.45) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-22-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-22-generic
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... /usr/sbin/update-grub: line 1413: /boot/grub/menu.lst: Operation not supported
User postinst hook script [/sbin/update-grub] exited with value 1
dpkg: error processing linux-image-2.6.24-22-generic (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-22-generic:
 linux-ubuntu-modules-2.6.24-22-generic depends on linux-image-2.6.24-22-generic; however:
  Package linux-image-2.6.24-22-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-22-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-22-generic; however:
  Package linux-image-2.6.24-22-generic is not configured yet.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-22-generic; however:
  Package linux-ubuntu-modules-2.6.24-22-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-22-generic:
 linux-restricted-modules-2.6.24-22-generic depends on linux-image-2.6.24-22-generic; however:
  Package linux-image-2.6.24-22-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-22-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-22-generic; however:
  Package linux-restricted-modules-2.6.24-22-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.22.24); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.24.22.24); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.24-22-generic
 linux-ubuntu-modules-2.6.24-22-generic
 linux-image-generic
 linux-restricted-modules-2.6.24-22-generic
 linux-restricted-modules-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any help would be appreciated.

---

### Post by stanz on 2009-01-10
Looks to me your trying to do something - out of order.
```
dependency problems prevent configuration
dpkg: error processing *linux-generic* (--configure):
 [COLOR=Red]***dependency problems***[/COLOR] - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.24-[COLOR=Red]**22**[/COLOR]-generic
 linux-image-2.6.24-[COLOR=Red]**19**[/COLOR]-generic
  
```Research more about removing irssi, which seems to concern the kernel version -- not the workings of apt-get.
Maybe synaptic can throw ya a detailed reason!?

---

### Post by transmition on 2009-01-10
No, it is not specific to irssi as I get this same error regardless of what I attempt to install.

---

### Post by dadozgb on 2009-01-10
You somehow managed to broke your package dependencies. hmm you can try to fix it buy running sudo apt-get -f but do it on your own risk 'cause I don't know do you have any other booting kernel.

---

### Post by transmition on 2009-01-10
I have win XP installed. No other linux kernel though.

---

### Post by stanz on 2009-01-10
> **transmition said:**
> No, it is not specific to irssi as I get this same error regardless of what I attempt to install.

Can you "apt-get update"?
or what dadozgb mentioned?

Did you try synaptic? and while there - click "reload"?
It's a gui - but may help.
Just trying to help... ;)

---

### Post by dadozgb on 2009-01-10
Well I don't know what to say to you. I don't want to give you a wrong answer but look at man apt-get and decide for yourshelf.Although I think, I'm not shure but I don't think that linux will left you without kernel.

---

### Post by transmition on 2009-01-10
Well, right now I am trying to an update via update manager, so in 8 minutes I'll test out the apt-get commands and synaptic. I doubt I will be able to do apt-get update though.

---

### Post by dadozgb on 2009-01-10
> **transmition said:**
> Well, right now I am trying to an update via update manager, so in 8 minutes I'll test out the apt-get commands and synaptic. I doubt I will be able to do apt-get update though.
You will not 'cause package dependices are broken.

---

### Post by ugm6hr on 2009-01-10
Have you recently updated?

It looks like the latest kernel and modules have only partly installed.

```
sudo apt-get install -f
```

Then I'd do a reboot before doing anything else.

---

### Post by dadozgb on 2009-01-10
> **ugm6hr said:**
> 

Then I'd do a reboot before doing anything else.

There is no need for reboot. If he can fix it with apt-get -f he is home free.

---

### Post by transmition on 2009-01-10
OK, apt-get update seems to run without any errors, provides this output:

```

Hit http://ca.archive.ubuntu.com hardy Release.gpg
Ign http://ca.archive.ubuntu.com hardy/main Translation-en_CA
Ign http://ca.archive.ubuntu.com hardy/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com hardy/universe Translation-en_CA
Ign http://ca.archive.ubuntu.com hardy/multiverse Translation-en_CA
Hit http://ca.archive.ubuntu.com hardy-updates Release.gpg
Ign http://ca.archive.ubuntu.com hardy-updates/main Translation-en_CA
Ign http://ppa.launchpad.net gutsy Release.gpg 
Ign http://ppa.launchpad.net gutsy/main Translation-en_CA
Ign http://ppa.launchpad.net hardy Release.gpg 
Ign http://ppa.launchpad.net hardy/main Translation-en_CA
Ign http://ca.archive.ubuntu.com hardy-updates/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com hardy-updates/universe Translation-en_CA
Ign http://ca.archive.ubuntu.com hardy-updates/multiverse Translation-en_CA
Get:1 http://ppa.launchpad.net gutsy Release [27.6kB]
Hit http://ca.archive.ubuntu.com hardy Release 
Hit http://ca.archive.ubuntu.com hardy-updates Release
Get:2 http://ppa.launchpad.net hardy Release [27.6kB]               
Hit http://ca.archive.ubuntu.com hardy/main Packages
Ign http://ppa.launchpad.net gutsy/main Packages
Hit http://ca.archive.ubuntu.com hardy/restricted Packages
Ign http://ppa.launchpad.net hardy/main Packages
Ign http://ppa.launchpad.net hardy/main Sources
Hit http://ca.archive.ubuntu.com hardy/main Sources
Hit http://ca.archive.ubuntu.com hardy/restricted Sources
Hit http://ca.archive.ubuntu.com hardy/universe Packages
Hit http://ca.archive.ubuntu.com hardy/universe Sources
Hit http://ca.archive.ubuntu.com hardy/multiverse Packages
Hit http://ca.archive.ubuntu.com hardy/multiverse Sources
Hit http://ca.archive.ubuntu.com hardy-updates/main Packages
Hit http://ca.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://ca.archive.ubuntu.com hardy-updates/main Sources
Hit http://ca.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://ppa.launchpad.net gutsy/main Packages
Hit http://ca.archive.ubuntu.com hardy-updates/universe Packages
Hit http://ca.archive.ubuntu.com hardy-updates/universe Sources
Hit http://ca.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://ca.archive.ubuntu.com hardy-updates/multiverse Sources
Hit http://ppa.launchpad.net hardy/main Packages
Hit http://ppa.launchpad.net hardy/main Sources
Fetched 2B in 1s (2B/s)  
Reading package lists... Done

```

As well, it appears that apt-get *is* working, I just get those errors every time I do remove or install.

---

### Post by transmition on 2009-01-10
No, I have not recently updated (to my knowledge at least ;)

sudo apt-get install -f outputs

```

mason@mason-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 32 not upgraded.
6 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.24-22-generic (2.6.24-22.45) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-22-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-22-generic
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... /usr/sbin/update-grub: line 1413: /boot/grub/menu.lst: Operation not supported
User postinst hook script [/sbin/update-grub] exited with value 1
dpkg: error processing linux-image-2.6.24-22-generic (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-22-generic:
 linux-ubuntu-modules-2.6.24-22-generic depends on linux-image-2.6.24-22-generic; however:
  Package linux-image-2.6.24-22-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-22-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-22-generic; however:
  Package linux-image-2.6.24-22-generic is not configured yet.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-22-generic; however:
  Package linux-ubuntu-modules-2.6.24-22-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-22-generic:
 linux-restricted-modules-2.6.24-22-generic depends on linux-image-2.6.24-22-generic; however:
  Package linux-image-2.6.24-22-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-22-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-22-generic; however:
  Package linux-restricted-modules-2.6.24-22-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.22.24); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.24.22.24); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.24-22-generic
 linux-ubuntu-modules-2.6.24-22-generic
 linux-image-generic
 linux-restricted-modules-2.6.24-22-generic
 linux-restricted-modules-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I'll try rebooting and tell you my progress from there.

---

### Post by dadozgb on 2009-01-10
> **transmition said:**
> OK, apt-get update seems to run without any errors, provides this output:

As well, it appears that apt-get *is* working, I just get those errors every time I do remove or install.

You broke your package dependencies! Meaning it will give you error on trying to install something. You have to fix package dependencies.There is no need for rebooting! This is not windows.

---

### Post by transmition on 2009-01-10
How would I go about fixing my dependencies then?

---

### Post by dadozgb on 2009-01-10
> **transmition said:**
> How would I go about fixing my dependencies then?

Well what the hell. do sudo apt-get -f and see where it will get you. Don't reboot.

---

### Post by transmition on 2009-01-10
Errr... I think I have to add something else to
```

sudo apt-get -f

```

Seeing as it presents with me a list of options when I type that.

---

### Post by dadozgb on 2009-01-10
apt-get install -f

---

### Post by transmition on 2009-01-10
apt 0.7.9ubuntu17.1 for amd64 compiled on Oct 27 2008 18:11:10
Usage: apt-get [options] command
       apt-get [options] install|remove pkg1 [pkg2 ...]
       apt-get [options] source pkg1 [pkg2 ...]

apt-get is a simple command line interface for downloading and
installing packages. The most frequently used commands are update
and install.

Commands:
   update - Retrieve new lists of packages
   upgrade - Perform an upgrade
   install - Install new packages (pkg is libc6 not libc6.deb)
   remove - Remove packages
   autoremove - Remove all automatic unused packages
   purge - Remove and purge packages
   source - Download source archives
   build-dep - Configure build-dependencies for source packages
   dist-upgrade - Distribution upgrade, see apt-get(8)
   dselect-upgrade - Follow dselect selections
   clean - Erase downloaded archive files
   autoclean - Erase old downloaded archive files
   check - Verify that there are no broken dependencies

Options:
  -h  This help text.
  -q  Loggable output - no progress indicator
  -qq No output except for errors
  -d  Download only - do NOT install or unpack archives
  -s  No-act. Perform ordering simulation
  -y  Assume Yes to all queries and do not prompt
  -f  Attempt to correct a system with broken dependencies in place
  -m  Attempt to continue if archives are unlocatable
  -u  Show a list of upgraded packages as well
  -b  Build the source package after fetching it
  -V  Show verbose version numbers
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See the apt-get(8), sources.list(5) and apt.conf(5) manual
pages for more information and options.
                       This APT has Super Cow Powers.

---

### Post by 2hot6ft2 on 2009-01-10
you can try

```
sudo dpkg --configure -a
```

this will fix any packages if it stopped during the install.

---

### Post by transmition on 2009-01-10
> **2hot6ft2 said:**
> you can try

```
sudo dpkg --configure -a
```

this will fix any packages if it stopped during the install.

While the code did not produce any errors, I still get the same ones as before when using apt-get.

---

### Post by dadozgb on 2009-01-10
did you try apt-get install -f ?

---

### Post by transmition on 2009-01-10
Yes, I did.

---

### Post by ugm6hr on 2009-01-10
> **dadozgb said:**
> There is no need for reboot. If he can fix it with apt-get -f he is home free.

If you install a new kernel, a reboot is necessary.  Since the dependency / configuration issues are with a kernel - I suspect a reboot is prudent (after the dependency issues are sorted).

Unfortunately, apt-get is unable to fix your problem:

```
Updating /boot/grub/menu.lst ... /usr/sbin/update-grub: line 1413: /boot/grub/menu.lst: Operation not supported
User postinst hook script [/sbin/update-grub] exited with value 1
dpkg: error processing linux-image-2.6.24-22-generic (--configure):
 subprocess post-installation script returned error exit status 1

```

Are you currently booting into the -19 or -22 kernel?  If the latter - it might be worth rebooting into the -19 kernel, and running "sudo apt-get install -f" again.

If that doesn't work, boot into the -19 kernel and try reinstalling the new kernel:
```
sudo apt-get install --reinstall linux-image-2.6.24-22-generic
```

---

### Post by 2hot6ft2 on 2009-01-10
I think ugm6hr is on the right track here.

---

### Post by dadozgb on 2009-01-10
> **ugm6hr said:**
> If you install a new kernel, a reboot is necessary.  Since the dependency / configuration issues are with a kernel - I suspect a reboot is prudent (after the dependency issues are sorted).


I don't know where did you picked up second kernel while he said he have only one kernel installed. Package dependencies are not issued in kernel than in package manager.Sorry I saw it now. I asked him insted of looking in his output. Although package dependencies are not issued in the kernel.

---

### Post by transmition on 2009-01-10
I am booting the 22 kernel, although when I hit F6(?) at bootup, I am not presented with an option to boot into a 19 kernel. 

(I don't even recall having anything to do with a second kernel, and it wasn't until recently that I started getting problems.)

---

### Post by dadozgb on 2009-01-10
dpkg -l | grep linux-image to see how many kernels you have installed.

---

### Post by transmition on 2009-01-10
ii  linux-image-2.6.24-19-generic              2.6.24-19.41                                         Linux kernel image for version 2.6.24 on x86
iF  linux-image-2.6.24-22-generic              2.6.24-22.45                                         Linux kernel image for version 2.6.24 on x86
iU  linux-image-generic                        2.6.24.22.24                                         Generic Linux kernel image

---

### Post by ugm6hr on 2009-01-10
> **transmition said:**
> I am booting the 22 kernel, although when I hit F6(?) at bootup, I am not presented with an option to boot into a 19 kernel. 

(I don't even recall having anything to do with a second kernel, and it wasn't until recently that I started getting problems.)

Press Escape during boot to enter the Grub menu.  It should give you options.

If that doesn't work, post the contents of /boot/grub/menu.lst here

---

### Post by dadozgb on 2009-01-10
> **transmition said:**
> ii  linux-image-2.6.24-19-generic              2.6.24-19.41                                         Linux kernel image for version 2.6.24 on x86
iF  linux-image-2.6.24-22-generic              2.6.24-22.45                                         Linux kernel image for version 2.6.24 on x86
iU  linux-image-generic                        2.6.24.22.24                                         Generic Linux kernel image

It doesn't look like one kernel image to me. But that's me.

---

### Post by 2hot6ft2 on 2009-01-10
Don't know if this will be any help or not. I take it you're running Hardy. I'm on Hardy 64 bit right now and my kernel is 2.6.24-23-generic. Maybe if you tried installing it? Just a thought. It would be.
```
sudo apt-get install linux-image-2.6.24-23-generic
```
This would be assuming it's available for the 32 bit OS.
Don't know if it would even work at this point. If it would install then at least you would have a second kernel and maybe without the errors.

Should note here I'm using Ultimate Edition.

---

### Post by transmition on 2009-01-10
Well, during bootup it says to press F6 for more options, and then lists a dell recover partition, windows xp, two 22 kernels, and a 22 recovery 33 kernel.

Anyway, here is the menu.lst:

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
# kopt=root=UUID=FA7C4DA17C4D5A11 loop=/ubuntu/disks/root.disk ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=FA7C4DA17C4D5A11 loop=/ubuntu/disks/root.disk ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=FA7C4DA17C4D5A11 loop=/ubuntu/disks/root.disk ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Dell Utility Partition
root		(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
chainloader	+1

```

---

### Post by dadozgb on 2009-01-10
It seems you have only *22-19 kernel in your grub menu. And that's corespond with your dpkg -l output 'cause the rest packages are broken as I understood. Oke do uname -a to see what kernel are you running.

---

### Post by 2hot6ft2 on 2009-01-10
This is all I see in the menu list kernel 2.6.24-19-generic
I don't see a 22 anywhere.

---

### Post by ugm6hr on 2009-01-10
OK. So you are booting into -19 kernel (it is the only option in Grub).

You can double-check with:
```
uname -a
```

Nevertheless, there is clearly a problem with the kernel image -22, so try reinstalling it:
```
sudo apt-get install --reinstall linux-image-2.6.24-22-generic
```

---

### Post by dadozgb on 2009-01-10
Did he went for reboot ? :-D

---

### Post by transmition on 2009-01-10
Attempting to reinstall the kernel produces this:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 32 not upgraded.
6 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-2.6.24-22-generic (2.6.24-22.45) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-22-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-22-generic
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... /usr/sbin/update-grub: line 1413: /boot/grub/menu.lst: Operation not supported
User postinst hook script [/sbin/update-grub] exited with value 1
dpkg: error processing linux-image-2.6.24-22-generic (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-22-generic:
 linux-ubuntu-modules-2.6.24-22-generic depends on linux-image-2.6.24-22-generic; however:
  Package linux-image-2.6.24-22-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-22-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-22-generic; however:
  Package linux-image-2.6.24-22-generic is not configured yet.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-22-generic; however:
  Package linux-ubuntu-modules-2.6.24-22-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by dadozgb on 2009-01-10
You have only one working kernel and it's *-19. Try to remove the rest of kernel images as dpkg -l | grep linux-image but don't remove running kernel marked as II infront.

---

### Post by transmition on 2009-01-10
> **dadozgb said:**
> You have only one working kernel and it's *-19. Try to remove the rest of kernel images as dpkg -l | grep linux-image but don't remove running kernel marked as II infront.

Could you explain how please?

---

### Post by dadozgb on 2009-01-10
> **transmition said:**
> Could you explain how please?

dpkg -l | grep linux-image you get output, sudo dpkg --purge linux-image-somethning but do not remove the one with 19. It's your running kernel. you can check it and do check it with uname -a.

---

### Post by transmition on 2009-01-10
sudo dpkg --purge linux-image-2.6.24-22-generic yields:

```
 
(Reading database ... 117784 files and directories currently installed.)
Removing linux-image-2.6.24-22-generic ...
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... /usr/sbin/update-grub: line 1413: /boot/grub/menu.lst: Operation not supported
User postrm hook script [/sbin/update-grub] exited with value 1
The link /vmlinuz is a damaged link
Removing symbolic link vmlinuz 
 you may need to re-run your boot loader[grub]
The link /vmlinuz.old is a damaged link
Removing symbolic link vmlinuz.old 
 you may need to re-run your boot loader[grub]
The link /initrd.img is a damaged link
Removing symbolic link initrd.img 
 you may need to re-run your boot loader[grub]
The link /initrd.img.old is a damaged link
Removing symbolic link initrd.img.old 
 you may need to re-run your boot loader[grub]
Purging configuration files for linux-image-2.6.24-22-generic ...
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... /usr/sbin/update-grub: line 1413: /boot/grub/menu.lst: Operation not supported
User postrm hook script [/sbin/update-grub] exited with value 1
rmdir: failed to remove `/lib/modules/2.6.24-22-generic': Directory not empty

```

---

### Post by ugm6hr on 2009-01-10
> **transmition said:**
> Well, during bootup it says to press F6 for more options, and then lists a dell recover partition, windows xp, two 22 kernels, and a 22 recovery 33 kernel.

I am a little confused by this.

Your menu.lst clearly has a 10 second timeout, with hidden menu commented out with a #.  Therefore, you should *always* be given a Grub menu (i.e. no need to press any key to get there), which counts down for 10 seconds.

The labeled options are:
Ubuntu 8.04.1, kernel 2.6.24-19-generic
Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
Ubuntu 8.04.1, memtest86+
Dell Utility Partition
Microsoft Windows XP Professional

If this is not the case, then something untoward has happened with your installation.

Judging by this:
```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=FA7C4DA17C4D5A11 loop=/ubuntu/disks/root.disk ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic

```

You have installed Ubuntu using a non-standard method.  Did you use Wubi (install within Windows)?  I have never used Wubi - that may be part of the problem.

With regard to the current problem. perhaps the kernel file itself is OK, but the update-grub script is causing the error:
```
Updating /boot/grub/menu.lst ... /usr/sbin/update-grub: line 1413: /boot/grub/menu.lst: Operation not supported
```

Line 1413 of that script copies over your existing menu.lst with the new modified menu.lst - which is part of the new kernel configuration.  Hence, if it is not allowed to do that, it doesn't complete the configuration.

First:
Did you use Wubi? Iif yes - please make that clear in any future requests for help, and consider using the Wubi subforum.
One possible solution would be to just remove the -22 kernel, along with those packages that depend on it.  As long as you are currently in the -19 kernel (check with "uname -a"), this should resolve your apt-get problems.
```
sudo apt-get remove linux-image-2.6.24-22-generic linux-ubuntu-modules-2.6.24-22-generic linux-image-generic linux-restricted-modules-2.6.24-22-generic 
```

---

### Post by dadozgb on 2009-01-10
sudo update-grub

---

### Post by transmition on 2009-01-10
Yes, I did use Wubi, sorry for not mentioning that.

Yes, I am running the -19 kernel.

Yes, the five options you listed appear, but only if I hit escape(?), not sure of the key. 

If I do not press escape, it gives me a countdown telling me it is going to choose the first option (or something along those lines)

I typed
```

sudo apt-get remove linux-image-2.6.24-22-generic linux-ubuntu-modules-2.6.24-22-generic linux-image-generic linux-restricted-modules-2.6.24-22-generic

```

which gave me an error, but told me to type
```

sudo apt-get -f install

```

Which I did, and installed 226mb of something.

Now I am presented with a menu, displaying the follwing:

```

    &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508;  &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
    &#9474; A new version of /boot/grub/menu.lst is available, but the version   &#9474; 
    &#9474; installed currently has been locally modified.                       &#9474; 
    &#9474;                                                                      &#9474; 
    &#9474; What would you like to do about menu.lst?                            &#9474; 
    &#9474;                                                                      &#9474; 
    &#9474;      install the package maintainer's version                        &#9474; 
    &#9474;      keep the local version currently installed                      &#9474; 
    &#9474;      show the differences between the versions                       &#9474; 
    &#9474;      show a side-by-side difference between the versions             &#9474; 
    &#9474;      show a 3-way difference between available versions              &#9474; 
    &#9474;      do a 3-way merge between available versions (experimental)      &#9474; 
    &#9474;      start a new shell to examine the situation                      &#9474; 
    &#9474;                                                                      &#9474; 
    &#9474;                                                                      &#9474; 
    &#9474;                                <Ok>                                  &#9474; 
    &#9474;                                                                      &#9474; 
    &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496; 
                                                                             

```

Sorry if that is difficult to read, it's using a kind of pseudo window with a blue background and a grey window.

---

### Post by dadozgb on 2009-01-10
The first option is very safe bet. And if he installed something that mean that your package manager is afterall working. But let him do configure and we can all rest in peace.

---

### Post by transmition on 2009-01-10
So, I should do the first option then?

---

### Post by dadozgb on 2009-01-10
It's the safest to do it as you edited something in menu.lst as you been told.

---

### Post by transmition on 2009-01-10
Ok, After doing that, I get 

```

Setting up linux-image-2.6.24-22-generic (2.6.24-22.45) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-22-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-23-generic
Found kernel: /boot/vmlinuz-2.6.24-22-generic
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... /usr/sbin/update-grub: line 1413: /boot/grub/menu.lst: Operation not supported
User postinst hook script [/sbin/update-grub] exited with value 1
dpkg: error processing linux-image-2.6.24-22-generic (--configure):
 subprocess post-installation script returned error exit status 1
Setting up linux-image-2.6.24-23-generic (2.6.24-23.46) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-23-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-23-generic
Found kernel: /boot/vmlinuz-2.6.24-22-generic
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... /usr/sbin/update-grub: line 1413: /boot/grub/menu.lst: Operation not supported
User postinst hook script [/sbin/update-grub] exited with value 1
dpkg: error processing linux-image-2.6.24-23-generic (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-22-generic:
 linux-ubuntu-modules-2.6.24-22-generic depends on linux-image-2.6.24-22-generic; however:
  Package linux-image-2.6.24-22-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-22-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-23-generic:
 linux-ubuntu-modules-2.6.24-23-generic depends on linux-image-2.6.24-23-generic; however:
  Package linux-image-2.6.24-23-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-23-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-23-generic; however:
  Package linux-image-2.6.24-23-generic is not configured yet.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-23-generic; however:
  Package linux-ubuntu-modules-2.6.24-23-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-23-generic:
 linux-restricted-modules-2.6.24-23-generic depends on linux-image-2.6.24-23-generic; however:
  Package linux-image-2.6.24-23-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-23-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-23-generic; however:
  Package linux-restricted-modules-2.6.24-23-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.23.25); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.24.23.25); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-22-generic:
 linux-restricted-modules-2.6.24-22-generic depends on linux-image-2.6.24-22-generic; however:
  Package linux-image-2.6.24-22-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-22-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.24-22-generic
 linux-image-2.6.24-23-generic
 linux-ubuntu-modules-2.6.24-22-generic
 linux-ubuntu-modules-2.6.24-23-generic
 linux-image-generic
 linux-restricted-modules-2.6.24-23-generic
 linux-restricted-modules-generic
 linux-generic
 linux-restricted-modules-2.6.24-22-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

When removing irssi.

As well, here is the contents of from previous commands prior and after the menu:

```

mason@mason-desktop:~$ sudo update-grub
[sudo] password for mason: 
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... /usr/sbin/update-grub: line 1413: /boot/grub/menu.lst: Operation not supported
mason@mason-desktop:~$ sudo apt-get remove linux-image-2.6.24-22-generic linux-ubuntu-modules-2.6.24-22-generic linux-image-generic linux-restricted-modules-2.6.24-22-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-image-2.6.24-22-generic is not installed, so not removed
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  linux-generic: Depends: linux-image-generic (= 2.6.24.22.24) but it is not going to be installed
  linux-restricted-modules-generic: Depends: linux-restricted-modules-2.6.24-22-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
mason@mason-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-generic linux-image-2.6.24-22-generic linux-image-2.6.24-23-generic
  linux-image-generic linux-restricted-modules-2.6.24-23-generic
  linux-restricted-modules-generic linux-ubuntu-modules-2.6.24-23-generic
Suggested packages:
  linux-doc-2.6.24 linux-source-2.6.24 avm-fritz-firmware-2.6.24-23 nvidia-glx
  nvidia-glx-legacy nvidia-glx-new
The following NEW packages will be installed:
  linux-image-2.6.24-22-generic linux-image-2.6.24-23-generic
  linux-restricted-modules-2.6.24-23-generic
  linux-ubuntu-modules-2.6.24-23-generic
The following packages will be upgraded:
  linux-generic linux-image-generic linux-restricted-modules-generic
3 upgraded, 4 newly installed, 0 to remove and 29 not upgraded.
5 not fully installed or removed.
Need to get 0B/56.9MB of archives.
After this operation, 225MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package linux-image-2.6.24-22-generic.
(Reading database ... 115697 files and directories currently installed.)
Unpacking linux-image-2.6.24-22-generic (from .../linux-image-2.6.24-22-generic_2.6.24-22.45_amd64.deb) ...
Done.
Selecting previously deselected package linux-image-2.6.24-23-generic.
Unpacking linux-image-2.6.24-23-generic (from .../linux-image-2.6.24-23-generic_2.6.24-23.46_amd64.deb) ...
Done.
Selecting previously deselected package linux-ubuntu-modules-2.6.24-23-generic.
Unpacking linux-ubuntu-modules-2.6.24-23-generic (from .../linux-ubuntu-modules-2.6.24-23-generic_2.6.24-23.36_amd64.deb) ...
Preparing to replace linux-generic 2.6.24.22.24 (using .../linux-generic_2.6.24.23.25_amd64.deb) ...
Unpacking replacement linux-generic ...
Preparing to replace linux-image-generic 2.6.24.22.24 (using .../linux-image-generic_2.6.24.23.25_amd64.deb) ...
Unpacking replacement linux-image-generic ...
Selecting previously deselected package linux-restricted-modules-2.6.24-23-generic.
Unpacking linux-restricted-modules-2.6.24-23-generic (from .../linux-restricted-modules-2.6.24-23-generic_2.6.24.16-23.56_amd64.deb) ...
Preparing to replace linux-restricted-modules-generic 2.6.24.22.24 (using .../linux-restricted-modules-generic_2.6.24.23.25_amd64.deb) ...
Unpacking replacement linux-restricted-modules-generic ...
Setting up linux-image-2.6.24-22-generic (2.6.24-22.45) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-22-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-23-generic
Found kernel: /boot/vmlinuz-2.6.24-22-generic
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... /usr/sbin/update-grub: line 1413: /boot/grub/menu.lst: Operation not supported
User postinst hook script [/sbin/update-grub] exited with value 1
dpkg: error processing linux-image-2.6.24-22-generic (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-22-generic:
 linux-ubuntu-modules-2.6.24-22-generic depends on linux-image-2.6.24-22-generic; however:
  Package linux-image-2.6.24-22-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-22-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-2.6.24-23-generic (2.6.24-23.46) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-23-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-23-generic
Found kernel: /boot/vmlinuz-2.6.24-22-generic
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... /usr/sbin/update-grub: line 1413: /boot/grub/menu.lst: Operation not supported
User postinst hook script [/sbin/update-grub] exited with value 1
dpkg: error processing linux-image-2.6.24-23-generic (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-23-generic:
 linux-ubuntu-modules-2.6.24-23-generic depends on linux-image-2.6.24-23-generic; however:
  Package linux-image-2.6.24-23-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-23-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-23-generic; however:
  Package linux-image-2.6.24-23-generic is not configured yet.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-23-generic; however:
  Package linux-ubuntu-modules-2.6.24-23-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-23-generic:
 linux-restricted-modules-2.6.24-23-generic depends on linux-image-2.6.24-23-generic; however:
  Package linux-image-2.6.24-23-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-23-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-23-generic; however:
  Package linux-restricted-modules-2.6.24-23-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.23.25); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.24.23.25); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-22-generic:
 linux-restricted-modules-2.6.24-22-generic depends on linux-image-2.6.24-22-generic; however:
  Package linux-image-2.6.24-22-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-22-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.24-22-generic
 linux-ubuntu-modules-2.6.24-22-generic
 linux-image-2.6.24-23-generic
 linux-ubuntu-modules-2.6.24-23-generic
 linux-image-generic
 linux-restricted-modules-2.6.24-23-generic
 linux-restricted-modules-generic
 linux-generic
 linux-restricted-modules-2.6.24-22-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by ugm6hr on 2009-01-10
You only get that option if menu.lst has been manually edited.

If you haven't edited it, it must be because wubi edits it.

I am uncertain whether allowing the auto-configure is the correct option for wubi installs.

When you say "apt-get install -f" installed 222MB of stuff - did that include a new kernel image?

---

### Post by transmition on 2009-01-10
> **ugm6hr said:**
> 
When you say "apt-get install -f" installed 222MB of stuff - did that include a new kernel image?

No, it included several :P

---

### Post by dadozgb on 2009-01-10
did you do it as the output told you so apt-get install -f ?

---

### Post by ugm6hr on 2009-01-10
Oh dear.

The problem is Wubi.

You removed the -22 kernel.  Then using apt-get to automatically fix dependencies reinstalled the -22 *as well as* the -23 kernel!

Unfortunately, it appears that Wubi does not like kernel upgrades.

In order to get apt working again, you will have to remove both those new kernels, make sure that your menu.lst is still OK after being automatically updated, and then try and correct the dependency issues manually.

---

### Post by dadozgb on 2009-01-10
> **ugm6hr said:**
> Oh dear.

The problem is Wubi.

You removed the -22 kernel.  Then using apt-get to automatically fix dependencies reinstalled the -22 *as well as* the -23 kernel!

Unfortunately, it appears that Wubi does not like kernel upgrades.

In order to get apt working again, you will have to remove both those new kernels, make sure that your menu.lst is still OK after being automatically updated, and then try and correct the dependency issues manually.
I really do hope that you are right. I would really like to go to bed with his problem solved. :-D

---

### Post by transmition on 2009-01-10
This is rather perturbing, but oh well. 

When I went to purge the -22 kernel, I am presented with a menu again.

```

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508;  &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
    &#9474; A new version of /boot/grub/menu.lst is available, but the version   &#9474; 
    &#9474; installed currently has been locally modified.                       &#9474; 
    &#9474;                                                                      &#9474; 
    &#9474; What would you like to do about menu.lst?                            &#9474; 
    &#9474;                                                                      &#9474; 
    &#9474;      install the package maintainer's version                        &#9474; 
    &#9474;      keep the local version currently installed                      &#9474; 
    &#9474;      show the differences between the versions                       &#9474; 
    &#9474;      show a side-by-side difference between the versions             &#9474; 
    &#9474;      show a 3-way difference between available versions              &#9474; 
    &#9474;      do a 3-way merge between available versions (experimental)      &#9474; 
    &#9474;      start a new shell to examine the situation                      &#9474; 
    &#9474;                                                                      &#9474; 
    &#9474;                                                                      &#9474; 
    &#9474;                                <Ok>                                  &#9474; 
    &#9474;                                                                      &#9474; 
    &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496; 

```

Which should I choose?

---

### Post by ugm6hr on 2009-01-10
```
sudo apt-get remove linux-generic linux-image-2.6.24-22-generic linux-image-2.6.24-23-generic linux-image-generic linux-restricted-modules-2.6.24-23-generic linux-restricted-modules-generic linux-ubuntu-modules-2.6.24-23-generic linux-image-2.6.24-22-generic linux-image-2.6.24-23-generic linux-restricted-modules-2.6.24-23-generic linux-ubuntu-modules-2.6.24-23-generic linux-generic linux-image-generic linux-restricted-modules-generic

```

Try that.

DON'T use any more commands after that - post the result here first.

---

### Post by ugm6hr on 2009-01-10
> **transmition said:**
> Which should I choose?

Keep the local version.

Stop what you are doing - and let me explain a second.

Once you have done this - look at your menu.lst again.

Make sure it looks like the one that existed before.  Luckily, you posted the entire contents here - so you could backup the existing one ("sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bkp") - and then recreate the original.

But before you do, please reiterate exactly what your boot options were.  I am still confused about whether Wubi even uses menu.lst at all.  It sounded like your boot options were completely different to what menu.lst contained (as I described earlier).  In which case, it doesn't matter at all which option you choose.

Once you've given this some thought - run the command I gave in the previous post.

---

### Post by transmition on 2009-01-10
Ok, chose the local version.

---

### Post by transmition on 2009-01-10
```

sudo apt-get remove linux-generic linux-image-2.6.24-22-generic linux-image-2.6.24-23-generic linux-image-generic linux-restricted-modules-2.6.24-23-generic linux-restricted-modules-generic linux-ubuntu-modules-2.6.24-23-generic linux-image-2.6.24-22-generic linux-image-2.6.24-23-generic linux-restricted-modules-2.6.24-23-generic linux-ubuntu-modules-2.6.24-23-generic linux-generic linux-image-generic linux-restricted-modules-generic

```

Yields:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-image-2.6.24-22-generic is not installed, so not removed
Package linux-image-2.6.24-22-generic is not installed, so not removed
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  linux-restricted-modules-2.6.24-22-generic: Depends: linux-image-2.6.24-22-generic but it is not going to be installed
  linux-ubuntu-modules-2.6.24-22-generic: Depends: linux-image-2.6.24-22-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by dadozgb on 2009-01-10
remove modules

---

### Post by transmition on 2009-01-10
> **dadozgb said:**
> remove modules

Could you expand upon this please?

---

### Post by ugm6hr on 2009-01-10
```
sudo apt-get remove linux-restricted-modules-2.6.24-22-generic linux-ubuntu-modules-2.6.24-22-generic
```

---

### Post by dadozgb on 2009-01-10
> **transmition said:**
> Could you expand upon this please?

You see from the output that you have kernel modules installed without kernel so remove it. dpkg --purge or try as suggested apt-get install -f

---

### Post by transmition on 2009-01-10
> **ugm6hr said:**
> ```
sudo apt-get remove linux-restricted-modules-2.6.24-22-generic linux-ubuntu-modules-2.6.24-22-generic
```

Yields:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-restricted-modules-2.6.24-22-generic
  linux-ubuntu-modules-2.6.24-22-generic
0 upgraded, 0 newly installed, 2 to remove and 29 not upgraded.
8 not fully installed or removed.
After this operation, 74.9MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 118184 files and directories currently installed.)
Removing linux-restricted-modules-2.6.24-22-generic ...
FATAL: Could not open '/boot/System.map-2.6.24-22-generic': No such file or directory
Removing linux-ubuntu-modules-2.6.24-22-generic ...
FATAL: Could not open '/boot/System.map-2.6.24-22-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.24-22-generic
Setting up linux-image-2.6.24-23-generic (2.6.24-23.46) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-23-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-23-generic
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... /usr/sbin/update-grub: line 1413: /boot/grub/menu.lst: Operation not supported
User postinst hook script [/sbin/update-grub] exited with value 1
dpkg: error processing linux-image-2.6.24-23-generic (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-23-generic:
 linux-ubuntu-modules-2.6.24-23-generic depends on linux-image-2.6.24-23-generic; however:
  Package linux-image-2.6.24-23-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-23-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-23-generic; however:
  Package linux-image-2.6.24-23-generic is not configured yet.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-23-generic; however:
  Package linux-ubuntu-modules-2.6.24-23-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-23-generic:
 linux-restricted-modules-2.6.24-23-generic depends on linux-image-2.6.24-23-generic; however:
  Package linux-image-2.6.24-23-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-23-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-23-generic; however:
  Package linux-restricted-modules-2.6.24-23-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.23.25); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.24.23.25); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.24-23-generic
 linux-ubuntu-modules-2.6.24-23-generic
 linux-image-generic
 linux-restricted-modules-2.6.24-23-generic
 linux-restricted-modules-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by dadozgb on 2009-01-10
You're a hacker and there is no doubt about it.

---

### Post by transmition on 2009-01-10
> **dadozgb said:**
> You're a hacker and there is no doubt about it.

Excuse me?

---

### Post by dadozgb on 2009-01-10
Just a joke. Never mind. I don't know any more. If ugm6hr have something to add..

---

### Post by ugm6hr on 2009-01-10
```

sudo apt-get remove linux-generic linux-image-2.6.24-23-generic linux-image-generic linux-restricted-modules-2.6.24-23-generic linux-restricted-modules-generic linux-ubuntu-modules-2.6.24-23-generic linux-image-2.6.24-23-generic linux-restricted-modules-2.6.24-23-generic linux-ubuntu-modules-2.6.24-23-generic linux-generic linux-image-generic linux-restricted-modules-generic

```

---

### Post by transmition on 2009-01-10
Well, that did not produce any errors. I suppose I may as well post the output:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-image-2.6.24-22-generic is not installed, so not removed
The following packages will be REMOVED:
  linux-generic linux-image-2.6.24-23-generic linux-image-generic
  linux-restricted-modules-2.6.24-23-generic linux-restricted-modules-generic
  linux-ubuntu-modules-2.6.24-23-generic
0 upgraded, 0 newly installed, 6 to remove and 29 not upgraded.
6 not fully installed or removed.
After this operation, 151MB disk space will be freed.
Do you want to continue [Y/n]? y 
(Reading database ... 117608 files and directories currently installed.)
Removing linux-generic ...
Removing linux-restricted-modules-generic ...
Removing linux-restricted-modules-2.6.24-23-generic ...
Removing linux-image-generic ...
Removing linux-ubuntu-modules-2.6.24-23-generic ...
update-initramfs: Generating /boot/initrd.img-2.6.24-23-generic
Removing linux-image-2.6.24-23-generic ...
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... /usr/sbin/update-grub: line 1413: /boot/grub/menu.lst: Operation not supported
User postrm hook script [/sbin/update-grub] exited with value 1
The link /vmlinuz is a damaged link
Removing symbolic link vmlinuz 
 you may need to re-run your boot loader[grub]
The link /vmlinuz.old is a damaged link
Removing symbolic link vmlinuz.old 
 you may need to re-run your boot loader[grub]
The link /initrd.img is a damaged link
Removing symbolic link initrd.img 
 you may need to re-run your boot loader[grub]
The link /initrd.img.old is a damaged link
Removing symbolic link initrd.img.old 
 you may need to re-run your boot loader[grub]

```

---

### Post by dadozgb on 2009-01-10
so do update-grub and if it produce errors past ih here along with menu.lst

---

### Post by transmition on 2009-01-10
> **dadozgb said:**
> so do update-grub and if it produce errors past ih here along with menu.lst

Which produces errors :D

```

mason@mason-desktop:~$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... /usr/sbin/update-grub: line 1413: /boot/grub/menu.lst: Operation not supported

```

I am never using wubi ever again. (If I ever reinstall/install on another machine, I obviously still have to use it now)

---

### Post by ugm6hr on 2009-01-10
> **dadozgb said:**
> so do update-grub and if it produce errors past ih here along with menu.lst

I'm not sure that's even necessary with Wubi.

Just have a look at your menu.lst, and see whether it has changed from the original.

However, I should point out that you have an old kernel, and Wubi is preventing you from updating it.

Ask at the Wubi subforum why.  Cos I have no idea.

EDIT:
I have removed the linux packages responsible for auto-updating to future kernels, so hopefully this shouldn't happen again.

---

### Post by dadozgb on 2009-01-10
what is this wubi? I don't know 'cause I'm updating my system as new distro comes out. Can it be removed from the system?

---

### Post by transmition on 2009-01-10
Wubi is a method of installing Ubuntu inside of windows using a simple installer. This was my first time installing linux, and so I chose to use it. Since you haven't used it, I wouldn't recommend it, seeing as it doesn't create a separate partition for /home, and is unnecessary.

---

### Post by transmition on 2009-01-10
Well, the new menu.lst looks like this:

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
# kopt=root=UUID=FA7C4DA17C4D5A11 loop=/ubuntu/disks/root.disk ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=FA7C4DA17C4D5A11 loop=/ubuntu/disks/root.disk ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=FA7C4DA17C4D5A11 loop=/ubuntu/disks/root.disk ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Dell Utility Partition
root		(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
chainloader	+1

```

I will check to see if anything is different, I believe there is a terminal command do this (I could paste the previous content of menu.lst into a different text file). Does anyone remember what it was?

---

### Post by dadozgb on 2009-01-10
> **transmition said:**
> Wubi is a method of installing Ubuntu inside of windows using a simple installer. This was my first time installing linux, and so I chose to use it. Since you haven't used it, I wouldn't recommend it, seeing as it doesn't create a separate partition for /home, and is unnecessary.

Well maybe the best thing to do is to ask on the wubi forum 'cause I also haven got a clue about his wubi thing.

---

### Post by ugm6hr on 2009-01-10
> **transmition said:**
> Wubi is a method of installing Ubuntu inside of windows using a simple installer. This was my first time installing linux, and so I chose to use it. 

It is supposed to be good for people who want to try it out, but want more speed than the LiveCD allows.

However, it is not a complete install, and obviously has some idiosyncrasies.

If you have any future problems, make sure you state that you used Wubi, and consider using the Wubi subforum for any problems regarding the OS (rather than applications).

Anyway, you should have a functioning apt now.  Don't install any new kernel files, and you should be OK.

---

### Post by transmition on 2009-01-10
Alright, thank you for all your help.

---

### Post by dadozgb on 2009-01-10
[QUOTE=transmition]

I will check to see if anything is different, I believe there is a terminal command do this (I could paste the previous content of menu.lst into a different text file). Does anyone remember what it was?[/QUOTE]

you mean crtl-left mouse button over xterm?

---

### Post by ugm6hr on 2009-01-10
> **transmition said:**
> I will check to see if anything is different, I believe there is a terminal command do this (I could paste the previous content of menu.lst into a different text file). Does anyone remember what it was?

The important bits are unchanged.

You should be OK now.

If you are keen to continue using Ubuntu, there is supposed to be a way to convert a wubi to a full install.

Try looking it up (or asking).

---

### Post by stanz on 2009-01-10
Geez...what'a direction this took!!
Well, there was some good help here! right on~
sleep well dadozgb...
great help ugm6hr !
transmition - enjoy Ubuntu!
:)

---

### Post by transmition on 2009-01-10
> **stanz said:**
> 
transmition - enjoy Ubuntu!
:)

Just because something is posted in "absolute beginner talk" does not mean that the poster is a beginner ;)

I just figured that this would be the best place to put this topic, as it seemed like a rather simple problem.

---

### Post by stanz on 2009-01-11
Ha...I didn't think that at all - :)

---

