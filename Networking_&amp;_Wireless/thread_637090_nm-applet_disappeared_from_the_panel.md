---
title: "nm-applet disappeared from the panel"
date: 2007-12-10
forum: Networking &amp; Wireless
---

### Post by Superdelphinus on 2007-12-10
Hi, for some reason nm-applet seams to have disappeared from the gnome panel! Network monitor is still there but i can't connect wirelessley to the internet from that. To connect now i've had to log on to my girlfriends log in then connect to the internet through there (her nm applet is still there) then switch user back to mine. How can i get it back?

---

### Post by chalewa on 2007-12-10
right click on the panel, hit add to panel, and then select network monitor.

---

### Post by aysiu on 2007-12-10
Or, if that doesn't work, press Alt-F2 and type ```
nm-applet --sm-disable
```

---

### Post by Junglizer on 2007-12-10
```
iwlist <device> scan
iwconfig <device> essid "essid"
dhclient <device>
```

[B][I]No GUI...?

NO PROBLEM![/I][/B]

---

