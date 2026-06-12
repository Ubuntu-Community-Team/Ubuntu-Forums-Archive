---
title: "I'm curious..."
date: 2009-06-11
forum: New to Ubuntu
---

### Post by mesmith on 2009-06-11
I'm a new user.  I'm curious about something.  In my /home directory, under the subdirectory /myname, I had moved some directories from my old Windows system.  Several of them.  In every case involving the directories I moved into my /home/myname directory, they appear as something like this: "My Documents" (no quotes).  But, if I open a Terminal windows and execute a "dir", they appear as "My/ Documents."  Why?  Why has the "/" been added to the Terminal representation of these directories?

---

### Post by philinux on 2009-06-11
Try ls instead of dir. It's just the space in the name that shows the /.

Try to use meaningful thread titles. Some people will not read some like this. ;)

---

### Post by PocketDog on 2009-06-11
The slash denotes a space in a filename, without having to mess about with speechmarks. For instance ```
cd My\ Documents
```  is exactly the same as typing ```
cd "My Documents"
```

---

### Post by nandemonai on 2009-06-11
**My\ Documents**

Has to be a \ to denote a space.

---

### Post by CatKiller on 2009-06-11
Strictly speaking, the \ is an escape character to tell the shell not to interpret the space, but just to treat it as a character. You might do the same for other characters that might be interpreted to have a special meaning, like * or ?. It means that "My Documents" will be treated as a single string instead of as "My" "Documents" which would be two.

---

### Post by mesmith on 2009-06-11
Thanks for clearing that up.  Appreciate all the comments.

---

