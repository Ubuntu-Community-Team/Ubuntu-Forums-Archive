---
title: "Internet Hangs"
date: 2007-10-22
forum: Networking &amp; Wireless
---

### Post by adamweyant on 2007-10-22
Ok, this is the situation:
Gutsy Gibbon fresh install.
Laptop with intel wireless card.
I turn on the computer plugged in to a wired network. Internet is connected. I unplug the network cable, wireless networking connects automatically to my hotspot. If I want to then plug the network cable back in, I try to switch to wired manually, the icon stays as wireless and the internet gets disconnected. If I try to disable networking, the icon stays as wireless, and the internet gets disconnected. To get a connection again I have to restart. What do I do to switch between wireless and wired networking with this hang? Thanks guys.

---

### Post by adamweyant on 2007-10-22
Sorry to bump this, but I really need some help. Anyone?

---

### Post by shad0w_walker on 2007-10-22
I assume you have nm-applet which shows your network status (The little icon that shows signal strength for wifi)

If so, have you tried right clicking on the icon and unticking the 'Enable wireless' box, waiting a few seconds and then re-enabling the option? That hopefully should get it going again (Not ideal but its something)

---

### Post by adamweyant on 2007-10-23
Yeah, I tried that. Also tried just disabling networking, that doesn't work either. Logging out doesn't work, it has to be a full restart for it to function again.

---

### Post by shad0w_walker on 2007-10-23
Have you tried running:

```
sudo /etc/init.d/networking restart
```

---

