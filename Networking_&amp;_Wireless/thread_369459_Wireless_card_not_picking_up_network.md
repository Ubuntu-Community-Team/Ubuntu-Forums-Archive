---
title: "Wireless card not picking up network"
date: 2007-02-24
forum: Networking &amp; Wireless
---

### Post by ashlesha on 2007-02-24
Hi,

Yesterday when I was at university, my wireless card on my Dell XPS M140 laptop, detected the network and could connect to it - however there was no wlan0 when i ran the ifconfig command --

however, now when I try to connect to the network at home (which my Windows picks up immediately) i cant see any signal strength --- i have connected to this network in the past --

I tried to configure it by writing the SSID and the password -- and i cant connect to it!! Pleaase help me out -- ifconfig still does not show a wlan0!

Thank you!
Ashlesha.

---

### Post by beanworks on 2007-02-24
It sounds like the wlan0 is not enabled, or is not set as the default.

Assuming you're in gnome ubuntu 6.06, you can change the settings by going to the Networking link on the System menu.  You will probably see the wireless card and ethernet card listed.  Set the default at the bottom, and use the deactivate button on the right to deactivate the eth0 card if it is active (and, of course, activate the wlan0 if it isn't already).

One more thing, you might try using the box at the top to create different "locations" to save the different settings since you visit different locations.

---

