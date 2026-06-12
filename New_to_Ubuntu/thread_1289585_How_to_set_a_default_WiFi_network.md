---
title: "How to set a default WiFi network?"
date: 2009-10-12
forum: New to Ubuntu
---

### Post by listerdl on 2009-10-12
Hi does anyone know how I can make my WiFi default - everytime I log on I have to set my WiFi network - this is a little bit annoying, I am sure there is a way to make it set.

Thanks for all advice!!

---

### Post by achase79 on 2009-10-12
I use wicd instead of network manager and it has a setting to connect automatically on a per network basis.

---

### Post by sandyd on 2009-10-12
> **achase79 said:**
> i use wicd instead of network manager and it has a setting to connect automatically on a per network basis.
+1

---

### Post by kimberlite on 2009-10-12
Left click to network-manager applet, than select AUTO >>NAME OF YOUR WIFI NETWORK<<, than click to EDIT, at WIRELESS TAB than you should select MODE >>INFRASTRUCTURE<< (rather than >>AD HOC<<). Network-manager applet's icon usually shows up at upper-right corner of gnome panel.

---

### Post by listerdl on 2009-10-12
> **kimberlite said:**
> Left click to network-manager applet.........

Is that the same as Network Monitor?

I dont seem to have the network-manager applet when I try to add items to the panel....

thanks

---

### Post by Schendje on 2009-10-12
No, it's not the same. You can also get there by System -> Admin/Prefs -> Network Connections.

---

### Post by markbuntu on 2009-10-13
wicd is definitely the easiest way to do it.

---

### Post by zkriesse on 2009-10-13
Ok....opposite click on System. Choose the edit menus option. You should see a bunch of stuff with checkboxes. Find the one that says Network Connections. Check it. Hit close and then go to System/Preferences/NetworkConnections. Choose the wirless tab. Pick the connection that you want in wireless and then click edit. Choose the auto connect option then close...close the other stuff and then try to connect to your network. Enter proper password and username and then turn off the pc. Start it up and it should auto connect! Let me know how it turns out.

---

### Post by kimberlite on 2009-10-15
> **listerdl said:**
> Is that the same as Network Monitor?

I dont seem to have the network-manager applet when I try to add items to the panel....

thanks

You can add network-manager from the gnome menu (->PREFERENCES -> STARTUP APPLICATIONS). You can select it from the list, or add "nm-applet" manually.

---

