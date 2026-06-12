---
title: "Deleted items folder in 9.04"
date: 2009-09-10
forum: New to Ubuntu
---

### Post by johntrublu on 2009-09-10
I deleted quite a lot of files (or moved them into the deleted items folder),  and yet the deleted items folder/wastebin is empty.  is there any reason for this ?

---

### Post by credobyte on 2009-09-10
```
ls -l ~/.local/share/Trash/files

```

If you get nothing, they might have been deleted permanently ( eg., file too big ).

---

### Post by johntrublu on 2009-09-10
thanks

---

### Post by johntrublu on 2009-09-10
I typed that code into terminal and it listed all the deleted files.  yet when i click on the wastebin it says empty

---

### Post by PukingPenguin on 2009-09-10
Dunno why. 
If you are looking to restore these files you can use either the cp or mv command. General syntax is <command> <source> <target>

---

### Post by johntrublu on 2009-09-11
thanks for all your help,  just like magic I have booted up today and the wastebin is full of the items i deleted

---

