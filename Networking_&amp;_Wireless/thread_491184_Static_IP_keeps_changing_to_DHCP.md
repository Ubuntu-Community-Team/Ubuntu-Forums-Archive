---
title: "Static IP keeps changing to DHCP"
date: 2007-07-03
forum: Networking &amp; Wireless
---

### Post by mudpile45 on 2007-07-03
I've had a static IP on my feisty box for awhile, but for the past few months my ip address will randomly switch back to a dhcp assigned address from my router. Doing 'sudo /etc/init/init.d/networking restart' switches me back to static ip, but after four or five hours go by I'm invariably switched back to the dhcp IP. I set up the static IP using the gnome network configurator, here's my /etc/network/interfaces file:

```
auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.1.99
netmask 255.255.255.0
gateway 192.168.1.1

auto eth0
```

I installed network manager a couple months ago and suspect that's related to the problem, but I have since deinstalled it since you can't use it's VPN capabilities if you have a static IP. Anyone have any ideas what could be causing this? I'm stumped

---

### Post by SpiritIsReality on 2007-10-06
howdy
bump 
buds

---

### Post by SpiritIsReality on 2007-10-13
hope this helps

[http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+static+ip+dhcp++noob12&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+static+ip+dhcp++noob12&btnG=Search&meta=)
[http://ubuntuforums.org/showthread.php?p=3475167](http://ubuntuforums.org/showthread.php?p=3475167)
[http://ubuntuforums.org/showthread.php?t=296880](http://ubuntuforums.org/showthread.php?t=296880)

trails

---

