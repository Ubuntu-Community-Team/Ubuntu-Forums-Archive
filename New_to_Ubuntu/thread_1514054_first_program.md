---
title: "first program"
date: 2010-06-20
forum: New to Ubuntu
---

### Post by maroofi on 2010-06-20
hi lately i installed linux and i am absolutely begginer...i knew i need g++ to compile c/cpp code.
when i typed g++ in bash it replied : The program 'g++' can be found in the following packages:
 * g++
 * pentium-builder
Try: sudo apt-get install <selected package>

and i installed g++ and pentium-builder like it said. and wrote a hello world program and compile it like this:
g++ hello.cpp -o hello
now i have two question:
1.do i need anything else for programming c/cpp in ubuntu?(i dont mean IDE i mean anything related to compiler or standard library or somethin like that...)
2.i know g++ is a compiler for c++ then what is pentium-builder? and is it necessary for c++ programming and if it is not ,how can i remove it from my system.
thx in advance 
and thx for your great support i feel i am not alone in this way.

by the way i am reading "The Linux Command line by william e.shotts ,Jr." book. any comment?(is it ok? i have download it from sourceforge)

---

### Post by Ozymandias_117 on 2010-06-20
pentium-builder is just supposed to make the resulting code more efficient for your processor. You don't need it. To remove it type ```
sudo aptitude remove pentium-builder
```

---

### Post by gmargo on 2010-06-20
Install the **build-essential **package and you'll have most of what you need for basic development.  As you go on, you'll have to install various "-dev" packages as needed for developing using specialized libraries.

> what is pentium-builder?Use "apt-cache show pentium-builder" or visit the site [http://packages.ubuntu.com/lucid/pentium-builder](http://packages.ubuntu.com/lucid/pentium-builder) or see Properties->Description in Synaptic to find out.

---

### Post by anewguy on 2010-06-20
> **gmargo said:**
> install the **build-essential **package and you'll have most of what you need for basic development.  As you go on, you'll have to install various "-dev" packages as needed for developing using specialized libraries.

+1

---

### Post by maroofi on 2010-06-20
i got it.thanks

---

