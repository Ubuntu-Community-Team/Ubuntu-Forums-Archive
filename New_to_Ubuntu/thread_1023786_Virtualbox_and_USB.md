---
title: "Virtualbox and USB"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by catniko on 2008-12-28
Hi,  I got an Ipod Touch for xmas and want to use it with Itunes on my linux computer.  I have Ubuntu 8.10 -Intrepid installed.

I was able to get VirtualBox (the free but not opensource version) installed and have XP running in it and Itunes installed with in XP.  It seems to work pretty good.  However, VirtualBox gives me this error message regarding USB use:

Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.

I had put this version of Virtual box on my computer because I saw within this forum that it works well with USBs.

Help please!

Thanks.

---

### Post by albinootje on 2008-12-28
> **catniko said:**
>  Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.


[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)
Scroll down to the USB section.

More options here :
[http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html](http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html)
In the "Setup VirtualBox USB Support" part.

---

### Post by scorp123 on 2008-12-28
To get USB with the "PUEL" edition of VirtualBox working you'd need to have this line in **/etc/fstab** (e.g. you could put this at the bottom of the file) ...
```
none  /proc/bus/usb   usbfs   devgid=46,devmode=664    0   0
```

EDIT:  This is assuming you have Ubuntu 8.10 installed .... 
.
.
.
.

---

### Post by catniko on 2008-12-28
I've tried both of your suggestions and some others.  I found that I don't have a usergroup created for using the usb.  I am thinking that I may have to remove it all and start from scratch again and be more mindful of setting up a virtual system.

Thank you for your help though.  I am going to research a bit before I do anything.  Guess I am learning more about working with Linux.

---

### Post by albinootje on 2008-12-28
> **catniko said:**
> I've tried both of your suggestions and some others.  I found that I don't have a usergroup created for using the usb.  I am thinking that I may have to remove it all and start from scratch again and be more mindful of setting up a virtual system.

Please don't start installing Ubuntu from scratch only because you think you don't have a group for usb.

You should have the group called vboxusers, and you can use the so-called gid of that group vboxusers to make the usb work for VirtualBox.

You can check in which groups your user is with the command :
```

groups

```

You can try adding the following line to your /etc/fstab file :

## usbfs is the USB group in fstab file:
none /proc/bus/usb usbfs devgid=124,devmode=664 0 0

And then type :
```

sudo mount -a

```
And try restart VirtualBox, and test usb.

[edited -> ]
In 8.10 I didn't have a group called vboxusers, but do have a group with gid 124 called sambashare and it now it works.

---

### Post by Michaelg14 on 2008-12-29
Most of the things required in earlier versions of Ubuntu to get usb working in Vbox are no longer required.  The line for fstab already given and a group called vboxusers is required and possibly a group called usbusers.  Make sure the divgid= is set to the number of your vboxuser group ID in your fstab file.

Nothing else is needed and in fact anything else will just mess it up.

YMMV

---

### Post by bumanie on 2008-12-29
As far as I am aware, vbox ose version doesn't have usb support (at least it never used to) - only the proprietary version does. As home user you can use the proprietary version under the terms of the 'free for home use'.

---

### Post by Master Chief on 2008-12-30
> **catniko said:**
> ...I was able to get VirtualBox (the free but not opensource version) installed and have XP running in it and Itunes installed with in XP.  It seems to work pretty good.

Not if you want CoverFlow support in iTunes, which currently only works with VMWare's player/workstation editions.

p.s. Just to be sure; how/which version of VirtualBox did you install?

---

### Post by catniko on 2008-12-31
Hi,  I installed the non opensource version of Virtualbox.

I ended up re-installing it.  Have not had the time to do xp and itunes on it yet.

---

### Post by catniko on 2008-12-31
Would VMWare be better for Itunes?

---

### Post by bumanie on 2008-12-31
I haven't used vbox for a while and have never used vmware, but this [tutorial ]("http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html")will help you set up usb support for vbox - it's a bit old, but still works asfaik.

---

### Post by Master Chief on 2008-12-31
> **catniko said:**
> Would VMWare be better for Itunes?

Let me start by stating that I am a huge fan of VirtualBox, but the lack of CoverFlow for iTunes forced me to install VMWare, and boy am I glad that I did it, yet I won't remove VirtualBox ;)

---

### Post by catniko on 2009-01-02
when I run the 
sudo gedit /etc/init.d/mountdevsubfs.sh
command in terminal, I get the following which does not look like what the tutorial says I should get:

#! /bin/sh
### BEGIN INIT INFO
# Provides:          mountdevsubfs
# Required-Start:    mountkernfs
# Required-Stop:
# Should-Start:      udev
# Default-Start:     S
# Default-Stop:
# Short-Description: Mount special file systems under /dev.
# Description:       Mount the virtual filesystems the kernel provides
#                    that ordinarily live under the /dev filesystem.
### END INIT INFO
#
# This script gets called multiple times during boot
#

PATH=/lib/init:/sbin:/bin
TTYGRP=5
TTYMODE=620
[ -f /etc/default/devpts ] && . /etc/default/devpts

TMPFS_SIZE=
[ -f /etc/default/tmpfs ] && . /etc/default/tmpfs

KERNEL="$(uname -s)"

. /lib/lsb/init-functions
. /lib/init/mount-functions.sh

do_start () {
	#
	# Mount a tmpfs on /dev/shm
	#
	SHM_OPT=
	[ "${SHM_SIZE:=$TMPFS_SIZE}" ] && SHM_OPT=",size=$SHM_SIZE"
	domount tmpfs shmfs /dev/shm tmpfs -onosuid,nodev$SHM_OPT

	#
	# Mount /dev/pts. Master ptmx node is already created by udev.
	#
        domount devpts "" /dev/pts devpts -onoexec,nosuid,gid=$TTYGRP,mode=$TTYMODE
}

