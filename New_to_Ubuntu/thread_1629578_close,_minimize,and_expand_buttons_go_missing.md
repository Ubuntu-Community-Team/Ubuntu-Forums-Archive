---
title: "close, minimize,and expand buttons go missing"
date: 2010-11-23
forum: New to Ubuntu
---

### Post by Coretj on 2010-11-23
the close, minimize,and expand buttons keep disappearing.. a reboot fixes the problem.. but I don't know why this would happen... it is sporadic but they seem to either not show from start up or when I log back in from Screen Saver.  But like I said it doesn't happen all the time.

Please Help.

---

### Post by Quackers on 2010-11-24
Which window manager are you using? If it's metacity press Alt+F2 and type in ```
metacity --replace
``` and hit enter.

---

### Post by sikander3786 on 2010-11-24
And fusion-icon is another handy replacement for that. Install it, add it to your startup and then access it from system tray and you'll be able to change/reload your Window Manager.

```
sudo apt-get install fusion-icon
```

Add to startup by going to System > Preferences > Startup Applications > Add and command would be

```
fusion-icon
```

Good Luck!

---

