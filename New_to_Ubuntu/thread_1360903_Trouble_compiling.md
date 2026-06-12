---
title: "Trouble compiling"
date: 2009-12-21
forum: New to Ubuntu
---

### Post by Extract_Here on 2009-12-21
I'm trying to compile a program

it says in the install readme that I should 

./configure

make && make install

when i type ./configure it gives me a error no such file or directory 

then when I change the directory to desktop it says the same thing.

Thanks in advance.

---

### Post by lukeiamyourfather on 2009-12-21
That script should be run in the directory where the source is (there's literally a script called configure that should exist with the source). Sometimes the file is there but its not executable so you might have to make it executable with chmod. Cheers!

---

### Post by nishant.singh28 on 2009-12-21
Check whether you actually are in the source code directory or not.......it happened with me the first time I compiled from source code....:D

---

### Post by Extract_Here on 2009-12-21
how do I get in the source code directory

---

### Post by lukeiamyourfather on 2009-12-21
> **Extract_Here said:**
> how do I get in the source code directory

Maybe you should do some more research before diving in. Here are a few good articles.

[http://www.tuxfiles.org/linuxhelp/linuxfiles.html](http://www.tuxfiles.org/linuxhelp/linuxfiles.html)
[http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html)
[http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)

Note from the Linux directories article that its a good practice to keep source code for user installed applications in the /usr/local/src directory. By the way, what are you trying to install? Is there not already a package for it in the repositories? Cheers!

---

