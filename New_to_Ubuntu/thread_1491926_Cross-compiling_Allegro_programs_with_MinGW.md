---
title: "Cross-compiling Allegro programs with MinGW"
date: 2010-05-24
forum: New to Ubuntu
---

### Post by TheUnwiseman on 2010-05-24
Hello Ubuntu forum.  I'm very new at Allegro, but I managed to make my first game, Pong, in C using Allegro 4.2.2 on my Ubuntu 9.04 computer. You can find the project, along with source code, at [http://sourceforge.net/projects/mvppong](http://sourceforge.net/projects/mvppong).  But not all of my friends use Linux!  I wanted to make a Windows executable file for my friends with a Microsoft inclination.  So I found out about MinGW and did a sudo apt-get install for it.  I've tried compiling it, but I can't manage to get MinGW to link the Allegro library files properly.

I try this command:
```
i586-mingw32msvc-gcc -v `allegro-config --cflags --libs` pong.c
```

And this is what spits back out:
```
Using built-in specs.
Target: i586-mingw32msvc
Configured with: /build/buildd/mingw32-4.2.1.dfsg/build_dir/src/gcc-4.2.1-2-dfsg/configure -v --prefix=/usr --target=i586-mingw32msvc --enable-languages=c,c++ --enable-threads --enable-sjlj-exceptions --disable-multilib --enable-version-specific-runtime-libs
Thread model: win32
gcc version 4.2.1-sjlj (mingw32-2)
 /usr/libexec/gcc/i586-mingw32msvc/4.2.1-sjlj/cc1 -quiet -v -I/usr/include pong.c -quiet -dumpbase pong.c -mtune=pentium -auxbase pong -version -o /tmp/ccfFt3qh.s
ignoring nonexistent directory "/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/sys-include"
#include "..." search starts here:
#include <...> search starts here:
 /usr/include
 /usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/include
 /usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include
End of search list.
GNU C version 4.2.1-sjlj (mingw32-2) (i586-mingw32msvc)
	compiled by GNU C version 4.2.3 20071210 (prerelease) (Ubuntu 4.2.2-4ubuntu2).
GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
Compiler executable checksum: 9f7339889766358351a8c487565f111d
 /usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/bin/as -o /tmp/cciRbuSz.o /tmp/ccfFt3qh.s
 /usr/libexec/gcc/i586-mingw32msvc/4.2.1-sjlj/collect2 -Bdynamic /usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/lib/crt2.o /usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/crtbegin.o -L/usr/lib -L/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj -L/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj -L/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/lib -Bsymbolic-functions -lalleg-4.2.2 /tmp/cciRbuSz.o -lmingw32 -lgcc -lmoldname -lmingwex -lmsvcrt -luser32 -lkernel32 -ladvapi32 -lshell32 -lmingw32 -lgcc -lmoldname -lmingwex -lmsvcrt /usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/crtend.o
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/bin/ld: cannot find -lalleg-4.2.2
collect2: ld returned 1 exit status
```

Note that I only have files pong.c and pong.h in my program altogether.  I have no problem compiling this with gcc normally.  Any help figuring this out would be appreciated.

---

### Post by TheUnwiseman on 2010-05-24
Shamefully self-bumping this one.  I can provide more information if necessary, if that's what is holding people back from helping me on this one.  I really don't know where to begin.

---

### Post by TheUnwiseman on 2010-05-24
Another self-bump.  Just trying to keep the thread current until someone notices...

---

### Post by TheUnwiseman on 2010-05-24
More shameful bumping.

---

### Post by TheUnwiseman on 2010-05-24
Bumping this again.

---

