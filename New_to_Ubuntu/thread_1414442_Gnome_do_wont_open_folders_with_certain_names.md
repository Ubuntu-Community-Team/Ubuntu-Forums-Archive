---
title: "Gnome do wont open folders with certain names"
date: 2010-02-23
forum: New to Ubuntu
---

### Post by Dangger on 2010-02-23
Gnome do wont open folders with accents (e.g. Música instead of Music). It wont open subfolders within one that has an accent. Any ideas on how to fix this? Thanks!

---

### Post by doas777 on 2010-02-23
can you get into the folder from the terminal using a shortcut like ~/M* or M*sica ? if so, what does 'pwd' return?

---

### Post by Dangger on 2010-02-23
> **doas777 said:**
> can you get into the folder from the terminal using a shortcut like ~/M* or M*sica ? if so, what does 'pwd' return?
It's not in my home folder but here:

> /media/Documents

When I hit ls the name of the folder appears as 

> Mi M??sica

But so far I can't get into the folder through the terminal since every time I enter 

> cd "Mi M??sica"

I get a:

> bash: cd: Mi M??sica : No such file or directory


---

### Post by rustutzman on 2010-02-23
Try typing the first few characters and hit "Tab"

```
cd Mi M
``` and then hit the tab key.

Russ

---

### Post by Dangger on 2010-02-23
> **rustutzman said:**
> Try typing the first few characters and hit "Tab"

```
cd Mi M
``` and then hit the tab key.

Russ

Thanks, I get the following:

> Mi M&#65533;&#65533;sica/

But still if I try:

> cd "Mi M&#65533;&#65533;sica"

I can't access it through the terminal.

---

