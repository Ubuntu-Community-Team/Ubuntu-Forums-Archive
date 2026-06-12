---
title: "Network Manager in Hiding"
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by DarthGroznii on 2007-04-20
Hello - 

I just upgraded from Edgy to Feisty; Edgy was an upgrade from Dapper.

I cannot locate Network Manager anywhere in the menu structure, nor is it an available panel applet, as it appears to be intended to be.

It is installed - a check on Synaptic indicates this, as does looking under Add / Remove under Applications.

How do I excavate the Network Manager for use?

Thanks.

---

### Post by VirtualTiger on 2007-04-20
Hey Darth...

I was having a similar problem and I was just able to fix it.

First you can try moving the "Notification Area" to your panel.  That worked for me but I messed up  and accidentally dragged the Network Manager off of that and lost it (dope...) and I couldn't put it back on.

I ended up uninstalling the following from Synaptic Package Manager:
network-manager
network-manager-gnome
network-manager-vpnc (if you have this installed)

and then I reinstalled them.

I had to reboot (probably could have just logged out and back in again), but I was then able to add the "Notification Area" back to my panel and it contained the Network Manager.

---