case "$1" in
  "")
	echo "Warning: mountdevsubfs should be called with the 'start' argument." >&2
	do_start
	;;
  start)
	do_start
	;;
  restart|reload|force-reload)
	echo "Error: argument '$1' not supported" >&2
	exit 3
	;;
  stop)
	# No-op
	;;
  *)
	echo "Usage: mountdevsubfs [start|stop]" >&2
	exit 3
	;;
esac

The tutorial says I should get:

something with this in it:

#
# Magic to make /proc/bus/usb work
#
#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb

Which is not what I am seeing.  I am obviously ignorant in Linux.  Any body have an idea what I may have done or am missing?

--Thanks!

---

### Post by albinootje on 2009-01-02
> **catniko said:**
>  Which is not what I am seeing.  I am obviously ignorant in Linux.  Any body have an idea what I may have done or am missing? 

Are you using 8.10 ? 
Here's a better and quicker solution :
[http://ubuntuforums.org/showthread.php?t=962726&highlight=virtualbox+fstab](http://ubuntuforums.org/showthread.php?t=962726&highlight=virtualbox+fstab)

---

### Post by catniko on 2009-01-02
Hello.  I have the usb showing as active now in Virtualbox.  However, when I hook the usb up within XP (within VB), I get the error message:

Unable to mount Apple, Inc Ipod
Error initializing camera: -60 
Could not lock the device.

---

### Post by catniko on 2009-01-04
Thanks for everyone's help.  I have the virtualbox running itunes now....

---

### Post by h3nk on 2009-01-06
so you are able to manage your ipod touch (fw version 2) with itunes via virtualbox? i also tried to, got virtualbox using my usb-devices, but virtual-windows-xp is complaining about driver-problems, when connecting my old ipod. i didn't dare to buy a new ipod touch so far, because i'm afraid i can't use it.

greetz

---

### Post by catniko on 2009-01-06
It took some trial and error.  The procedure to fix the USB  depends on which version of Ubuntu you have and which version of VirtualBox you get. 

The free but non proprietary (not open source) VirtualBox is the version that has the USB support and I have the most current Ubuntu (Intrepid 8.10).  Read the responses throughout this thread and you will see....

I am new to using a Linux OS and have found that this forum is very helpful.  I also looked up other places in Google to look at other places with similar info.  

I had to sync my Itouch to Itunes to get it usable.  I also have gotten some songs from Itunes downloaded.  I can also download them directly from the Itouch itself.  BUT...I really want to be able to use something else besides Itunes....and I still want to put my own music on it without using Itunes and will probably have to use another computer for that.

---

### Post by OldTimeTech on 2009-01-06
Actually according to other posts throughout the forums, you should be able to use your ipod with Amarok here in Ubuntu.

---

### Post by h3nk on 2009-01-07
i'm using intrepid with the closed source version of virtualbox. i also use vmware workstation which also perfectly works with other usb devices. my problem still is the old ipod i'm trying to connect. it doesn't even get recognized as usb mass storage device. 

is there something i can do to make my ipod communicate with virtual-windows?

---

### Post by bearTM on 2009-02-15
> **Master Chief said:**
> Let me start by stating that I am a huge fan of VirtualBox, but the lack of CoverFlow for iTunes forced me to install VMWare, and boy am I glad that I did it, yet I won't remove VirtualBox ;)

Well ... go back to VirtualBox ... Coverflow DOES work now!

Installing the latest build version into a WindowsXP SP3 [VirtualBox]("http://www.virtualbox.org/wiki/VirtualBox") VM hosted on Ubuntu Intrepid 8.10 (2.6.27-11 / AMD64 / Gnome 2.24.1 / Compiz enabled), permitted iTunes Coverflow to work! It's not quite moving at the speed of light, but works 100% properly, without fault on my system.

Just use the Wine D3D support in your Windows XP SP3 installation:
[http://wiki.winehq.org/WineD3DOnWindows](http://wiki.winehq.org/WineD3DOnWindows)

Download the latest version from here:
[http://aybabtu.com/rmh/wined3d/](http://aybabtu.com/rmh/wined3d/)

Also ... all of the other iPod (& Touch) related details like upgrading the firmware, etc. can also be entirely done through the VirtualBox VM. During the restore process, it is necessary to manually disconnect and reconnect the iPod through the USB control in VirtualBox - but this works flawlessly. Wait for the timeouts, the device changes in Device Manager, watch for when iTunes is obviously pausing to detect the device resets. Basically ... just take your time, and monitor your device manager/USB connections in both Windows XP & Ubuntu.

Cheers.

---

### Post by MonsterMaxx on 2009-11-10
I can't get coverflow to work.

XPSP3, w/ latest patches
iTunes 9.0.2.25

Tried Virtual box 3.0.8 and 3.0.10. 
Tried the vid driver w/ and w/o direct 3d
Tried various versions of the wine addin.

No joy.

Suggestions?

---

### Post by larsman1 on 2009-11-10
9.10 Karmic Koala: download the VirtualBox from Sun Micro's website.
[http://dlc.sun.com/virtualbox/vboxdownload.html](http://dlc.sun.com/virtualbox/vboxdownload.html)
1. before doing following steps, your virtual OS must be powered off.
2. click on the settings (gear) icon.
3. In the left column of settings, click on USB, then check the box Enable USB controller.
4. Have all your USB devices connected and turned on (printers, USB external drives, etc)
5. Click the green "+" USB icon and add all of your USB devices.

---

