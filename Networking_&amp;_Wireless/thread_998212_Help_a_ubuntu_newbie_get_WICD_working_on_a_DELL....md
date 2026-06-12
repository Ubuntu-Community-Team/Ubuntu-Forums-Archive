---
title: "Help a ubuntu newbie get WICD working on a DELL..."
date: 2008-11-30
forum: Networking &amp; Wireless
---

### Post by KevinJD on 2008-11-30
So I have managed to get WICD working great, except there is one big problem. When I open up WICD I get a "no wireless networks found" message.

I know there are 3 wireless networks, 1 unsecure (my own, the router is in the same room) and 2 secure ones from houses in the neighborhood. I know this because the PC I have beside the laptop finds these networks in Vista.

Why is this not working?

Heres what I get when I type "iwlist scan" in the terminal:

lo Interface doesn't support scanning
eth0 Interface doesn't support scanning
wmaster0 Interface doesn't support scanning
wlan0 No scan results

also, lshw -C network shows "network DISABLED" for the wireless interface

---

### Post by xircon on 2008-11-30
Did wireless work with gnome network manager?

Stupid question, but is the wireless turned on? I made this mistake (once!) mine toggles with fn+f11

In the preferences in wicd, is the wireless interface set? mine = wlan0

There is a very helpful wicd forum at [http://wicd.sourceforge.net/punbb/](http://wicd.sourceforge.net/punbb/) if all else fails.

I find it strange that lshw -C network displays nothing.

---

### Post by Ayuthia on 2008-11-30
Can you post the results of lshw -C network?  If the card is currently DISABLED, then it might either be turned off or else might be missing the driver/firmware.

---

