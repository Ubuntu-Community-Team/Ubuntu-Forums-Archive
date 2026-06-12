---
title: "Compile errors..."
date: 2010-06-14
forum: New to Ubuntu
---

### Post by hopelessone on 2010-06-14
Hi,

```
blade@desktop:~/Temp/sdlmess0136$ make -f makefile.sdl PTR64=1 -j3
Compiling src/osd/sdl/dview.c...
Compiling src/osd/sdl/debug-sup.c...
Compiling src/osd/sdl/debug-intf.c...
Compiling src/mess/osd/sdl/sdlutil.c...
cc1: warnings being treated as errors
src/osd/sdl/dview.c: In function ‘dview_size_allocate’:
src/osd/sdl/dview.c:216: error: implicit declaration of function ‘GTK_WIDGET_REALIZED’
make: *** [obj/sdl/mess/osd/sdl/dview.o] Error 1
make: *** Waiting for unfinished jobs....
blade@desktop:~/Temp/sdlmess0136$ 

```

I'm trying to compile for 64bit what error is this? and how can i fix it?

Thanks...

---

### Post by hopelessone on 2010-06-14
[http://www.bannister.org/forums/ubbthreads.php?ubb=showflat&Number=62109&page=all](http://www.bannister.org/forums/ubbthreads.php?ubb=showflat&Number=62109&page=all)


Basically you have to change the "GTK_WIDGET_REALIZED" object in "/src/osd/sdl/dview.c" with "gtk_widget_get_realized".

---

### Post by hopelessone on 2010-06-14
OK went ti install now it gives me:
```
blade@desktop:/usr/share/games/sdlmess$ sudo make install
make: *** No rule to make target `install'.  Stop.

```

What to do now? am stumped.....?

Thanks

---

