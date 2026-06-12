---
title: "g++ compilation problem."
date: 2010-05-20
forum: New to Ubuntu
---

### Post by rockingshan on 2010-05-20
Hi. I have installed ubuntu 9.04 somedays ago. Everything works fine. Except when I try to compile a c++ program with g++ I get many error. 
error: graphics.h: no such file or directory. Please help me to solve this problem.

---

### Post by Ozymandias_117 on 2010-05-20
Sounds like a problem with the code you're trying to compile. Either it wasn't completed, or you're missing some of it.

---

### Post by QIII on 2010-05-20
The problem is not with your compiler.

What you have given us indicates that the compiler/linker is not able to find a header file that you have probably used in an include statement.

Did you write your program in an IDE, or with something like EMACS?

I don't recall that header in C++, but it may just be that I have never run across it.

Did you add something to one of your files something like

```
#include <graphics.h>
```

which would indicate something standard, or something like

```
#include "graphics.h"
```

which would indicate something you wrote yourself?

---

### Post by Ozymandias_117 on 2010-05-20
@QIII Oh yeah... I never thought to consider the OP might be trying to write a program :D

---

### Post by lisati on 2010-05-20
And what's a reference to "graphics.h" doing in a C++ file? That's a C header, isn't it?

---

### Post by QIII on 2010-05-20
It's been so long since I wrote in C.  It may be a C header, but old C stuff can still often be used.

And .h is still common.  NetBeans, for instance, assigns .h to headers by default.


Edit:  You may need to install the C++ libraries from Synaptic if you don't have them, by the way.  I think that should be libstdc++.

---

