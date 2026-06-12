---
title: "Files I have edited"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by douglasja on 2009-11-17
So I have done a bit of adding stuff to files recently to get my ubuntu working smoothly. Only thing is I would like to keep note of what I have done to what files and I have deleted my recent files list.

So is there a way to find out all the files I have edited?

---

### Post by mprince on 2009-11-18
If you launched the files for editing using a terminal-- it has a command history function that you can cycle through to see what commands you have used. 

This would help you see exactly which files you brought up for editing. It will not tell you how you modified them though.

Just open a terminal and keep pressing the "up arrow" key to go further back. (the "down arrow" will take you forward)

---

### Post by oldos2er on 2009-11-18
If you used gedit, by default it will create a backup copy of any file you edit, with the name foo.txt~. Run ls *~ in a given directory to find them.

---

### Post by philinux on 2009-11-18
```
cd /

then 

sudo find -name *~

```

---

