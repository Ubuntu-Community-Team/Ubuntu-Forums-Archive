---
title: "network manager GNOME"
date: 2010-09-10
forum: New to Ubuntu
---

### Post by William S on 2010-09-10
Hi!
For some reason the Networkmanager in GNOME is gone from the panel. I can't find it when I right click and add to panel and I have tried the notification area option, but still doesn't display. Any hints for what to do? I really miss that nice little program.

---

### Post by TNT1 on 2010-09-10
Try "alt+f2" and type NetworkManager.

Also, when adding to panel, I believe it's part of an indicator applet, might not be, will check...

Yip, when you add to panel, select "Notification Area"...

---

### Post by migs73 on 2010-09-10
If the three horizontal lines are still there (the edge of the notification area) right click on them and delete from panel. Then add to panel the new notification area. If it still does not appear try log out/in again. If it still does not appear after that, I am now lost;)

---

### Post by coffeecat on 2010-09-10
> **migs73 said:**
> If it still does not appear after that, I am now lost;)

If it still doesn't appear :p go to System > Preferences > Startup Applications > Startup Programs tab. Make sure the Network Manager entry is ticked. If it's missing, click on 'Add' to add a new entry, and type this lot in:

Name: Network Manager
Command: nm-applet --sm-disable
Comment: Control your network connections

---

