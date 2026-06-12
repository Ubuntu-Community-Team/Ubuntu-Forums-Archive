---
title: "Make folder in application browser"
date: 2011-03-15
forum: New to Ubuntu
---

### Post by Canime on 2011-03-15
I would like to create a folder in the lib directory using the application browser. I have root permissions but, I want to enable them for the folder that is in the lib/themes folder. How can I do it so that I can create a folder. Is the only way to do this through the terminal?

---

### Post by Blutkoete on 2011-03-15
Do I get this right?

You want to create a folder in a root-only part of your harddisk (*/lib*) from within the file manager?

**These instructions won't work with Kubuntu, Lubuntu or Xubuntu.**

Therefore you'd need to launch the file manager itself with the correct permissions. You can do that without the terminal, through the *Application Launcher*:


[LIST=1]
[*]Press ALT-F2 to show the Application Launcher window
[*]Type *gksudo nautilus* and hit *Enter. *It'll ask for your password.
[*]This (and only this) Nautilus file manager window should be able to create a folder there.
[/LIST]
*gksudo* enables *sudo* access for graphical applications, *nautilus* is the name of the file manager.

**Be aware that the file manager window has ultimate powers - it can ruin your system if you delete something important with it, and it won't warn you. Be sure you know what you do.**

Isn't there a better way to install a new theme? It appears you just want to do that.

---

