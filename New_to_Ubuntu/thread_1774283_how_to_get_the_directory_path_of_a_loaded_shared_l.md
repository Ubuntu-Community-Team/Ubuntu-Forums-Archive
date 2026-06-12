---
title: "how to get the directory path of a loaded shared library within itself?"
date: 2011-06-03
forum: New to Ubuntu
---

### Post by veenkumar2003 on 2011-06-03
Hello All,

Is there any way to get the directory path of loaded shared library from inside of the library itself?

Thanks in advance

R,
P

---

### Post by jaacko on 2011-06-03
I'm not exactly sure what you mean, but in terminal command
```
pwd
```
shows the current working directory.

So while you're in the folder you want, typing that command will show the absolute path to that folder.

---

### Post by veenkumar2003 on 2011-06-06
The situation is like: I have a shared_obj(1) which loads another shared_obj(2). Both of them are present in the same directory. The shared_obj(1) is loaded by an application. After it has been loaded I have to get the path of it to load the shared_obj(2).
So within the shared_obj(1) I have to get the path of it from where it is loaded. I am working with c-files.

---

