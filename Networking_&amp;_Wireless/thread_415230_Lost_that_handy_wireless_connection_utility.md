---
title: "Lost that handy wireless connection utility"
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by nilihm on 2007-04-20
In a bout of overzealous reconfiguration, I somehow lost that nice little wireless connection utility that drops down from the top panel in default Feisty.  The network interface still works (in the sense that the hardware functions), but there's no longer any way to select a preferred network when in roaming mode.

Any idea what that app is called and how to get it back?  It's not listed among the "add to panel" choices.

Thank you!

---

### Post by disabled_20220313 on 2007-04-20
It's called network-manager.

Sorry can't be more help.

Good luck.

---

### Post by nilihm on 2007-04-20
Thanks for the tip.  The only thing I've got in /usr/lib/network-manager is a crash log, which would be useful to share, except that it doesn't seem to be human-readable.

Another lead: clicking configure in Network Monitor throws a "missing interface" error.

---

### Post by nilihm on 2007-04-20
Okay, after uninstalling and reinstalling network-manager using apt, I finally have a useful error. . .

"The NetworkManager applet could not find some required resources.  It cannot continue."  Hmm?

---

### Post by disabled_20220313 on 2007-04-21
This is a stab in the dark. Are you sure that you have the wireless hardware installed and recognised properly?


Use
```
iwconfig
```

in the terminal and check that your hardware shows up.

---

### Post by nilihm on 2007-04-21
Indeed, it's installed just fine.  I often receive notification that I've successfully connected to one or another preferred network.

Something's up.  Reinstalling network-manager and network-manager-gnome did nothing to help.

Thank you for your assistance so far!

---

### Post by disabled_20220313 on 2007-04-22
Sorry I'm stumpped.

---

### Post by nilihm on 2007-04-22
Well, thanks anyway.  I'll try posting this in the Gnome forum, as it's a Gnome app.

---

### Post by ssam on 2007-04-23
you need to add notification-area to your panel

---

### Post by nilihm on 2007-04-23
I thought I had that, as the status balloons pop up without problem.  I'll try adding it again for good measure. . .

EDIT:  Seems you were right.  Thank you!

---

