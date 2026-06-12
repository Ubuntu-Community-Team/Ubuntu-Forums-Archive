---
title: "lm.h: No such file or directory"
date: 2009-06-16
forum: New to Ubuntu
---

### Post by santhust on 2009-06-16
Hello.
I tried to compile a program using gcc, which had a command 
#include <lm.h>

I suppose that the compiler couldn't find lm.h in usr/include and so reported it.
Now, I have lm.h with me. I would like to know how to put this file in usr/include directory.

A simple copy and paste didn't worked. A pop-up appeared

[B]there was an error copying the files to /usr/include
Error opening file '/usr/include/lm.h': Permission denied
[/B]
I think if I am able to put lm.h in /usr/include this might solve the problem.

Can someone help me please with this problem?

---

### Post by _Purple_ on 2009-06-16
Use sudo to copy files to /usr/include or use the GUI with root privilege
```
gksudo nautilus
```

---

