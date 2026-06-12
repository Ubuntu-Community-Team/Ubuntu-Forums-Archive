---
title: "How to compile a C program from terminal?"
date: 2010-01-14
forum: New to Ubuntu
---

### Post by Sandeepkumar on 2010-01-14
I heard that there's an inbuilt compiler in ubuntu ... so how do i utilise it???:P

---

### Post by lorsen on 2010-01-14
```
gcc program.c 
``` gives you an executable file a.out

```
gcc program.cpp -o program.out 
``` gives you an executable file programm.out
there is also g++ for C++

Of course you need the required packages installed.

Have a look at: [http://www.ubuntugeek.com/how-to-install-c-and-c-compilers-in-ubuntu-and-testing-your-first-c-and-c-program.html](http://www.ubuntugeek.com/how-to-install-c-and-c-compilers-in-ubuntu-and-testing-your-first-c-and-c-program.html)

---

### Post by muteXe on 2010-01-14
and then it's 
```
./a.out
```

or, if you've called it something else

```
./program.out
```

in the folder you've compiled to run that program.

---

### Post by anand_30 on 2010-01-14
Thank you lorsen & muteXe  I was also searching for such information.
Sorry to jump in but can anyone tell me how one can use header file conio.h in gcc?
I have heard something of ncurses but how to get that?Or is there any alternative for conio.h?

---

### Post by lorsen on 2010-01-14
I never heard of conio.h before, but have a look at:
[http://en.wikipedia.org/wiki/Conio.h](http://en.wikipedia.org/wiki/Conio.h)
[http://www.daniweb.com/forums/thread17584.html#](http://www.daniweb.com/forums/thread17584.html#)
[http://www.tldp.org/HOWTO/NCURSES-Programming-HOWTO/](http://www.tldp.org/HOWTO/NCURSES-Programming-HOWTO/)
Maybe this helps you.

Otherwise it would be interesting what you are planning to do in order to give you suggestions.

---

### Post by EssexEagle on 2010-01-14
> **muteXe said:**
> and then it's 
```
./a.out
```

or, if you've called it something else

```
./program.out
```

in the folder you've compiled to run that program.

I believe you have to make the file executable first:

```
chmod +x program.out
```

---

### Post by muteXe on 2010-01-14
yeah maybe. I never had to when i used to do this stuff, but that was on unix boxes.  Might check at home tonight.
I'm a scummy .net coder by day now :(

---

