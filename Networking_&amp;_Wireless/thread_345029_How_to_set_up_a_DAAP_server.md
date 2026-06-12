---
title: "How to set up a DAAP server"
date: 2007-01-23
forum: Networking &amp; Wireless
---

### Post by tikal26 on 2007-01-23
Hello,

I am looking to share my music using amarok, but the instruction on the wiki
[http://amarok.kde.org/wiki/Music_Sharing](http://amarok.kde.org/wiki/Music_Sharing)
takes for granted that I already have a DAAP server configure. How do I do that, I goolge and I have find tangerine and firefly, but I have no idea how to use it or if there is something else in the repos that I can use and how to configure it.

---

### Post by mrgrapefruit on 2007-01-24
tikal, 

depending on how your system is set up, you might to able to go to [http://au.ubuntu.cafuego.net/dists/edgy-cafuego/media/](http://au.ubuntu.cafuego.net/dists/edgy-cafuego/media/) and get the mt-daapd package. Package installer should sort it out for you. then just 

```
sudo gedit /etc/mt-daapd.conf
```

and thats that. It should auto-register itself on avahi and come up in your DAAP enabled player/hardware. If it doesn't, then just manually add a *.service file to /etc/avahi/services/

best of luck

---

