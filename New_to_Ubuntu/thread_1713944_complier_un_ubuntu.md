---
title: "complier un ubuntu"
date: 2011-03-24
forum: New to Ubuntu
---

### Post by Heroes96_1989 on 2011-03-24
hi guys im learing c++ it has been a hard day trying to get all his tutorials together i was wondering if ya could tell me a good and eaasy way tu comply under ubuntu :) and please if some1 has enough time and wanna help me i wouldn't mind donating you :D


thanks

---

### Post by The Cog on 2011-03-24
Install package **build-essential** which installs the compiler and some supporting software.

I suggest **geany** as an editor. It has syntax highlighting and a compile button.

---

### Post by Heroes96_1989 on 2011-03-24
ok so im super noob can u guide thru?



thanks in advance

---

### Post by Morrad on 2011-03-24
To install **build-essential** (from the terminal):

```
sudo apt-get install build-essential
```

Then (still from the terminal) you can use **g++** to compile your code (it's included as one of the dependencies of build-essential).  To see how to use it, check out the manual (**man g++** from the terminal), or check out the C++ section in the following link:

[http://www.ubuntugeek.com/how-to-install-c-and-c-compilers-in-ubuntu-and-testing-your-first-c-and-c-program.html](http://www.ubuntugeek.com/how-to-install-c-and-c-compilers-in-ubuntu-and-testing-your-first-c-and-c-program.html)

The above poster recommends you use **geany** to write your code (install the same as above, but replace build-essential with geany), but you could just as easily use **gedit** or whatever other editor you like.  **Gedit** should already be installed on your system.

---

### Post by Heroes96_1989 on 2011-03-24
> **Morrad said:**
> To install **build-essential** (from the terminal):

```
sudo apt-get install build-essential
```Then (still from the terminal) you can use **g++** to compile your code (it's included as one of the dependencies of build-essential).  To see how to use it, check out the manual (**man g++** from the terminal), or check out the C++ section in the following link:

[http://www.ubuntugeek.com/how-to-install-c-and-c-compilers-in-ubuntu-and-testing-your-first-c-and-c-program.html](http://www.ubuntugeek.com/how-to-install-c-and-c-compilers-in-ubuntu-and-testing-your-first-c-and-c-program.html)

The above poster recommends you use **geany** to write your code (install the same as above, but replace build-essential with geany), but you could just as easily use **gedit** or whatever other editor you like.  **Gedit** should already be installed on your system.




You are awesome im starting to love ubuntu community 


thanks you 
i will do and ill let you know if i ran with any problem:lolflag:

---

### Post by Heroes96_1989 on 2011-03-25
> **Morrad said:**
> To install **build-essential** (from the terminal):

```
sudo apt-get install build-essential
```Then (still from the terminal) you can use **g++** to compile your code (it's included as one of the dependencies of build-essential).  To see how to use it, check out the manual (**man g++** from the terminal), or check out the C++ section in the following link:

[http://www.ubuntugeek.com/how-to-install-c-and-c-compilers-in-ubuntu-and-testing-your-first-c-and-c-program.html](http://www.ubuntugeek.com/how-to-install-c-and-c-compilers-in-ubuntu-and-testing-your-first-c-and-c-program.html)

The above poster recommends you use **geany** to write your code (install the same as above, but replace build-essential with geany), but you could just as easily use **gedit** or whatever other editor you like.  **Gedit** should already be installed on your system.



by any chance do u know how to type brases {} in ubuntu im using a laptop :D

---

### Post by The Cog on 2011-03-25
**Ctrl-Shift-U 7 B Enter** will give you **{**
**Ctrl-Shift-U 7 D Enter** will give you **}**
but you had better find a shorter way to type them if you are learning C/C++ because you will want them a lot. Sorry, I don't know how to help there (I use a UK keyboard which always has them).

---

### Post by The Cog on 2011-03-26
I just discovered by accident that AltGr-7 and AltGr-0 produce { and }. AltGr is the right-hand Alt key (if your laptop has one of those).

---

