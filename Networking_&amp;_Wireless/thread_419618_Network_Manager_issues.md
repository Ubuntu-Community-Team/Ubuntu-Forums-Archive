---
title: "Network Manager issues"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by Sleeping123 on 2007-04-23
My first post... How nice.
Anyways, I just installed 7.04 (like all of you) and got my wireless working relatively free of problems. I can connect to my wireless just through the gnome network manager applet and haven't hade issues. Until now!

Here's my issue. Every so often (usually around 6 AM EST, does that help?) the network manager applet will close itself! I can usually fix the problem with a reboot, but I betcha you guys out there have a solution that doesn't take that long. Thanks in advance!

---

### Post by spd106 on 2007-04-24
You can restart Network Manager through a dbus signal.
```
sudo /etc/dbus-1/event.d/25NetworkManager restart
```
Failing this restart dbus
```
sudo /etc/init.d/dbus restart
```

This won't solve your underlying problem though. Perhaps check the log files in /var/log/.

---

