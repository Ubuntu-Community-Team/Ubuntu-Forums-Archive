---
title: "Gnome Network Setup: Locations?"
date: 2007-07-13
forum: Networking &amp; Wireless
---

### Post by wildbillnj1975 on 2007-07-13
I have a Ubuntu (6.06) server and just set up the laptop with 6.06 as an NIS client.  Works great all over the house.  However, the laptop will also roam with us when we travel, so it has a local user who is authenticated locally (not by NIS on the server).  Two problems in this area...

1) When roaming, get lots of errors from ypbind because it cannot find the server (naturally).  I can kill ypbind, but is there a way to have it detect which network I'm on, and only start it if I'm on my home network?

2) The Gnome Network Settings widget has a "Locations" field, so you can store sets of settings and load them en masse, i.e. "home" for my network, and "roaming" for picking up the local wifi net at hotels, airports, etc.  How does it choose which one is the "default"?  Can I tweak it externally so that it chooses the correct default based on whether it finds my home SSID?  This is more than just an annoyance - when I return home after roaming, I have to log in with the local user and change the Location to "home" before I do anything else, because otherwise my NIS users cannot log in.

3) I'm not really happy with the whole widget (#2) in general - anyone know of another GUI network configurator that I can use within Gnome, as a replacement for the original?

---

