---
title: "g++ help"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by kickbot on 2009-01-28
How do I run g++ in ubuntu?
I've tried "sudo apt-get install build-essential" in the terminal
I've downloaded it in the synaptic package manager.
I have downloaded gcc-4.3.3.tar.gz several times, but I can't get it to run.
Nothing resembling gcc, g++ or gnu appear in the add programs menu.

Thanks,

---

### Post by appi2012 on 2009-01-28
type "man gcc" in the terminal

In general, syntax is gcc -o [where you want the output file] [location of input file]

---

### Post by Hospadar on 2009-01-28
What happens when you run it? (and what command are you using)

also when you are looking for command-line tools like g++ i would use System->Administration->Synatic instead of add/remove

---

### Post by lakersforce on 2009-01-28
> **kickbot said:**
> 
Nothing resembling gcc, g++ or gnu appear in the add programs menu.


It's command-line only. It does not appear in the menus. Follow the advice above and do a "man gcc" (or download the gcc manual in pdf format from somewhere) . If you don't feel competent in using the command-line do a "man intro" at the command-line.

---

### Post by kickbot on 2009-01-28
> **lakersforce said:**
> It's command-line only. It does not appear in the menus. Follow the advice above and do a "man gcc" (or download the gcc manual in pdf format from somewhere) . If you don't feel competent in using the command-line do a "man intro" at the command-line.

Oh... command line. I'm obviously really new to this.  I'll read up on using the command line.  Thank you all for your help.

---

### Post by kickbot on 2009-01-28
ok,so say I have a program called "beginner.cpp" that I want to compile.  what would I put in the command line?

---

### Post by Cypher on 2009-01-28
Well what you put in the command line depends on what libraries the file needs. In it's most basic form you should be able to do
```

g++ -o beginner beginner.cpp

```
this will generate an executable named 'beginner' from the CPP file.

---

### Post by fastn on 2009-01-28
Open the terminal and write
```

sudo apt-get install g++

```

To compile a program simply write
```
g++ filename.cpp -o filename
```

For more information you can always do *man g++*

---

### Post by stchman on 2009-01-28
There are many IDEs on Ubuntu that will use the gcc/g++.  Eclipse is one that comes to mind.

I personally use Geany as it is a lightweight IDE with Java and C/C++ editor.

There are a wealth of development tools for Linux for almost any programming language.

---

