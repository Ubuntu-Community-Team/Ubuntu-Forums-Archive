---
title: "Wireless: Roaming Mode vs Manual Config"
date: 2007-08-06
forum: Networking &amp; Wireless
---

### Post by Sand Lee on 2007-08-06
What is the difference between the two (in network manager)? I get the notion that manual config constantly tries to connect with one network and roaming mode tries to do the same, but at the same time it looks for other surrounding networks. Is this correct? If so, does that mean that manual config uses up less energy and resources than roaming mode? 

As of this moment, I am using wicd and prefer it over gnome-network-manager. I'm irked that wicd is constantly in roaming mode AFAIK. :confused:

---

### Post by kevdog on 2007-08-06
WICD is not in constant roaming mode if you set a static IP addressed with your profile.

As far as roaming vs manual configuration

Manual configuration gives you more control (to set various wifi parameters that nm manager does not -- depending on the chipset of your card).  In fact nm does not work correctly with some chipset/driver combinations.

While roaming mode does give you the benefit and rapid network connection and identification (through a GUI), many of the same things can be done in manual mode -- albeit with more work on the part of the user.

---

### Post by Sand Lee on 2007-08-06
Cool, I've just set a static IP in wicd. So I take it that the only difference between the two is the amount of configurability?

---

### Post by imdano on 2007-08-06
Setting a static IP in wicd just means it doesn't run dhclient when it connects, and uses your inputted settings instead.  When you're just running the wicd tray and don't have the GUI open, it's almost never scanning for networks.  It only starts scanning when you get disconnected, or open the GUI (so it can show you the networks that are around).  If you disable autoreconnect it won't even scan on disconnect.  The only things it's constantly (every 3 seconds) doing is checking your current connection status (what your ip address is, if an ethernet cable is plugged in, signal strength, etc).

---

### Post by Sand Lee on 2007-08-06
Thanks imdano!! That cleared everything up, now I don't have to worry about what my network manager is doing. :)

---

