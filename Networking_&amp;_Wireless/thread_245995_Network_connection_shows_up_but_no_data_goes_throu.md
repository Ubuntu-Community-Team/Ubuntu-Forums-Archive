---
title: "Network connection shows up but no data goes through"
date: 2006-08-28
forum: Networking &amp; Wireless
---

### Post by KaeseEs on 2006-08-28
I've been having some serious issues with the networking on my new ThinkPad.      My wired ethernet connection, which shows up as eth0, works correctly only when plugged in before boot and left in.  In other cases, the gnome network panel applet will show that a connection is present, and even that some packets have been transmitted and received, but any attempts to connect to the internet fail, and pings of websites known to be up return 100% packet loss.  Wireless, which shows up as eth1, has yet to work at all - again, it shows up as working in the panel applet, with even a signal strength readout, but data throughput appears to be nil.  I that whatever is causing this may also be the culprit behind some sketchiness with the gnome network configuration applet as well ( changes don't always 'stick', and will show as their unchanged state when closing the applet and opening it again ).  I doubt it's a hardware problem, as the WinXP partition on the same machine has perfect wired and wireless networking regardless of whether a connection is present at startup or how many times it is dis- and re-connected.  I've never had any facet of one of my machines work better on Windoze than Linux, and I'd rather hate to start now.  Any help would be much appreciated.



Specs:

IBM (no Lenovo stickers present; mf'd in July) ThinkPad T60
Intel CoreDuo T2500 @ 2.00 GhZ
Intel PCI gigabit ethernet controller
Intel 802.11a/b/g wireless interface

Ubuntu 6.06

---

### Post by KaeseEs on 2006-08-29
Any help would be appreciated!  Really!

---

### Post by rcd412 on 2006-08-29
try running dhclient, my wireless adapter did the same thing for some reason... "sudo dhclient (your device)" see if that helps any.

---

### Post by KaeseEs on 2006-08-29
rcd412, running dhclient seems to help, but the connection seems to time out every 10-12 minutes after applying this fix, and dhclient must be run again on the device.  While (mostly) workable, this is still sub-ideal, and seems not to address the root of the problem.  Thanks for the help, though!

---

### Post by rcd412 on 2006-08-30
check your router settings for the length of dns lease or something like that... it should be set to one day. Thats the only other thing i can think of.

---

### Post by KaeseEs on 2006-08-31
rcd412,

    Thanks again for the tip... however, I'm not connecting through a router ( at least not one that I have access to - my connection is in a college dorm with some sort of broadband shared between about 20 rooms ).  I installed NetworkManager, so I'm going to try disabling my default GNOME network progs and letting it do its thing.

---

### Post by rcd412 on 2006-08-31
thats a pretty good idea, msg me with how it works out

---

