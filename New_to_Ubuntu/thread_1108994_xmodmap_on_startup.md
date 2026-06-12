---
title: "xmodmap on startup"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by netimen on 2009-03-28
I have found many topics on it in these forums, but most of them were not about kubuntu.
So, I can't get my xmodmap settings loaded automatically on system startup. I have put them into .xmodmap file, copied to .Xmodmap, added a command launching "xmodmap /home/netimen/.xmodmap" in Autostart, but nothing helped: still I have to launch xmodmap manually if I want my settings be applied. What can I do to solve the problem?

---

### Post by ronocdh on 2009-03-28
> **netimen said:**
> I have found many topics on it in these forums, but most of them were not about kubuntu.
So, I can't get my xmodmap settings loaded automatically on system startup. I have put them into .xmodmap file, copied to .Xmodmap, added a command launching "xmodmap /home/netimen/.xmodmap" in Autostart, but nothing helped: still I have to launch xmodmap manually if I want my settings be applied. What can I do to solve the problem?
If you read the man page on xmodmap, there should be a command to set a custom one (that you have saved somewhere locally). Then you should be able to write a small bash script with that command and have that bash script be a startup item.

Make sure you have it set to pre-KDE startup and then it should work for login.

---

### Post by JohnnyK on 2009-07-04
Old topic, and I am using Gnome, but I had the same issue here until I changed the autostart to a script that also used a sleep command:
```

#!/bin/bash

sleep 10 && xmodmap .Xmodmap;
```

Otherwise I had to manually load my xmodmap file every time even though it was in the startup programs.

---

