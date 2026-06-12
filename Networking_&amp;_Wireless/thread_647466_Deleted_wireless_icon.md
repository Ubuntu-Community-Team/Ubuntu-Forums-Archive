---
title: "Deleted wireless icon"
date: 2007-12-22
forum: Networking &amp; Wireless
---

### Post by Barrett1734 on 2007-12-22
I am trying to customise my GNOME desktop, and in the process I deleted the network icon from the top panel and cannot figure out how to get it back. I can no longer access the internet on that computer. Any suggestions?

---

### Post by chewearn on 2007-12-22
Are you referring to the icon inside the notification applet?  That icon will appear when NetworkManager is running.

1. Check your System Monitor, see if you find NetworkManager in the list.
2. If you restart your PC, does the NetworkManager comes back?

To run the NetworkManager, press ALT+F2, then enter:
```
nm-applet --sm-disable
``` 

If the NetworkManager does not come back after restart, go to:
Top Panel Menu > System > Preferences > Sessions
Click the +Add button, enter:
Name: Network Manager
Command: nm-applet --sm-disable
Comment: Network Manager applet

---

### Post by Barrett1734 on 2007-12-22
That worked. Thanks.

---

