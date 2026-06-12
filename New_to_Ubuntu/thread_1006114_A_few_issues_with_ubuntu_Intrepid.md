---
title: "A few issues with ubuntu Intrepid"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by karimruan on 2008-12-09
Hi, I have just installed Ubuntu 8.10 ( I think, I have the latest stable). I have a few concerns though. When X is started, everything is very big. It seems the screen resolution is set to 800 x 600. That is also my only option for the screen resolution, I don't know why. Also, I guess I am supposed to have 'network manager' under System > Administration > Network manager, but I don't. I want to connect to my wireless network, but without that program, I do not know how. Is there a way to scan for the network and connect to it once found. One last thing, I installed some games from add/remove programs and also from the synaptic installer. They will not work. When I click them, nothing happens. When I right click, go to 'open', nothing happens.

My box specs:
 AMD Turion64 x2 
Nvidia graphics
4 gigs ram
250 gigs hard drive.

Thanks for your help.

---

### Post by Kareeser on 2008-12-09
Hi Karimruan...

One thing at a time... firstly, your wireless card...

Ubuntu may not come with compatible drivers for your wireless card, but there may be a non-free alternative out there (as well as some other options, including recompiling a Windows driver to Linux).

System -> Administration -> Hardware Drivers

Is there a wireless card driver there?

---

### Post by Tatty on 2008-12-09
For your graphics issue, try installing the proprietry drivers for your card.  System->Administration->Hardware Drivers.

Network manager is not in the System menu, it should load by default in your top panel on the right hand side,  simply click on it to view all the detected networks.  If it is not loading, try running the update manager - it did not load on my laptop at first when I installed intrepid, but running the update manager fixed that.

If it still does not load, you can manually load it by running "nm-applet".

Try running your non-functioning games from a terminal and see if they output an error message.

---

### Post by Kareeser on 2008-12-09
lol tatty. Good to know we're on the same track.

---

### Post by 3rdalbum on 2008-12-09
If you don't have 3D graphics drivers, then any games that require 3D acceleration will not run. The lack of 3D drivers also explains why you have such a low resolution.

---

