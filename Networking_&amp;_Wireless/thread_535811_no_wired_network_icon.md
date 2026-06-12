---
title: "no wired network icon"
date: 2007-08-26
forum: Networking &amp; Wireless
---

### Post by silverhat on 2007-08-26
the icon of wired connection disappeared & i don't know how to get it back. (i tried to add to panel the network monitor but it seems to be diff from the origin)
Can anyone help me?  i'm a newbie in Linux.
Thanks.

---

### Post by spd106 on 2007-08-27
Try restarting the nm-applet by pressing Alt+F2 and typing (or cut & pasting) in the following ```
nm-applet --sm-disable
```

If this doesn't work make sure you have a notification area on the panel and try again. Rhythmbox also uses the notification area for it's panel icon.

---

### Post by silverhat on 2007-08-27
> **spd106 said:**
> Try restarting the nm-applet by pressing Alt+F2 and typing (or cut & pasting) in the following ```
nm-applet --sm-disable
```

If this doesn't work make sure you have a notification area on the panel and try again. Rhythmbox also uses the notification area for it's panel icon.

I've already tried it but nothing happen.
But in my notification area there are some blank spaces between icons, i think nm-aplet is still there but i can't see it :confused:

Since this icon disappeared, i must plug cable & turn on modem before booting machine. If not, i must restart to access internet. i try to use /etc/init.d/dbus restart or /etc/init.d/networking restart  but it doesn't work:(

---

### Post by shadowcat on 2007-09-13
You need to a re-add the Notification Area to your panel: Right-click on the panel > Click Notification Area under Utilities.

--SC

---

