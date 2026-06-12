---
title: "How do I show the full path in file browser rather than buttons to folders?"
date: 2010-05-27
forum: New to Ubuntu
---

### Post by manwood on 2010-05-27
I need a way of copying a full file path from the file browser but I only have a list of button to represent the file path.. any suggestions?
 
thanks

---

### Post by philinux on 2010-05-27
See the forum sticky in General Help.

---

### Post by Sir Jasper on 2010-05-27
Hi,

You could drag and drop the folder or file into an open ternimal; then copy and paste to where you need it if you do not want it in the terminal.

There are almost certainly other methods as well.

My regards

---

### Post by Jakiejake on 2010-05-27
> **philinux said:**
> See the forum sticky in General Help.

Hey Phil
Thought Of getting a more interesting signature, Just Sayin

---

### Post by Jakiejake on 2010-05-27
> **Jakiejake said:**
> Hey Phil
Thought Of getting a more interesting signature, Just Sayin

Ur Gonna ban me for saying that aren't you
JK
Ok i'm getting off topic now
Sorry :(

---

### Post by Jakiejake on 2010-05-27
> **manwood said:**
> I need a way of copying a full file path from the file browser but I only have a list of button to represent the file path.. any suggestions?
 
thanks

Right Click on the folder button then click Properties Then In that window it will show the location!
:lolflag:

---

### Post by Morbius1 on 2010-05-27
Press Ctrl+L in Nautilus

---

### Post by Jakiejake on 2010-05-28
> **Morbius1 said:**
> Press Ctrl+L in Nautilus

That Works!

---

### Post by walkerchuckwalker on 2010-05-28
Ctrl+L does work. I was wondering that exact thing and I was even going to  make a thread for it. Thanks Man!

---

### Post by rousseau09 on 2012-01-11
Close **Nautilus/File Browser**.
Press Alt-F2 and type the following in the run box:
```
gconf-editor
```
Expand Configuration Editor
```
apps --> nautilus --> preferences
```
Tick **‘always_use_location_entry’** and close Configuration Editor.

Open Nautilus. Voila!

Hope this is what you've been looking for.

---

### Post by overdrank on 2012-01-11
Back to sleep thread. :)

---

