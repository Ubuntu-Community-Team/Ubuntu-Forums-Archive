---
title: "Makefile error *** No rule to make target"
date: 2009-07-17
forum: New to Ubuntu
---

### Post by Java Geek on 2009-07-17
Hello, I keep getting a makefile error on Kubuntu 9.04.
This is the error code:

```

make: *** No rule to make target `hello.c', needed by `hello.o'.  Stop.

```

The file is named Makefile and the command i'm using is "make".

Here is the makefile:
```

hello:	hello.o
	gcc -o hello hello.o

hello.o:	hello.c
	gcc -0 -c hello.c
	

```

If you can offer assistance please feel free.

---

### Post by sisco311 on 2009-07-17
your source file (hello.c) doesn't exist. ;)

---

### Post by Java Geek on 2009-07-17
> **sisco311 said:**
> your source file (hello.c) doesn't exist. ;)

I'm looking at it. Sitting happily next to Makefile.

---

### Post by sisco311 on 2009-07-17
> **Java Geek said:**
> I'm looking at it. Sitting happily next to Makefile.

are you sure? linux is case sensitive (hello.c != Hello.c).

what's the output of:
```
cat hello.c
cat {M,m}akefile
```

---

### Post by Java Geek on 2009-07-17
> **sisco311 said:**
> are you sure? linux is case sensitive (hello.c != Hello.c).

what's the output of:
```
cat hello.c
cat {M,m}akefile
```

lol...I fixed it...I was being stupid...thanks

---

