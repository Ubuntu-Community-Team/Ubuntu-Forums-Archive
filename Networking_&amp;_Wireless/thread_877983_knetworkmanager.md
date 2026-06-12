---
title: "knetworkmanager"
date: 2008-08-02
forum: Networking &amp; Wireless
---

### Post by stitchmysmile93 on 2008-08-02
Can someone enlighten me on knetworkmanager and networkmanager...

I installed kde 3.5 on ubuntu 8.04 everything works great...

I installed knetworkmanager and the only options it gives is 40/104 hex what is the deal with that.

Then in gnome I have the option for 64/128 hex, what I need.

Not really a problem aslong as I log in gnome connect and then log into kde... 

But it would be nice to log into kde and connect using knetworkmanager...

---

### Post by caljohnsmith on 2008-08-04
I've had no problems with knetworkmanager, but if network manager works for you, you can still use it in Kubuntu (this is exactly what I do). First exit knetworkmanager, and then do:
```
nm-applet &
```
Click on the network manager system tray icon and configure your network. If all goes well and you want to continue using it, you can add a shortcut to it in your ~/.kde/Autostart directory so that the network manager applet is loaded on startup.

---

