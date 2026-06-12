---
title: "how to switch display mgr's  ???"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by ozark_hillbilly on 2009-11-13
I have been kubuntu after gnome became corrupt. I have since purged old gnome and reinstalled. 

Code:
---------
sudo apt-get purge "gnome*"
---------

Code:
---------
sudo aptitude install ubuntu-desktop
---------

When it finished I got a message about the display mgr selection but it froze. Selecting Ok would do nothing. I'm still locked on kde and need to know where to go to switch over to gde.

Ed

---

### Post by JBAlaska on 2009-11-13
Must be the screen asking you if you want to install GDM, if KDM is working you can keep that or change to GDM, Like so:
You can modify the ```
/etc/X11/default-display-manager
``` file. 
For KDM, the file should read ```
/usr/bin/kdm
``` for GDM, the file should read ```
/usr/sbin/gdm
```

---

