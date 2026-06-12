---
title: "newbie question regarding shell scripting"
date: 2009-06-03
forum: New to Ubuntu
---

### Post by sempiris on 2009-06-03
Hello ubuntuforums.

Let me begin by saying I am a complete beginer to Linux, and that I tried but was unsuccessful at searching the forums for an answer.

I am trying to compile and make an executable out of some c++ code.  I've tried using emacs to compile, but it wouldn't create the executable I needed, and I've tried using "make -k filename.cc", to which I get the feedback "make: Nothing to be done for 'filename.cc'.

thanks for any help

---

### Post by Celauran on 2009-06-03
You need to use gcc to compile c/c++ code.

```
man gcc
```

---

### Post by doas777 on 2009-06-03
> **sempiris said:**
> Hello ubuntuforums.

Let me begin by saying I am a complete beginer to Linux, and that I tried but was unsuccessful at searching the forums for an answer.

I am trying to compile and make an executable out of some c++ code.  I've tried using emacs to compile, but it wouldn't create the executable I needed, and I've tried using "make -k filename.cc", to which I get the feedback "make: Nothing to be done for 'filename.cc'.

thanks for any help

'make' only works if you have a makefile. you prolly want to use gcc 
Last time I had a cpp file to compile, i used:

```
gcc ./<filename>
```
it automarically creates a compiled file in that dir, called 'a.out'

---

### Post by sempiris on 2009-06-03
> **doas777 said:**
> 'make' only works if you have a makefile. you prolly want to use gcc 
Last time I had a cpp file to compile, i used:

```
gcc ./<filename>
```it automarically creates a compiled file in that dir, called 'a.out'


thanks!

I tried using g++ and that got me somewhere

---

