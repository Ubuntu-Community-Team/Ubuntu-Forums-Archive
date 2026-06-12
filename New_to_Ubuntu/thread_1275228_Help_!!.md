---
title: "Help !!"
date: 2009-09-25
forum: New to Ubuntu
---

### Post by twinaxel on 2009-09-25
Thought I would give LXDE a try much prefer gnome but how do I
back to gnome again?

Tried log out - switch session - clicked on gnome logged back 
in still get LXDE desktop.

---

### Post by Axess_Denied on 2009-09-25
Try rebooting and then selecting GNOME in your sessions.

---

### Post by jerrrys on 2009-09-25
during boot-up do you get an option to select gdm? if so, that would be gnome

---

### Post by Paqman on 2009-09-25
Do you still have all the Gnome apps in your menus? If not, install the package ubuntu-desktop and log out, you should be able to log back into a Gnome session.

---

### Post by twinaxel on 2009-09-25
> **Paqman said:**
> Do you still have all the Gnome apps in your menus? If not, install the package ubuntu-desktop and log out, you should be able to log back into a Gnome session.

 Many thanks that worked! How do I remove LXDE ?

---

### Post by credobyte on 2009-09-25
```
sudo apt-get purge lubuntu-desktop

```

or

```
sudo apt-get purge lxde
```

---

### Post by twinaxel on 2009-09-25
> **credobyte said:**
> ```
sudo apt-get purge lubuntu-desktop

```

or

```
sudo apt-get purge lxde
```

 Thanks

---

