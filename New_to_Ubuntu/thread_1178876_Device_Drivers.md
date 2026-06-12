---
title: "Device Drivers"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by GaretJax on 2009-06-05
I found a game written for Linux and I am trying to get it to run in Ubuntu but having a little difficulty.  So I visited the game's forums and people are posting what video card drivers they are using.  I would like to join this conversation but I can't find where to look at my device drivers.

I found Hardware Drivers under Administration but it only says that there are no proprietary drivers in use on the system.  Is there an applet like the Device Manager list in Windows where I can see all the hardware that Ubuntu detected on my system and also see which drivers it employed?

---

### Post by Ravernomina on 2009-06-05
in the system repositories quick search "device manager" their is something like that i forget the full name and right now im on my Mac book or i would give you the name :l

---

### Post by GaretJax on 2009-06-05
> **Ravernomina said:**
> in the system repositories quick search "device manager" their is something like that i forget the full name and right now im on my Mac book or i would give you the name :l

System repositories.  What is that?  Is that something on my computer or on this forum somewhere?

---

### Post by QIII on 2009-06-05
Go to the terminal and type

sudo apt-get install hwinfo
Supply your password when prompted (the password you use when you log in)

Still in the terminal, type

hwinfo

You'll get a big, long list of your hardware.  You'll have to sort through it, because it is pretty detailed.

If you don't like using the terminal and want a more graphical tool, go to System -> Administration -> Synaptic Package Manager and search for libgnome-device-manager0 and install it.

Third option is to go to Applications -> Add/Remove  search for SysInfo and install it.  You'll get an icon for it in Applications -> System Tools

---

