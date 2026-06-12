---
title: "Change order in grub screen for 10.04"
date: 2010-05-30
forum: New to Ubuntu
---

### Post by Blobface on 2010-05-30
Hi, Does anyone know how to change the order of the grub screen for Ubuntu 10.04 so that windows is on top?
 
I have found instructions for previous versions but with comments from other people saying not to change grub2 or something like that.

---

### Post by ibuclaw on 2010-05-30
Open a terminal, and type in:
```
gksu gedit /etc/default/grub
```

And change the number on the GRUB_DEFAULT line to the entry number that Windows is on, you can determine this by counting from top down, starting with 0.
```
GRUB_DEFAULT=0
```
Once updated, save, quit, and run:
```
sudo update-grub
```
To set it in the grub.cfg file.

Regards
Iain

---

### Post by n213978745 on 2010-05-30
> **ibuclaw said:**
> Open a terminal, and type in:
```
gksu gedit /etc/default/grub
```And change the number on the GRUB_DEFAULT line to the entry number that Windows is on, you can determine this by counting from top down, starting with 0.
```
GRUB_DEFAULT=0
```Once updated, save, quit, and run:
```
sudo update-grub
```To set it in the grub.cfg file.

Regards
Iain


You may also try this method
Change the following entry on your /etc/default/grub

```

GRUB_DEFAULT=saved
GRUB_SAVEDEFAULT=true
```I am NOT sure whether the second line is needed or not.  My method will help you to SAVE your last used line as default.

And if you don't see the second line on your gedit, add it yourself below the first line.

You can also find out more info in the following link:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)


EX: if you use Windows Vista to boot last time, the next time when you start your computer again, the highlighted line will go to Windows Vista.

---

