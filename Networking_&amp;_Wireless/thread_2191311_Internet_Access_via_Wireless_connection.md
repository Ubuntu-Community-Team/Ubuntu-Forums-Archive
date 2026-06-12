---
title: "Internet Access via Wireless connection"
date: 2013-12-01
forum: Networking &amp; Wireless
---

### Post by sakal-yim on 2013-12-01
My PC is connected to 2 networks: Wired (without internet connection) and Wireless (with internet connection). Both of them are up but it seems that I do not have access to internet unless I disconnect the wired connection. Is there anyway to keep both connection active and have the internet connection available?

---

### Post by varunendra on 2013-12-03
Welcome to the forums sakal-yim !

The Network Manager application is designed to prefer the wired connection if available. But it can be configured to use wireless instead. Please try this -

Click the NM applet icon at the top right of the screen > click "Edit Connections" > double-click your wired connection to edit it > go to "IPv4" tab (assuming you are using IPv4 to connect) > click "Routes" button > put a tick mark in the second checkbox that says "Use this connection only for resources on its network" > OK > Save > Close

Reboot if necessary and let us know if it helped.

If not, please open a terminal (Ctrl-Alt-T) and post back the outputs of the following commands (while both wired and wireless connections are active) -
```
ifconfig -a
nm-tool
route -n
```

---

