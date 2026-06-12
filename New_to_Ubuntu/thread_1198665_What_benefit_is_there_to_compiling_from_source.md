---
title: "What benefit is there to compiling from source?"
date: 2009-06-27
forum: New to Ubuntu
---

### Post by l-x-l on 2009-06-27
I'm still consider myself a linux noob so here's a noob question.

I see apps for Linux that allow to compile from source as opposed to simply providing a .deb or .rpm. Is there a benefit to this? Does the software get optimized for your hardware when you compile from source?

---

### Post by philcamlin on 2009-06-27
you can customize it the way you want :D

---

### Post by MasterProg on 2009-06-27
You can also check that the code is free from viruses, if you are really paranoid.

---

### Post by l-x-l on 2009-06-27
> **philcamlin said:**
> you can customize it the way you want :D

Doesn't that entail a lot of work? Basically you're trying to reverse engineer what the programmer did & figuring out where (or if) there's anything to customize.

---

### Post by ymra on 2009-06-27
The only real advantage to installing from sourcecode is portability. sourcecode can be used on any disto.

---

### Post by SunnyRabbiera on 2009-06-27
Well the advantage of source code is that it can be compiled to fit your system better then a pre made .deb or .rpm package.
It also helps those interested in programming understand how a application works and behaves.
But the compiling itself can be discouraging, you need quite a few packages to get it started and learning how to run the commands can be a little rough.
But these days the source code isnt as needed as it used to be, almost everything has a .deb or .rpm.

---

### Post by Mark Phelps on 2009-06-29
Unless you're really interested in the source code, the primary advantage is that the source version is always the most current.  Takes time and effort to build packages ... which the package builders don't always have.  Source is always there, and the time and effort is entirely yours.

But ... as has been said, it can involve a LOT of work.  Recently, I wanted the latest version of a Linux app I use every day, so I downloaded the source.  Even though I had previously install build-essentials on my box, I still had to spend an entire morning downloading and installing other packages and libraries in order to do the makes on the new source.

---

### Post by LowSky on 2009-06-29
depending on what your compiling from source it could actually run faster than a precompiled program. this is because the program/driver will be optimised for your machine

---

### Post by binbash on 2009-06-29
It may run faster or slower.This depends on what you included at configure progress.Best advantage of compiling is 

1- You do not rely on any packager, so you can get the software faster
2- You can customize it.For example , pulse audio support for mplayer, alsa support etc
3 - It may run faster

---

