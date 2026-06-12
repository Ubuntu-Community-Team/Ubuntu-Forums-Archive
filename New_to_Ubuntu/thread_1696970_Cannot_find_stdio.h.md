---
title: "Cannot find stdio.h"
date: 2011-02-28
forum: New to Ubuntu
---

### Post by Termites on 2011-02-28
Hi!

I'm trying to compile the famous "hello world" program  for C in Ubuntu. 
and I'm failing miserably.

this is the code in hello.c:

```
#include < stdio.h>

void main()
{
    printf("\nHello World\n");
}

```and I'm trying to compile with:

```
gcc hello.c
```And the output is:
```
hello.c:1: fatal error: stio.h: File or catalogue doesn't exist.

```I've tried the following:

```
sudo apt-get install libstdc6
sudo apt-get install build-essential
sudo apt-get install libc6-dev
```

but none of those commands has helped.

furthermore I can locate stdio.h:

```
/host/Qt/qtcreator-2.0.1/mingw/include/stdio.h
/host/Qt/qtcreator-2.0.1/mingw/lib/gcc/mingw32/4.4.0/include/c++/tr1/stdio.h
/host/Qt/qtcreator-2.0.1/mingw/lib/gcc/mingw32/4.4.0/include/ssp/stdio.h
/host/Wascana/mingw/include/stdio.h
/host/Wascana/mingw/lib/gcc/mingw32/4.4.1-dw2/include/c++/tr1/stdio.h
/host/Wascana/mingw/lib/gcc/mingw32/4.4.1-dw2/include/ssp/stdio.h
/host/Wascana/msys/include/stdio.h
/host/rhcygwin/lib/gcc/i686-pc-cygwin/4.3.4/include/c++/tr1/stdio.h
/host/rhcygwin/lib/gcc/i686-pc-cygwin/4.3.4/include/ssp/stdio.h
/host/rhcygwin/lib/perl5/5.10/i686-cygwin/CORE/nostdio.h
/host/rhcygwin/usr/include/stdio.h
/host/rhcygwin/usr/include/mingw/stdio.h
/host/rhcygwin/usr/include/sys/stdio.h
/usr/include/stdio.h
/usr/include/bits/stdio.h
/usr/lib/perl/5.10.1/CORE/nostdio.h
/usr/lib/syslinux/com32/include/stdio.h
```So apparently stdio.h does exist!

What am I doing wrong?

thanks for the help in advance!

/Termites

---

### Post by muteXe on 2011-02-28
this line:
```

hello.c:1: fatal error: stio.h: File or catalogue doesn't exist.

```

"stio.h" is spelt wrong surely?  Although it looks ok in the source you've pasted in?!

---

### Post by vivek.pandey on 2011-02-28
just check once more you wrote stdio.h only in your original code right and not stio.h?

---

### Post by john77eipe on 2011-02-28
the problem is with the space in 
```

< stdio.h>

```
No spaces are allowed.

---

