---
title: "Make and Configure Command errors please help!"
date: 2010-08-08
forum: New to Ubuntu
---

### Post by ElijahPenney on 2010-08-08
I'm trying to install a game from a .tar.gz file, I've been able to untar it but when I run the "./configure" and "make" commands in the dir it gives me errors

Make error:
```
lonelygamer@LonelyLaptop:~/Desktop/neverball-1.5.4$ make
Will make a "release" build of Neverball 1.5.4.
make: sdl-config: Command not found
make: libpng-config: Command not found
make: sdl-config: Command not found
make: libpng-config: Command not found
cc -Wall -ansi -pedantic -O2  -U_GNU_SOURCE  -Ishare -DVERSION=\"1.5.4\" -DCONFIG_USER=\".neverball\" -DCONFIG_DATA=\"./data\" -DCONFIG_LOCALE=\"./locale\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF share/lang.d -MT "share/lang.o" share/lang.c
cc -Wall -ansi -pedantic -O2  -U_GNU_SOURCE  -Ishare -DVERSION=\"1.5.4\" -DCONFIG_USER=\".neverball\" -DCONFIG_lonelygamer@LonelyLaptop:~/Desktop/neverball-1.5.4$ make
Will make a "release" build of Neverball 1.5.4.
make: sdl-config: Command not found
make: libpng-config: Command not found
make: sdl-config: Command not found
make: libpng-config: Command not found
cc -Wall -ansi -pedantic -O2  -U_GNU_SOURCE  -Ishare -DVERSION=\"1.5.4\" -DCONFIG_USER=\".neverball\" -DCONFIG_DATA=\"./data\" -DCONFIG_LOCALE=\"./locale\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF share/lang.d -MT "share/lang.o" share/lang.c
cc -Wall -ansi -pedantic -O2  -U_GNU_SOURCE  -Ishare -DVERSION=\"1.5.4\" -DCONFIG_USER=\".neverball\" -DCONFIG_DATA=\"./data\" -DCONFIG_LOCALE=\"./locale\" -DENABLE_NLS=1 -DNDEBUG -o share/lang.o -c share/lang.c
In file included from share/lang.c:24:
share/base_config.h:24:24: error: SDL_endian.h: No such file or directory
make: *** [share/lang.o] Error 1
DATA=\"./data\" -DCONFIG_LOCALE=\"./locale\" -DENABLE_NLS=1 -DNDEBUG -o share/lang.o -c share/lang.c
In file included from share/lang.c:24:
share/base_config.h:24:24: error: SDL_endian.h: No such file or directory
make: *** [share/lang.o] Error 1

```

./configure error:
```
lonelygamer@LonelyLaptop:~/Desktop/neverball-1.5.4$ ./configure
bash: ./configure: No such file or directory

```

Im completely new, any advice?

---

### Post by bodhi.zazen on 2010-08-08
What is in the archive ? is it distributed as a binary ? Is there a README file ?

---

### Post by ElijahPenney on 2010-08-08
I don't see any binary, but it says the release is the source code. If it helps almost every file is named either ".h" or ".c". Ive checked the read me and that just talks about the game itself. There is also a "INSTALL" file, that contains all the info about installing such as the make command and ./configure. When I follow the directions I just end up back where I was in the first post. There are multiple folders with mousepad files in them. Almost all files are labeled ".h" or ".c" except for the maps.

---

### Post by JBAlaska on 2010-08-08
Neverball 1.5.4-2 is in the Ubuntu repositories.

Just install it from Synaptic Package Manager.

---

