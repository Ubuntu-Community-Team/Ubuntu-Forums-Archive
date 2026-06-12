---
title: "I think my wireless connection is causing my wired connection to constantly reset"
date: 2007-12-09
forum: Networking &amp; Wireless
---

### Post by tnunamak on 2007-12-09
When I have an ethernet cable plugged into my laptop and turn on that connection, every 30 seconds or so I think the connection temporarily tries switching to the wireless connection, fails, and then goes back to the wired connection. The reason this causes problems for me is that I have to re-authenticate with my school's network, so this behavior is not transparent.

When I boot up, I typically run

```
sudo ifconfig eth1 up
sudo dhclient eth1
```

to turn on the ethernet connection.

Any help would be appreciated

---

### Post by tnunamak on 2007-12-09
I'm not certain, but I think this might be KDE related. I just logged into gnome and everything works wired.

---

### Post by tnunamak on 2007-12-10
bump?

---

### Post by kevdog on 2007-12-10
Did you bring down the wireless connection with sudo ifconfig wlan0 down (or whatever your wireless interface is.

---

### Post by tnunamak on 2008-01-31
This issue has resurfaced after a fresh install... I've brought down the wireless network with ifconfig and also by unloading the module, and the problem still occurs, so I really don't know what's causing it. Any ideas would be extremely helpful.

---

### Post by tnunamak on 2008-01-31
Bump

---

### Post by tnunamak on 2008-01-31
My temporary fix is to uninstall wireless drivers completely... that seems to work, but now I don't have wireless :/

Hmm...........

---

### Post by tnunamak on 2008-02-06
Apprently that wasn't a fix... it has suddenly started again. Any help?

---

