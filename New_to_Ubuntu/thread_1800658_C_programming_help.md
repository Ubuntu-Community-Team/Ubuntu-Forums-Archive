---
title: "C programming help?"
date: 2011-07-09
forum: New to Ubuntu
---

### Post by amiacamal on 2011-07-09
Im having a little problem, im trying to do some C programming to help my cousin, but im missing header files. im using conio.h and programming using geany. when i try to compile it, i get 

    fatal error: conio.h: No such file or directory
my question is... where the hell are they? :) how do i get the other libraries?

---

### Post by matt_symes on 2011-07-09
Hi

conio.h is an old DOS header file.

Kind regards

---

### Post by amiacamal on 2011-07-09
Huh....  so how can i use stuff like getch() etc....?

---

### Post by raja.genupula on 2011-07-09
> **amiacamal said:**
> Im having a little problem, im trying to do some C programming to help my cousin, but im missing header files. im using conio.h and programming using geany. when i try to compile it, i get 

    fatal error: conio.h: No such file or directory
my question is... where the hell are they? :) how do i get the other libraries?


in the options of geany at libraries conio.h library will be there . i am sure it will be . but i dont know the exact location , its in my 10.04 and i am in 11.04 thats the problem . but i am sure man select the conio,h from that library list . then it will works ,.

---

### Post by amiacamal on 2011-07-09
Im using 11.04 myself if that helps at all...

---

### Post by matt_symes on 2011-07-09
Hi

Here is an implementation of conio for linux if you don't have it. It uses ncurses.

[http://sourceforge.net/projects/linux-conioh/](http://sourceforge.net/projects/linux-conioh/)

Kind regards

---

