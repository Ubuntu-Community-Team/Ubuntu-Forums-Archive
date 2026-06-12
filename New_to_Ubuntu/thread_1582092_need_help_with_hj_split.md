---
title: "need help with hj split"
date: 2010-09-26
forum: New to Ubuntu
---

### Post by afbkb on 2010-09-26
:confused:

1. how do you join hj split file in ubuntu?

2. is there a specific software for  linux in windows?

all help is much appreciated.

---

### Post by papibe on 2010-09-26
I don't know how hjsplit works, but if it just "splits" the files you may be able to join them using:
```
$ cat file.* > file
```
Be careful since 'file' it is overwritten.

Regards.

---

### Post by Hendronicus on 2010-09-26
There is a Java version of HJSplit. You start it in a terminal with a command like :

java -jar hjsplit_g.jar

Or right click on the jar file and choose Open with > your_version_of_java

It then runs graphically just like any other version. I've had good use out of it.

There is also a command line program called lxsplit. I don't know if it's in the repos or not though.

All versions can be found at

[www.freebyte.com/hjsplit](www.freebyte.com/hjsplit)

There's a bunch of choices there. I suppose if you wanted Windows compatibility for other things as well, you could install Wine and run the Windows version. It's kind of "round the tree" but that works, too.

---

### Post by JohnHeikkila on 2010-09-26
And an target link:
[http://www.freebyte.com/hjsplit/#linux](http://www.freebyte.com/hjsplit/#linux)

lxSplit should do the same trick but it doesn't have the GTK or "visual frontend".

---

