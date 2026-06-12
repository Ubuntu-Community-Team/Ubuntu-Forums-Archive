---
title: "nm applet no longer shows"
date: 2014-12-26
forum: Networking &amp; Wireless
---

### Post by Steve1961 on 2014-12-26
This disappeared after the last update.  I'm still connected on my thinkpad but I can't seem to launch nm-applet or whatever it's now called.  Any workarounds known for this?  I see a bug has been reported

---

### Post by praseodym on 2014-12-27
Check if the NM is still started after login (autostart). Alternatively, create a starter for it and click it several times to see where it is shortly shown in the panel. If you click on that point afterwards the NM setting should be shown. If so, tick "activate network" then.

---

### Post by Steve1961 on 2014-12-27
> **praseodym said:**
> Check if the NM is still started after login (autostart). Alternatively, create a starter for it and click it several times to see where it is shortly shown in the panel. If you click on that point afterwards the NM setting should be shown. If so, tick "activate network" then.

It wasn't in autostart but adding it made no difference.  Attempting to launch the applet from the terminal just returns this message

nm-applet-Message: using fallback from indicator to GtkStatusIcon

---

### Post by praseodym on 2014-12-27
Ad a new starting panel there (don't know how to explain it in English, in German its "Benachrichtigungsfeld"). Sth. like notification panel?!

---

