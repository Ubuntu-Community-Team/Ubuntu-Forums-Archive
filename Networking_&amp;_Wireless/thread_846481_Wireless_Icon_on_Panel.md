---
title: "Wireless Icon on Panel"
date: 2008-07-01
forum: Networking &amp; Wireless
---

### Post by Eureka89 on 2008-07-01
Hello,
Accidentally, I removed the wireless icon that appears on the top panel and I can't seem to get it back. It's the icon that tells you if you're connected to the internet or not. If connected, it would show some bars and if it's attempting to connect, it shows two dots that turns green if the signal is picked up. Also, if left-clicked, it shows a dropdown menu of available connections.

Does anyone know how to get that icon back?

Thanks in advance,
Ken

---

### Post by Eureka89 on 2008-07-02
*bump*

---

### Post by jolx on 2008-07-02
right click on the panel, select add to panel and add network monitor

---

### Post by Eureka89 on 2008-07-02
> **jolx said:**
> right click on the panel, select add to panel and add network monitor
Thanks for the reply. Unfortunately, that's not the one I want. I'm sure by default, Ubuntu has its network thing that it displays and if someone ever removes it, it doesn't come back. =[

---

### Post by Krydahl on 2008-07-02
Go into system->preferences->sessions.

Make sure that you have a tick next to Network Manager and it should be back next time you boot.

To check it gives you what you're looking for, type: 

nm-applet --sm-disable

into a terminal. Note, the applet shows up in the notification area on your panel, so if you haven't got that you need to add it to your panel. (Right click on panel, add to panel, notification area).

---

### Post by rosyatrandom on 2008-08-29
All of the above is correct - however, to avoid having to restart in order for the wireless utility to appear in the notification area, just run (using [Alt]+[F2]) 'nm-applet'.

---

### Post by roboa1983 on 2009-04-04
I had a recent problem, but could not solve it through this method, since when I typed the command above, I got:

> $ nm-applet --sm-disable

** (nm-applet:7376): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3


(nm-applet:7376): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed


To get the wireless part, you need to add to panel the Notifications Area.

---

### Post by gabo.cr on 2009-08-14
> All of the above is correct - however, to avoid having to restart in order for the wireless utility to appear in the notification area, just run (using [Alt]+[F2]) 'nm-applet'. 

Yes, it works!

Thank you.

---

