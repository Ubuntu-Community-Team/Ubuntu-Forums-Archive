---
title: "Video problem with virtualbox"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by choko on 2009-02-02
I installed virtualbox-ose

Then the guide [https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

says to install virtualbox-ose-modules-`uname -r`

This package was not found, never mind (?) I continued

$virtualbox

Application seems ok, I create an ubuntu virtual disk
cdrom=iso file
start

Now, the box will start ok, but nothing is showing on
screen?

I then close the windows, as I do so, virtual pops up
a window asking if to save the session etc, at this 
very point the video behind the popup becomes visible

I am using 8.10 while the guide is for 8.04

Thank you

---

### Post by halovivek on 2009-02-03
Hi
could you post more details about your system configuration?

---

### Post by lkraemer on 2009-02-05
choko,
What they are trying to tell you is........

Open a Terminal window.

type uname -r

You will see the following:
larry@LK-Ubuntu:~$ uname -r
2.6.24-23-generic
larry@LK-Ubuntu:~$

Now you need to add this information to replace 'uname -r' below: 

install virtualbox-ose-modules-`uname -r`
install virtualbox-ose-modules-2.6.24-23-generic

So, use Synaptic to install this Kernel module for VirtualBox-OSE.

Better yet, remove/uninstall the OSE version, and and download/install
the latest version for your distro from [www.VirtualBox.org](www.VirtualBox.org)

If you are going to be running a Windows version as GUEST, be sure to install
the Guest Additions too....inside VirtualBox's VDI!

lkraemer

---

