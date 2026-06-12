---
title: "Howto:  Restart NetworkManager"
date: 2007-10-25
forum: Networking &amp; Wireless
---

### Post by T_W on 2007-10-25
Hopefully a simple question.

How do you restart NetworkManager?

There does not appear to be an init script in /etc/init.d.

Sometimes on my system, NetworkManager becomes unresponsive and I would like to restart it to see if this clears the issue.

---

### Post by T_W on 2007-10-25
Replying to my own post... 
This page: [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

says:

> sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
sudo /etc/dbus-1/event.d/25NetworkManager stop

will stop NetworkManager.

These scripts seem to support  restart as well.

---

