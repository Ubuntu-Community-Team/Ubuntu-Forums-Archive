---
title: "allegro library in ubuntu"
date: 2009-02-26
forum: New to Ubuntu
---

### Post by deepugtm on 2009-02-26
I have recently installed code blocks .I want to use allegro library with it....,But I don't know how to do it.Please help me....

---

### Post by Hospadar on 2009-02-26
I assume you mean that you want to link the library in a program.

You need to go to Settings->Compiler->linker
and either add the library file directly, or (I think, I've never actually used code blocks, I tend to stick to vi or kate and my makefiles) you can add in the "additional linker flags" the linker flag that you would pass to gcc, for example ```
-lallegro
```Is probably the flag for that library.  You might want to read up on gcc and linking before you get going if you arn't familiar with it.
make sure you have liballegro<some version number> and liballegro<some version number>-dev installed

---

