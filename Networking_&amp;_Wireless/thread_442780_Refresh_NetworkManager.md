---
title: "Refresh NetworkManager"
date: 2007-05-13
forum: Networking &amp; Wireless
---

### Post by goandeatsomestuff on 2007-05-13
Hello,
Is there a way, either through the terminal or the gui, to manually refresh the wi-fi list maintained by NetworkManager ([http://www.gnome.org/projects/NetworkManager/)?](http://www.gnome.org/projects/NetworkManager/)?)  I am having problems moving around my home and connecting to one of the various access points we have.  

There are two ways I can refresh it: a restart (not ideal at all) or, I can switch via System/Admin./Network from Roaming to Manual and back again, which is a bit cumbersome.

Thanks in advance!

---

### Post by spd106 on 2007-05-14
The wireless AP list should be refreshed every time you click on nm-applet.

I must admit that doesn't always work for me either. To restart Network Manager completely you can send a dbus signal via this command
```
sudo /etc/dbus-1/event.d/25NetworkManager restart
```

This will lose any current connection you have, though the keyring will not require you to re-enter your password.

---

### Post by fago on 2007-11-19
thanks for that tip, it helps :)

My list doesn't refresh if the laptop was suspended. Is there a way to automate calling this after resuming from standby?

---

### Post by spd106 on 2007-11-19
Yep, see [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

---

