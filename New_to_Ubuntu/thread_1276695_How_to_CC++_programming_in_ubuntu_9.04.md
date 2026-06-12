---
title: "How to C/C++ programming in ubuntu 9.04"
date: 2009-09-27
forum: New to Ubuntu
---

### Post by infotechwizkid on 2009-09-27
Hi there guys i was just wondering how can i do c/c++ programming on ubuntu 9.04 ? And what is the best c/c++ programming compiler for ubuntu 9.04 ?

Guys Pls help me as you can see i'm an IT student here in the Philippines. And soon we will be studying c/c++ programming and i have to prepare a compiler for it in ubuntu 9.04 =)

PLs give me the best compiler here in ubuntu and give me some details where to get it and how to install it ^_^ ,thanks and more power :)

---

### Post by JordyD on 2009-09-27
You should be asking in this forum: [Programming Talk]("http://ubuntuforums.org/forumdisplay.php?f=39")

And there are the stickies there:

[Read Before Posting: Forum FAQ's, how to learn to program, and Linux programming]("http://ubuntuforums.org/showthread.php?t=1006666")
[Programming Tools and References]("http://ubuntuforums.org/showthread.php?t=1006662")

Good luck.

---

### Post by yobird42 on 2009-09-27
Search c++ in synaptic. There are a few options to choose from. I have no exeperience with c++ in ubuntu so I can't offer my opinion as to which one is the best.

---

### Post by ve4cib on 2009-09-27
For compilers you'll want gcc and g++ (for C and C++ respectively).  Those are the standard compilers that pretty much everyone uses.

The packages are on the Ubuntu repositories; you can search for them with synaptic or execute:

```
$ sudo apt-get install gcc g++
```

To compile a program something like:

```
$ g++ *.cpp
```

is often sufficient, but you should have a look through the man pages for more options and details.

---

### Post by credobyte on 2009-09-27
```
sudo apt-get install build-essential

```

This will install the basics of what you need to get started ( C/C++ compiler, etc. ). Everything else, related to "how to program", belongs to [Programming Talk]("http://ubuntuforums.org/forumdisplay.php?f=39").

---

