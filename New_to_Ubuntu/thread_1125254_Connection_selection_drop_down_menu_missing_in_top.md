---
title: "Connection selection drop down menu missing in top panel! Pls help."
date: 2009-04-14
forum: New to Ubuntu
---

### Post by VasanthS on 2009-04-14
Hi. I'm a new Ubuntu user. I installed Ubuntu 8.10 this morning and its working fine. I have two broadband connections and i use both the connections alternatively. There was a drop down menu to select the connection (radio buttons) in the top right panel(next to the volume control icon). The problem is that the drop down menu is missing now. I tried googling and went through all the threads in this forum, but couldn't find a solution to get it back. I know this is a silly problem but i found it very comfortable while swapping connections. Anybody pls help...

Regards, 
Vasanth.

---

### Post by mcduck on 2009-04-14
Most likely you have just accidentally removed the Notification Area-applet from your panel. (it's kind of like the systray in Windows, and Network Manager puts it's icon there).

Right-click on empty space in your panel, select "Add to panel", find the "Notification Area"-applet and drag&drop it into the panel.

---

### Post by VasanthS on 2009-04-14
I did as u said. But only a red arrow(updates) appears.

---

### Post by mcduck on 2009-04-14
> **VasanthS said:**
> I did as u said. But only a red arrow(updates) appears.

Try logging out and back again. If that doesn't help, open a terminal and run "nm-applet --sm-disable" (& post possible error messages here).

If that works but Network Manager still doesn't start on it's own make sure you have it enabled in your session (System/Preferences/Startup Applications).

---

### Post by VasanthS on 2009-04-14
Ok i'll be back in a jiffy.

---

### Post by VasanthS on 2009-04-14
Okay i did as u instructed. Even restarted my pc. Still no use. When i ran the command in terminal, i got this error
-------------------------------------------------------------------------
** (nm-applet:5568): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3


(nm-applet:5568): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
--------------------------------------------------------------------------
Is there any other way??

---

