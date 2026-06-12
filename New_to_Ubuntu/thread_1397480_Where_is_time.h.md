---
title: "Where is time.h?"
date: 2010-02-03
forum: New to Ubuntu
---

### Post by newport_j on 2010-02-03
I insert the line 
 
#include "sys/time.h"
 
when I want to put my own timer on a program. That is done by first defining a structure:
 
struct timeval t1_start,t1-end,t2_start,t2_end;
 
then I put in the code
 
gettimeofday($t1_start,0); 
 
when I want to start the time; 
 
gettimeofday(&t1_end,0);
 
when i want to stop the timer.
 
Finally, I use 
 
time = (t1.end.tv_sec-t1_start.tv_sec)*1000000 + t1.end.tv_usec - t1_start.tv_sec;
 
 
Thus, I get the time taken between those two last statements: gettimeofday($t1_start,0); and gettimeofday(&t1_end,0); in microseconds. Cool!
 
However, I must add the statement at the beggining of the program 
 
#include "sys/time.h"
 
or nothing will work.
 
My question is where is the time.h statement? I did a search on time.h and came up with several time.h statements. Also. since it is enclosed in quotes it should be in the same directory as the program being complied. It is not in my program.
 
The statement sys/time.h 
 
suggests it is in the sys directory so which one? I have been working on this all morning and cannot seem to nail it. 
 
The procedure I describe above works most of the time, sometimes it does not. 
 
That is why I feel that I must ask these questions. The c manual that I have is weak on this topic.
 
Newport_j

---

### Post by KIAaze on 2010-02-03
If you don't have "sys/time.h" in the current directory and haven't manually defined additional include paths, it is in "/usr/include/sys/time.h" (from the package libc6-dev by the way).
On GNU/Linux, the default include paths are usually /usr/include and /usr/local/include.

> If the filename is enclosed within angle brackets, the file is searched for in the standard compiler include paths. If the filename is enclosed within double quotes, the search path is expanded to include the current source directory.
cf [http://en.wikipedia.org/wiki/C_preprocessor#Including_files](http://en.wikipedia.org/wiki/C_preprocessor#Including_files)

The default include paths can be determined by running "cpp -v" and "gcc -v".
ex:
```
$ cpp -v
Using built-in specs.
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.4.1-4ubuntu9' --with-bugurl=file:///usr/share/doc/gcc-4.4/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --enable-multiarch --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.4 --program-suffix=-4.4 --enable-nls --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --disable-werror --with-arch-32=i486 --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu9)
COLLECT_GCC_OPTIONS='-E' '-v' '-mtune=generic'
 /usr/lib/gcc/x86_64-linux-gnu/4.4.1/cc1 -E -quiet -v - -D_FORTIFY_SOURCE=2 -mtune=generic -fstack-protector
ignoring nonexistent directory "/usr/local/include/x86_64-linux-gnu"
ignoring nonexistent directory "/usr/lib/gcc/x86_64-linux-gnu/4.4.1/../../../../x86_64-linux-gnu/include"
ignoring nonexistent directory "/usr/include/x86_64-linux-gnu"
#include "..." search starts here:
#include <...> search starts here:
 /usr/local/include
 /usr/lib/gcc/x86_64-linux-gnu/4.4.1/include
 /usr/lib/gcc/x86_64-linux-gnu/4.4.1/include-fixed
 /usr/include
End of search list.

```
```
$ gcc -v
Using built-in specs.
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.4.1-4ubuntu9' --with-bugurl=file:///usr/share/doc/gcc-4.4/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --enable-multiarch --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.4 --program-suffix=-4.4 --enable-nls --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --disable-werror --with-arch-32=i486 --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu9)

```
cf [http://gcc.gnu.org/ml/gcc-help/2007-09/msg00205.html](http://gcc.gnu.org/ml/gcc-help/2007-09/msg00205.html)

---

