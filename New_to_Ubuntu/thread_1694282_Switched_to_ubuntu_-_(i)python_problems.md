---
title: "Switched to ubuntu - (i)python problems"
date: 2011-02-24
forum: New to Ubuntu
---

### Post by Young_blood on 2011-02-24
Hi everyone!
I decided to learn python because I needed for my computational biology project.
I picked a book called A Primer for Scientific Programming with Python. The book suggested to learn python in Ubuntu environment, using iPython as an interactive shell.

Anyway, since I'm new to Ubuntu (using 10.04)  and Python, I've been having problems configuring it properly. This is what I get when I run iPyhon (the problem manifests itself when I try to use arrow keys to edit previously typed commands.

```

sta11:~$ ipython
WARNING: Readline services not available on this platform.
WARNING: The auto-indent feature requires the readline library
Python 2.6.5 (r265:79063, Apr 16 2010, 13:57:41) 
Type "copyright", "credits" or "license" for more information.

IPython 0.10.1 -- An enhanced Interactive Python.
?         -> Introduction and overview of IPython's features.
%quickref -> Quick reference.
help      -> Python's own help system.
object?   -> Details about 'object'. ?object also works, ?? prints more.

In [1]: 

```Hope someone can help me with this.

I tried installing pyreadline by using easy_install, but the problem still persists.
If it's relevant, I also tried (re)installing libreadline6-dev

---

### Post by zenwalker on 2011-02-24
Please check the ipython README/Install file for any specific ver of read line packages it works correctly with.

---

### Post by sanderd17 on 2011-02-24
can you use python instead of ipython? the differences aren't that big.

---

### Post by DaithiF on 2011-02-24
How did you install ipython?  From a package or manually?

installing from the ubuntu packaged version includes working readline support.  Well at least it does on my version (ubuntu 10.10)

```
sudo apt-get install ipython
```

---

### Post by Young_blood on 2011-02-24
I solved the problem. Looks like I forgot that I installed pyreadline via easy_install. Now I removed it and everything works perfectly.

Thanks for your help.

---

