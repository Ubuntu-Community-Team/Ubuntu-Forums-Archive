---
title: "shut down icon on Desktop"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by bu2971x on 2009-05-10
how to put a shut down icon on the desktop( not the panel)??
thanks  9.04

---

### Post by cholericfun on 2009-05-10
try right click and create launcher
type the command there:
```
gksudo shutdown -hP now
```

at least thats what i've seen "should" work
-didnt for me when i tried it out...

---

### Post by LoloftheRings on 2009-05-10
I've been searching for this too, I figured this script, but it requires root privileges..

```

#!/bin/bash
echo yourpassword|sudo shutdown -hP now

```

There should be a better solution :p

---

### Post by LoloftheRings on 2009-05-10
[http://www.unix.com/linux/14373-non-root-shutdown.html](http://www.unix.com/linux/14373-non-root-shutdown.html)

when reading comment 5, this command should allow you to shutdown without root privileges:
sudo chmod +s `which shutdown` `which reboot`

then, create an application launcher at the desktop, and enter the command:
shutdown -hP now

Hope this should do it :D

---

### Post by CatKiller on 2009-05-10
Create a launcher. Call it whatever you want, and give it whatever icon you want. In the Command box, put ```
gnome-session-save --shutdown-dialog
```

---

