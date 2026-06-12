---
title: "cannot take window screenshots while dropdown menu opened"
date: 2009-10-28
forum: New to Ubuntu
---

### Post by infestor on 2009-10-28
is there a way to take screenshots with *prt scr* key while a dropdown menu is active? drove me crazy so far. :(

---

### Post by Lod on 2009-10-28
In Gnome there is a program called "Take screenshot" in Applications - Accessoires. You can start a timer before taking the screenshot giving you time to open the menu.

---

### Post by lavinog on 2009-10-28
can you press prtscn then activate the drop menu immediatly afterwards?
There is a slight delay from pressing prtscn on my machine that allowed me to do it.

could be a bug though.

---

### Post by infestor on 2009-10-28
very exotic methods but i am afraid they dont help

---

### Post by lavinog on 2009-10-28
what dropdown menu are you trying to get a screenshot of.

---

### Post by infestor on 2009-10-28
keyboard preferences>layouts>add

i want to take denmark's layout list.

---

### Post by Sir Jasper on 2009-10-28
Hi,

Do as[COLOR="Blue"] Lod [/COLOR]suggests @ #2:

[[img]http://i.imagehost.org/t/0411/menu.jpg[/img]](http://i.imagehost.org/view/0411/menu)

Above taken with delay set to 30 seconds.

My regards

---

### Post by philinux on 2009-10-28
> **Sir Jasper said:**
> Hi,

Do as[COLOR="Blue"] Lod [/COLOR]suggests @ #2:

[[img]http://i.imagehost.org/t/0411/menu.jpg[/img]](http://i.imagehost.org/view/0411/menu)

Above taken with delay set to 30 seconds.

My regards

+1 post 2 is not exotic but simple ;)

---

### Post by lavinog on 2009-10-28
I was able to do it by first disabling desktop effects, then using import (part of the imagemagick package)

```

sleep 5 ; import -window root /tmp/screenshot.png

```

---

### Post by Lod on 2009-10-29
It took me about 5 seconds to take this one. Without disabling anything or using the commandline. Just with the application take screenshot.
8-)

[IMG]http://www.louistielens.nl/bestanden/example.png[/IMG]

---

