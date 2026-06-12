---
title: "make or gcc"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by mowa7id on 2009-02-03
hello
i am new to ubuntu and unix in general
i learned to use some basic commands and now i'm trying to make my first program in c language and run it.

do i have to install **make**?
i don't understand what make is but with gcc i can't compile neither un my hello world

thank u in advance

---

### Post by Eisenwinter on 2009-02-03
You need to install some compiling tools.

Go to **Applications -> Accessories -> Terminal**.

In there, type:
```
sudo apt-get install build-essential
```

Once installation is done, navigate to your project's folder, with the **cd** command:
```
cd <wherever your project is, without these arrows>
```

And then type:
```
gcc <source_file.c without these arrows>
```

---

### Post by snova on 2009-02-03
> **mowa7id said:**
> do i have to install **make**?

You do if you want to use it. ;)

> i don't understand what make is but with gcc i can't compile neither un my hello world

GCC is the compiler; make is a tool to automate rebuilding your code (but only the parts that have changed).

What errors are you getting?

---

