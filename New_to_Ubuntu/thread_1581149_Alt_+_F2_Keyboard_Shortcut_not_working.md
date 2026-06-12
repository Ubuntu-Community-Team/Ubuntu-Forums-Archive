---
title: "Alt + F2 Keyboard Shortcut not working"
date: 2010-09-24
forum: New to Ubuntu
---

### Post by Manoj.C on 2010-09-24
I am using Ubuntu 10.04 and I installed AWN and removed gnome panels as given in [http://www.omgubuntu.co.uk/2010/09/how-to-fully-replace-your-gnome-panels-with-awn/]("http://www.omgubuntu.co.uk/2010/09/how-to-fully-replace-your-gnome-panels-with-awn/") . Now, the keyboard shortcut Alt+F1 and Alt+F2 are not working. I tried Changing the keyboard shortcut and assigned new keys. But, I dint work. Can anyone help me out to make the shortcuts work?

---

### Post by Tibuda on 2010-09-24
The standard "Run" dialog is done by gnome-panel, so it won't work if you remove them. You could try to use an alternative like [gmrun](apt://gmrun) and assign it to Alt+F2, using the Compiz commands plugin.

---

### Post by kerry_s on 2010-09-24
you need gnome panels for those.

what i do is disable the normal 1 using the backspace & install grun.

i'm using a micro keyboard so i set it to alt+2 so i don't have to hold the fn key.

---

### Post by beew on 2010-09-24
If you are using awn you can install grun from the repository. After it is installed, there will be a launcher simply called "launch" in the AWN main menu. Clicking it will bring up a run dialogue box just like pressing ALT+F2 when you use the gnome panel.

EDIT: Just realized Kerry_S already mentioned grun

---

