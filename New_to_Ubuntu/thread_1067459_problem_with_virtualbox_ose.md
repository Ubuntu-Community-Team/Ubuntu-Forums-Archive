---
title: "problem with virtualbox ose"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by bahsarie on 2009-02-11
I installed virtual box ose to try to run SPSS, since it was not working well with wine. However I can not get virtual box to run. It gives me the following message when it fails to start the machine.

VERR_VM_DRIVER_NOT_INSTALLED (rc=-1908)
The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Re-setup the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu or Fedora should install the DKMS package at first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.

however i can not find the driver nor the dkms package in synaptic package manner.

---

### Post by Vaedrah on 2009-02-11
I have Virtual Box on 3 machines - also from a XP OS and Ubuntu 8.04 OS. Neither complain - the "dkms" thing is needed for "guest additions" - these let you file share etc, but you don't need dkms to install Virtual Box.

Did you download the correct version? There are two - the web site tells of the download that works ("PUEL" version the other version isn't what you want)

I find that Virtual Box "just works" - there is no need for special "tweaks" - however to use the USB ports you need to set this up in "System" / Ubuntu so you are added as a "user" to the "usb group" - stupidity +++ in my mind but so there it will stay. 

The "guest additions" are a bit silly-billy also but don't stop the installation. If the installation fails it may be a hardware inadequacy or some other fault. But then, I can only report from hands on (my own) experience with these things :popcorn:

---

### Post by bahsarie on 2009-02-11
thanks but that was really no help

---

### Post by theApokalypsis on 2009-02-12
I believe it could be just a permissions thing, where you need to add the vboxdrv user to the root group i.e. give it root privileges so it can boot the machine.

I can recall once i had to do that to get any machines running.

good luck!

---

### Post by Vaedrah on 2009-02-12
I suggest this to you - if you have a problem and no-one else does the problem is at YOUR END.

Get a new machine or fix the hardware fault you have,

otherwise no-one here is at blame for your hardware

---

### Post by bahsarie on 2009-02-12
> **theApokalypsis said:**
> I believe it could be just a permissions thing, where you need to add the vboxdrv user to the root group i.e. give it root privileges so it can boot the machine.

I can recall once i had to do that to get any machines running.

good luck!

How do i do that?

Vaedrah, your comment makes no sense what so ever. There has to be a first time for every problem. Software is inherently buggy. That is why there are constant upgrades and patches coming out. To tell someone to get new hardware because it does not work makes no sense most people are here to help you to get it to work with your current hardware. Please do not leave messages if they are not going to be helpful.

---

### Post by Vico Vicario on 2009-02-12
Did you add the user to group vboxusers?
If not do 'sudo usermod -a -G vboxusers <user>' where <user> is the login name of the user.

V.

---

### Post by bahsarie on 2009-02-12
did not work but thanks

---

