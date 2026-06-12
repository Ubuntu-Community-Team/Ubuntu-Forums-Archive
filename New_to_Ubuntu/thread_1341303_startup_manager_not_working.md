---
title: "startup manager not working"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by hebebl on 2009-11-29
hi all,
I want to change the time to choose and the default os in the grub menu. i used the startup-manager to change these settings but they do not take effect.

My suspicion is that, occasionally (while doing updates and stuff) i get messages like "grub menu.lst not found, do you want to create?", and i have said no so far, fearing that it may mess up with the windows 7 option in the grub. Is it possible that the startup manager's inability to change the settings might be caused by this and is it likely that letting it create the menu.lst file mess up the grub option? thanks in advance.

---

### Post by jrrader on 2009-11-29
If you are using 9.10, menu.lst is no longer used.  The startup-manager you are using works with grub legacy, not grub 2.  If it creates menu.lst, nothing will happen because grub will ignore that file.  The grub configuration files used by grub 2 are in /etc/grub.d

You must have upgraded from 9.04 to 9.10 and you still have the startup manager from 9.04.  

Open terminal and do this:
```
sudo apt-get -y --reinstall install startupmanager
```

and try again.

If that doesn't work
```
sudo apt-get -y purge startupmanager
sudo apt-get -y install startupmanager
```

---

### Post by MadsRH on 2010-08-12
Did this solve your problem **hebebl**? 

> **jrrader said:**
> If you are using 9.10, menu.lst is no longer used.  The startup-manager you are using works with grub legacy, not grub 2.  If it creates menu.lst, nothing will happen because grub will ignore that file.  The grub configuration files used by grub 2 are in /etc/grub.d

You must have upgraded from 9.04 to 9.10 and you still have the startup manager from 9.04.  

Open terminal and do this:
```
sudo apt-get -y --reinstall install startupmanager
```

and try again.

If that doesn't work
```
sudo apt-get -y purge startupmanager
sudo apt-get -y install startupmanager
```

