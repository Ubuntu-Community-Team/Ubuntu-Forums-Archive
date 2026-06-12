---
title: "can I remove the password requirement"
date: 2010-03-03
forum: New to Ubuntu
---

### Post by PegM_4 on 2010-03-03
I don't take my laptop anywhere and only use it in my home.  Is there any way to remove the requirement for a password after it goes into "Suspend"?  

Thanks
Peg

---

### Post by snowpine on 2010-03-03
System->Preferences->Screensaver

Uncheck the "Lock screen..." box.

:)

---

### Post by mcduck on 2010-03-03
...note that this won't work if you use the Notification-Applet-Session -applet (the one in the top right corner of your desktop) because of a bug in that applet. Any other method of suspending will work like it should but suspending from that applet will *always* lock your screen, regardless of any options you have set in the screen saver or power management settings (or directly through gconf).

---

