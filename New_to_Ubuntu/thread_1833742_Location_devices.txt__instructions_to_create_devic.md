---
title: "Location devices.txt / instructions to create devices"
date: 2011-08-26
forum: New to Ubuntu
---

### Post by gnometorule on 2011-08-26
Whereever I google for it, and whichever documentation I check, devices are said to be listed in the file

devices.txt,

its location said to be at

/usr/src/linux/documentation.

In my /usr/src folder, I have 4 folders of the sort linux-headers and linux-headers-generic. I cannot 'find' it on my system either doing a root search. 

(1) Does the file still exist? If yes, how do I find it? If no, what has it been substituted by? (source to read up on this is fine obviously)

(2) For a **netbook**, I need to enable a scc0 or cdrom device, then mount it, for some other purpose. I meant to follow the instructions in 18.6. in 

[http://rute.2038bug.com/node21.html.gz#SECTION002110000000000000000](http://rute.2038bug.com/node21.html.gz#SECTION002110000000000000000)

but as these instructions too still refer to 'devices.txt', are they even still current? If not, how to proceed?

Obviously, if you just know the answer to (1) but not (2), kindly reply. :)

P.S.: The need to do what I say comes from

[https://help.ubuntu.com/community/VirtualBox/SharedFolders](https://help.ubuntu.com/community/VirtualBox/SharedFolders)

As part of the instructions from the source (VirtualBox), I needed to install linux-headers-generic. Is this related to my problem?

Edit: When I check in /dev (which, as I understand it, has the currently declared devices), I find neither scc0 or cdrom (not surprisingly).

---

### Post by gnometorule on 2011-08-26
I describe my struggles with what seems to be a rather changed way how to manage devices under Ubuntu in this post in more detail (on the VirtualBox forums)...

[http://forums.virtualbox.org/viewtopic.php?f=10&t=44167](http://forums.virtualbox.org/viewtopic.php?f=10&t=44167)

Maybe I am missing something, but it appears to me that either a helpful link to updated instructions (which I seem unable to find) or an illumination of these apparent issues by one of the crack users on here would be very helpful to the community in general. It seems just all wrong when my MAKEDEV file isn't even in the 'proper' (as in, where it should be per all the docs I find) location, and I need to guess where to run it (its current location - sbin? the one per docs where it should be - /dev? the impact on the system is different as its output is saved in the respective directory). It is entirely possible that maybe what I mean to do is impossible; however, that still keeps the point open that it should be possible to track down how to add devices and such.

---

### Post by sandyd on 2011-08-26
> **gnometorule said:**
> Whereever I google for it, and whichever documentation I check, devices are said to be listed in the file

devices.txt,

its location said to be at

/usr/src/linux/documentation.

In my /usr/src folder, I have 4 folders of the sort linux-headers and linux-headers-generic. I cannot 'find' it on my system either doing a root search. 

(1) Does the file still exist? If yes, how do I find it? If no, what has it been substituted by? (source to read up on this is fine obviously)

(2) For a **netbook**, I need to enable a scc0 or cdrom device, then mount it, for some other purpose. I meant to follow the instructions in 18.6. in 

[http://rute.2038bug.com/node21.html.gz#SECTION002110000000000000000](http://rute.2038bug.com/node21.html.gz#SECTION002110000000000000000)

but as these instructions too still refer to 'devices.txt', are they even still current? If not, how to proceed?

Obviously, if you just know the answer to (1) but not (2), kindly reply. :)

P.S.: The need to do what I say comes from

[https://help.ubuntu.com/community/VirtualBox/SharedFolders](https://help.ubuntu.com/community/VirtualBox/SharedFolders)

As part of the instructions from the source (VirtualBox), I needed to install linux-headers-generic. Is this related to my problem?

Edit: When I check in /dev (which, as I understand it, has the currently declared devices), I find neither scc0 or cdrom (not surprisingly).
```

sandyd@icegirl-mobile ~ $ uname -a
Linux icegirl-mobile 3.0.3 #7 SMP PREEMPT Mon Aug 22 14:00:20 EDT 2011 x86_64 Intel(R) Core(TM)2 Duo CPU T6500 @ 2.10GHz GenuineIntel GNU/Linux

sandyd@icegirl-mobile ~ $ cat /usr/src/linux/Documentation/devices.txt
```Its there. If you install linux-sources that is. I have it only because I don't use Ubuntu.

Anyways, you shouldn't need to check the devices.txt . It doesn't apply anymore to newer versions of virtualbox. I can't open virtualbox, because I use a Xen HyperVisor, but theirs a menu item to install the guest additions in virtualbox (the opened VM window I mean)

---

