---
title: "How can I change the font in gdm/xsplash?"
date: 2010-03-09
forum: New to Ubuntu
---

### Post by the8thstar on 2010-03-09
"Sans" is the default font in the gdm/xsplash screen.

How can you change it to a different font?

---

### Post by wojox on 2010-03-09
Here's how I did it: [http://wojox.homelinux.net/?p=15](http://wojox.homelinux.net/?p=15)

When it opens the control center select appearance and set your font that way. ;)

---

### Post by the8thstar on 2010-03-11
Your tip worked. Excellent! And thanks a lot for that info!!!

---

### Post by sisco311 on 2010-03-11
```
sudo -u gdm dbus-launch gnome-control-center
```should also work & you don't have to log out.

---

### Post by the8thstar on 2010-03-13
Just tried it and it works too!

---

