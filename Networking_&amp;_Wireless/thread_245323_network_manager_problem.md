---
title: "network manager problem"
date: 2006-08-27
forum: Networking &amp; Wireless
---

### Post by djf on 2006-08-27
Hi all,

I've got a strange problem. I've installed network-manager-gnome and initially everything was fine. But now the nm-applet isn't displayed anymore in the top-panel. I can tell that it is running because it still connects me to my default wireless network. It's also shown in preferences->sessions (as well as ps aux | grep nm-applet). Normally I would just try to add the applet to the panel again, but there's no nm-applet in the list! Today I created a dummy user. Logging as such user, the nm-applet appeared in the top panel.

It's probably just a configuration issue, but even a google search marathon couldn't produce an answer.

I'm a fairly experienced BSD user and know my way around a UNIX environment, but I totally new to linux. It's possible that I've messed up some settings in a configuration frenzy :mrgreen:

Oh yeah, I've almost forgot: I use ubuntu 6.06 LTS and Gnome nm-applet 0.6.2

---

### Post by funchords on 2006-08-27
Network Manager displays in "Notification Area," which appears under Utilities in the "Add to Panel" dialog box.

---

### Post by djf on 2006-08-27
Yep, that was it. 

I managed to figure it out myself. It's funny how that always happens 5 minutes _after_ you post to a forum ;)

Thanks anyway!

---

