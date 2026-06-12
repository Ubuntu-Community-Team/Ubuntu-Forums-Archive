---
title: "gcc libraries help (C)"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by gunnar13 on 2009-03-03
Ubuntu 8.10, new standard desktop install, PC arch.

Already added the build-essential package.

Just wanted to get back into some C programming, so to test things out, I wrote the minimal Hello World source.

stdio.h is included in the source

When I compile using gcc, it finds stdio, but from there, it goes down the drain....

Here is a short list of the errors:

In file included from /usr/include/stdio.h:34,
                 from testhw.c:3:
/usr/lib/gcc/i486-linux-gnu/4.3.2/include/stddef.h: In function ‘main’:
/usr/lib/gcc/i486-linux-gnu/4.3.2/include/stddef.h:214: error: storage class specified for parameter ‘size_t’
In file included from /usr/include/stdio.h:36,
                 from testhw.c:3:
/usr/include/bits/types.h:31: error: storage class specified for parameter ‘__u_char’
/usr/include/bits/types.h:32: error: storage class specified for parameter ‘__u_short’
/usr/include/bits/types.h:33: error: storage class specified for parameter ‘__u_int’


About 70 lines of similar errors.

It looks like there are missing libraries and/or definition files...

Any thoughts?

I am new to Linux, but used to use Unix and C very long ago...think PDP11...

Thanks

Gunnar

---

### Post by taurus on 2009-03-03
Why don't you post your C program to see if there are any syntax errors.

---

### Post by gunnar13 on 2009-03-03
OK, here's the source


main()

#include <stdio.h>

{
	printf("Hello World\n");
}



Thanks,

Gunnar

---

### Post by ken22 on 2009-03-03
#include <stdio.h>

main(){
printf("Hello World\n");
}

---

