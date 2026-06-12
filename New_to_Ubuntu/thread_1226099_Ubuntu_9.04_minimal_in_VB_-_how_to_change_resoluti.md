---
title: "Ubuntu 9.04 minimal in VB - how to change resolution"
date: 2009-07-29
forum: New to Ubuntu
---

### Post by longtom on 2009-07-29
Hi,

I am trying to eventually arrive at making a customized version of 9.04.  I installed in in VirtualBox, did the minimal install, have a gui by now, a theme and all looks familiar.

However - I get one error message when I start up:

```

Xsession: warning: xrdb command not found;
xsources not merged

```

Together with this I can not reset my resolution from 800x600 to something mor workable.

Any ideas how to rectify that?

---

### Post by longtom on 2009-07-30
Update:

I don't get that error message anymore - must have something right.  However, I still can't change the resolution.  The xorg.conf file is empty - or is it at a different place in Jaunty?

I run Arch, OpenSuse, Debian, Slitaz and WinXP in VirtualBox - and with all of them I got my choice resolution (1280 x 1024) going.

Any ideas?

BTW, I don't run these other Os' because I am such an expert but more because its fun....and I learn something every now and again.

---

### Post by longtom on 2009-07-30
Another one in longtoms monologe:

When trying to install VB Guest Addition I get the following error in the log file:

> 
Installing VirtualBox 2.2.2 Guest Additions, built Mon Apr 27 20:21:11 CEST 2009

Testing the setup of the guest system

Could not find the Linux kernel header files - the directories
  /lib/modules/2.6.28-13-generic/build/include and /usr/src/linux/include
  do not exist.
Giving up due to the problems mentioned above.


My guess is, that the minimal install didn't install what VB Guest Additions wants.  The problem is - I don't know what it is.

Please assist if possible

---

### Post by longtom on 2009-08-04
bump...:confused:

---

### Post by Cheesemill on 2009-08-04
Try
```
 
sudo apt-get install build-essential linux-headers-`uname -r`

```this will install the packages needed for building the VirtualBox Guest Addition kernel modules from source.
 
Then try reinstalling Guest Additions.

---

### Post by longtom on 2009-08-04
@Cheesemill

that did it.  

I had build-essential installed - but not linux-headers.  Care to tell me what `uname -r` does?

Thank you very much - I enjoy 9.04 now in a VB in the resolution of my choice.

I will mark this [solved]

---

### Post by hetx on 2009-08-04
It's a command for your kernel version.

Try running uname -a in a terminal, it will show which one you're running.

---

### Post by Cheesemill on 2009-08-04
The `uname -r` gets substituted for the version number of the currently running kernel. Try the command
```
 
uname -r

```by itself to see what I mean.

---

### Post by longtom on 2009-08-04
Thank you very much.  Another gap filled - only.....many to go.

---

