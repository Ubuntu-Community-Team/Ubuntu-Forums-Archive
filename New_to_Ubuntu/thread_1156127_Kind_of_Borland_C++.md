---
title: "Kind of Borland C++"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by uki12 on 2009-05-11
hey there:)

um...i'm really beginning to "understand" ubuntu....and..i'd like to rely on...ubuntu only..that is why i have the following question..:

Is there a C++ program like the windows Borland C++...and..something like..builder/complier ...in the same program...i mean..the kind of program that can do just the things that the windows C++ does:)...(i really need this porgram...i really need it at school>:) )

Thanks in advance:)

---

### Post by Didius Falco on 2009-05-11
I'm not a programmer (C++ was my highest grade in math class <G>), but you could have a look at this:

[http://gcc.gnu.org/](http://gcc.gnu.org/)

---

### Post by Alterax on 2009-05-11
Sure is!  The C compiler is the GNU C compiler (which also does C++).  Just use this to get it:
```

sudo apt-get install build-essential
```

The other part you are talking about is called an IDE, short for Integrated Development Environment.  And you have a lot of choices:

Anjuta (good for standard Ubuntu)
Netbeans (May have to add the C++ plugin for it.  Good too)
Kdevelop (haven't worked with it in years)
Eclipse (Again, been a while since I worked with it).

Any of these are available within the repository.  My personal favorites are Anjuta and Netbeans.  That isn't saying that the others are somehow inferior (they aren't), I've just worked with these two more.

---

### Post by gtr32 on 2009-05-11
> **Alterax said:**
> 
Anjuta (good for standard Ubuntu)
Netbeans (May have to add the C++ plugin for it.  Good too)
Kdevelop (haven't worked with it in years)
Eclipse (Again, been a while since I worked with it).


Yes, I think the OP is looking for IDE rather than just a compiler. Here's a few others:

Code::Blocks
Monodevelop

---

