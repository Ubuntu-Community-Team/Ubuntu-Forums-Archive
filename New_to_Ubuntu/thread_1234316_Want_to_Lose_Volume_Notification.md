---
title: "Want to Lose Volume Notification"
date: 2009-08-07
forum: New to Ubuntu
---

### Post by pteri498 on 2009-08-07
Jaunty works like a dream on my EEE, except where it comes to the volume notifier that pops up when I increase or decrease my volume. Then everything grinds to a halt until the flashing notifier turns off.

Is there a way to switch it off? I would rather be blind to my volume level than have to watch it blinking at me while I wait for it to close.

---

### Post by Flimm on 2009-08-07
According to [this](http://www.killertechtips.com/2009/04/26/disable-notifications-in-ubuntu-904-jaunty-jackalope/), all you need to do is:
```
sudo mv /usr/share/dbus-1/services/org.freedesktop.Notifications.service /usr/share/dbus-1/services/org.freedesktop.Notifications.service.disabled
```

---

