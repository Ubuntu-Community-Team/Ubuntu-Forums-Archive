---
title: "network manager tray icon and fbpanel/openbox"
date: 2008-08-23
forum: Networking &amp; Wireless
---

### Post by teddmeister2 on 2008-08-23
Is there a way i can set up my openbox/fbpanel so that i can run the network manager applet in my fbpanel tray?  I'm needing to set up my openbox version to be able to connect/disconnect from my wireless network.

thanks a lot.

---

### Post by spd106 on 2008-08-23
I've never tried Openbox, so I can't really help very much. However I do know that nm-applet (Network-Manager) uses the notification area, so you'll probably want to check that you have this added to the panel.

---

### Post by commodianus on 2010-09-28
> **teddmeister2 said:**
> Is there a way i can set up my openbox/fbpanel so that i can run the network manager applet in my fbpanel tray?  I'm needing to set up my openbox version to be able to connect/disconnect from my wireless network.

thanks a lot.

You may wish to look into wicd.

---

### Post by Mathieu G on 2011-01-13
I just use a notification area tool like "trayer" or "docker".
Then just start the network manager applet "nm-applet".

I do that in my openbox's auto start file (~/.config/openbox/autostart.sh):
trayer --widthtype request --heighttype request --edge bottom --align right &
nm-applet &

---

