---
title: "GTK+ program compile error"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by luckydeveloper on 2009-04-29
Hi,

I am just getting started to do gtk+ programming.. but my first program failed to compile.. the following was the error when i tried to compile.. please help me in rectifying the error.

```
~$ gcc -o simple simple.c `pkg-config --libs --cflags gtk+-2.0`
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
simple.c:1:21: error: gtk/gtk.h: No such file or directory
simple.c: In function ‘main’:
simple.c:5: error: ‘GtkWidget’ undeclared (first use in this function)
simple.c:5: error: (Each undeclared identifier is reported only once
simple.c:5: error: for each function it appears in.)
simple.c:5: error: ‘window’ undeclared (first use in this function)
simple.c:9: error: ‘GTK_WINDOW_TOPLEVEL’ undeclared (first use in this function)
lakshmanan@ubuntu:~$ gtk+
bash: gtk+: command not found
```

thanks

---

### Post by Tibuda on 2009-04-29
Do you have the [libgtk2.0-dev]("apt:libgtk2.0-dev") package installed? This package contains the development headers for GTK+.

---

