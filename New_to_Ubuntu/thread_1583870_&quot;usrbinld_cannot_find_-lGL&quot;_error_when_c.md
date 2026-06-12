---
title: "&quot;/usr/bin/ld: cannot find -lGL&quot; error when compiling a file"
date: 2010-09-28
forum: New to Ubuntu
---

### Post by Mearis on 2010-09-28
I am compiling a C++ (cytosim, an academic simulator) and somehow I always get this mistake.  I googled for the error messages and found a few people having similar problems, apparently due to linking mistakes.  I tried to follow the example given in the various forums and creating a 'link' to the correct library, but it isn't working at all.

Typing:

ls -l /usr/lib/libGL*

Gives me:

lrwxrwxrwx 1 root root     24 2010-09-28 16:33 /usr/lib/libGL.so -> /usr/lib/mesa/libGL.so.1
-rw-r--r-- 1 root root 716290 2010-04-29 07:43 /usr/lib/libGLU.a
lrwxrwxrwx 1 root root     11 2010-09-28 16:28 /usr/lib/libGLU.so -> libGLU.so.1
lrwxrwxrwx 1 root root     20 2010-09-28 16:21 /usr/lib/libGLU.so.1 -> libGLU.so.1.3.070701
-rw-r--r-- 1 root root 456380 2010-04-29 07:43 /usr/lib/libGLU.so.1.3.070701
federicov@federicov-laptop:~/cytosim$ ls -l /usr/lib/libGL*
lrwxrwxrwx 1 root root     24 2010-09-28 16:33 /usr/lib/libGL.so -> /usr/lib/mesa/libGL.so.1
-rw-r--r-- 1 root root 716290 2010-04-29 07:43 /usr/lib/libGLU.a
lrwxrwxrwx 1 root root     11 2010-09-28 16:28 /usr/lib/libGLU.so -> libGLU.so.1
lrwxrwxrwx 1 root root     20 2010-09-28 16:21 /usr/lib/libGLU.so.1 -> libGLU.so.1.3.070701
-rw-r--r-- 1 root root 456380 2010-04-29 07:43 /usr/lib/libGLU.so.1.3.070701

Any advice is welcome, I might be missing something very trivial, I just started using Ubuntu.

---

### Post by Mearis on 2010-09-28
Solved it in a really weird way - removing a -STATIC flag in the makefile somehow allowed the linkage to work.

Oh well!

---

