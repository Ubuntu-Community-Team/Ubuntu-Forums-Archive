---
title: "Changed GDM login screen background reverts after update manager runs"
date: 2011-02-02
forum: New to Ubuntu
---

### Post by jcoles on 2011-02-02
I changed the background for the GDM login screen by editing /var/lib/gconf/debian.defaults/%gconf-tree.xml. (That bright purple splash is just too ugly!) After running Update Manager, the purple splash (warty-final-ubuntu.png) is back. Is it really necessary to dictate user's choice of background image like this? 

Is there a better way to change this background image?

I know I could probably rename my background image to warty-final-ubuntu.png, but that would be a kluge.

---

### Post by CryNGRoad on 2011-02-05
This is how I changed the gdm backgound: [http://ubuntuforums.org/showthread.php?t=1611691](http://ubuntuforums.org/showthread.php?t=1611691)
I'm not sure if this way will get messed up during an update, but I tried reinstalling gdm and it didn't reset.

The way you changed it would be bound to get overwritten on an update, because /var/lib/gconf/debian.defaults/%gconf-tree.xml is not owned by the user and is a file provided by the gconf2-common package. Even just reinstalling that package will overwrite the file.

---

### Post by jcoles on 2011-02-05
Thanks. I'll get Ubuntu Tweak. 

I worked out the background change by grep'ing the files looking for "warty-final-ubuntu.png". Theoretically, anything in Ubuntu can be changed, but you have to know how it works.

---

