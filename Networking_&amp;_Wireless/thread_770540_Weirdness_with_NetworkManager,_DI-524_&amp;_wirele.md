---
title: "Weirdness with NetworkManager, DI-524 &amp; wireless"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by emanuel.landeholm on 2008-04-27
I'm having some problems configuring a protected  wlan network using NetworkManagar.

0. How do I configure a protected wlan, simplest possible, that works with windows XP & NetworkManager, on my DLINK DI-524?
1. How do I make the wlan network available on boot? As it is now I need to login to start nm-applet, which messes upp my servers & ntp-client until I do.
2. I can't figure out how to use static DHCP  with the DLINK DI-524. My wired connection gets handed a dynamic IP and I'm 100 % positive I got the MAC ok.

[Here's a screenshot from the DI-524 config pages...](http://jel-desktop.no-ip.org/di-524-config-1.png)
[ifconfig from a root shell](http://jel-desktop.no-ip.org/ifconfig.png)

As you can see, I have been handed a dynamic IP even though the MAC is lin the static list.

---

