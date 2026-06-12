---
title: "Network Manager, ndiswrapper, WICD, MadWifi - So Confused!"
date: 2008-11-12
forum: Networking &amp; Wireless
---

### Post by cforput on 2008-11-12
Help!

I am trying to get my Acer 5520-5334 with an Atheros 5007 wireless card connected. I have read many posts and tried many things to no avail. I need some basic help to get me back on track.

First, people refer to network manager, ndiswrapper, WiCD and MadWifi. What does each of these do and which ones do I need?

Also, I am afraid that I have tried so many things that I want to uninstall everything and start over. How do I uninstall network manager, and MadWifi? When I search Synaptic for MadWifi the only thing that shows as being installed is linux-restricted-modules-2.6.22-14-generic. Do I leave this?

I am on Gutsy 64-bit and at one point my wireless was working, then I made the HUGE mistake of upgrading to Hardy. My video blew up, my wireless went kaput and so I reinstalled Gutsy and plan on staying there if I can get my wireless working.

PLEASE HELP!

I am so lost..........

---

### Post by randy78 on 2008-11-12
I can't directly solve your wireless problem, but I can say that Gutsy is fairly dated now, and that you should, at the very least, upgrade to Hardy.
It may contain the proper modules to get you up and running :)

---

### Post by ragonz on 2008-11-12
Well i've been through in ur position before, but my wireless adapter is broadcom. I don't know whether it'll work the same way, but i think it's worth to try.

subtitue the *inf and *sys file with ur wireless files (*.inf and *.sys either).

there goes my ndiswrapper-utils, wish helpfull

visit here, [http://ragonzapp.blogspot.com](http://ragonzapp.blogspot.com)

---

### Post by kevdog on 2008-11-12
I believe the atheros 5007 will work with a patched madwifi set of drivers. Do a search for this:

ndiswrapper (+ window driver), Madwifi = card drivers

WICD, Network Manager = GUIs that allow you to interact with the card.

---

### Post by cforput on 2008-11-13
Thanks Kevdog for the clarity on ndiswrapper, madwifi, etc. My wireless is working. I cleaned out everything to do with ndis and madwifi then downloaded the madwifi again, installed it and my wireless is working!!!!

One last question. Can I now install WiCD or Network Manager and it won't cause my madwifi set up to be lost? Which one would you recommend?

---

### Post by kevdog on 2008-11-13
Either package works -- since both provide GUIs to interact and pass commands to the underlying network driver

Network Manager is the default -- works for most -- other prefer WICD or Wifi Radar.  Why don't you try NWM first and then roll to WICD if it doesn't work.

---

