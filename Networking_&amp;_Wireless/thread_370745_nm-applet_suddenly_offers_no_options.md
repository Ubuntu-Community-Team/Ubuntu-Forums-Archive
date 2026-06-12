---
title: "nm-applet suddenly offers no options"
date: 2007-02-26
forum: Networking &amp; Wireless
---

### Post by frisket on 2007-02-26
[Edgy, Dell Inspiron 4150; NEC PCMCIA ATERM WL54SC wifi card]
I had NM working nicely for all my wireless networks. I then installed Enlightenment (e16) to see what it offered (very nice) and found that I had lost all connections except my default home wifi (which may well be being detected and connected by some other daemon -- I don't know and can't tell). 

The Network Manager (and Dispatcher) daemons were running, but nm-applet couldn't run because there is no systray in e16.

I logged out and logged back into Gnome, and nm-applet is now dead: it shows in the tray, but says:

[hover] No network connection
[left-click] No network devices have been found
[right-click] Enable networking (checked); Connection information (greyed out); About

I went back into e16 and installed Trayer in an attempt to allow nm-applet to execute, which it did, but it gave the same result. I have now uninstalled all the Enlightenment packages and returned to Gnome. Still no spark from nm-applet.

I managed to get a wired connection in the office by manually rewriting /etc/network/interfaces, and I've uninstalled NM and NM-gnome and reinstalled them, but how do I get things back to the state where nm-applet sees my network devices (eth0, ath0, wlan0...) and their associated configs and keyring data. Right now there seems to be no way to force it to see that they are there.

[And if nm-applet is dead in the water, *what* is seeing my home wifi and connecting to it?]

Both wifi-radar and wireless assistant agree that the wireless networks I want are there, in range, and active, and that they are the relevant office networks, but as they are all using WPA/PEAP/Dynamic WEP, and my username/password is in my keyring (presumably---still) I can't connect to them without nm-applet.

Does anyone know why nm-applet is refusing to see them?

---

