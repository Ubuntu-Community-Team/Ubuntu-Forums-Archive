---
title: "ld linking problem"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by Mariane on 2009-02-21
Hi, 

Could someone please move this post to "Development & Programming"? I tried to post it there but the "New post" link didn't appear. Thank you. 

I am trying to compile Sphere, the NIST program, because 
I need it to open a .sph file and convert it to .wav. 

The libraries compiles. This produces two files called libsp.a and a file called libutil.a

But I keep getting:
/usr/bin/ld: cannot find -libsp
(Or /usr/bin/ld: cannot find -libsp depending upon 
what I try, I've tried many combinations...)

So I have 7 questions about the ld linker. 

My first question is: are .a sufficient or do I need a 
libsp.so and a libutil.so? 

Second: If I need a libsp.so and a libutil.so, how 
do I get them? 

Third: Should I copy these files to /usr/lib, 
/usr/local or whatever? There is a problem with that, 
/usr/lib already contains a /usr/lib/libutil.a

Fourth: In the Makefile I tried to set 
INCLUDE = -I/home/tux/Desktop/sphere3/src/lib -I/home 
etc etc etc with many possible combinations. Where 
should I point the INCLUDE, is it to the directory 
where there are the .a or to the source code of the 
libs, and if so which one (because .c and .h are not 
in the same directory). 

Fifth: Should I call the lib "libsp.a" in the Makefile 
or just "libsp" or nothing at all (just give the 
directory path ending in a /)? 

Sixth and Seventh: same as Fourth and Fifth but 
concerning LIBS = -L/bla bla bla

Mariane

---

### Post by snova on 2009-02-21
> **Mariane said:**
> Could someone please move this post to "Development & Programming"? I tried to post it there but the "New post" link didn't appear. Thank you.

Developement & Programming isn't a forum in itself, it's a category- the Programming Talk subforum in there would have been appropriate.

> The libraries compiles. This produces two files called libsp.a and a file called libutil.a

But I keep getting:
/usr/bin/ld: cannot find -libsp
(Or /usr/bin/ld: cannot find -libsp depending upon what I try, I've tried many combinations...)

**-lsp** is all you need- the prefix and suffix are automatic.

> So I have 7 questions about the ld linker. 

My first question is: are .a sufficient or do I need a libsp.so and a libutil.so?

.a files are static libraries, when you link them they become part of the program. .so files are shared libraries, like .dll's if you're familiar with them- separate entities, you need both present at runtime.

> Third: Should I copy these files to /usr/lib, /usr/local or whatever? There is a problem with that, /usr/lib already contains a /usr/lib/libutil.a

I suggest /usr/local/lib, however if you build other programs from source they may have problems trying to link to -lutil, as the one you install in /usr/local/lib will be found before /usr/lib, and they are probably entirely different libraries.

> Fourth: In the Makefile I tried to set

INCLUDE = -I/home/tux/Desktop/sphere3/src/lib -I/home

etc etc etc with many possible combinations. Where should I point the INCLUDE, is it to the directory where there are the .a or to the source code of the libs, and if so which one (because .c and .h are not in the same directory).

Point it to the .h files; the headers.

For example, if you have the following directory structure:

headers/
headers/libsp/
headers/libsp/file.h

And headers are included with

[php]#include <libsp/file.h>[/php]

You would need **-I/path/to/headers**, but not **-I/path/to/headers/libsp**.

> Fifth: Should I call the lib "libsp.a" in the Makefile or just "libsp" or nothing at all (just give the directory path ending in a /)?

Not quite sure what you mean...

> Sixth and Seventh: same as Fourth and Fifth but concerning LIBS = -L/bla bla bla

-L/path/to/directory/containing/libraries -lsp -lutil

In your case. -L to tell the linker where the files are; -lsp and -lutil to tell the linker to link the libraries in.

---

