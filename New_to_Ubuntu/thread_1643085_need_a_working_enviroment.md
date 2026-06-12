---
title: "need a working enviroment"
date: 2010-12-11
forum: New to Ubuntu
---

### Post by thierry-le-th on 2010-12-11
i'm new in the use of ubuntu 10.10 camerooneen team.
I'm studying industrial automation and i need to know if on Ubuntu i can have a working environment to compile my c programs like in turbo c and were to write and compile programs for micro-controllers.
tank you in advance for your answer .
I'm new in the Ubuntu world but i already love it,nice job

---

### Post by Spyderkid on 2010-12-11
if you want to be able to compile C++ programs go this:
```

sudo apt-get install build-essential.

```


then just create a file in a folder by right clicking "create new file" then type in the C++ code (save the file with a .cpp on the end)

then go into a terminal and find the file and enter this 
```

g++ example.cpp -o example

```
replace the 'example' with the file name and the second example with what you want it to be called after you compile it

---

### Post by TeoBigusGeekus on 2010-12-11
Linux is essentially C world. A variety of choices for you to choose from:
From straight command line environments to advanced IDEs, I'm sure you can find what you want and suits you.
Micro controllers: either with C or Assembly, I don't think you'll face any problems.

---

### Post by Spyderkid on 2010-12-11
Also you can install *CodeLite* from the software centre for writing and compiling C and C++ code (which would be easier)

---

