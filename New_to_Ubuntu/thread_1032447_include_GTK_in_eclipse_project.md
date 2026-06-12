---
title: "include GTK in eclipse project"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by SpectacularNick on 2009-01-06
Hi all. 

I am trying to get compilation of a gtk project to work. Using a managed C Eclipse project. I have included /usr/include/gtk-2.0/gtk in the compiler include path. But i'm not sure what to set in the linker search path?


Another thing. I have seen example code using 

#include <gtk/gtk.h>

I assumed this meant that the include directory should be set to the /usr/include/gtk-2.0.
However, doing this resulted in tons of syntax errors, even though i didn't use any includes in the source code? I assume this has to do with the compiler going into non C source due to the settings of the managed makefile?

---

### Post by zizzdude on 2010-03-25
Would it be alright if you post the source code you are trying to compile? Just so I can see the problem. :)

---

