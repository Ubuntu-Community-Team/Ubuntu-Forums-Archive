---
title: "[SOLVED] home folder"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by penguinee on 2008-12-22
Hi! I was wondering how I could make my home folder visible on my desktop.

Sorry for my wording if it is incoherent. I will clarify if need be.


Thank you! :KS

---

### Post by atngplusultra on 2008-12-22
right click on your desktop.
select "create launcher"
under Name: /home/
under Command: Nautilus

that should do it

---

### Post by unutbu on 2008-12-22
The follow will display the contents of your home directory on your desktop:

Edit your ~/.config/user-dirs.dirs:

```
gedit  ~/.config/user-dirs.dirs
```
Change
```

XDG_DESKTOP_DIR="$HOME/Desktop"
```
to
```

XDG_DESKTOP_DIR="$HOME"
```
Log out, and log back in.
That's all it takes.

---

### Post by penguinee on 2008-12-22
I'll try those methods soon.
Thanks so much for your quick replies! :)

---

### Post by nhasian on 2008-12-22
there's more than one way to skin a cat.

you can also use your middle mouse button to drag your home folder to the desktop and create a link :)

---

