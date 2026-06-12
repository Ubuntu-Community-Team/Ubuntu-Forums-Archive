---
title: "accidentally deleted &quot;duluge&quot; from panel"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by servicetech on 2009-07-10
I accidentally deleted deluge from going to panel when minimized, how do I get it back? Deluge is still running and I can't maximize it.

---

### Post by koleoptero on 2009-07-10
> **servicetech said:**
> I accidentally deleted deluge from going to panel when minimized, how do I get it back? Deluge is still running and I can't maximize it.

Go to System -> Administration -> System Monitor
Go to the list off apps running, find deluge, right click on it and select stop.
Run deluge again.

If the problem persists, delete the settings of deluge by **rm -r ~/.deluge** and run deluge with the default settings. Unfortunately this will remove any active torrents which you will have to add again manually.

If Deluge opens in a window but doesn't show in the taskbar or system notification area try checking its options and see if you can restore it there.

---

### Post by servicetech on 2009-07-10
Disabling system tray icon prevents deluge form "hiding" and resolves the problem for now. I'd like to figure out how to enable the icon. Is there a way to "undo" what you removed from panel?

---

### Post by koleoptero on 2009-07-10
This seems weird... Do other windows show in the panel? I can think of no reason why deluge would remove itself from the windowlist of the panel...

---

### Post by servicetech on 2009-07-10
All other windows in panel work fine

I actually removed the deluge tray icon by accident, even enabling in deluge doesn't bring it back. I even tried unistalling and reinstalling deluge.

---

### Post by koleoptero on 2009-07-10
Did you try deleting the settings of deluge?

---

