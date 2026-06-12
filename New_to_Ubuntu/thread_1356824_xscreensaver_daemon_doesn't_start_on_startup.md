---
title: "xscreensaver daemon doesn't start on startup"
date: 2009-12-16
forum: New to Ubuntu
---

### Post by werecatomega on 2009-12-16
i've just switched to xscreensaver, but the daemon doesn't start when i start up the computer:confused:. can anyone help me?

---

### Post by rCXer on 2009-12-16
You have to add xscreensaver to the list of startup programs. Go to System->Preferences->Startup Applications. Press Add. Type "xscreensaver" for the name and "xscreensaver -no-splash" for the command.

---