I've got exactly the same issue (upgraded from 9.04), but your fix isn't working :(
If I remember correctly I might have edited some files manually. Could that be why StartUp-manager has no effect?

---

### Post by jtarin on 2010-08-12
Your startup application command will determine what you can enter into the file /etc/rc.d/rc.local . It's the Linux way of doing things without a GUI.Programs listed in this file will run at boot.
Make sure its executable.
```
$chmod +x /etc/rc.d/rc.local
```

---

### Post by MadsRH on 2010-08-12
> **jtarin said:**
> Your startup application command will determine what you can enter into the file /etc/rc.d/rc.local . It's the Linux way of doing things without a GUI.Programs listed in this file will run at boot.
Make sure its executable.
```
$chmod +x /etc/rc.d/rc.local
```

I've got **rc0.d** up to **rc5.d**, but no **rc.d** folder :(

---

### Post by jtarin on 2010-08-12
My bad...that's my Slackware location. Ubuntu is  **/etc/rc.local**,so the command after changing to make executable would be ```
$chmod +x /etc/rc.local
```

---

### Post by Elmer Fudd on 2010-08-12
> **MadsRH said:**
> Did this solve your problem **hebebl**? 



I've got exactly the same issue (upgraded from 9.04), but your fix isn't working :(
If I remember correctly I might have edited some files manually. Could that be why StartUp-manager has no effect?

Since HEBEBL hasn't checked in since last november, I guess we are dealing with MadsRH problem now.

May I ask what it is in StartupManager that is not working. Is it everything or just the Default OS choice function?

Do you know if you are running GRUB, GRUB2 or BURG?

---

### Post by MadsRH on 2010-08-13
**jtarin**: Thanks, I'll give it a try.

> **Elmer Fudd said:**
> Since HEBEBL hasn't checked in since last november, I guess we are dealing with MadsRH problem now.

May I ask what it is in StartupManager that is not working. Is it everything or just the Default OS choice function?

Do you know if you are running GRUB, GRUB2 or BURG?

None of the settings I change (= everything) in StartupManager have any effect, but it shows the correct options in the *Default OS* dropdown menu.

Good question about the version. **GRUB 1.97 beta4**

---

### Post by Elmer Fudd on 2010-08-13
OK. So your using grub2. Lets first see if you can change the startup order with some edits and then try and figure out what is going on with the startup manager.

When your grub menu comes up, decide which one you want to boot by default. Note its position in the list.
If you want to boot windows and it is the 4th item in the list then

```
gksu gedit /etc/default/grub
```

and replace the value of GRUB_DEFAULT=  with 3 - one less than the position of your choice on the list. 
(The default is usually 0 and points to the last linux kernel to which you updated)
Save and close gedit.

```
sudo update-grub
```

Reboot. Let Grub timeout to the default and see if your chosen image boots. 
I believe that:
If it does not then we have a Grub issue. 
If it does, then a StartupManager issue.

---

### Post by MadsRH on 2010-08-14
**jtarin **-> Didn't work.

**Elmer Fudd** -> Thanks for the thorough explanation :-D When I open *gedit * the file reflects the changes I've made in Startup-Manager (GRUB_DEFAULT=4 , 11 sec timeout), but during the boot there's no change. So this must be a Grub issue :(

---

### Post by jtarin on 2010-08-14
> **MadsRH said:**
> **jtarin **-> Didn't work.

**Elmer Fudd** -> Thanks for the thorough explanation :-D When I open *gedit * the file reflects the changes I've made in Startup-Manager (GRUB_DEFAULT=4 , 11 sec timeout), but during the boot there's no change. So this must be a Grub issue :(
Yea I misread your post. I thought you had an application to run after boot.

---

### Post by MadsRH on 2010-08-15
**Elmer Fudd** did you have any suggestions to how I can fix GRUB?

---

### Post by JKyleOKC on 2010-08-15
Did you remember to do the "sudo update-grub" after making the changes to the defaults? I almost always forget this step myself, being in a hurry to see the effect of my changes -- and without it, the changes to the file have no effect on the actual grub actions.

Sometimes it even takes me a couple of restarts to figure out what I forgot to do!

---

### Post by MadsRH on 2010-08-15
> **JKyleOKC said:**
> Did you remember to do the "sudo update-grub" after making the changes to the defaults? I almost always forget this step myself, being in a hurry to see the effect of my changes -- and without it, the changes to the file have no effect on the actual grub actions.

Sometimes it even takes me a couple of restarts to figure out what I forgot to do!

Could have been, but no I didn't forget that thanks to **Elmer Fudd**s thorough explanation (#9)
:(

---

### Post by Elmer Fudd on 2010-08-16
> **MadsRH said:**
> **Elmer Fudd** did you have any suggestions to how I can fix GRUB?

Haven't seen an unfixable one yet.

Sorry for being offline. Am a pilot and have been tied up with some international operations.

Just so we are clear.
-The OS that you want to boot is the 5th one one the GRUB menu, so you put in GRUB_DEFAULT=4 when you edited /etc/default/grub
-After that you did an "sudo update-grub" with no error messages.
-You then re-booted and let it time out- and the first OS, not the 5th one, on the list Booted.

Was this a clean install or an ugrade from a previous (which) version of Ubuntu?

Please post /etc/default/grub and /boot/grub/grub.cfg

Also the latest GRUB-PC (GRUB2) package is 1.98. Have you run update manager lately? It should show up.

---

### Post by MadsRH on 2010-08-17
> Haven't seen an unfixable one yet.
Sounds good ;-D

> Sorry for being offline. Am a pilot and have been tied up with some international operations.
Well, I'm just happy someone wants to help me.

> Just so we are clear.
-The OS that you want to boot is the 5th one one the GRUB menu, so you put in GRUB_DEFAULT=4 when you edited /etc/default/grub
-After that you did an "sudo update-grub" with no error messages.
-You then re-booted and let it time out- and the first OS, not the 5th one, on the list Booted.

Was this a clean install or an ugrade from a previous (which) version of Ubuntu?
Right, I'm not sure but I think it was a upgrade from 9.04 -> 9.10 -> 10.04

> Please post /etc/default/grub and /boot/grub/grub.cfg


```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=4
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=11
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" splash quiet vga=771"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"
```

```
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set 13bc9d39-9d1b-4957-aeed-2000b7b7de91
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 13bc9d39-9d1b-4957-aeed-2000b7b7de91
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=13bc9d39-9d1b-4957-aeed-2000b7b7de91 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 13bc9d39-9d1b-4957-aeed-2000b7b7de91
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=13bc9d39-9d1b-4957-aeed-2000b7b7de91 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda3)" {
	insmod ntfs
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set b62c67f82c67b1d3
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
```

Also the latest GRUB-PC (GRUB2) package is 1.98. Have you run update manager lately? It should show up.[/QUOTE]

Update manager is up to date.

> [B]$ grub --version
grub (GNU GRUB 0.97)[/B]

---

### Post by JKyleOKC on 2010-08-17
That version of grub indicates that you have the original, not grub2. Look in your /boot/grub directory for the file menu.lst; if it's there, use ```
gksudo gedit /boot/grub/menu.lst
```to edit it. Near the front of the file you'll see a line "default=0" and you should change the "0" to "4" to get what you want. Save the file, run "sudo update-grub" again, and it should be working.

You must have upgraded your version from one of the older ones that was in place before the switch to grub2. That would have kept the older grub in place rather than replacing it. You can keep it indefinitely, but be sure to tell folk you have "legacy grub" if you have more problems since the cures are very different from one version to the other.

---

### Post by Elmer Fudd on 2010-08-17
In your response to my first question you noted that

> Good question about the version. GRUB 1.97 beta4
 
How did you determine that?

You do appear to have the original Grub installed from 9.04, but also all the config files for grub2 (grub-pc).

Also your grub2 files show that the latest kernel you have is 2.6.31-14.
I believe that the latest stable version is 32-24.

Checking your System monitor will probably confirm (if you have 32-24) that when you "update-grub" you are updating the /boot/grub/menu.lst as JKyleOKC points out.

Per JKyleOKC, editing the /boot/grub/menu.lst should fix your existing issue and, while I have all my systems and clients running burg for the nicer interface, I don't see any compelling reason for you to upgrade from grub to grub2.

---

### Post by Elmer Fudd on 2010-08-17
And back to your original problem "startup manager not working".

Startup manager appears to be tied to the partial implementation of grub-pc.
So, after you edit menu.lst and find that things are working, you might want to remove grub-pc and reinstall startup manager.

---

### Post by MadsRH on 2010-08-17
Thanks for all the feedback guys :-D

> **Elmer Fudd said:**
> How did you determine that?

During boot this version number is displayed at the top of the screen.

/boot/grub/menu.lst
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
**default		4**

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
**timeout		3**

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
# kopt=root=UUID=13bc9d39-9d1b-4957-aeed-2000b7b7de91 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=13bc9d39-9d1b-4957-aeed-2000b7b7de91

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

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic
uuid		13bc9d39-9d1b-4957-aeed-2000b7b7de91
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=13bc9d39-9d1b-4957-aeed-2000b7b7de91 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-24-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic (recovery mode)
uuid		13bc9d39-9d1b-4957-aeed-2000b7b7de91
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=13bc9d39-9d1b-4957-aeed-2000b7b7de91 ro  single
initrd		/boot/initrd.img-2.6.32-24-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.31-14-generic
uuid		13bc9d39-9d1b-4957-aeed-2000b7b7de91
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=13bc9d39-9d1b-4957-aeed-2000b7b7de91 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.31-14-generic (recovery mode)
uuid		13bc9d39-9d1b-4957-aeed-2000b7b7de91
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=13bc9d39-9d1b-4957-aeed-2000b7b7de91 ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Chainload into GRUB 2
root		13bc9d39-9d1b-4957-aeed-2000b7b7de91
kernel		/boot/grub/core.img

title		Ubuntu 10.04.1 LTS, memtest86+
uuid		13bc9d39-9d1b-4957-aeed-2000b7b7de91
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
```

