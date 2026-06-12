---
title: "locking network manger to panel"
date: 2007-03-21
forum: Networking &amp; Wireless
---

### Post by bvmou on 2007-03-21
I have a strange problem; occasionally and unpredictably the NetworkManager applet disappears, it generally doesn't affect the connection itself but it makes it impossible to switch networks if it does.  I can always display the Network Monitor.  Is there any way to lock the manager applet to the notification area or another part of the panel?  If I use iwlist ... scan, iwconfig etc. will that effect my other defaults?  Is there some way to launch the NetworkManager independently?  Any help much appreciated.

---

### Post by Pseudo Idol on 2007-03-21
I can't help you on the disappearing part, but to launch Network Manager independently run
```
nm-applet
```
That is the front-end applet for Network Manager that contains the icon in the tray.

---

### Post by bvmou on 2007-03-21
Nothing pseudo about it, you're an idol.  Thanks a million.  A funny thing, that problem always happens when I am logging into a particular network.  If anyone is reading this an has any idea why a particular network might cause the NetworkManager applet to disappear, I'd be fascinated to learn what's happening.  Thanks again PI

---

