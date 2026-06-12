---
title: "Blacklisting wireless networks on Edgy"
date: 2007-03-21
forum: Networking &amp; Wireless
---

### Post by seuaniu on 2007-03-21
Hi all.  I've got my wireless kit running with nm-applet and wifi-radar (No real configuration needed, just commented out eth1 in /etc/networking/interfaces and it worked), and can't find any software to blacklist networks.  I can see 3 networks from my house - mine, my next-door neighbor's and somebody else's.  

The laptop always, without exception auto-connects to my neighbor's open network instead of mine.  His is  broadcasting his essid, and mine's WEP encrypted and not broadcasting.  I can connect to mine easily enough by re-typing in the network info everytime I open the lid on the laptop, but that's a pain.  

Is there any way to have nm-applet or something else totally ignore his?

This seems to be a universal thing, since there are other networks that I've setup in nm-applet that don't connect when in range.  It always connects to the first one it sees.

FWIW, running Edgy on a Toshiba Satellite with a PCMCIA Netgear 802.11b card, model # MA401

---

### Post by DonnieP on 2007-03-22
You can use the gconf editor to get rid of unwanted insecure wireless networks.  The way the applet works, if you connect one time to an insecure network, you're stuck with the thing defaulting to that ad infinitum whenever if it's in range.  But you can make it go away with gconf editor and then be sure not to ever select that network again.  (To an old Windows user, gconf looks an awful lot like the Registry.  It's a way to get at an app's parameters when the app provides no direct way to do it.)

---

### Post by seuaniu on 2007-03-22
Thanks for the heads up.  I wasn't aware that nm-applet used gconf.  I'll have to see whether or not it'll still pick up my network automatically after I get rid of the neighbor's network.

---

