---
title: "network aplet"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by trinidadflores on 2009-06-05
how can i find the network aplet again.  Its missing on my panels.  help!!!!!


Trinidad Flores

---

### Post by NilsE on 2009-06-05
> **trinidadflores said:**
> how can i find the network aplet again.  Its missing on my panels.  help!!!!!


Trinidad Flores

You should be able to add the Notification Area to the panel which includes the Network applet. Jus right click the panel and select add to panel

---

### Post by mocoloco on 2009-06-05
The name is misleading.  I think it used to be a regular panel applet, but it now runs in the "notification area" or system tray.  Press alt-F2 and type "nm-applet" and see if that starts it.  If it's not coming up after you first log-in check your "startup items" in System -> Preferences.  If it's not there you can add it.

---

### Post by doas777 on 2009-06-05
are all your interfaces configured in the /etc/network/interfaces ? if so, NM will exit saying in the system log that it could not find any managed interfaces. appearently once you manually configure it, the interface becomes "unmanaged".

---

