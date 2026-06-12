---
title: "Need help with latest VirtualBox! (3.0.6)"
date: 2009-09-22
forum: New to Ubuntu
---

### Post by azzronulation on 2009-09-22
I want to activate my USB External Hard Drive, but its currently Greyed Out! 

Help me get VirtualBox to detect my USB EHDD.

---

### Post by scrooge_74 on 2009-09-22
I think you need to enable them before you start the machine, you need to make a filter or something first before enabling them.

Go to the setups for the machine and put them there

---

### Post by Geoff918 on 2009-09-22
Here's the 64-dollar question: Are you using VirtualBox or VirtualBox OSE?

VirtualBox OSE does not support USB devices.

VirtualBox does support USB devices, and you need to go to the settings on the Virtual Drive and there should be a setting for "Enable:" and that will have a list of things. One of those will be USB, you need to select that.

If you've done all that (and yes, I admit given your description you may have) then what OS are you running in VirtualBox and how is your external HDD formatted (ntfs, fat16, fat32, ext2, ext3, ext4, jfs, reiserfs, etc.)?

---

### Post by azzronulation on 2009-09-22
I'm in desperate need of finding out how to attatch a "greyed out" USB device?

I have the most recent VirtualBox & Ubuntu

& i am running Vista on the VB.

help!

---

### Post by ~sHyLoCk~ on 2009-09-22
Are you using Virtualbox OSE or PUEL? I think PUEL has the USB support that OSE lacks.

---

### Post by azzronulation on 2009-09-22
I'm running the PUEL version, the evaluation one?

---

### Post by overdrank on 2009-09-22
Hi and welcome, please do not create multiple threads on the same issue. Threads merged.

---

### Post by ~sHyLoCk~ on 2009-09-22
> **azzronulation said:**
> I'm running the PUEL version, the evaluation one?

The PUEL version shouldn't have USB devices greyed out. No clue sorry. :confused:

---

### Post by azzronulation on 2009-09-22
bah! no worries, thanks. :)

---

### Post by Darkwing-Duck on 2009-09-23
Here is more information on Virtual Box too. Maybe there is something in there that can help you out.

[http://gwos.org/udsf/doku.php/software:virtualbox](http://gwos.org/udsf/doku.php/software:virtualbox)

---

### Post by lkraemer on 2009-09-23
First of all, Download the manual for the PUEL version from their
website and start reading the manual.  It's all in there, or posted
on their FAQ.  You can also use Google to search for a HOWTO: or search 
this forum, in which case you will find:

Setup USB:
USB is disabled by default, so you'll probably want to enable it. Otherwise you'll get an error when you go into the "Settings" of your virtual machine. To correct this, you'll need to edit the mountdevsubfs.sh file:

[In Terminal]
```

sudo gedit /etc/init.d/mountdevsubfs.sh

```
Inside, you'll see a block of code that looks like this:
```

    #
    # Magic to make /proc/bus/usb work
    #
    #mkdir -p /dev/bus/usb/.usbfs
    #domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
    #ln -s .usbfs/devices /dev/bus/usb/devices
    #mount --rbind /dev/bus/usb /proc/bus/usb

```
Change it to look like this (uncomment out the region by deleting the "#'s"):
```

    #
    # Magic to make /proc/bus/usb work
    #
    mkdir -p /dev/bus/usb/.usbfs
    domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
    ln -s .usbfs/devices /dev/bus/usb/devices
    mount --rbind /dev/bus/usb /proc/bus/usb

```
Save the changes, log out, and then log back in again for the changes to take place.

ref:
[http://ohioloco.ubuntuforums.org/showthread.php?t=770745](http://ohioloco.ubuntuforums.org/showthread.php?t=770745)

Make sure you follow their full instructions, and don't miss anything.

Google is your friend!

lk

---

### Post by azzronulation on 2009-09-23
I've come across this solution and unfortunately when i put


```
sudo gedit /etc/init.d/mountdevsubfs.sh 
```I don't get 

 ```
#
    # Magic to make /proc/bus/usb work
    #
    #mkdir -p /dev/bus/usb/.usbfs
    #domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
    #ln -s .usbfs/devices /dev/bus/usb/devices
    #mount --rbind /dev/bus/usb /proc/bus/usb
```
its something completely different all together```
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
```that is all that's in the file, should i add the code you provided into this?

---

### Post by azzronulation on 2009-09-23
I've read somewhere that the older version has no problems with USB so how would i possibly downgrade VirtualBox?

also are their any other virtual OS programs that are similar?

---

### Post by lkraemer on 2009-09-23
What version of Ubuntu are you using?  Maybe they changed the location
of the file, or it is a different file on later versions?  I am using
8.04LTS.

lk

---

### Post by PhilGil on 2009-09-23
I've had this problem - I think that you're not yet a member of the vboxusers group.  You're prompted to do this during the install but it doesn't always work.

I'm sure this can be done via the command line, but I'm a GUI guy so here goes...

1. Click on System --> Administration --> Users and Groups

2. When the Users Settings window opens, click the "Unlock" button and enter your admin password and click the "Authenticate" button.

3. After returning to the Users and Groups window, click the "Manage Groups" button.

4. Scroll down and select "vboxusers" (if it exists) and click the "Properties" button.  If the group does not yet exist create it by clicking on the "Add Group" button.

5. In the Properties window, click in the box next to your user name (this will place a check mark in the box).

You may have to log out and back in to Ubuntu for this change to become effective.

HTH

---

### Post by azzronulation on 2009-09-23
USB Devices greyed out or unavailable problem SOLVED.

How to allow VirtualBox to read and write USB Devices

Solution Thanks to Perryg on the Sun VirtualBox Forums..

First in terminal

```
sudo -i
```then

```
cd /etc
```then type

```
gedit fstab
```Then add this code to the bottom of fstab

```
none /sys/bus/usb/drivers usbfs devgid=501,devmode=664 0 0
```replace the 501 with the actual number that the vboxusers group has.

Find this by System > Administration > Users and Groups

Click "Unlock" and enter password when prompted

Click on "Manage Groups" on the right hand side

Scroll down until you find "vboxusers" and double click

Then "Group ID" is the second box down

Make sure that you are in the vboxusers group by running the following
```
usermod -aG vboxusers <your username>
```Or make sure you're username is ticked when finding "Group ID"

ref:
[http://forums.virtualbox.org/viewtopic.php?f=7&t=22702](http://forums.virtualbox.org/viewtopic.php?f=7&t=22702)

---

