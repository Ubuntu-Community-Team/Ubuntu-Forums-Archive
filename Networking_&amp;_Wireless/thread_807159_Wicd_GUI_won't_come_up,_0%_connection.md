---
title: "Wicd GUI won't come up, 0% connection"
date: 2008-05-25
forum: Networking &amp; Wireless
---

### Post by HappyUser123 on 2008-05-25
I use wicd for my wireless networking. Periodically and seemingly randomly while I'm connected, the wicd "system tray" icon will go black like it's disconnected, and the tooltip says "Connected to <my correct SSID> at 0% <my correct ip info>". The connection appears to work fine though. Right-click/Connect... does nothing, but Right-click/About... brings up the about screen like normal. I'm using a hidden SSID if that makes any difference. Everything usually fixes itself after a reboot.

Is anyone else getting this? Any ideas? Thanks.

---

### Post by imdano on 2008-05-26
Sounds like something is making the GUI crash when you try to open it.  My guess is the daemon crashed, but I'm not sure.  What happens if you run /opt/wicd/gui.py from a terminal?

---

### Post by HappyUser123 on 2008-05-27
Thanks for responding. I'll wait for the problem to happen again and then try gui.py from the console to see if there is any interesting info, and I'll check to see what wicd processes are running (normally it's daemon.py and tray.py).

Just so I understand the flow here, is it

* The icon in my system tray is tray.py

* tray.py gets its info from daemon.py

* daemon.py gets its info from the actual wireless hardware/driver

and you're thinking that daemon.py went down, which would explain why tray.py is reporting failure while the wireless connection itself continues to run without a problem?

---

