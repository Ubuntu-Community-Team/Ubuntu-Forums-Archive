---
title: "Not Able to Launch my application"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by kapsule on 2009-08-25
Hi All,
i have made a debian package using dpkg tool with the menu entry and desktop entry files.
I am able to successfully install the package.
I am facing two problems :
1) Not able to launch the application from the menu-entry (though menu-entry for the application is listed ), but i am able to run the application from the shell.
2) Not able to create desktop icon. While i am able to create softlink using postinst script but that softlink is not able to launch the application.

Please help me..!!!:confused:

Thanks in advance.

---

### Post by zkriesse on 2009-08-25
What exactly are you trying to run? That would be a really good place to start.

---

### Post by Ocxic on 2009-08-25
try running the app from a terminal and see if the works, if it does compare the commend with the one for the menu entry for any differences.

---

### Post by kapsule on 2009-08-25
Actually i am running an application written in C, which in turns spawn other processes (executables).
In the app.desktop file and menu entry file, i am giving the path of that executable e.g /usr/bin/myapp.
Also all the other executables are also at the same place i.e /usr/bin

---

### Post by kapsule on 2009-08-25
To Ocxic: i have tried to run that exe from the terminal, it is running. But it is not running from the menu entry even if command is same.

---

