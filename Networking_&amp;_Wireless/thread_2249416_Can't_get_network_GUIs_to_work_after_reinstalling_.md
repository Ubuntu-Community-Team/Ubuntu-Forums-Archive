---
title: "Can't get network GUIs to work after reinstalling some programs"
date: 2014-10-22
forum: Networking &amp; Wireless
---

### Post by bth5032 on 2014-10-22
I'm running Lubuntu 14.04 and earlier today I ran into some weird trouble where my computer would hang on login. Basically whenever I logged in I would just end up sitting at a screen with the background there and no way to interact with my machine. So I eventually reinstalled everything that I could think of that wasn't X and had to do with GUIs through the terminal (like openbox/pcmanfm/lxdm/lxde). That fixed the login problem, but now nm-applet thinks NetworkManager is not running. When I start NetworkManager through the terminal, it says it is running. Basically I don't know anything about how to use wireless networks through the command line so I need a GUI to manage that for me. I tried installing wicd (not sure if this can work while NetworkManager is running), but that says that DBus gave it an access denied error and my user in not in the netdev group(I checked and I am in that group). So basically I'm at a loss here, any idea why nm-applet isn't working or how I can go about getting another GUI up? My computer is actually still connected to the wireless even though I don't know how to control it. 

Thanks in advance!

---

### Post by bapoumba on 2014-10-23
If you run **nm-applet** from a terminal, do you see it appear in the panel ?

---

### Post by bth5032 on 2014-10-23
> **bapoumba said:**
> If you run **nm-applet** from a terminal, do you see it appear in the panel ?


Yeah, it would create another nm-applet icon in my panel but would still say network manager is not running. I don't know exactly what happened, but I managed to find a workaround by running ```
apt-get install --reinstall ubuntu-desktop
```. The problem had something to do with my permissions getting all out of wack. For instance, my sound wasn't working, if I tried to run alsamixer without being root, I'd get a message saying mixer wasn't a file or something. Thankfully that command seemed to fix the issues for the most part.

---

### Post by bapoumba on 2014-10-23
Oh, good to see you fixed it :)

---

