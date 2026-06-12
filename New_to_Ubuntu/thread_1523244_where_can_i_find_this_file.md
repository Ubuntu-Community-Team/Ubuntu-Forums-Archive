---
title: "where can i find this file ?"
date: 2010-07-03
forum: New to Ubuntu
---

### Post by levis lover on 2010-07-03
hi i am trying to install sonypid but when i use **make** command, i get this error
```

ln -sf /usr/include/linux/sonypi.h
gcc -Wall -Wstrict-prototypes -O2 -pipe -c sonypid.c -o sonypid.o
sonypid.c:35:34: error: X11/extensions/XTest.h: No such file or directory
sonypid.c: In function ‘simulateKeyPress’:
sonypid.c:44: warning: implicit declaration of function ‘XTestGrabControl’
sonypid.c:45: warning: implicit declaration of function ‘XTestFakeKeyEvent’
sonypid.c: In function ‘simulateButton’:
sonypid.c:65: warning: implicit declaration of function ‘XTestFakeButtonEvent’
sonypid.c: In function ‘main’:
sonypid.c:205: warning: missing sentinel in function call
make: *** [sonypid.o] Error 1

```

where can i find XTest.h file ?

---

### Post by Bachstelze on 2010-07-03
You can find which package provides a give file by using the search tool at [http://packages.ubuntu.com](http://packages.ubuntu.com)

In your case it is libxtst-dev, but you'll probably need a lot of other X headers, so just install xorg-dev.

---

### Post by levis lover on 2010-07-03
wow, thanks a lot.. that worked but gave me new errors..
```


 make
ln -sf /usr/include/linux/sonypi.h
gcc -Wall -Wstrict-prototypes -O2 -pipe -c sonypid.c -o sonypid.o
sonypid.c: In function &#8216;main&#8217;:
sonypid.c:205: warning: missing sentinel in function call
gcc  sonypid.o -L/usr/X11R6/lib -lX11 -lXtst -o sonypid

```

---

### Post by mc4man on 2010-07-03
> but gave me new errors..
That's just a  warning  - probably doesn't matter - your build should be done. 



(the warning can be removed, [see here]("http://www.linuxonly.nl/docs/2/2_Sentinel_warning_missing_sentinel_in_function_call.html")

> doug@doug-laptop:~/Downloads/sonypid-1.9.1$ make
ln -sf /usr/include/linux/sonypi.h
gcc -Wall -Wstrict-prototypes -O2 -pipe -c sonypid.c -o sonypid.o
gcc  sonypid.o -L/usr/X11R6/lib -lX11 -lXtst -o sonypid
doug@doug-laptop:~/Downloads/sonypid-1.9.1$

---

