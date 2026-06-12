---
title: "Problem with USB WLAN adapter"
date: 2005-08-17
forum: Networking &amp; Wireless
---

### Post by Maupertus on 2005-08-17
I've just revamped my dad's old Compaq Laptop.
To acces the home network and the one at Uni I used to connect via a small USB connector. As I'm used to working with a cable-LAN I haven't really got an idea how to get it to work. 

Although the USB works, I can't figure out if Ubuntu knows what to do with the connector. The driver cd is written exclusively for XP so that wasn't any help.

So any ideas (at the moment I'm not even asking the right questions) will be helpfull.

---

### Post by az on 2005-08-17
1- boot into ubuntu
2-  Wait for the desktop to appear.
3-  Open a terminal
4-  Plug in your thinggie.
5-  Wait ten seconds
6-  type 
dmesg
and post the last ten or fifteen lines or so.  We'll take it from there.


The reasoning is that hotplug will load the appropriate drivers if they are part of the kernel.  Ubuntu includes some drivers, but not all of them.  You would have to use ndiswrapper to use your XP drivers for the device in Ubuntu (NDISwrapper only works for wireless drivers)
When hotplug does something, it sends a message which you can access by typing dmesg.

---

