---
title: "Network Manager Intel 2200"
date: 2006-10-11
forum: Networking &amp; Wireless
---

### Post by chanco on 2006-10-11
So I've been trying for hours now to get my wireless working.  The only way it works is on a unsecured network with broadcast SSID.  Obviously not good.

I've tried the various methods of using wpasupplicant, to no avail.

I've uninstalled wpasupplicant and reinstalled using synaptic a few times and thats where I'm currently at.  A fresh install of wpasupplicant and network manager.

I'd really like to get it working with Network Manager, but I don't even get a wireless icon with Network Manager.  Just wired.  Even when my network is wide open.  Whats going on here?  

Do I need to do something to get network manager to play with my card?

BTW... this is the 6.06 Dapper version freshly installed on a latitude 600 laptop.

---

### Post by chanco on 2006-10-12
Well... for anyone else searching here...

I finally got it working by doing 3 things.... Which one fixed it I don't know. 

1) I commented out all entries in /etc/network/interfaces except lo.  (I had done this previously as well... but somehow they got put back.  And something else must have kept it from working at the time.

2) Toggled wireless on the laptop and rebooted (Fn + F2 for me).  There is no idiot light indicating if it is on or off on this thing.  And there was nothing happening in the OS either.  After seeing someone elses post on this, I tried cat /var/log/messages | grep wireless and saw a message saying the kill switch must be turned off.  I would press it a few times and saw no difference.... Tried rebooting and didn't get the message again from that reboot, so I guess I'm good.  Sure would be nice to know somehow if wireless is on or off.  Weird thing is now that I have network manager running properly, it does enable/diable when I press the buttons.  But before it was running, there was no indication.

3) Added Notification panel to gnome.  I guess its not there by default?

So I hope this saves someone else some time.  

Cheers!

---

