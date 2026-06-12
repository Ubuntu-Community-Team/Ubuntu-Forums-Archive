---
title: "Installing CMake"
date: 2011-04-16
forum: New to Ubuntu
---

### Post by arnold.pietersen on 2011-04-16
I am trying to install recordit, but it requires cmake.  I have downloaded the cmake file and untarred it.

How do I compile cmake in order to compile recordit?

Any help will be appreciated 

Regards

ARNOLD

---

### Post by Paul820 on 2011-04-16
Cmake is in synaptic. System -> Administration -> Synaptic Package Manager, search for 'cmake', click install. No need to compile it, it's already done for you.

EDIT: Plus, it will install all the dependencies for it instead of you trying to find them. Always try synaptic first.

---

### Post by arnold.pietersen on 2011-04-16
Hi Paul

I failed to mention that I did try Synaptic. Nothing appears when I type cmake. Even if I try sudo apt-get install cmake from the terminal.This what I get:

arnold@arnold-laptop:~$ sudo apt-get install cmake
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package cmake
arnold@arnold-laptop:~$

I am a bit at a lost.

Thanks for your reply.

ARNOLD

---

