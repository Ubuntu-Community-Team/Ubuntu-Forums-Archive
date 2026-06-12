---
title: "NetGear WG511T problem"
date: 2006-12-26
forum: Networking &amp; Wireless
---

### Post by jml on 2006-12-26
I have an IBM ThinkPad R40.  It has an internal 802.11b wireless card which I no longer use.  I use a NetGear WG511T 802.11g  PCMCIA card with WPA encrypted wireless.  This configuration worked with Kanotix.  But now that Kanotix's prospects look a bit dim, I wanted to use Ubuntu.  I've successfully installed it on my HP nx6110,and got encryption working.  But I have a strange problem with Ubuntu on the ThinkPad.  The install goes well, but at random times (from 2 to 10 minutes after booting, the system freezes.  No response, the only thing that works is forcing a poweroff and restart, then the freeze happens again.  This does not happen when I remove the wireless card.  With the card out, it runs perfectly.  When I enable the wired connection, that works well too.  As soon as I plug in the wireless card, the freeze ups happen again.  I am running 6.10, Network-Manager and Network-Manager-Gnome are installed and seem to be working correctly.  The internal card has the power switched off.  The same configuration works well with my other laptop (the HP)  I am reasonably certain it is not a hardware problem, (the card, computer still works with a Kanotix Live CD.)  So I am homing in on a possible driver conflict.  I want to "blacklist" the driver for the internal wireless card.  I've seen reference to it on this forum in the past, but I have been unable to find it now.  If someone would send me the URL, or point me some other way, I would appreciate it.  If anyone has any other ideas, please feel free to share them.  The only other diference between the two laptops is the HP uses integrated Intel graphics and the ThinkPad uses an ATI Radeon accelerated Graphics adapter.  Thanks in advance for your help..

Joe

---

### Post by tannedin on 2007-01-21
I'm not sure exactly how much help this will be, since I'm not really providing an answer...

However my thinkpad Z60m is working fine with its onboard

I'm replying because I'm looking for what would be causing my desktop to freeze.
Using a NetGear USB Dongle.  Using Network Manager, it connected fine plug-and-play but any sort of net traffic (down to include SSH) causes my machine to lock.  If I use NDisWrapper, it freezes as soon as Network Manager makes the connection to my wireless.  Also, my comp froze when using Gnome-Network Applet that comes in the base install.

---

