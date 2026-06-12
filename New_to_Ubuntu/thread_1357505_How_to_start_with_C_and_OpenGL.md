---
title: "How to start with C and OpenGL"
date: 2009-12-17
forum: New to Ubuntu
---

### Post by starstalker on 2009-12-17
Hi
I have been programming in openGL c using visual studio after I installed ubuntu I was wandering if there is a way to program openGL in ubuntu.
I am a totally new to ubuntu what kind of C compiler should I download and how can I add the GL libraries I need (GL/glut.h, stdlib.h, and if possible math.h will help)

easy terminal commands will be great :P

thank you for your help

---

### Post by Bölvaður on 2009-12-17
you can use what ever editor you want, I like Geany, but others might be uber pro and use Vim.

c compiler should already be installed. it's called gcc.
that is the gnu c compiler.

I guess glut is already in the repos.


btw this is the wrong subforum you should post in under the programming subforum.

---

### Post by starstalker on 2009-12-17
I just tried geany and its great but it seems that the glut library isnt included in it or maybe i am doing some thing wrong I start my code with

#include <GL/glut.h>
#include <stdlib.h>
#include <math.h> 

I made a simple pyramid code that i am sure of and it compiled fine but when i clicked build I got 

/tmp/cc731NKl.o: In function `init':
light.c:(.text+0x6a): undefined reference to `glClearColor'
light.c:(.text+0x76): undefined reference to `glShadeModel'
etc.
etc.

for every gl command

I used this code it install the glut libs

```
sudo apt-get install libglu1-mesa-dev freeglut3-dev mesa-common-dev
```

and also used the synaptic to install glutg3,glutg3-dev ,libglut3,libglut3-dev
ps:can I move it or should I start a new one or just ignore it :P

---

### Post by Hetepeperfan on 2009-12-17
> **starstalker said:**
> Hi
I have been programming in openGL c using visual studio after I installed ubuntu I was wandering if there is a way to program openGL in ubuntu.
I am a totally new to ubuntu what kind of C compiler should I download and how can I add the GL libraries I need (GL/glut.h, stdlib.h, and if possible math.h will help)

easy terminal commands will be great :P

thank you for your help

This website shows a lot of openGL stuff. But also how to install the necessities in/under linux and it really works fine. The author tell you to visit the debian packages site. But all package are in the ubuntu repositories as well and for me this work fine.

the website: [http://www.videotutorialsrock.com/](http://www.videotutorialsrock.com/)

It helped me a lot

---

### Post by Hetepeperfan on 2009-12-17
> **starstalker said:**
> I just tried geany and its great but it seems that the glut library isnt included in it or maybe i am doing some thing wrong I start my code with

#include <GL/glut.h>
#include <stdlib.h>
#include <math.h> 

I made a simple pyramid code that i am sure of and it compiled fine but when i clicked build I got 

/tmp/cc731NKl.o: In function `init':
light.c:(.text+0x6a): undefined reference to `glClearColor'
light.c:(.text+0x76): undefined reference to `glShadeModel'
etc.
etc.

for every gl command


ps:can I move it or should I start a new one or just ignore it :P


u can use: gcc myfile.c -o myoutputexecutabe -Wall -lglut
especcially the -lglut option, which links the glut library is important
and u can use g++ instead of gcc for C++ files

---

### Post by Some Penguin on 2009-12-17
Ask yourself how you expect the build system to know what libraries to link in, and you'll realize that you need to *tell* it which libraries to include.  Check your IDE's instructions on how to pass options to the linker.

---

### Post by starstalker on 2009-12-17
[http://www.videotutorialsrock.com/](http://www.videotutorialsrock.com/)
it was so helpfull it mad me cry thank you very much

thank you for every thing else every thing was so helpful
thank you again :P

---

### Post by Bölvaður on 2009-12-17
you would put "gcc %n -o %e -Wall -lglut" into the compile or build option in the menus. Ok I cannot remember what stands for the full name and the name without the tag. But there is info on it when you change it. Very useful.

---

### Post by starstalker on 2009-12-17
here it is if anyone cant get what happend here it turned out to be simple thanks for the people who replyed up here 

if you are using geany goto build ==> set includes and arguments "gcc -Wall -o "%e" "%f" -lglut" write this in the build field 

thanks for your time it helped alot

---

