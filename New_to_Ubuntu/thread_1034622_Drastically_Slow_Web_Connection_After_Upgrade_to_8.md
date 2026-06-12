---
title: "Drastically Slow Web Connection After Upgrade to 8.10"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by PrairieShaman on 2009-01-08
Hello folks. 

I have been using Ubuntu for a few years now. When I upgraded my distro to 8.10 I noticed that my internet connection now cuts out and I need to unplug the connection or reset it at my router for it to work again, and when it is working it is incredibly slow compared to what it used to be. 

I figured it might have been from the upgrade, so what I did was backed up what I wanted to keep to my external USB hard disk and did a fresh install of 8.10 with a good Ubuntu 8.10 disc. I changed my partitioning this time as well so that I have /home as its own partition for more convenience next time. . But after the fresh install of 8.10 I am still experiencing the same problem. My internet connection is DHCP I run it through a linksys router, but the problem is being experienced on my WIRED connection as well as the wireless connections. 

Is there any reason for this? How can I get my connection speed back up?

---

### Post by unutbu on 2009-01-08
Perhaps try disabling IPv6:```

gksu gedit /etc/modprobe.d/aliases
```
Change```

alias net-pf-10 ipv6
```
to```

alias net-pf-10 off
```
(See [http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html](http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html))
For reasons which I do not really understand, IPv6 seems to slow down some people's internet connections.

---

### Post by Iowan on 2009-01-08
IPv6 is a frequent cause of slowdowns, but the last few versions of Ubuntu have all had IPv6 (the *disable* link in my sig is kinda old).

---

