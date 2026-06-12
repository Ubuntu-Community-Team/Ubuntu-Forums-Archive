---
title: "nm-applet can't start. reason: Icon 'nm-vpn-lock' not present."
date: 2006-08-07
forum: Networking &amp; Wireless
---

### Post by Buffalo Soldier on 2006-08-07
Whenever I logon to gnome now the nm-applet won't load and I get a warning window message. And If I start nm-applet in terminal, this is what I get:

> $ nm-applet --sm-disable 
** (nm-applet:6311): WARNING **: Icon nm-vpn-lock missing: Icon 'nm-vpn-lock' not present in theme

(nm-applet:6311): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJE CT (object)' failed

Any suggestions?

---

### Post by Buffalo Soldier on 2006-08-07
SOLVED

refer to [http://ubuntuforums.org/showthread.php?p=1296466](http://ubuntuforums.org/showthread.php?p=1296466) and [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

Run this command in terminal
```
sudo gtk-update-icon-cache -f /usr/share/icons/hicolor/
```

p/s: thanks to byen :)

---

