---
title: "C++ complier worked, where do I find out why?"
date: 2009-04-06
forum: New to Ubuntu
---

### Post by audit on 2009-04-06
I am very new and I would like if someone could point me in the direction of some reference material. I just entered the following line of code at the command prompt: sudo aptitude install build-essential 

And for the first time in two days what I wanted to happen did happen--a C++ compiler was installed. I know it worked because I created and ran a "hello world" program. Both the source code with the .cpp extension and the executable program seem to be in the directory where I wanted them to be. 

Now here is my question--where can I find out why it worked,and in particularly how I should be using the g++ compiler.

---

### Post by kanikilu on 2009-04-06
That worked, because as you can see from the package information, build-essential requires g++ as a dependency:

[http://packages.ubuntu.com/intrepid/build-essential](http://packages.ubuntu.com/intrepid/build-essential)

I'm not a programmer, so I can't really tell you how to use it, but the man page would probably be a good first start ```
man g++
```

---

### Post by audit on 2009-04-06
I am new enough that telling me I should read the man page was helpful; thank you. Now I am just hoping for a recommendation for an online resource or a book I can buy that might be g++ specific.

---

### Post by oldos2er on 2009-04-06
[http://gcc.gnu.org/onlinedocs/](http://gcc.gnu.org/onlinedocs/)

---

