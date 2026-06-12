---
title: "getting Error 127 after typing make"
date: 2010-12-09
forum: New to Ubuntu
---

### Post by alexibm on 2010-12-09
Hi !

Recently installed Ubuntu as Virtual machine running on Windows.
I am doing school project, and keep getting an error Error 127 after typing make.

```

alex@ubuntu:~/Desktop/malloclab$ make
/usr/local/bin/gcc -Wall      -c -o mdriver.o mdriver.c
make: /usr/local/bin/gcc: Command not found
make: *** [mdriver.o] Error 127
alex@ubuntu:~/Desktop/malloclab$


```What might be the cause of the problem ? 
Please, let me know if you need any additional information, since I really don't know what to proved.

Thanks !

---

### Post by wt8008 on 2010-12-09
If it is possible, you may want to post your Makefile.

One thing I notice is that your CC=/usr/local/bin/gcc, did you install your own version of gcc there? If you are trying to use the pre-installed version you can set CC=gcc, assuming you have it installed.

The key error to read is:
make: /usr/local/bin/gcc: Command not found
meaning make cannot find the executable /usr/local/bin/gcc

---

