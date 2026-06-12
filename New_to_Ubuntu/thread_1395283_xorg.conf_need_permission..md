---
title: "xorg.conf need permission."
date: 2010-01-31
forum: New to Ubuntu
---

### Post by soryu on 2010-01-31
im trying to configure xorg but when i try to save it . i get a i dont have permission to save message in red.
 what  command can i use to save the settings?

---

### Post by chewearn on 2010-01-31
You need to open the file with admin privileges.
```
gksudo gedit /etc/X11/xorg.conf
```Make sure to create a backup before you begin, in case you need to revert the changes.
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

---

### Post by mattbutsko on 2010-01-31
you should be able to hit Alt+F2 and type "gksudo nautilus" then navigate to xorg.conf and open it in gedit. in the past gedit has inherited admin rights before.

or do gksudo gedit and open xorg.conf from within gedit and that should work to.

make sure you back up your xorg!

edit: awww beat me to it.

---

### Post by soryu on 2010-01-31
thank's

---

