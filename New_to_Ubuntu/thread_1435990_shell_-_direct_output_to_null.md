---
title: "shell - direct output to null"
date: 2010-03-22
forum: New to Ubuntu
---

### Post by anewguy on 2010-03-22
I know this is simple, and somewhere in the back of my head I already know, but right now I can't remember and I can't find the answer via help, man or searching the net.

In a shell script, I need to execute several copy statements, some rm and rmdir statements, etc., as part of a script to build a program.  I thought in the past I had used redirect to NULL as >> NULL on the end of the cp, rm and rmdir statements, but it's creating a file called NULL instead of just directing the output to the "bit bucket".  

How do I just dump the output of a command?

Thanks in advance!

Dave ;)

---

### Post by mechro on 2010-03-22
It's the null device: **/dev/null**

---

### Post by mcduck on 2010-03-22
The null device on Linux is /dev/null, not NULL. :)
```
command > /dev/null 2>&1
```

---

### Post by anewguy on 2010-03-22
THANK YOU!!!


Dave :)

---

