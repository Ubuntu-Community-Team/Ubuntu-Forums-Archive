---
title: "Wubi issues"
date: 2009-07-17
forum: New to Ubuntu
---

### Post by FunkySpider on 2009-07-17
I installed Ubuntu using Wubi a couple of months ago and have to say I love it. Unfortunately when Vista SP2 as released the only way i seemed to be able to install the service pack properly was to uninstall Ubuntu which really annoyed me. I tried to reinstall Ubuntu using Wubi recently and the install seemed to run fine the CD ejected and it asked to restart yet there was no boot screen which really annoyed me, i tried looking it up but to no avail. No solid solutions anyhow. Anyone know why this is happening? I run a Acer Aspire M3640 and was installing from a CD i made myself which worked the first time. Hope someone can help :)

---

### Post by AndThenWhat on 2009-07-17
No boot screen meaning it didn't have the ubuntu logo with a loading bar?

---

### Post by darolu on 2009-07-17
> **FunkySpider said:**
> I installed Ubuntu using Wubi a couple of months ago and have to say I love it. Unfortunately when Vista SP2 as released the only way i seemed to be able to install the service pack properly was to uninstall Ubuntu which really annoyed me. I tried to reinstall Ubuntu using Wubi recently and the install seemed to run fine the CD ejected and it asked to restart yet there was no boot screen which really annoyed me, i tried looking it up but to no avail. No solid solutions anyhow. Anyone know why this is happening? I run a Acer Aspire M3640 and was installing from a CD i made myself which worked the first time. Hope someone can help :)

Seems like the SP2 rewrote the MBR with windows' booter, so I think you need to reinstall GRUB.
I'm not familiar with Wubi installations so this steps may change a little (the devices part) but this what you usually do to restore GRUB: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

In short, boot with the LiveCD and open a terminal and do:
```
sudo grub
```
then:
```
find /boot/grub/stage1
```
Then depending on the info it gave you:
```
grub> root (hdX,Y)
```
and then you install GRUB:
```
grub> setup (hdX)
```
finally exit grub:
```
grub> quit
```
Then you can reboot without liveCd; if you need to make changes to GRUB:
```
gksu gedit /boot/grub/menu.lst
```
or with the startupmanager.

---

### Post by earthpigg on 2009-07-17
WUBI installs do not use GRUB.

**_FunkySpider, do not do what darolu just told you to do._**

i have no idea what you should do to fix your problem, since i have never used WUBI, but i know it will not involve 'standard' directions for fixing an MBR with GRUB on it.... WUBI uses the Windows Bootloader, not GRUB.

(Windows Bootloader is the Windows Equivelent of the GRand Universal Bootloader [GRUB], the most common linux bootloader)

---

### Post by steveneddy on 2009-07-17
My experience:

I have never used Wubi, but I under stand that it is a way to TRY out Ubuntu BEFORE you actually install it.

My suggestion:

is to partition your harddrive and dual boot

OR:

install Virtualbox for Windows (free) and install Ubuntu on virtualbox while it run under Windows.

I believe Windows and Ubuntu will run better and faster and you won't be compromised by two OS's potentially "messing with" the others.

I use Virtualbox on Ubuntu to run XP and Vista and it runs very well with no noticeable degradation of performance on either OS.

Note:

I have 2 Gig RAM and assign 512 mb to XP and 768 mb to Vista

---

### Post by AndThenWhat on 2009-07-17
Just to clarify Wubi is an installation of Ubuntu that uses a virtual hard disk (a file on the windows hard drive).  I also believe that wubi does use Grub, however it probably works differently than a hard install because of the setup.

---

### Post by earthpigg on 2009-07-17
this is not GNU GRUB.

[IMG]http://www.dedoimedo.com/images/computers/wubi-bootloader.jpg[/IMG]

---

### Post by lisati on 2009-07-17
The rare occasion I've had a wubi install on any of my machines, the initial bootloader screen is similar to what earthpigg posted, and only if I have chosen Ubuntu, does it go to a version of grub.

---

### Post by pizza-is-good on 2009-07-17
Are you able to get inot windows at all?

---

