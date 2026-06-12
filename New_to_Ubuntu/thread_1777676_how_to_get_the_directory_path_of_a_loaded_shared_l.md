---
title: "how to get the directory path of a loaded shared library within itself?"
date: 2011-06-08
forum: New to Ubuntu
---

### Post by veenkumar2003 on 2011-06-08
Hello All,

Is there any way to get the directory path of loaded shared library from inside of the library itself?

The situation is like: I have a shared_obj(1) which loads another shared_obj(2) which is present in the same directory. The shared_obj(1) is loaded by an application from a different directory. After shared_obj(1) has been loaded I have to get the path of shared_obj(1) to load the shared_obj(2).

So within the shared_obj(1) I have to get the path of it from where it is loaded. I am working with c-files.

Thanks in advance

R,
P

---

