---
title: "network applet menu doesn't stay up"
date: 2018-05-18
forum: Networking &amp; Wireless
---

### Post by quatrezoneilles on 2018-05-18
This might be due to lxde, but I'll start here.  I have the following problem on lubuntu 18.04 :  clicking on the network icon on the system tray applet will produce a menu, but it's really hard to click on an entry before the menu disappears.  After several attempts I managed tu turn on ethernet and wifi, but reaching any submenu is impossible.  I reinstalled network-manager-gnome to no avail.

Somebody have an idea?[COLOR=#000000][FONT=&quot]
[/FONT][/COLOR]

---

### Post by quatrezoneilles on 2018-05-18
OK, I've solved the problem by disabling the "minimize panel when not in use" option.  So that was an lxde problem after all, something to do with the interaction between the system tray applet and the panel.

---

