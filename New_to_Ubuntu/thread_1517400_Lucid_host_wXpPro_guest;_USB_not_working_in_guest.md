---
title: "Lucid host w/XpPro guest; USB not working in guest"
date: 2010-06-25
forum: New to Ubuntu
---

### Post by nikola43 on 2010-06-25
Running Lucid 64bit with XpPro/sp2 as a guest,using Virtual Box 3.2.4 r62467 (Oracle)-I'm a "vboxuser" and the usb device I'm trying to use in the VM is on the usb list in the quest, along with all the other usb devices on the machine, but is greyed-out ("unavailable"). I've tried several suggestions found in the forums and others places and nothing works so far. I know this subject has been dealt with, but most of what is said about how to make it work doesn't make sense to me. 

What I need is a step-by-step procedure to get the guest to use all the resources of the host.

I tried starting VB as su as suggested in several places I visited, but it comes back with "command not found" or vbox "not installed...apt-get...ose...", etc. First of all, I don't want to use OSE (or I wouldn't have installed the Oracle files). How do I start VB from the command line anyway--and if I do, how's that help?

I thought the latest version of Ubuntu and the latest version of VB was supposed to have solved this problem...I've been dinkin with it now since about 4 or 5 versions back. I've read dozens and dozens of threads about it, but can't seem to solve anything.

Surely someone has a solution that's easy enough to use for us folks who are relatively new to all this geek stuff (and lovin it!)!

---

### Post by Ocxic on 2010-06-25
make sure you have the NON-OSE version, and after adding yourself to the "vboxuser" group you must logout and back in.

---

### Post by nikola43 on 2010-06-25
Oracle is the non-ose version and I did log out/back in (several times)trying stuff

---

### Post by Ocxic on 2010-06-25
try this: (from the VBox Manual)
```

12.6.7 USB not working
If USB is not working on your Linux host, make sure that the current user is a member
of the vboxusers group. On older hosts, you need to make sure that the user has
permission to access the USB filesystem (usbfs), which VirtualBox relies on to retrieve
valid information about your host&#8217;s USB devices. The rest of this section only applies
to those older systems.

Note: The current rdesktop-vrdp implementation does not support accessing
USB devices through the sysfs!
As usbfs is a virtual filesystem, a chmod on /proc/bus/usb has no effect. The
permissions for usbfs can therefore only be changed by editing the /etc/fstab file.
For example, most Linux distributions have a user group called usb or similar, of
which the current user must be a member. To give all users of that group access to
usbfs, make sure the following line is present:
# 85 is the USB group
none /proc/bus/usb usbfs devgid=85,devmode=664 0 0

Replace 85 with the group ID that matches your system (search /etc/group for &#8220;usb&#8221;
or similar). Alternatively, if you don&#8217;t mind the security hole, give all users access to
USB by changing &#8220;664&#8221; to &#8220;666&#8221;.
The various distributions are very creative from which script the usbfs filesys-
tem is mounted.
Sometimes the command is hidden in unexpected places.

For SuSE 10.0 the mount command is part of the udev configuration file
/etc/udev/rules.d/50-udev.rules. As this distribution has no user group called
usb, you may e.g. use the vboxusers group which was created by the VirtualBox
installer. Since group numbers are allocated dynamically, the following example uses
85 as a placeholder. Modify the line containing (a linebreak has been inserted to
improve readability)
DEVPATH="/module/usbcore", ACTION=="add",
RUN+="/bin/mount -t usbfs usbfs /proc/bus/usb"
and add the necessary options (make sure that everything is in a single line):
DEVPATH="/module/usbcore", ACTION=="add",
RUN+="/bin/mount -t usbfs usbfs /proc/bus/usb -o devgid=85,devmode=664"
Debian Etch has the mount command in /etc/init.d/mountkernfs.sh. Since
that distribution has no group usb, it is also the easiest solution to allow all members
of the group vboxusers to access the USB subsystem. Modify the line 

domount usbfs usbdevfs /proc/bus/usb -onoexec,nosuid,nodev

so that it contains

domount usbfs usbdevfs /proc/bus/usb -onoexec,nosuid,nodev,devgid=85,devmode=664

As usual, replace the 85 with the actual group number which should get access to USB devices.
Other distributions do similar operations in scripts stored in the /etc/init.d directory.

```

---

### Post by nikola43 on 2010-06-25
I've read the stuff in the VB manual and it doesn't appear to relate the latest version (3.2.4)even though when looking for the 3.2.4 manual, this is where you end up. In any case, none of this makes any sense to me-as I said in the post, I am in the vboxuser group and have permissions, as far as I can tell.

Also, my post is not about USB not working in the HOST, its about not working in the guest....  :confused:

---

