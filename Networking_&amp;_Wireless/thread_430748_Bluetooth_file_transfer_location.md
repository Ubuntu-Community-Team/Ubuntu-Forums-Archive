---
title: "Bluetooth file transfer location"
date: 2007-05-02
forum: Networking &amp; Wireless
---

### Post by Dubstar_04 on 2007-05-02
How do I change the location that files are saved to when using bluetooth  transfers? At present everything is appearing on the desktop and i can find how to change it.

I am using feisty and the gnome bluetooth stuff

---

### Post by fabertawe on 2007-05-08
Press Alt and F2 and enter ```
gconf-editor
```Then navigate to```
/apps/gnome-obex-server
``` where you can specify the save directory and also turn off that annoying dialogue box! Enjoy ;)

Paul

---

