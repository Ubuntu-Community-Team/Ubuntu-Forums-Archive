---
title: "File I made just disappeared"
date: 2010-03-21
forum: New to Ubuntu
---

### Post by razorseal on 2010-03-21
I made a .conkyrc file on the desktop, saved it, and it disappeared! It's nowhere to be found, and I just tried making a new file named the same thing and it says it can't be created because a file with the same name already exists in this folder?

wtf? help? so lost... lol

---

### Post by howefield on 2010-03-21
The period before the file name means it is a hidden file.

Open Places > Home Folder > Desktop and press the Ctrl + H keys and you'll see your file. (Or from the Nautilus View menu, select show hidden files).

---

### Post by razorseal on 2010-03-21
ahhh got it, thanks :)

---

### Post by n0dix on 2010-03-21
Or if you use the console, with the command:
```
$ ls -la $HOME 
``` you can see the all hidden files too.

---

