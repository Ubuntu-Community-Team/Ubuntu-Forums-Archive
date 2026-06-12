---
title: "How to Execute a Python Scripts"
date: 2011-08-22
forum: New to Ubuntu
---

### Post by dniMretsaM on 2011-08-22
So I just started my Python "class" for school (I'm homeschooled) and I'm wondering how to execute the scripts I write. I use the Eclipse IDE with the PyDev plug-in to write them. When I run a script within Eclipse, it works just fine, but I can't seem to figure out how to execute them outside of Eclipse. I have marked them as executable. I have written them in Python 3.2, so I'm wondering if I am somehow trying to run them with a different version of Python (I believe 2.7 is the default version installed in 11.04). How would I check/correct this issue? Should I simply uninstall all versions of Python (which I don't want to do) or can I set 3.2 as the default for when I try to execute scripts (or denote which version I want to run each script with)? I hope this made sense, please ask if you need anything clarified.

---

### Post by JC Cheloven on 2011-08-22
Hi, not completely sure to understand your question, but if you open a terminal, navigate (using the cd command) to the folder where your script is (say thingie.py), and type ```
python thingie.py
```, does it works? (it should...)

---

### Post by LemursDontExist on 2011-08-22
> **JC Cheloven said:**
> Hi, not completely sure to understand your question, but if you open a terminal, navigate (using the cd command) to the folder where your script is (say thingie.py), and type ```
python thingie.py
```, does it works? (it should...)

Alternatively, if you put a shebang:

```
#!/usr/bin/env python
```

as the first line of your python script you can run it directly - via

```
./thingie.py
```

The shebang lets your shell know what program to use to interpret  the file.

---

### Post by dniMretsaM on 2011-08-22
> **JC Cheloven said:**
> Hi, not completely sure to understand your  question, but if you open a terminal, navigate (using the cd command) to  the folder where your script is (say thingie.py), and type ```
python  thingie.py
```, does it works? (it should...)

No, it doesn't. It runs it, but it doesn't show up correctly.

> **LemursDontExist said:**
> Alternatively, if you put a shebang:

```
#!/usr/bin/env python
```as the first line of your python script you can run it directly - via

```
./thingie.py
```The shebang lets your shell know what program to use to interpret  the file.

That worked. Thank you very much! I think that using ```
python thingie.py
``` was trying to run the program with the wrong interpreter.

P.S. Lemurs do exist. I have seen them personally. ;)

---

