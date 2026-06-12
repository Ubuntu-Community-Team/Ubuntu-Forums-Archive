---
title: "Disable Notifications"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by jbrown96 on 2009-02-17
I'm using Ubuntu 8.10. Is there a way to disable notifications in the system bar. Ideally, I would like to eliminate the popup notifications that the update manager and network manager make. I suppose I could just disable automatically checking for updates, but I do like having the icon there (just not the popup that covers my windows). I just don't want to be bothered by constant popups. At my University, the wireless resets about every 10 minutes, and network manager decides I need a popup that lasts ~10 seconds every time it disconnects and then another when it reconnects. I know perfectly well what the "connection in progress" icon looks like; I don't need a reminder Gnome.


Thanks for the help

---

### Post by adult swim on 2009-02-17
a fix for this is to make the daemon that is responsible for notifications non executable.  to do taht open a terminal and run ```
sudo chmod -x /usr/lib/notification-daemon/notification-daemon

killall notification-daemon
```  if for some reason in the future you find yourself awake at night wishing you hadnt run off those cute little balloons of  
information and your heart longs to see the yellow popups return, simply run ```
sudo chmod +x /usr/lib/notification-daemon/notification-daemon

/usr/lib/notification-daemon/notification-daemon &
``` and they will come running back.

---

### Post by jbrown96 on 2009-02-17
> **adult swim said:**
> a fix for this is to make the daemon that is responsible for notifications non executable.  to do taht open a terminal and run ```
sudo chmod -x /usr/lib/notification-daemon/notification-daemon

killall notification-daemon
```  if for some reason in the future you find yourself awake at night wishing you hadnt run off those cute little balloons of  
information and your heart longs to see the yellow popups return, simply run ```
sudo chmod +x /usr/lib/notification-daemon/notification-daemon

/usr/lib/notification-daemon/notification-daemon &
``` and they will come running back.

Thanks, it seems to work perfectly.

---

