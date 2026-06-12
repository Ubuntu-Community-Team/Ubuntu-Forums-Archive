---
title: "Getting Wireless to work"
date: 2010-04-27
forum: New to Ubuntu
---

### Post by AutumnPhoenix on 2010-04-27
I need the sudo-apt get for the lenovo s10-2 netbook wireless.  It won't work.

Trying to run xubuntu 9.10

---

### Post by mcoleman44 on 2010-04-27
Have you taken a look under system>admin>hardware drivers?

---

### Post by AutumnPhoenix on 2010-04-27
see, I have to download it while on my thinkpad z60m so if I detect hardware then put the drive back in my lenovo s10-2

---

### Post by mcoleman44 on 2010-04-27
What type of wireless card is it?

---

### Post by AutumnPhoenix on 2010-04-27
how would I find that?

---

### Post by mcoleman44 on 2010-04-27
Open a terminal and type
```
lspci
```
It should be near the bottom.

---

### Post by booshire on 2010-04-27
Hello -

Open a terminal (in Accessories), type in lspci

Usually towards the bottom.

---

### Post by AutumnPhoenix on 2010-04-27
thanks

brodcam bcm 4312 802.11b/g
realteck rtl8101e/rtl8102e

---

### Post by mcoleman44 on 2010-04-27
Try this:
1 Open Synaptic Pacakage Manager
2 Ensure the LiveCd is in CD drive
3 Settings > Repositories > Ubuntu Software
4 Check the "installable from cd" Box and close
5 Refresh
6 Search for "bcmwl-kernel-source"
7 Mark for installation
8 Install it
9 Reboot computer

This should take care of the problem

---

### Post by AutumnPhoenix on 2010-04-27
it's a netbook, it dosn't have a CD drive

---

### Post by mcoleman44 on 2010-04-27
****... lol I forgot about that. Give me a minute, Im rethinking.

---

### Post by mcoleman44 on 2010-04-27
Can you get to an ethernet connection?

---

### Post by anewguy on 2010-04-27
*IF* you have a way to hard-wire it to a router, please do so and then do the following:

sudo apt-get update

Unplug the hard-wire cable, wait a few seconds, then (EDIT BEGINS HERE)check to see if there is a driver listed (in regular Ubuntu it would be under System/Administration/Hardware Drivers) and if you need to enable it, then check your wireless again.

Dave ;)

---

### Post by AutumnPhoenix on 2010-04-27
no, I share wireless with my downstairs neighbors


they're shall we say....preoccupied right now....

I was wondering if I could put the hard drive into my main machiene, download the drivers for the netbook (it has the drivers for the main machiene) and then put it back into the netbook

---

### Post by mcoleman44 on 2010-04-27
When you insert the usb key tha you used to install ubuntu what happens?

---

### Post by AutumnPhoenix on 2010-04-27
actually I'm using an old hard drive from the z60m

---

### Post by mcoleman44 on 2010-04-27
Haha...hmm... Do you have a usb key at all?

---

### Post by mcoleman44 on 2010-04-27
Here is the bcmwl-kernel-source.deb [http://packages.ubuntu.com/karmic/i386/bcmwl-kernel-source/download](http://packages.ubuntu.com/karmic/i386/bcmwl-kernel-source/download)
If you can get this to the netbook then you can get wireless to work. Hopefully. 

Your idea about putting this hard drive in your old computer and downloading this file is probably your best bet.

---

