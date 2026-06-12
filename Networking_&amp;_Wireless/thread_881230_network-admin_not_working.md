---
title: "network-admin not working"
date: 2008-08-05
forum: Networking &amp; Wireless
---

### Post by topher1kenobe on 2008-08-05
I have a dell d630 with a Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express.  I'm running Hardy on it.

I can get online no problem with wifi-radar, that works great, so it tells me there's nothing wrong with that.

Network Admin has everything grayed out, nothing is accessible.  There's an Unlock button, but that's grayed out too.

The problem I'm really trying to solve is that my laptop doesn't connect automatically to my wifi at home.  My previous laptop, a D610 with Feisty, did that no sweat.  In fact, it would connect to any wifi I had previously created a profile for that was in range.  Now I have to fire up wifi-radar every time I boot.

I don't run Gnome, so I don't care if the solution is fixing network-admin or using something else.  Any ideas?

---

### Post by topher1kenobe on 2008-08-19
wicd works great as a network manager, and has an option for "connect automatically".  wifi-radar may have had that, I don't remember, but if it did, it wasn't obvious.  :)

So, wicd does the trick marvelously.

---

### Post by Bahb on 2008-08-24
I am seconding this. Network-admin is grey. how do i get to where i can have my way with it?

---

### Post by dzyubam on 2008-09-18
I'm having the same problem. Additionally, this message appears when I run 'network-admin' in console:

> 
(network-admin:6901): Gtk-WARNING **: Unknown property: GtkComboBox.items


** (network-admin:6901): CRITICAL **: Unable to lookup session information for process '6901'

Anyone please help.

---

