---
title: "getting wireless to play with openbox"
date: 2008-11-24
forum: Networking &amp; Wireless
---

### Post by rswoods on 2008-11-24
My wireless connection works fine in Gnome, I manage it via nm-applet in the notification area of the gnome-panel.  When I right-click I get two options: Enable Networking and Enable Wireless.

However, when I log into openbox and run nm-applet a right-click only reveals one option: Enable Networking.  Wireless is not functional in openbox.

When I type ifconfig in Gnome I recieve three results: eth0 (wired ethernet), eth1 (my wireless card), and lo (loopback).  When I run ifconfig in Openbox I only recieve eth0 and lo, it doesn't seem to recognize that I have a wireless card.

It is probably important to note that when I log into Gnome, then log out and log into Openbox, nm-applets behavior is as expected.  My goal, however, is to be able to boot directly into openbox without having to swap between sessions to make everything work.  Gnome is probably loading some service or module for me that openbox isn't, and I haven't been able to figure out what it is.  Does anyone know what I'm missing?

---

### Post by rswoods on 2008-11-24
Using 'lsmod' and 'modprobe wl' I successfully identified and loaded the proper module.  Now when booting directly into openbox and loading nm-applet, on right-click I do get the 'enable wireless' option and I also get a list of wireless networks on left click.  However, when I try to connect to one I get the connection animation but the dot on the lower left representing my computer does not activate.  It fails and goes to the "not connected" icon.  Is there a backend for this applet or a more featureful application I could use to get some meaningful feedback so I could know what to troubleshoot here?

---

### Post by Magneto on 2008-12-09
bump

i want to use openbox too but I dont want gnome applets for networking. I can't find how that applet is configuring my intel wifi card iwl3945 - wpa. I've tried wpa_supplicant but it doesnt want iwl3945 - ipw3945 isnt available. I just want simple machine wide network settings for my laptop. It'd be nicer if instead of a gnome applet there was a network app that performed the same tasks without being tied to the gui and blocked roaming.

this is pretty aggravating. bout to see how well other distros work with my wifi chipset and change from ubuntu if I cant find a solution

---

### Post by Magneto on 2008-12-10
i got it working by hand
using the info here
[http://ubuntuforums.org/showpost.php?p=1176169&postcount=1](http://ubuntuforums.org/showpost.php?p=1176169&postcount=1)

---

