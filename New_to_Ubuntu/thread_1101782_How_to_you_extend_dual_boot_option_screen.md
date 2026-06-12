---
title: "How to you extend dual boot option screen?"
date: 2009-03-20
forum: New to Ubuntu
---

### Post by suomalainen on 2009-03-20
Ubunteros,

I just did a fresh dual boot install and want to extend the length of time that the automatic boot process kicks in....

Currently it's set at 10 seconds.. I'd like to make it 30-45 seconds maybe even a minute....

Thanks!!!

---

### Post by lisati on 2009-03-20
You will need to edit grub's "menu.lst" file.

From the command line (Applications->accessories->Terminal) type
```
gksudo gedit /boot/grub/menu.lst
```
Enter your password when asked
Then look for the line which reads something like
> timeout		10
Change the number to whatever delay you'd like. (Changing it to 0 not recommended.)
Save your file then exit the editor.

---

