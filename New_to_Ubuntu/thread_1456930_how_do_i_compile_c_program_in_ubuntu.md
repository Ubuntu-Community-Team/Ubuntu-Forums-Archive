---
title: "how do i compile c program in ubuntu"
date: 2010-04-17
forum: New to Ubuntu
---

### Post by tejashs on 2010-04-17
say i have written a c program for checking whether a no is prime or not how do i see the output like i see in turbo c which we use in college

---

### Post by lisati on 2010-04-17
From the terminal, assuming you have typed up your program and saved it in a file, one way is something like this:
```
gcc <name-of-file-with-source-code> -o <name-of-compiled-program>
```
If all goes well and there are no errors, you can then run the program with something like this:
```
./<name-of-compiled-program>
```

You *might* have to install the build-essential package first.

---

### Post by Linuxforall on 2010-04-17
Or you can use GUI interface like Eclipse and Anjuta for Visual Studio like experience.

---

### Post by unixisfreedom on 2010-04-19
Turbo C?  I remember Borland.  Borland rocks :-)  ... Linuxforall, thanks for pointing this out... I tend to associate Eclipse with Java and keep forgetting that Eclipse can be used for other Languages as well...

---

### Post by unixisfreedom on 2010-04-19
Oh... speaking of Borland.. I wanna write a native Ubuntu app... I've been writing little tools in Java cause I'm new and writing native windowed Unix apps in C intimidates me (As if Windows API didn't :-D)... Like what are my options?  Didn't Borland have something like Delphi for Unix like a billion years ago?  Called Kylix or something?  What are people who don't want to mess around with lowlevel APIs using these days to write windowed Unix apps?

---

### Post by unixisfreedom on 2010-04-19
Oh... The first responder's comment "You might have to install the build-essential package first."..

I was able a week ago to compile C code (done only as a test--  I didn't try to run the output) off a brand new Karmic 9.1 install I'm pretty sure using gcc.  I was -NOT- able to compile a C++ app using gcc.  I assume that Ubuntu only comes with 'core' gcc and I need to upgrade mine... I'm a beginner and not sure how to do this... Do I have to be worried about having the same version of the C++ extension as the gcc I have?  and if so, which one do I need for Karmic?

---

### Post by lisati on 2010-04-19
> **unixisfreedom said:**
> Oh... The first responder's comment "You might have to install the build-essential package first."..

I was able a week ago to compile C code (done only as a test--  I didn't try to run the output) off a brand new Karmic 9.1 install I'm pretty sure using gcc.  I was -NOT- able to compile a C++ app using gcc.  I assume that Ubuntu only comes with 'core' gcc and I need to upgrade mine... I'm a beginner and not sure how to do this... Do I have to be worried about having the same version of the C++ extension as the gcc I have?  and if so, which one do I need for Karmic?

For C++, use the g++ compiler instead of gcc.

---

### Post by anewguy on 2010-04-19
If you know C, then for GUI'd apps it's actually easier to me in Linux than in Windows if you just use GTK for the windows and widgets.  I have written some apps using GTK and also installed GTK in Windows (as well as Mingw and MSys) so I actually can compile the same code on either platform with the same result.  It might take a couple of #ifdef in the code in special places so you can use a Windows path for example in place of a Linux path.

Dave ;)

---

