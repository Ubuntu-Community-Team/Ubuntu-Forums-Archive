---
title: "i want to run my c program"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by kumar.nareshb on 2009-03-02
friends
           i installed ubuntu OS in my 32 bit system.. and i want to do my c programs in this os .  For this is there any           [COLOR="Magenta"][SIZE="4"]**" c compilers"**[/SIZE][/COLOR] in this OS. or any editors available to me.. to do the c programs and run them. and how i run a c program in this Linux...

      Because i don't know abt anything this OS

---

### Post by taurus on 2009-03-02
You need the build-essential package if you want to compile a C program.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install build-essential
gcc -v
```
You can use any text editor to write a C program and then you can compile and run it with

```
gcc program.c
./a.out
```

---

### Post by Vantrax on 2009-03-02
gcc is the standard compiler for linux and will quite happily compile C for you. It should also be already installed.

If you would like a more windows style graphical development environment I recommend Eclipse as a nice starting point.

---

