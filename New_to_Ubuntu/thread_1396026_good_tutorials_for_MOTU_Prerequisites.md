---
title: "good tutorials for MOTU Prerequisites"
date: 2010-02-01
forum: New to Ubuntu
---

### Post by Nebelhom on 2010-02-01
Hi guys,

I want to slowly but surely start learning how to package and by following several posts, I got to the [_[COLOR="Blue"]MOTU[/COLOR]_]("http://wiki.ubuntu.com/MOTU/GettingStarted") and their [_[COLOR="Blue"]Packaging Guide[/COLOR]_]("http://wiki.ubuntu.com/PackagingGuide/Complete").
Now on the Packaging Guide they give Prerequisites like learning to use "make" etc.

Do you guys know any good texts or tutorials to learn the prerequisites for this (it would be best with worked examples)? And also can you add anything to that list, that will be of definite use for these sorts of tasks (do I have to learn to use C, for example?)

So far I have read the ubuntupocketguide and I know some python programming, so I was wondering where to go next with this. The GNU tutorial for make is very bland and not really any use for me :( so alternatives would be great.

The idea behind this is that I want to learn more about linux and while I am at it, once I am ready, I thought I'll make myself useful. Best way to learn is by doing it after all.

Thanks guys

---

### Post by Nebelhom on 2010-02-02
bump

---

### Post by niffcreature on 2010-02-02
c is just c, linux doesnt particularly have anything to do with it. just get a book on c programming if you want to learn it. there are plenty.

---

### Post by Flimm on 2010-02-02
The packaging guides have a huge bias towards programs in C or C++. They all assume that the program you're trying to package has a makefile, which I found very frustrating as a Python developer and packager.

You need to know the basic theory behind compiling programs. Most projects have some sort of automatic building set up, but there are quite a lot of different systems. (automake, CMake and other for C and C++ programs, distutils and setuptools for Python programs). Here's a [quick tutorial on makefiles](http://www.cprogramming.com/tutorial/makefiles.html).

And BTW, you should really ask in the packaging sub-forum, or programming talk. I'm getting quite concerned for all the genuine "absolute beginners" who wander into ubuntuforums.

---

### Post by Nebelhom on 2010-02-02
Brilliant! Thanks Flimm!

hehe. I actually still think of myself as a beginner. Just a beginner who started learning to use the big words ;)

Thanks for the hint tho. will put it over there next time.

---

