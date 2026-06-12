---
title: "How to start Network Manger automatically"
date: 2007-07-01
forum: Networking &amp; Wireless
---

### Post by partymanbg on 2007-07-01
hi all,

 I am using Ubuntu 6.10 with Desktop Manger Beryl 

I have this entry - "nm -applet" - in System->Preferences->Sessions->StartUp Programms  but my NetworkManager still don't want to start automatically on login. (there is no notification icon on start up ) I have to run nm-applet from the terminal in order to see the programm icon.

What can I do to make Network Manager start automatically on login???

10x for you help

---

### Post by benanzo on 2007-07-01
try this:
```
nm-applet --sm-disable
```

---

### Post by partymanbg on 2007-07-01
still not working...

Do you have some other ideas?

10x

---

