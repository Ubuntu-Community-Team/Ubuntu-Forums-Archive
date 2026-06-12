---
title: "[really basic] so i've got this annoying icon on my desktop space ;)"
date: 2011-04-11
forum: New to Ubuntu
---

### Post by RememberWhenItRained on 2011-04-11
...which happens to be the OS (or at least, so it's labeled.) I tried moving it to the trash, but it said it could not be trashed, only immediately deleted. That and the icon made me wonder if this was not simply a shortcut to the filepath. (A shortcut would look like an open file folder with an arrow, no?)

So, how do i get this pesky thing of my desktop space without deleting the whole folder?
(sorry, yes very basic)

---

### Post by wolfen69 on 2011-04-12
> **RememberWhenItRained said:**
>  (A shortcut would look like an open file folder with an arrow, no?)


Correct.

Open a terminal and do 
```
gksu nautilus
```
then you can navigate to the file in question and delete it.

---

### Post by RememberWhenItRained on 2011-04-12
> **wolfen69 said:**
> Correct.

Open a terminal and do 
```
gksu nautilus
```then you can navigate to the file in question and delete it.
ooh, nautilus is cool, but it's not showing anything on desktop. could that be because I'm in root > desktop? But nautilus uses Root by default since it needs administrative privileges right?

Here, screencap:

---

### Post by K_45 on 2011-04-12
That OS is a mounted drive[SIZE=2]. Do you have multiple internal hard drivers or external devices plugged in?[/SIZE]

---

### Post by RememberWhenItRained on 2011-04-12
> **K_45 said:**
> That OS is a mounted drive[SIZE=2]. Do you have multiple internal hard drivers or external devices plugged in?[/SIZE]
nope, just  one HD with no external devices plugged in.

---

### Post by K_45 on 2011-04-12
Hmm, click on the drive entry in Nautilus. What do you see?

---

### Post by RememberWhenItRained on 2011-04-12
> **K_45 said:**
> Hmm, click on the drive entry in Nautilus. What do you see?
looks like my windows stuff (im dual booting)

---

### Post by K_45 on 2011-04-12
> **RememberWhenItRained said:**
> looks like my windows stuff (im dual booting)

That explains it. Ubuntu is automounting your Windows partition.

---

### Post by RememberWhenItRained on 2011-04-12
> **K_45 said:**
> That explains it. Ubuntu is automounting your Windows partition.
can i get the icon off the desktop without screwing it up?
and while i get what your saying well enough, what exactly is mounting?
ETA: strange. it's gone. (for now?)

---

### Post by el_koraco on 2011-04-12
Nautilus is showing the mounted windows system on the desktop. You can either unmount it manually by right clicking it and selecting "unmount", or you can fire up ALT-F2, typing gconf-editor, then going to 'apps - nautilus - desktop', and unticking the last entry (volumes visible).

---

### Post by deathadder on 2011-04-12
If you unmount it, it'll still be displayed on the desktop but mount the device again when you double click on it. 

Unfortinuately it seems that the only way to stop it is to fireup gconf-editor unlike in XFCE:tongue:

---

