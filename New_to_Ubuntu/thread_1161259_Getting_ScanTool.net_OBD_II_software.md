---
title: "Getting ScanTool.net OBD II software"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by Coolsaber57 on 2009-05-16
Ok, 

I'm trying to get the OBD II software called ScanTooll.net to work on my laptop. I've read that I need to install Allegro first, but when I try to do a "make" this is what is shown on the console

> gcc -DALLEGRO_MODULES_PATH=\"/usr/local/lib/allegro\" -DHAVE_CONFIG_H -I. -Iinclude -Iinclude/allegro -I./include -I./include/allegro  -DALLEGRO_LIB_BUILD  -mtune=pentium -O2 -funroll-loops -ffast-math -fomit-frame-pointer -Wall -Wno-unused  -x assembler-with-cpp -c ./src/i386/icpus.s -o obj/unix/shared/alleg/icpus.o
./src/i386/icpus.s: Assembler messages:
./src/i386/icpus.s:70: Error: suffix or operands invalid for `fnstsw'
make: *** [obj/unix/shared/alleg/icpus.o] Error 1


I'm not really sure what to do from here.  Help?

---

### Post by gcvisel on 2009-09-21
> **Coolsaber57 said:**
> Ok, 

I'm trying to get the OBD II software called ScanTooll.net to work on my laptop. I've read that I need to install Allegro first, but when I try to do a "make" this is what is shown on the console



I'm not really sure what to do from here.  Help?

I got it running with WINE.  See this link:
[http://ubuntuforums.org/showthread.php?p=7986807#post7986807](http://ubuntuforums.org/showthread.php?p=7986807#post7986807)

Gerry

---

### Post by lkraemer on 2009-11-27
I have ver 1.15 scantool.net running under Crossover.
[http://ubuntuforums.org/showthread.php?t=1339775](http://ubuntuforums.org/showthread.php?t=1339775)

lk

---

