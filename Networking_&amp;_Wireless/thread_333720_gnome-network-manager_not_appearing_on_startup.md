---
title: "gnome-network-manager not appearing on startup"
date: 2007-01-07
forum: Networking &amp; Wireless
---

### Post by LogicalDash on 2007-01-07
I've installed network-manager and gnome-network-manager. When I click on the Run Command icon and type nm-applet, the applet appears and lets me connect to wireless networks, just as it's supposed to. Now I've put nm-applet into Startup Applications, logged out, and logged back in again, and the applet doesn't show up in the notification area. I go into System Monitor, and nm-applet is running all right, it's just not showing up in the notification area. If I click on Run Command and type nm-applet again, it shows up and behaves normally.

What can I do to make it appear on startup?

---

### Post by jpeddicord on 2007-01-07
I'm not completely sure about this, but instead of adding nm-applet to the startup, add:```
nm-applet --sm-disable
```

That was how it appeared in my startup config when I last used Network Manager. I haven't researched the sm-disable option, but I have a feeling it has to do with session startup.

---

