---
title: "How to compile and Run C progs in Eclipse"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by atish.sihi on 2009-05-09
Hi ..

I've been using the gcc compiler so now I know how to compile and run C programs.

Right now I've installed the eclipse-cdt plugin and I'm trying to run the "hello world" C program to test it.

But I am not able to compile and run.

I got the make file also:

main : main.o
g++ -o main main.o -L C:/MinGW/lib/gcc-lib/mingw32/3.2.3/ -lstdc++
main.o : main.c
g++ -ggdb -c main.c
all :
${MAKE} main
clean :
-del main.o

But I am not sure how to use it properly.
Kindly help me.

Regards,
Atish Sihi

---

### Post by smudi on 2009-05-09
Paste your errors please

---

### Post by atish.sihi on 2009-05-09
While running the program what to write in C/C++ application field.
For example while running in windows we use progname.exe but in linux we can't execute exe file. So for linux I don't know what to write for the same field.
Kindly help me.

---

### Post by smudi on 2009-05-09
Are you using eclipse on ubuntu or on windows?

---

### Post by atish.sihi on 2009-05-09
I am using Eclipse in Ubuntu 8.04 hardy heron

---

### Post by smudi on 2009-05-09
Eclipse automagically puts the name of the executable in the C/C++ application field.
For 'HelloWorld' application it can be:
/Debug/HelloWorld (for debug configuration)
/Release/HelloWorld (for release configuration)

Both are actually executable files. You can look into the Debug or Release directory in your project directory and see this file.
Linux does not coerce file extensions like Windows.

Under terminal you can execute the file as follows:
$ cd /<your Debug or Release project directory>
$ ./HelloWorld

---

### Post by atish.sihi on 2009-05-09
I had tried but it's not working or may be I am not able to it properly.

Can you please tell me stepwise after writing the code in the Eclipse editor what exactly I need to Do.

Thanks
Atish

---

