---
title: "Where did my app go and how do I launch it?"
date: 2010-02-16
forum: New to Ubuntu
---

### Post by bholtby on 2010-02-16
A live USB install of Xubuntu 9.1. I've used synaptic to install some applications (UCBlogo (from universe), R (from universe) and openoffice.

For openoffice, writer, impress, etc. appear as applications in the office menu item and work fine. But the shell app called soffice only appears as a link to a shell script in the usr\bin folder not in the menu. If I open the shell script, WOW! 2 pages of incomprehensible stuff. So where is the script and how to I get the link to it into the applications menu?

UCBlogo is in use\bin as an executable but double clicking it gets a brief bout of disk activity and then nothing. What gives?

A R, seems to install but is nowhere to be found.

Does all this mean that the only apps that can be installed are those that have the orange and yellow circle indicating officially supported?

Help!!

---

### Post by MinimalBin on 2010-02-16
*soffice* is the *OpeOffice.org* launcher - if Writer / Calc / Impress are already in place, why bother ?

---

### Post by bholtby on 2010-02-16
True, but my post was more about figuring out how one launches apps and creates links to get that done. The launcher also gives immediate access to all of the apps in soffice not just the big four.

---

### Post by magellancraig on 2010-02-16
I am new to Xumbuntu also, but I created  the equavalent of a windows shortcut by right clicking on the desktop, and choosing:
 
"Create Launcher"
 
from the menu. Once you fill in the name to give the launcher (shortcut). you ban click the folder icon next to the command box. That will let you browse the file system. On my system, it brings me to /usr/bin. Most of my apps are either in "/usr/bin" or in "/usr/lib". But m X-Plane app installed in /home/simop1/X_Plane 9. (simop1 is my user name). But most apps are in one of the folders under /usr. You might have to poke around, or use the applications menu, select accessories, then search to locate the app.
 
Hope this helps a little
 
Craig

---

### Post by bholtby on 2010-02-17
Thanks for the help with launcher, I didn't know about that. But that isn't the problem. I install software, even ubuntu supported software and it just seems to vanish - meaning there is no entry in the applications menu. An executable is present in usr\bin. I looked at the shell script for soffice (like a DOS batch file?) and realized that many of the files identified in the file browser need to be invoked from a command line. And lo and behold my programs worked. Way different from Windows!

So now back to the other questions. Is there a dummies guide to writing shell scripts? ( so that I can click on a script and start the program instead of manually starting a terminal and typing the program name). 

And how do you manually make an entry in the applications menu?

---

### Post by 3rdalbum on 2010-02-17
> **bholtby said:**
> Thanks for the help with launcher, I didn't know about that. But that isn't the problem. I install software, even ubuntu supported software and it just seems to vanish - meaning there is no entry in the applications menu. An executable is present in usr\bin. I looked at the shell script for soffice (like a DOS batch file?) and realized that many of the files identified in the file browser need to be invoked from a command line. And lo and behold my programs worked. Way different from Windows!

If it's a GUI program, then you should try filing a bug against the package, because I think all GUI programs should have .desktop files included that will create a menu item.

Terminal programs shouldn't - any more than Windows.

> So now back to the other questions. Is there a dummies guide to writing shell scripts? ( so that I can click on a script and start the program instead of manually starting a terminal and typing the program name).

Easy-peasy-lemon-squeezy. To create a shell script that launches Firefox:

```
#!/bin/bash
firefox
```

'firefox' will automatically resolve to /usr/bin/firefox.

> And how do you manually make an entry in the applications menu?

Right-click on the Applications menu and go to Edit Menus. The rest is pretty self-explanatory - when you're creating the launcher you can either click the "Browse" button and navigate to the program, or you can just specify the filename if it's inside /usr/bin or /usr/local/bin.

---

### Post by bholtby on 2010-02-17
Thanks 3rdalbum for your clear and patient reply. That really helped get me going!

---

