---
title: "wi-fi woes"
date: 2007-03-21
forum: Networking &amp; Wireless
---

### Post by chefjames on 2007-03-21
I recently upgraded from Dapper to Edgy.  My wireless ability has gone away.  In Dapper, my pcmcia card (TP -Link TL-WN510G Wireless CardBus) worked.  I was able to go to "network settings" and select a wi-fi network and connect.  Now the card is not even there.  If I go to "System>Administration>Device Manager"  the device is listed as AR5005G 802.11abg NIC.  Running the commands "ifconfig" and "iwconfig" did not show the device either. Installing the package "networkmanager-gnome" gave me an icon at the top of the screen that says I have no network connection.  I am lost as to what to do next.  Thanks in advance for any guidance.

---

### Post by Floppyjoe on 2007-03-21
Try adding the linux-restricted-modules for your kernel version with synaptic package manager.

---

### Post by chefjames on 2007-03-21
This worked in a round about way.  Thanks.  Going to "System>Administration>Networking" still does not show any networks, but the little icon in the bar at the top of the screen did.  In "Network Setting" my pcmcia card now shows up, but I am unable to enable or configure it.  I was able to select a network and connect using the networkmanager applet.  Thanks to all.  This did what I wanted, but  I am curious to know more about what is going on and why things worked or didn't.  Thanks again especially to Floppyjoe.

---

