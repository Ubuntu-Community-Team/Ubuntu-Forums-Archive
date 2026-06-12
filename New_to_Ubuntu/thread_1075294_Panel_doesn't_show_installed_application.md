---
title: "Panel doesn't show installed application"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by promis_solution on 2009-02-20
Don't know what happened. 

Installed Applications are any longer shown in the panel. Alt-F2 opens the application starter but also here not installed applications are shown. The application >System>main menu does also not start.

---

### Post by swoll1980 on 2009-02-20
some apps don't add them selfs to the menu. Right click the menu and add the apps

---

### Post by promis_solution on 2009-02-21
The problem is is connected to the application "alacarte". This application cannot be started although it is running without any problems under a second user name. Seems to be corrupted for the first user.

Have found the solution under Ubuntu wiki alacarte. Renamed folder .local/share/applications and .config/menus to reset the menu.

---

