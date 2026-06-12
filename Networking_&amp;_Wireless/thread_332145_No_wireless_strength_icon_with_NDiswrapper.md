---
title: "No wireless strength icon with NDiswrapper?"
date: 2007-01-05
forum: Networking &amp; Wireless
---

### Post by bone2006 on 2007-01-05
My Internet has been working fine, but on my other system that I didn't need to install ndiswrapper it shows my signal strength next to the system tray on the top right.

I can't seem to find out how to show the singal strength of my usb wifi dongle, any suggestions?

---

### Post by teaker1s on 2007-01-05
sudo apt-get install network-manager-gnome

---

### Post by bone2006 on 2007-01-06
thank you so much
It installed and I rebooted and saw the status in the task tray area as I have before.  The only problem is that it's somehow checking the status of my ethernet connection and not my wifi connection, so it shows no connection, even though I'm online.
when I put the mouse over it, it says no network connection and if I click on it, it has a grayed out box that says no wired connection

---

### Post by bone2006 on 2007-01-06
from this link [http://live.gnome.org/NetworkManagerHardware](http://live.gnome.org/NetworkManagerHardware)

it seems that using Ndiswrapper isn't supported, but madwifi is
I had better luck with ndiswrapper

---

