---
title: "compiling C program written in gedit"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by william_arackal on 2009-03-16
I wrote hello.c in gedit and saved it. When i tried to see the content using cat the out put is

xp@xp-desktop:~$ cat hello.c
cat: hello.c: No such file or directory

when  tried to compile it using gcc the output was

xp@xp-desktop:~$ gcc -o hello ./hello.c
gcc: ./hello.c: No such file or directory
gcc: no input files

but when i did the same program in vi editor it worked.
Why i am not able to compile the program in gedit using gcc?

---

### Post by Berserker v7 on 2009-03-16
Are you sure you saved the file in your home directory? i beleive, gedit by default saves them in the Documents folder within your home.

---

### Post by taurus on 2009-03-16
Here is his original thread, [http://ubuntuforums.org/showthread.php?t=1097081](http://ubuntuforums.org/showthread.php?t=1097081).

---

