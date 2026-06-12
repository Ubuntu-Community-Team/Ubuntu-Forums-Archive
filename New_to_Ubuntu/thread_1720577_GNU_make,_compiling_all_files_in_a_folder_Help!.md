---
title: "GNU make, compiling all files in a folder? Help!"
date: 2011-04-03
forum: New to Ubuntu
---

### Post by Zombir on 2011-04-03
I've got this folder with lots of C files which I want to compile at once. I'm thinking of writing a GNU Makefile to do this. But the problem is, I don't know how to compile each separately. 

Now I know how to read every C file into the Make 

```

CFILES := $(shell ls | grep .c) 

```

But the problem is, how can I take each file separately and compile. For an example, if the folder contains two files a.c and b.c, they should be compiled into a.o and b.o separately. Plus I don't know the name of the files in the folder when I'm writing the makefile. 

I tried to look up make tutorials and everything but they look rather complicated. Please help!!!

---

### Post by 23dornot23d on 2011-04-03
This link may help ..... [LINK]("http://www.unix.com/shell-programming-scripting/131346-compiling-multiple-c-files-starting-xxx.html")

Another way [LINK]("http://www.commandlinefu.com/commands/view/3230/compile-all-c-files-in-a-directory")

---

### Post by gmargo on 2011-04-03
Here's one way to do it in a makefile, taking advantage of built-in rules:
```

$ ls -lgG
total 16
-rw-r--r-- 1 158 2011-04-03 09:06 Makefile
-rw-r--r-- 1  24 2011-04-03 08:58 one.c
-rw-r--r-- 1  24 2011-04-03 08:59 six.c
-rw-r--r-- 1  24 2011-04-03 08:58 two.c

$ cat Makefile
CFILES := $(wildcard *.c)
OFILES := $(CFILES:%.c=%.o)

test:
        @echo "CFILES=${CFILES}"
        @echo "OFILES=${OFILES}"

compile:        $(OFILES)

clean:
        rm -f $(OFILES)

$ make test
CFILES=one.c six.c two.c
OFILES=one.o six.o two.o

$ make compile
cc    -c -o one.o one.c
cc    -c -o six.o six.c
cc    -c -o two.o two.c

$ ls -lgG *.o
-rw-r--r-- 1 1224 2011-04-03 09:06 one.o
-rw-r--r-- 1 1224 2011-04-03 09:06 six.o
-rw-r--r-- 1 1224 2011-04-03 09:06 two.o

```

---

