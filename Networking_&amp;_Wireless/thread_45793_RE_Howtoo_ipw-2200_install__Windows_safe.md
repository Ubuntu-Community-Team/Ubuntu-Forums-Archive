---
title: "RE Howtoo ipw-2200 install:  Windows safe?"
date: 2005-07-01
forum: Networking &amp; Wireless
---

### Post by Zerileous on 2005-07-01
My dell 9300s wifi is not working, many places have direced me to the thread that tells you how to do wpa with ipw-2200 except to skip the wpa.  My worry is in installing new firmware.  This is a dual boot system and I would hate to break something in windows with new firmware.  is this a danger?


Scroll down for problems.

---

### Post by luca_linux on 2005-07-01
Don't worry about!
The firmware doesn't overwrite the one in the chip! It has nothing to do. It just influences Linux, not Windows.

---

### Post by Zerileous on 2005-07-01
[QUOTE=luca_linux]Don't worry about!
The firmware doesn't overwrite the one in the chip! It has nothing to do. It just influences Linux, not Windows.[/QUOTE]
 awesome thank you!  So when they say firmware its a different level of firmware in this case...?  How can I distinguish between linux firmware and chip firmware?

---

### Post by Zerileous on 2005-07-01
now i am having some issues.  The install of the firmware went fine, but i cant make the drivers.  Here is the part of my Makefile that I modified in accordance with the instructions.
```
KMISC := /lib/modules/$(KVER)/kernel/drivers/net/wireless/
```

Here is what happensd when I try to make.
```
justin@ubuntu:~/Desktop/ipw2200-1.0.4$ make
make -C /lib/modules/2.6.10-5-386/build SUBDIRS=/home/justin/Desktop/ipw2200-1.0.4 MODVERDIR=/home/justin/Desktop/ipw2200-1.0.4 modules
make: *** /lib/modules/2.6.10-5-386/build: No such file or directory.  Stop.
make: *** [modules] Error 2
justin@ubuntu:~/Desktop/ipw2200-1.0.4$

```

I am considering doing a 
```
mkdir /lib/modules/2.6.10-5-386/
``` but I dont want to hose anything yet, because at my level of experience it would either be a reinstall or many hours of work.

---

### Post by luca_linux on 2005-07-02
Have you installed all the packages mentioned in the HowTo (kernel-headers, build-essential, etc.)?

---

### Post by Zerileous on 2005-07-03
hrm, i went back and checked it out and for somereason I didnt get the inux-headers-myOwnKernelVersion.  Hrm strange, I must have missed the msg that it didnt install, I was pulling an all nighter so ya never know.  Ok it appears to be working now.  Thanks for the help.  What about my other question, about telling a firmware for linux from a on chip firmware?

---

### Post by luca_linux on 2005-07-03
The firmware loaded in Linux has nothing to do with the one flashed in the chip.
The one coming with ipw2200 is not flashed in the chip, but it's just a software layer that provides an interface of callable functions for the linux driver and makes ipw2200 driver able to manage the card functions.
You cannot edit the firmware of the chip unless you flash the chip.
So, don't worry! It has nothing to do with Windows because it's loaded on every Linux boot and gets unloaded on every Linux shutdown. The wireless card is not edited by the the Linux firmware in any way.

---

### Post by scottylans on 2005-07-05
Luca:

This is the second post (similar to mine) where someone has tried to follow your tutorial and failed.


I'm sorry to be a nag and hassle you but you really need to make the tutorial have all the information.

A user should be able to download 5.04
Install it
and get the instructions from there - the whole lot - the repositories to be added, the packages downloaded the WHOLE kit and kaboodle

So any chump can install barebones ubuntu CD - standard options - then be online with WPA on the 2200

---

### Post by luca_linux on 2005-07-06
[QUOTE=scottylans]Luca:

This is the second post (similar to mine) where someone has tried to follow your tutorial and failed.


I'm sorry to be a nag and hassle you but you really need to make the tutorial have all the information.

A user should be able to download 5.04
Install it
and get the instructions from there - the whole lot - the repositories to be added, the packages downloaded the WHOLE kit and kaboodle

So any chump can install barebones ubuntu CD - standard options - then be online with WPA on the 2200[/QUOTE]
 My HowTo supposed the user to have a bit of linux knownledge.
Anyway, I'll edit it and add more information.

---

### Post by brim4brim on 2005-07-06
I followed your how to no problem.  I have had nothing but bad experiences with previous Linux distro's with installing drivers but yours was perfect.  Just enough info to get it done but not too much info that makes you half read it and make an attempt at install yourself.

Maybe in the howto's you could tell people what packages to search for in Synaptics to install if they need to install libraries but that's about it.  People get lost when it comes to installing libraries I think.  I'm used to it now but at first I got a bit lost there.

---

### Post by luca_linux on 2005-07-06
[QUOTE=brim4brim]I followed your how to no problem.  I have had nothing but bad experiences with previous Linux distro's with installing drivers but yours was perfect.  Just enough info to get it done but not too much info that makes you half read it and make an attempt at install yourself.

Maybe in the howto's you could tell people what packages to search for in Synaptics to install if they need to install libraries but that's about it.  People get lost when it comes to installing libraries I think.  I'm used to it now but at first I got a bit lost there.[/QUOTE]
 Ok, thanks for the suggestions...

---

