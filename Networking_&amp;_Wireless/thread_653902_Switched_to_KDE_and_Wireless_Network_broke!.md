---
title: "Switched to KDE and Wireless Network broke!"
date: 2007-12-30
forum: Networking &amp; Wireless
---

### Post by andykimbrey on 2007-12-30
Firstly, tech info: Ubuntu 7.10 (Gusty Gibbon), Belkin 45g Wireless USB card, Netgear DG834GT Router.

Secondly, Hi :) I have recently installed Ubuntu 7.10 with no problems. Since, I switched to KDE (using Synaptic to install it), logged in to a KDE session and all was well with the Internet.

Today, I hit Ctrl-Alt-Backspace to restart X and log into Gnome and the wireless icon was gone, only "manual configuration" was available. I switched back to KDE and the wireless was broken there as well.

I have tried using both the Gnome and KDE GUI config tools, using iwconfig via the CLI, I've tried DHCP, static IP, I've been through these forums, Google, Unix help files, everything. The only clues I have are as follows:

1) I used ctrl-alt-backspace to kill KDE when going in to Gnome,
2) Just before the wireless stopped working, I had installed the gtkpod and kdepod packages for iPod connectivity,
3) The Wireless icon is missing from the Gnome app bar interface since, either, installing KDE, or hitting ctrl-alt-backspace.

I have rebooted and done all the idiot tests, I am just at a loss as to what I've done to break my wireless! Many thanks in advance for any advice!

*Andy Kimbrey*

---

### Post by (((X))) on 2007-12-30
Did your wifi light turned  off too?

---

### Post by andykimbrey on 2007-12-30
> **(((X))) said:**
> Did your wifi light turned  off too?

The light on my USB adapter is on and flashing, and my wireless router is working fine because I am connected to it on my windows laptop now!

An iwconfig reveals that my wireless (currently configured for a static IP rather than DHCP) is functioning correctly, but I have no connectivity to the network (pings to the router/gateway just fail). I've tried the Troubleshooter on the Ubuntu website but it hasn't helped at all.

My wireless router and USB connector are working fine, I just seem to have no connectivity to the network or Internet since installing KDE and switching between it and Gnome :S

*Andy Kimbrey*

---

### Post by andykimbrey on 2007-12-31
I managed to fix this issue by disabling security on my Wireless Router and restricting access by MAC address. Unsure whether this was a problem that Ubuntu was giving my network key as a WEP instead of a WPA, but it all seems to be working now.

---

