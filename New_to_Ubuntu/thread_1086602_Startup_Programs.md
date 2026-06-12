---
title: "Startup Programs?"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by Gp. on 2009-03-04
Hey,
I want pidgeon messenger to automatically start when Ubuntu loads.

How do I choose startup programs?

---

### Post by jaminux on 2009-03-04
System > Preferences > Sessions (just for your user account)

You have to know the command for the program though. In the case of Pidgin just type pidgin for the command.

---

### Post by konqueror7 on 2009-03-04
Go to *System > Preferences > Sessions*, add pidgin there, and the next time you will boot it will start automatically...

---

### Post by Gp. on 2009-03-04
How do I set the Compiz Fusion icon to stay?

---

### Post by skymera on 2009-03-04
Add new, and in the command box type in whatever command it is you use to load fusion icon :)

fusion-icon is it?

---

### Post by konqueror7 on 2009-03-04
what do you mean by stay? just the same, put the command equivalent of compiz-fusion icon (i think its *fusion-icon*), but i don't usually do that because it slows my start-up...:D

---

### Post by Gp. on 2009-03-06
How do you find out those values (like fusion-icon)?

---

### Post by Paqman on 2009-03-06
> **Gp. said:**
> How do you find out those values (like fusion-icon)?

It's generally the name of the package in Synaptic. For stuff which is already in your menus you can right click on a menu > edit menus and go to that entry and check the properties. That'll show the command used to launch it from the menu.

---

### Post by oldos2er on 2009-03-06
> **Gp. said:**
> How do you find out those values (like fusion-icon)?

 Use the 'which' or 'whereis' command, e.g.
```
which fusion-icon
```
 should show you
```
/usr/bin/fusion-icon
```
 Since /usr/bin is in your path, type 'fusion-icon' into Sessions' startup programs.

---

