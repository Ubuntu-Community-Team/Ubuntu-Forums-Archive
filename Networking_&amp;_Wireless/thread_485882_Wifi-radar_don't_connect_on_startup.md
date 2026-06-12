---
title: "Wifi-radar don't connect on startup"
date: 2007-06-27
forum: Networking &amp; Wireless
---

### Post by guano on 2007-06-27
Hello all.
I got this new laptop, a Samsung R20, with an Atheror wireless card. It works great, just that when I turn it on, it won't connect to my wireless router, unless I onpen a terminal, run 
```
dhclient -r ath0 
ifconfig ath0 down
ifconfig ath0 up
dhclient  ath0 
```

In my other laptop (Xubuntu install), I have wifi-radar working perfectly. It recognizes which network I am in (home, university) and auto-connect. In this new laptop (gnome-ubuntu alternate install, because of the video driver), it doesn't. I removed network-manager, gnome-network-manager, and the wifi-radar.conf is the same of the old laptop.

any hints? Did I forgot to remove something else?

thanks

---

