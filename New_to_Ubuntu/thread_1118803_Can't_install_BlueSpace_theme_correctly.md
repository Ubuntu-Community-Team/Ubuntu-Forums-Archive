---
title: "Can't install BlueSpace theme correctly"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by nanikusasaki on 2009-04-07
I installed the theme Bluespace onto my computer (ubuntu 8.10) and dragged it into my Appearances box. Now when I click on the theme to apply it, it tells me that "This theme will not look as intended because the required GTK+ theme engine " is not installed"

This has happened with some other themes too. Could someone please tell me what I have to do (I'm pretty sure it requires editing the gtkrc file) to make it work?

:) Thanks in advance to anyone who helps me

---

### Post by iBurger on 2009-04-09
it just works with 8.04. However, its very ugly. are you sure you want this theme ? 

:p

> I tried this one: [http://www.gnome-look.org/content/show.php/BlueSpace+II?content=78633](http://www.gnome-look.org/content/show.php/BlueSpace+II?content=78633)

---

### Post by hesjnet on 2009-04-09
Install the gtk2 engine:

Write this in a terminal:

```
sudo apt-get install gtk2-engines
```

---

### Post by Jakey_TheSnake on 2009-04-09
It will work anyway >_>

---