This file doesn't reflect the options displayed in GRUB at boot :-k

System monitor says 2.6.31-14.

---

### Post by Elmer Fudd on 2010-08-17
Looks like update-grub is updating your legacy grub, as reflected in your menu.lst.
It also shows that the 2.6.32-24-generic image is on your system.

You are appearantly not using the legacy grub as the loader if you are actually loading 2.6.31-14 which is what grub2 is setup to boot.

Just to confirm some of this.
SYSTEM/ADMINISTRATION/SYNAPTIC PACKAGE MANAGER
In the quick search box type [COLOR="RoyalBlue"]grub[/COLOR]
In the left box selec Installed.
Are both grub (0.97-29) and grub-pc (1.98-1) installed?

Then in the quick-search box type [COLOR="Blue"]linux-image[/COLOR].
Again with Installed selected on the left,
How many/what images are installed?

Try update-grub2

Found this explanation on upgrading from legacy to grub2. 
You seem to be suffering the symtoms of a partial upgrade to grub2.

[http://www.howtoforge.com/how-to-install-grub-2-on-ubuntu-9.04](http://www.howtoforge.com/how-to-install-grub-2-on-ubuntu-9.04)
Don't do anything until you read the users comments.

---

### Post by Elmer Fudd on 2010-08-17
I have installed Burg as a replacement to grub in all the systems that I support. It has, for reasons unknown to me, fixed various issues. I install it cuz it is a much more elegant interface. I am a little reluctant to install it on systems to which I do not have physical access- just in case there are dual-boot issues.

If you want to try burg. First download and burn and test a supergrub disk.

[http://prdownload.berlios.de/supergrub/super_grub_disk_hybrid-1.98s1.iso](http://prdownload.berlios.de/supergrub/super_grub_disk_hybrid-1.98s1.iso)

in case there are problems with the install.

then

```
gksu gedit /etc/apt/sources.list 
```

add these lines to the file

deb [http://ppa.launchpad.net/bean123ch/burg/ubuntu](http://ppa.launchpad.net/bean123ch/burg/ubuntu) lucid main
deb-src [http://ppa.launchpad.net/bean123ch/burg/ubuntu](http://ppa.launchpad.net/bean123ch/burg/ubuntu) lucid main

save and close..
then

```
sudo apt-get update
sudo apt-get install burg

```
These commands should stop warnings about unknown signatures.

```
gpg --keyserver keyserver.ubuntu.com --recv 55708F1EE06803C5
gpg --export --armor 55708F1EE06803C5 | sudo apt-key add -

```

(assuming install to the first hard drive..)
then the normal(note next item) install is 
```
sudo burg-install /dev/sda
sudo update-burg
```
but I have had less problems with losing some dual boots using
```
burg-install --alt /dev/sda
sudo update-burg
```

reboot

At the burg boot menu, play with the following commands.
    * t - Open theme selection menu
    * f - Toggle between folding mode
    * h - Display help dialog
    * F9 - shutdown
    * F10 - reboot
    * ESC - quit from the current popup menu or dialog. 
    * r - resolution


also available
    * e - Edit the command of current boot item
    * c - Open a terminal window
    * 2 - Open two terminal windows
    * i - Display about dialog 
    * q - Return to old grub menu
    * F5/ctrl-x - Finish edit
    * F6 - Switch window in dual terminal mode
    * F7 - List the folded boot items
    * F8 - Toggle between graphic and text mode

---

### Post by QLee on 2010-08-18
[QUOTE=Elmer Fudd]...
You seem to be suffering the symtoms of a partial upgrade to grub2.
...[/QUOTE]

From the symptoms stated by MadsRH, I agree with this diagnosis. Looks like the second part of the upgrade wasn't carried out after verifying chainload, the part where GRUB2 was supposed to be written to the MBR, so the system is still booting from the legacy GRUB MBR info. Probably could be cleaned up with an upgrading GRUB to GRUB2, GRUB2 install to the MBR, update-grub, and probably manual deletion of the old GRUB files.

---

### Post by MadsRH on 2010-08-22
Hi again *(sorry for the slow reply)*

grub-pc is not installed. I can't do a update-grub2 :-(

[ATTACH]167197[/ATTACH]

[ATTACH]167198[/ATTACH]

I think I'll wait a bit with the Burg installation and get things running (if possible) with Grub first. But thanks for the guide (must try it on my other machine)

It seems like it's very risky business to fix this issue and messing with the MBR.

---

### Post by QLee on 2010-08-22
Sorry, when I wrote, " upgrading GRUB to GRUB2", I thought that implied installing GRUB2. That's what I meant. I think somehow you missed this step during your upgrade. You'll need to find some way to get the GRUB version and the startup manager version to be for the same Ubuntu version if you want the GUI to work as well as it can and you need "update-grub" to be the one that updates your install grub.cfg.


Edit: 
Shouldn't need to mess with MBR, just install and update-grub.

From your symptoms looks like GRUB2 did get installed correctly to MBR, just not to your system, it's booting correctly just not GRUB updating correctly.

---

### Post by MadsRH on 2010-08-22
> **QLee said:**
> ...
Shouldn't need to mess with MBR, just install and update-grub.

From your symptoms looks like GRUB2 did get installed correctly to MBR, just not to your system, it's booting correctly just not GRUB updating correctly.

Okay, do you have any idea how I can do this? Do you mean *sudo apt-get install grub2*

---

### Post by QLee on 2010-08-22
[QUOTE=MadsRH]Okay, do you have any idea how I can do this? Do you mean *sudo apt-get install grub2*[/QUOTE]

Well, you could do that. By the way, if you use apt-get with the , -s, option, it will just show you what the system proposes to do, not actually carry out the actions. However, you showed a couple of pictures of Synaptic, so I thought you might use that for installing grub-pc. The install should remove the legacy GRUB but you still might have to remove menu.lst and any of those old GRUB files manually.

---

### Post by desiinus on 2011-07-24
> **MadsRH said:**
> Okay, do you have any idea how I can do this? Do you mean *sudo apt-get install grub2*

Hopefully the startup manager issue was resolved for hebebl. I found a solution to this issue by observing that startup manager was not updating the default OS number to the correct number. Instead of counting from 0, it was counting from 1. I fixed this by updating the default number to the right number, i.e. reduce the number updated by startup manager by 1. My startup manager was defaulting to 6; I made it 5. I am running Ubuntu 11.04; my Grub version is 1.99. Just thought I would share my solution. It has worked so far. All the best to hebebl or anyone trying to resolve this issue!

---

### Post by Piney on 2011-08-01
> **desiinus said:**
> Hopefully the startup manager issue was resolved for hebebl. I found a solution to this issue by observing that startup manager was not updating the default OS number to the correct number. Instead of counting from 0, it was counting from 1. I fixed this by updating the default number to the right number, i.e. reduce the number updated by startup manager by 1. My startup manager was defaulting to 6; I made it 5. I am running Ubuntu 11.04; my Grub version is 1.99. Just thought I would share my solution. It has worked so far. All the best to hebebl or anyone trying to resolve this issue!

THANK YOU desiinus :D
I've had an issue with the defult boot option not being selected on boot.

Your suggestion fixed it for me :D.

I just selected the boot option before the one I wanted and now it defults the the right one.

---

