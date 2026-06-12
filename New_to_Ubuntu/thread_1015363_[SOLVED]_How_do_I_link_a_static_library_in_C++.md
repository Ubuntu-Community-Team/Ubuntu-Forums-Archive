---
title: "[SOLVED] How do I link a static library in C++?"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by DeathByChocolate on 2008-12-18
This is a really elementary CodeBlocks question.  I made a library function:

    int Add(int a, int b)
    {
        return a+b;
    } 

It compiled it successfully to an ".a" file.  I tried to call it from my main program like this:

    extern int Add(int,int);
    int main()
    {
        int sum = Add( 5, 8 );
    }

In Project-> build options-> linker settings I added a path to the .a library file.

But the compiler complains "undefined reference to 'Add(int, int)'"

What am I doing wrong?

---

### Post by DeathByChocolate on 2008-12-18
The secret seems to be the "C" modifer:

    extern **"C"** int Add(int,int);

This confuses me because both the main program and library function are written in C++.

---

