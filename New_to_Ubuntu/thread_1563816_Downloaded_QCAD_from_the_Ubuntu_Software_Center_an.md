---
title: "Downloaded QCAD from the Ubuntu Software Center and now I cant find it"
date: 2010-08-29
forum: New to Ubuntu
---

### Post by FlightFollower on 2010-08-29
Like the Title says, I dl QCAD, but now I can find it on my machine anywhere, Im running Ubuntu 10.04 UNR. Any help you could provide would be greatly appreciated

---

### Post by jcolyn on 2010-08-29
You have to open the terminal and type ```
qcad
``` to start it..

---

### Post by FlightFollower on 2010-08-29
> **jcolyn said:**
> You have to open the terminal and type ```
qcad
``` to start it..

AWESOME!!! 

Thanks,  is there a way that I can get a menu button ?

---

### Post by davidmohammed on 2010-08-29
system-> preferences-> main menu

you can add a launcher from there.

---

### Post by jcolyn on 2010-08-29
> **FlightFollower said:**
> AWESOME!!! 

Thanks,  is there a way that I can get a menu button ?

I haven't tried to see if that is possible. You might try adding a desktop widget. I believe you need to find application launcher and locate the Qcad executable.

---

### Post by gcvisel on 2010-09-05
To put that on a menu, _right-click_ over the Applications menu and choose **Edit Menus**.  The main menu will pop up.  Choose which sub-menu you want it to show in, and there click **New Item**.  Choose Application, give it a name, enter the command to start it, and any words you want to pop up when you hover over the menu item to tell you what it is.  

Click OK and Close, and check that it works.  If not, go back and edit the menu again and find your new item.  Click **Properties** and change **Application** to **Application in Terminal.**    If you had to start it from a terminal window, that should do it.

Spook

---

### Post by Themotorman on 2010-12-08
> **gcvisel said:**
> To put that on a menu, _right-click_ over the Applications menu and choose **Edit Menus**.  The main menu will pop up.  Choose which sub-menu you want it to show in, and there click **New Item**.  Choose Application, give it a name, enter the command to start it, and any words you want to pop up when you hover over the menu item to tell you what it is.  

Click OK and Close, and check that it works.  If not, go back and edit the menu again and find your new item.  Click **Properties** and change **Application** to **Application in Terminal.**    If you had to start it from a terminal window, that should do it.

Spook

Thank you. Sometimes the obvious isn't!

---

