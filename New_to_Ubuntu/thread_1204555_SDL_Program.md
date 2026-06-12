---
title: "SDL Program"
date: 2009-07-04
forum: New to Ubuntu
---

### Post by hayden92 on 2009-07-04
Hey everyone,

I've made a program using c++ and SDL (SimpleDirectmediaLayer)

I want to give a copy of this program to my family members that live all around the world. The trouble is, they aren't computer-savvy and they might have trouble setting up SDL (or they won't be bothered).

Is there a way of making an SDL program that does not require SDL to be installed on the computer. I thought that maybe I could copy the headers into the program directory, but I don't know how to do that.

Any help would be appreciated.

Thank you in advance,
Hayden M

---

### Post by earthpigg on 2009-07-04
include sdl with the binaries you distribute?

(to make the forumlawyers happy, make sure you tell your family members that you will give them the source code if they ask for it :) )

---

### Post by hayden92 on 2009-07-04
Earthpig, thanks

That's pretty much what I thought, but how exactly do I do this?
#include"SDL/SDL.h"? That's what I have already, but it doesn't work.

EDIT: I found "SDL" in usr/include/ and copied it into my program directory, but when I try to run the program on my family computer (without SDL installed) it still doesn't run.

---

### Post by hayden92 on 2009-07-04
I realised I should have checked for error messages ;)

What does this mean?
error while loading shared libraries: libSDL_image-1.2.so.0: cannot open shared object file: No such file or directory


Ok, I think I worked out what the problem is; I am compiling my programs to link to dynamic libraries. Now my question is: how do I compile my program with static libraries, or at least, how do I make them 'stand-alone' so that SDL doesn't need to be installed on the client's computer?

---

