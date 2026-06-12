---
title: "I accidentally removed the WiFi icon on my panel!"
date: 2009-06-22
forum: New to Ubuntu
---

### Post by ramoj02 on 2009-06-22
I have Ubuntu 9.04 (Jaunty Jackalope) and when I was customizing my panel, I accidentally removed the WiFi icon near the clock. I don't know how to add the WiFi icon on the panel once again. I can connect to the Internet but I can't see the WiFi connection I'm connected to or how much signal do i get from the wireless connection.

PLEASE! Can somebody help me?

---

### Post by Nepherte on 2009-06-22
Try issueing nm-applet in a terminal or in the <Alt>+F2 Run dialog:
```
nm-applet
```

To run it every time you log in, you should add it to system > preferences > session (or startup programs)

---

### Post by ramoj02 on 2009-06-22
The Network Manager is running. I can connect to the Internet and everything but the only thing is there's no Network Manager icon on the panel. I tried Right Click>Add to Panel... but the Network Manager is not on the list.

---

### Post by Dark006 on 2009-06-22
I've had this happen before and what I think I did to fix it was add the "Notification Area" back to my panel. Right-click, select 'Add to panel' and add the Notification Area one and see if that works.

---

### Post by ramoj02 on 2009-06-22
> **Dark006 said:**
> I've had this happen before and what I think I did to fix it was add the "Notification Area" back to my panel. Right-click, select 'Add to panel' and add the Notification Area one and see if that works.

THANK YOU SO MUCH!!!

That fixed it! I didn't know its the "Notification Area"!
:D

---

