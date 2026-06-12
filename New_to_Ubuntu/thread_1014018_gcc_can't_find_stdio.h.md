---
title: "gcc can't find stdio.h"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by seegreen on 2008-12-17
hello.c

#include < stdio.h >

int main()
{    
	printf("\nHello World\n");
	return 0;
}

$ gcc hello.c
hello.c:1:21: error:  stdio.h : No such file or directory
hello.c: In function ‘main’:
hello.c:5: warning: incompatible implicit declaration of built-in function ‘printf’

I have installed build-essential
and I used locate to find all stdio.h

$ locate stdio.h
/usr/include/stdio.h
/usr/include/bits/stdio.h
/usr/include/c++/4.2/tr1/stdio.h
/usr/include/c++/4.3/tr1/stdio.h
/usr/lib/perl/5.10.0/CORE/nostdio.h

Am I doing something completely wrong? How do I get code to compile.

---

### Post by taurus on 2008-12-17
Should there be space between < > and stdio.h?

```
#include <stdio.h>
```
Also, make sure you have installed the build-essential package.

```
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by unutbu on 2008-12-17
Take the spaces out of "< stdio.h >", so it looks like this:
```
#include <stdio.h>
```

---

### Post by rlunger on 2008-12-17
> **seegreen said:**
> hello.c

#include < stdio.h >

int main()
{    
	printf("\nHello World\n");
	return 0;
}

$ gcc hello.c
hello.c:1:21: error:  stdio.h : No such file or directory
hello.c: In function ‘main’:
hello.c:5: warning: incompatible implicit declaration of built-in function ‘printf’

I have installed build-essential
and I used locate to find all stdio.h

$ locate stdio.h
/usr/include/stdio.h
/usr/include/bits/stdio.h
/usr/include/c++/4.2/tr1/stdio.h
/usr/include/c++/4.3/tr1/stdio.h
/usr/lib/perl/5.10.0/CORE/nostdio.h

Am I doing something completely wrong? How do I get code to compile.

Try this: 
    gcc -I /usr/include/ hello.c

---

### Post by seegreen on 2008-12-17
wow. That makes me feel stupid. The spaces were the problem. thanks.

---

