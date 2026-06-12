---
title: "Install multiple packages?"
date: 2011-07-14
forum: New to Ubuntu
---

### Post by villnn on 2011-07-14
I am looking for a program/script that will allow me to install multiple packages, one after another. Does such a thing exist?

You see, I have in excess of 109 packages that need to install for certain applications to function properly, and it would be a pain to install **every single one of them manually. **

Perhaps I haven't been looking in the right places, and if this is the case, would someone be so kind to point me in the right direction.

---

### Post by irw on 2011-07-14
are all of these .deb files?

 If so, and all in one directory, you could try```
sudo dpkg -i *.deb
``` in a terminal.

Alternatively, in Synaptic, select "Add downloaded packages" from the File menu, and select the folder where your files are.

---

### Post by villnn on 2011-07-14
#-o

How could have I missed that?

Well, at any rate, thank you.

---

### Post by Sef on 2011-07-14
Moved to ABT.

---

