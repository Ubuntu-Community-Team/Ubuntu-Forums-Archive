---
title: "nm-applet doesn't display on panel"
date: 2007-11-03
forum: Networking &amp; Wireless
---

### Post by demian0311 on 2007-11-03
Network Manager is running:
```
demian@kabar:~$ ps -ef | grep NetworkManager
root      4541     1  0 16:38 ?        00:00:00 /usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/NetworkManager.pid
root      4555     1  0 16:38 ?        00:00:00 /usr/sbin/NetworkManagerDispatcher --pid-file /var/run/NetworkManager/NetworkManagerDispatcher.pid

```

And nm-applet is running as well:
```
demian@kabar:~$ ps -ef | grep nm-applet
demian    5617  5453  0 16:38 ?        00:00:00 nm-applet --sm-disable
```

But I can't see nm-applet on my Gnome panel.

This is on a fresh 7.10 install, but it _was_ working earlier.

Anyone have any ideas what I'm doing wrong?

---

### Post by demian0311 on 2007-11-04
Okay, I feel stupid.  I was just missing the 'Notification Area' from my panel.  Apparently that's where the Network Manager applet lives.  

right click on panel -> add to panel -> drag 'Notification Area' on to the panel.

---

