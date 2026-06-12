---
title: "how to delete old menu that are created during updates"
date: 2009-12-13
forum: New to Ubuntu
---

### Post by respect_dashal on 2009-12-13
how can i delete the old menu after i get new one when i install updates. it appears when i start my PC and when it give me to choose between 8 ubuntu menu and 1 windows.

---

### Post by emigrant on 2009-12-13
go to:
```
 sudo gedit /boot/grub/menu.lst
```

and comment out those lines you don't want to be shown during startup. (leave atleast one recovery mode and the windows partition if you are dual booting)

---

### Post by PocketDog on 2009-12-13
[http://ubuntuforums.org/showthread.php?t=1346397](http://ubuntuforums.org/showthread.php?t=1346397)

---

