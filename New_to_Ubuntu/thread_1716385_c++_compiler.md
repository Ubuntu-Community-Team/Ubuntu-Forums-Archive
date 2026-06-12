---
title: "c++ compiler"
date: 2011-03-28
forum: New to Ubuntu
---

### Post by sid_rama on 2011-03-28
hi! Just switched to ubuntu 10.10 !! :D  
does anyone know a good c++ compiler for ubuntu???

---

### Post by pdkakaro on 2011-03-28
For C/C++ gcc/g++ is the standard compiler. I think you also need to install the build-essential package to be able to compile your code.

---

### Post by Heroes96_1989 on 2011-03-28
[QUOTE=sid_rama;10611160]hi! Just switched to ubuntu 10.10 !! :D  
does anyone know a good c++ compiler for ubuntu???[/QUO



anjuta 
codelite 
they are pretty good me been a total noob i could do it

---

### Post by blind2314 on 2011-03-28
g++
 
 
```
sudo apt-get build-essential
```
 
That will make sure you have it.

---

### Post by aG93IGRvIGkgdWJ1bnR1Pw== on 2011-03-28
> anjuta 
codelite 
they are pretty good me been a total noob i could do it

Those are IDEs, not compilers. And Vim is the best IDE there is.

---

### Post by blind2314 on 2011-03-28
> **aG93IGRvIGkgdWJ1bnR1Pw== said:**
> Those are IDEs, not compilers. And Vim is the best IDE there is.
 
 
That's sort of a subjective answer..vi is a great editor too, if you know your way around it. However, for people that prefer a graphical type interface, there are "better" IDEs to pick from.

---

### Post by safarin on 2011-03-28
> **blind2314 said:**
> That's sort of a subjective answer..vi is a great editor too, if you know your way around it. However, for people that prefer a graphical type interface, there are "better" IDEs to pick from.

I just learned C++ Programming, 
maybe you could try KDevelop or Qt Creator. :D

---

### Post by aG93IGRvIGkgdWJ1bnR1Pw== on 2011-03-29
> **blind2314 said:**
> That's sort of a subjective answer..vi is a great editor too, if you know your way around it. However, for people that prefer a graphical type interface, there are "better" IDEs to pick from.

For the people who prefer a graphical interface, there's gvim.

Vim is designed to be easy to use once you learn to use it properly. 
Other IDEs are easy to learn, but tedious to use.

---

### Post by deconstrained on 2011-03-29
> **aG93IGRvIGkgdWJ1bnR1Pw== said:**
> Those are IDEs, not compilers. And Vim is the best IDE there is.
Vim is not an IDE, it's a text editor. And almost every IDE I know of has compilers integrated-in as dependencies that can controlled through its interface, so installing an IDE would probably grab the necessary compilers.

---

### Post by devnedprog on 2011-03-29
Code::Bloks is the best for school, but QT4 is the best for develop :) i think that :)

---

### Post by aG93IGRvIGkgdWJ1bnR1Pw== on 2011-03-30
> **deconstrained said:**
> Vim is not an IDE, it's a text editor.

It can be both, if you set it up properly.

> **deconstrained said:**
> And almost every IDE I know of has compilers integrated-in as dependencies that can controlled through its interface, so installing an IDE would probably grab the necessary compilers.

That's not a standard, it's an exception that became a (kind of) rule. I don't see why my IDE choice should lock me into a single compiler. It doesn't make sense.

---

### Post by kroy23 on 2011-07-25
What do additional IDE's provide in way of developing? Additional header files and libraries? Some GUI functionality like run push buttons? Could someone tell me the advantages? For example, I am doing some visual image processing and trying to integrate an opencv downloaded library with the R.O.S. framework. I would think that if I got the build-essentials compiler, it might be harder to find specific pathways and find out where to keep my included header files and such (this coming from a complete noob btw). Thanks for the help!

---

### Post by anewguy on 2011-07-25
The IDE's are just that - Integrated Development Environments, not just a compiler.  I don't know most of them, so I can't say, but I know some of them provide debugging windows, tracing, the ability to step through code, "run" within the IDE, compile, etc..  Think of it as your all-in-one stop for developing programs.  The difference is just like in Windows:  In Windows you can edit your code with a text editor, compile it at the command line, run it and have it fail, and go back with the editor to start all over again.  Then there are IDE's - such as the Microsoft "Visual" series - makes things a lot easier.  Same in Linux - do it the hard way to install and learn an IDE.  And.....with Linux you get them for free, so you can try as many as you like.  And these are full-blown - not like the free Microsoft Visual xxxxx Express series.

---

### Post by anewguy on 2011-07-25
> **aG93IGRvIGkgdWJ1bnR1Pw== said:**
> It can be both, if you set it up properly.



That's not a standard, it's an exception that became a (kind of) rule. I don't see why my IDE choice should lock me into a single compiler. It doesn't make sense.

Not to be rude, but what does this p****ng contest have to do with answering the OP's question?

---

