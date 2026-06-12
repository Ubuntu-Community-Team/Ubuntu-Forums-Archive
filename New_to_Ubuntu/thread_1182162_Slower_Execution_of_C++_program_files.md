---
title: "Slower Execution of C++ program files"
date: 2009-06-08
forum: New to Ubuntu
---

### Post by allenbradley on 2009-06-08
I have a bunch of C++ code that is highly computationally intensive. When I compile the same code in Windows using Bloodshed DevC++, it runs on Windows really fast, and finishes computation in 3 minutes. On Linux, when compiled and executed with g++, it takes close to 15 minutes! This is not a processor issue as well ( Ubuntu is sitting on a better processor, in fact ). Conky/ps aux shows the process taking 50% of the proessor. What should I do? Am I compiling wrong?

---

### Post by durand on 2009-06-08
Try compiling with multiple threads. I don't know about g++ but if you use make, you can use make -j 3 (or more).

---

### Post by allenbradley on 2009-06-08
Thanks for the quick reply :). I don't use make, and I'm not too familiar with the concept as well. I have over 1000+ lines of code, and no particular mood to recast the code :(. I was thinking along the lines of increasing processor share to the process ie increase priority or something. Is that possible?

---

### Post by HavocXphere on 2009-06-08
> **allenbradley said:**
> Conky/ps aux shows the process taking 50% of the proessor.
Yeah, that sounds like its only using one core (You've got a dual core right?)

Is it using 100% on windows?

---

### Post by allenbradley on 2009-06-08
70%, methinks. But I can see via Task Manager that both cores are being used.

---

### Post by durand on 2009-06-08
Make is widely used in linux to build big programs. I think that it's fairly easy to set up so you might want to give it a try. You don't need to change any code. Try the [programming forums]("http://ubuntuforums.org/forumdisplay.php?f=44") for more help. Programs normally run high priority anyway.

---

### Post by lisati on 2009-06-08
This is just a random musing from someone who spotted this thread but without necessarily having much (if anything) to contribute: I'm wondering if an 32-bit or 64-bit OS would make a difference.

---

### Post by durand on 2009-06-08
> **lisati said:**
> This is just a random musing from someone who spotted this thread but without necessarily having much (if anything) to contribute: I'm wondering if an 32-bit or 64-bit OS would make a difference.

It would but probably not a 500% difference as between ubuntu and windows.

---

### Post by unknownPoster on 2009-06-08
Although I doubt it makes a huge difference in this case, different compilers optimize code differently.

---

### Post by allenbradley on 2009-06-08
@durand : I'll definitely give it a try. Could you guide me to some simple intro to make? I've been trying to google it but the links i see assume you are familiar with the concept.
@lisati : I don't think so either.
@unknownPoster : DevC++ uses gcc, the same as linux.

---

### Post by durand on 2009-06-08
Uh sorry, I'm not a programmer and that was just knowledge I picked up. Just ask in those forums!

---

### Post by durand on 2009-06-08
What are you using to build programs anyway, if not something like make?

---

### Post by allenbradley on 2009-06-08
Sure, no problem. Anyways, thanks for the link. I'll be sure to check the forum out.

---

### Post by allenbradley on 2009-06-08
g++ <filename> -o <file>
./<file>

---

### Post by ibuclaw on 2009-06-08
> **allenbradley said:**
> g++ <filename> -o <file>
./<file>

```
g++ -O3 <filename> -i <file>
```
Will rigorously optimise the code...

Although the **-O2** switch should be sufficient.

Regards
Iain

---

### Post by durand on 2009-06-08
> **allenbradley said:**
> g++ <filename> -o <file>
./<file>

I thought you said that you had lots of files?

---

### Post by allenbradley on 2009-06-10
@durand I include the files in the program ie #include "file"

---

### Post by allenbradley on 2009-06-10
@tinivole I'll try it out now and post back in a few minutes

---

### Post by allenbradley on 2009-06-10
@tinivole Still doesn't do the trick. The code till executes quite slowly.

---

