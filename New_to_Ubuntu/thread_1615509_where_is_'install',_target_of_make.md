---
title: "where is 'install', target of make?"
date: 2010-11-07
forum: New to Ubuntu
---

### Post by SteelCore on 2010-11-07
I'm trying out an example from a book that shows how to compile a program on Linux from source code. The program used is called 'diction'. Everything went fine but I was wondering about the last command
```
make install
```
I am assuming 'install' is a file argument of 'make' but I was not able to find it at all. There was an INSTALL file in the extracted tree but it was a type of documentation so where exactly is 'install'?
Thanks

---

### Post by Hippytaff on 2010-11-07
Not quite sure what you mean (I am a bit slow sometimes), but have you read the install man page?

```

man install

```You might find the info there useful. press q to exit it

---

### Post by Gone fishing on 2010-11-07
When you untared the diction file you downloaded it made a directory. You need to open a terminal from inside the directory using the cd command. Then do the sudo make install command.

However, do you need to diction is in the repositories and can be installed easily using synaptic.

---

### Post by QLee on 2010-11-07
[QUOTE=SteelCore]...
```
make install
```I am assuming 'install' is a file argument of 'make' but I was not able to find it at all....[/QUOTE][FONT=monospace] 
[/FONT]
Seems like a reasonable assumption to me, make install [FONT=monospace]-[/FONT] invokes make, make finds the target install in Makefile and the directions to install the program. The file named INSTALL contains installation instructions.

---

### Post by Verbeck on 2010-11-07
> **SteelCore said:**
>  so where exactly is 'install'?

```
verbeck@Vector-Sigma:~$ whereis install
**install: /usr/bin/install** /usr/share/man/man1/install.1.gz

```
there it is ;)

---

### Post by AngusH on 2010-11-07
install in this case is neither a program nor a file. install is a special (or "phony") target in the make file. In other words it is not used to build a particular file, but instead used to run a set of commands that perform a purpose, in this case installing the program that you downloaded.
There is also a program called install, but that is not what we are dealing with here. 
Angus

---

