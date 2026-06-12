---
title: "Iwl4965 and Avahi"
date: 2007-11-07
forum: Networking &amp; Wireless
---

### Post by realvz on 2007-11-07
OS: Gutsy Gibbon
Kernel 2.6.22
DE: Gnome

I used to have perfectly working DAAP on both WLAN and Lan, then i installed KDE and uninstalled Gnome...now i went back to gnome and uninstalled KDE and now Rhythmbox doesnt see any DAAP shares ONLY when connected to WLAN...if i connect to my router using wire then everything works perfectly.

I have also tried DLINK and linksys routers...no config changes were made to the router...

experts?

---

### Post by spd106 on 2007-11-09
The usual things to check are that avahi-daemon is running.
```
ps ax | grep avahi
```

and that the interface has multicast enabled.
```
ip a
```

It might also be a good idea to look through the /var/log/syslog for any errors in avahi starting as the interface is brought up.

---

