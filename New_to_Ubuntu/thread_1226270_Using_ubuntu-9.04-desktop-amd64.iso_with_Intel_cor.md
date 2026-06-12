---
title: "Using ubuntu-9.04-desktop-amd64.iso with Intel core"
date: 2009-07-29
forum: New to Ubuntu
---

### Post by hitekwaiter on 2009-07-29
I only see one 64 bit os on the website and it is labled AMD. I have an intel core 2 duo, can I install it safely?

---

### Post by philinux on 2009-07-29
Ignore the amd bit. It's fine.

---

### Post by ikt on 2009-07-29
> **hitekwaiter said:**
> I only see one 64 bit os on the website and it is labled AMD. I have an intel core 2 duo, can I install it safely?

yes, just as you can use i(intel)386 on amd cpus.

amd64 refers to the fact that it will install a 64 bit version of the linux software, where as i386 will install the 32 bit version.

If your cpu is 64bit compatible there is really no reason why you shouldn't use the 64 bit version.

---

### Post by philinux on 2009-07-29
The reason it is called AMD64 is because AMD was the first company to come out with 64 bit processors for consumers.

The iso file is so named. They dont seem to want to change the name either.

---

### Post by ikt on 2009-07-29
> **philinux said:**
> The reason it is called AMD64 is because AMD was the first company to come out with 64 bit processors for consumers.

It's called amd64 because Intel and AMD both use the 64 bit instruction set named amd64.

AMD came up with it, and intel licenses it from them.

---

### Post by jerome1232 on 2009-07-29
Which is so named because amd developed the x86_64 architecture. Therefore his initial statement is correct.

---

### Post by ikt on 2009-07-29
> **jerome1232 said:**
> Which is so named because amd developed the x86_64 architecture. Therefore his initial statement is correct.

Actually I wonder why it isn't called x86_64 to imply compatibility between intel and amd 64.

>     * Debian, Ubuntu, and Gentoo refer to both AMD64 and Intel 64 under the architecture name "amd64".

    * Fedora PackageKit, openSUSE, and Arch Linux refers to 64-bit architecture as "x86_64".

[http://en.wikipedia.org/wiki/Amd64#Industry_naming_conventions](http://en.wikipedia.org/wiki/Amd64#Industry_naming_conventions)

---

### Post by jerome1232 on 2009-07-29
> **ikt said:**
> Actually I wonder why it isn't called x86_64 to imply compatibility between intel and amd 64.



[http://en.wikipedia.org/wiki/Amd64#Industry_naming_conventions](http://en.wikipedia.org/wiki/Amd64#Industry_naming_conventions)

It would clear up some confusion for some, people don't get confused by the Intel branding on 32 bit though, i386 = Intel 386.

/shrug lol.

---

### Post by hitekwaiter on 2009-07-29
So, it seems this is the one I want and not the 32 bit edition. Thank you all. I've been using he 32 bit and wondering why i was not getting better performance.

---

### Post by gn2 on 2009-07-29
> **hitekwaiter said:**
> I've been using he 32 bit and wondering why i was not getting better performance.

64 won't make a huge difference, just in CPU intensive tasks like encoding where tasks will complete faster.
In general use you will not see any difference.

---

### Post by MichealH on 2009-07-29
Ubuntu 9.04 works on my computer:

Packard Bell MX
intel Celeron (Dual Core)
1.5GB RAM
101GB HDD but has 2 partitions which i set up:
one 81GB
Ubuntu partiton = 20 GB

---

### Post by jerome1232 on 2009-07-29
> **gn2 said:**
> 64 won't make a huge difference, just in CPU intensive tasks like encoding where tasks will complete faster.
In general use you will not see any difference.

This, but encoding goes ALOT faster on my 64 bit Linux vs 32 bit Windows, both using handbrake.

---

