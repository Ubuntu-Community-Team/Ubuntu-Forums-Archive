---
title: "gcc specs file?"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by anewguy on 2009-01-31
I have a cross-platform application that I use gcc on both Windows and Ubuntu to compile.  I *think* I learned something tonight, and it leaves me with a big question.  Given:

gcc *.c -o c:/cvs/cvsgtk -I c:/Progra~1/LibUSB-Win32-0.1.10.1/include  -L c:/Progra~1/LibUSB-Win32-0.1.10.1/lib/gcc -lusb `pkg-config --cflags --libs gtk+-2.0`

I believe the single tick marks are signals to the shell to execute pkg-config with the following 2 parameters and put the output here.

I don't seem to find a way to do this in the cli for Windows, so I'm guessing I need to use a specs file.  The problem is I don't have a clue as to how to do this.  I've tried reading all kinds of things on it but I think they all assume some sort of knowledge I don't have.

Any help would be greatly appreciated!

Thanks in advance!
Dave :)

---

